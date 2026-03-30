---
title: Payment Providers
description: Admin-side setup and operational checks for Stripe, Paddle, and Lemon Squeezy.
---

Use this guide when payment routing, credentials, or provider readiness needs to be checked from the admin side.

## Supported providers

The admin resource includes dedicated settings pages for:

- Stripe
- Paddle
- Lemon Squeezy

Offline payment support exists at the application level, but the provider-specific admin settings pages currently focus on the hosted providers above.

## What operators should manage here

- enable or disable a provider
- review provider records
- confirm provider-specific configuration is complete
- align admin-side state with the environment variables configured for the deployment

## Environment variables to validate

### Stripe

```env
STRIPE_SECRET_KEY=""
STRIPE_PUBLISHABLE_KEY=""
STRIPE_WEBHOOK_SIGNING_SECRET=""
```

### Paddle

```env
PADDLE_VENDOR_ID=""
PADDLE_CLIENT_SIDE_TOKEN=""
PADDLE_VENDOR_AUTH_CODE=""
PADDLE_PUBLIC_KEY=""
PADDLE_WEBHOOK_SECRET=""
PADDLE_IS_SANDBOX=true
```

### Lemon Squeezy

```env
LEMON_SQUEEZY_API_KEY=""
LEMON_SQUEEZY_STORE_ID=""
LEMON_SQUEEZY_SIGNING_SECRET=""
LEMON_SQUEEZY_IS_TEST_MODE=false
```

## Operational checks

Before launch, verify for each enabled provider:

- credentials are valid
- sandbox versus production mode is correct
- webhook secret is configured
- provider-specific products or plan mappings exist
- successful checkout returns to the expected success route
- failed or cancelled states behave as expected

## Webhooks

The webhook endpoints are:

- `/api/payments-providers/stripe/webhook`
- `/api/payments-providers/paddle/webhook`
- `/api/payments-providers/lemon-squeezy/webhook`

When changing domains or environments, update provider dashboards so webhook delivery still targets the correct public URL.

## Launch recommendation

Avoid enabling multiple providers in production unless you have tested all downstream behaviors, including checkout, webhook delivery, invoice generation, and transaction recording.
