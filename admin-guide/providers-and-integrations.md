---
title: Providers and Integrations
description: Admin-side setup areas for payment, email, OAuth, and verification providers.
---

# Providers and Integrations

ADMIN9 exposes several provider systems directly in the admin panel so operators can manage integrations without code changes.

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

## Verification providers

The panel includes a `Verification Providers` resource with Twilio settings support.

Use this section when phone verification or SMS-gated trials are part of your release plan.

## Operator guidance

Keep an internal runbook that documents:

- which settings live in `.env`
- which settings live in the admin panel
- who owns credential rotation
- how webhook changes are tested before production rollout
