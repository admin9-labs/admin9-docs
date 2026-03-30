---
title: Launch Runbook
description: Operator-focused first-release runbook for ADMIN9 before opening the product to external users.
---

Use this runbook to coordinate the final admin-side checks before opening a new ADMIN9 deployment to external users.

## When to use this runbook

Use this page when:

- you are preparing the first public launch of a deployment
- you need a final cross-functional review across admin settings, content, and infrastructure
- you want a single release checklist that links operator tasks together

## Scope of this runbook

This runbook assumes:

- core implementation work is already complete
- provider credentials are available or about to be applied
- operators are validating readiness, not designing features from scratch

## 1. Freeze scope

Before the release window:

- stop adding non-critical features
- identify the single payment provider or provider set you will support at launch
- identify the social login providers you will support at launch
- define who owns production credentials and rollback decisions

## 2. Finalize admin configuration

In `/admin`, review:

- products and plans
- one-time products if enabled
- discounts
- payment providers
- email providers
- OAuth providers
- verification providers
- general settings
- legal pages settings
- invoice settings
- referral settings
- Open Graph settings

## 3. Finalize public content

Verify:

- homepage copy and links
- FAQ content
- blog content if used for launch
- roadmap visibility
- announcements
- terms of service
- privacy policy

## 4. Validate critical user flows

Test with a production-like environment:

- registration
- email verification
- social login
- 2FA if enabled
- subscription checkout
- one-time purchase checkout
- payment webhook delivery
- invoice generation
- dashboard access
- admin access

## 5. Validate infrastructure

- database backups are configured
- Redis is running if queues depend on it
- Horizon or queue workers are running
- mail delivery is verified
- HTTPS is enforced
- public callback URLs are correct

## 6. Validate observability

- logs are accessible
- failed jobs are monitored
- payment failures can be diagnosed
- support staff know where to inspect users, subscriptions, orders, and transactions

## 7. Go-live decision

Only publish when:

- launch-critical flows all pass
- provider credentials are confirmed
- legal content is ready
- no placeholder branding remains
- owners agree on support coverage for the first launch window

## Related guides

- [Products and Pricing](/admin-guide/products-and-pricing)
- [Payment Providers](/admin-guide/payment-providers)
- [Users and Access](/admin-guide/users-and-access)
- [Support Playbook](/admin-guide/support-playbook)
- [Content and Site Settings](/admin-guide/content-and-site-settings)
- [Settings Matrix](/admin-guide/settings-matrix)
