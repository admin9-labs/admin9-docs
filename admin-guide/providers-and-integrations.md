---
title: Providers and Integrations
description: Admin-side setup areas for payment, email, OAuth, and verification providers.
---

Use this page to route a task to the right provider family in `/admin`.

## Payment providers

The admin panel contains a `Payment Providers` resource with provider-specific settings pages for:

- Stripe
- Paddle
- Lemon Squeezy

Use this area to:

- enable or disable providers
- review provider records
- configure provider-specific settings pages
- align panel configuration with the values present in `.env`

Before going live:

- verify API credentials
- verify webhook secrets
- verify sandbox versus production mode
- verify end-to-end checkout behavior for each enabled provider

See also: [Payment Providers](/admin-guide/payment-providers)

## Email providers

The panel includes an `Email Providers` resource with dedicated settings pages for:

- SMTP
- Mailgun
- Postmark
- Amazon SES
- Resend

This area should match your actual delivery strategy and DNS setup.

Before release:

- verify sender identity
- verify outbound delivery
- verify template rendering for critical emails

See also: [Email Providers](/admin-guide/email-providers)

## OAuth login providers

The panel includes an `Oauth Login Providers` resource with settings pages for:

- Google
- GitHub
- Facebook
- Twitter OAuth 2
- LinkedIn
- Bitbucket
- GitLab

Use this section to control which social providers are available on the public authentication screens.

Before release:

- verify enabled providers match your policy
- verify callback URLs
- verify branding and app approval requirements on each provider platform

See also: [OAuth Providers](/admin-guide/oauth-providers)

## Verification providers

The panel includes a `Verification Providers` resource with Twilio settings support.

Use this section when phone verification or SMS-gated trials are part of your release plan.

See also: [Verification Providers](/admin-guide/verification-providers)

## Operator guidance

Keep an internal runbook that documents:

- which settings live in `.env`
- which settings live in the admin panel
- who owns credential rotation
- how webhook changes are tested before production rollout

## Usage order

1. Identify the provider family.
2. Open the provider-specific page for field-level setup and validation steps.
3. Record the final production values in the launch runbook or internal credential inventory.
