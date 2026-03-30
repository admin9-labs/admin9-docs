---
title: Release Checklist
description: Pre-release checks for shipping ADMIN9 safely and with complete developer-facing documentation.
---

# Release Checklist

Use this checklist before tagging or deploying a release.

## 1. Validate environment configuration

- Confirm `APP_URL` matches the real public domain
- Confirm database, cache, session, and queue drivers are production-safe
- Confirm Redis is available if Horizon or queued jobs are expected
- Confirm mail provider credentials are valid
- Confirm payment provider credentials and webhook secrets are configured
- Confirm social login credentials and callback URLs are correct
- If your deployment adds identity-provider features beyond the default route set, confirm any related issuer and authorization-server settings explicitly

## 2. Validate operational features

- Log into `/admin`
- Log into `/dashboard`
- Verify product, plan, currency, and provider seed data or production data exists
- Verify legal pages render
- Verify blog and roadmap routes resolve
- Verify invoice generation works

## 3. Validate critical flows

- Registration
- Email verification
- Social login
- Subscription checkout
- One-time product checkout
- Plan change flow
- Balance top-up flow if enabled
- Webhook handling for the enabled payment provider

## 4. Validate platform integrations

- Queue workers or Horizon
- Mail delivery
- reCAPTCHA where enabled
- Twilio verification where enabled
- Analytics scripts where enabled
- localized routes
- theme switching

## 5. Run quality gates

```bash
vendor/bin/phpunit
vendor/bin/phpstan analyse
vendor/bin/pint
npm run build
```

If you deploy with Deployer, also validate the target hosts and deployment configuration before executing:

```bash
php dep deploy
```

## 6. Validate documentation completeness

Before release, make sure the external docs site covers:

- installation
- environment setup
- architecture overview
- payments
- auth and OAuth/OIDC
- localization
- deployment
- release notes or upgrade notes for breaking changes

## 7. Call out known mismatches

If older prose or internal notes still reference outdated framework versions, resolve those mismatches before publishing public-facing documentation.
