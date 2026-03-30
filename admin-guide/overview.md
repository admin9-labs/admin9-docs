---
title: Admin Overview
description: Operational map of the ADMIN9 admin panel for operators, product managers, and maintainers.
---

# Admin Overview

The ADMIN9 admin panel is the operational control surface for the product. It is mounted at:

```text
/admin
```

This section is written for operators and maintainers who manage the application through Filament rather than through code.

## What the admin panel covers

Based on the current Filament resources and pages, the admin panel supports:

- revenue monitoring and SaaS metrics
- product and plan management
- one-time product management
- discounts and discount codes
- subscriptions, transactions, orders, balances, and balance transactions
- user and role management
- blog, announcements, FAQs, and roadmap items
- payment provider, email provider, OAuth provider, and verification provider setup
- legal, invoice, referral, and Open Graph settings

## Main navigation groups

The panel provider defines these top-level groups:

- Revenue
- Product Management
- User Management
- Content
- Roadmap
- Settings

These groups reflect the intended operating model of the product.

## Related admin pages

The admin panel also includes several standalone settings pages:

- Dashboard
- General Settings
- Invoice Settings
- Legal Pages Settings
- Open Graph Image Settings
- Referral Settings

## How to use this section

1. Read [Products and Pricing](./products-and-pricing.md) for catalog and billing setup.
2. Read [Subscriptions and Transactions](./subscriptions-and-transactions.md) for billing operations, support workflows, and transaction review.
3. Read [Providers and Integrations](./providers-and-integrations.md) for the provider landscape across payments, email, OAuth, and verification.
4. Use [Payment Providers](./payment-providers.md), [Email Providers](./email-providers.md), and [OAuth Providers](./oauth-providers.md) for provider-specific setup guidance.
5. Use [Verification Providers](./verification-providers.md) when SMS verification or trial gating is part of launch scope.
6. Read [Users and Access](./users-and-access.md) for user, role, and permission operations.
7. Use [Support Playbook](./support-playbook.md) for day-to-day user issue triage after launch.
8. Read [Content and Site Settings](./content-and-site-settings.md), [Content Operations](./content-operations.md), and [Legal Pages and Compliance](./legal-pages-and-compliance.md) for public content and settings management.
9. Review [Settings Matrix](./settings-matrix.md), [General Settings](./general-settings.md), [Invoice Settings](./invoice-settings.md), [Referral Settings](./referral-settings.md), and [Analytics and Open Graph](./analytics-and-open-graph.md) before launch.
10. Use [Launch Runbook](./launch-runbook.md) for first-release operational preparation.

## Audience boundary

This admin guide explains what operators do in the panel. For implementation details, extension points, and code structure, use the developer sections under Architecture and Guides.
