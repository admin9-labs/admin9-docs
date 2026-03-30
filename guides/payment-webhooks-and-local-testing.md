---
title: Payment Webhooks and Local Testing
description: How to test payment webhooks locally in ADMIN9 using Stripe CLI and ngrok-backed workflows.
---

If local billing work depends on provider callbacks, this is the workflow reference you want.

## Current webhook routes

ADMIN9 currently exposes:

- `/api/payments-providers/stripe/webhook`
- `/api/payments-providers/paddle/webhook`
- `/api/payments-providers/lemon-squeezy/webhook`

These paths should be treated as release-sensitive integration points.

## Stripe local workflow

The most direct local workflow is to use the Stripe CLI to forward events to your local application.

Example:

```bash
stripe listen --forward-to localhost:8080/api/payments-providers/stripe/webhook --skip-verify
```

Adjust the host and port if your app is not running on `localhost:8080`.

## Paddle and Lemon Squeezy local workflow

The repository already ships a Docker Compose setup with an `ngrok` service. Use it to expose local webhook endpoints for providers that need a public callback URL.

Relevant environment variables from `.env.example`:

```env
NGROK_AUTHTOKEN=
NGROK_STATIC_DOMAIN=
FORWARD_NGROK_PORT=4040
```

Typical workflow:

1. configure ngrok credentials
2. start the Docker Compose stack
3. open the ngrok inspector
4. point the provider's sandbox webhook destination at the forwarded public URL

## What to verify during local testing

- webhook delivery reaches the expected route
- signature validation succeeds
- transaction records update correctly
- subscription or order state changes are persisted
- related side effects still work with your queue configuration

## Common failure modes

- wrong local port
- provider dashboard still pointing at an old ngrok domain
- wrong webhook secret
- queue workers not running when the side effect depends on queued jobs
- long-lived cached config after changing provider credentials

## Recommended test matrix

Before release, simulate at least:

- successful checkout
- failed payment
- subscription renewal or equivalent recurring event
- refund or cancellation flow if the provider supports it in your launch scope

## Team rule

Do not merge billing changes without replaying at least one real or sandbox webhook through the current local stack.
