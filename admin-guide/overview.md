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

## When to use this section

Use the admin guide when you need to:

- understand which operational tasks happen in `/admin`
- find the right page for a launch or support workflow
- separate operator responsibilities from developer implementation details

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

## How this guide is organized

The admin guide is grouped by operator workflow rather than by code structure:

- `Start Here` for orientation, launch preparation, and settings discovery
- `Catalog & Revenue` for products, billing, invoices, and referrals
- `Users & Access` for roles, login providers, verification, and support triage
- `Content & Site Operations` for public content, legal copy, branding, and analytics
- `Integrations` for cross-provider navigation and email delivery setup

## Recommended reading order

### 1. Start Here

- [Overview](./overview.md) for the operating map of the admin panel
- [Launch Runbook](./launch-runbook.md) for first-release preparation
- [Settings Matrix](./settings-matrix.md) for a quick map of standalone settings pages

### 2. Catalog and revenue operations

- [Products and Pricing](./products-and-pricing.md) for catalog, plans, discounts, and billing entities
- [Subscriptions and Transactions](./subscriptions-and-transactions.md) for day-to-day billing operations and audit trails
- [Payment Providers](./payment-providers.md) for Stripe, Paddle, and Lemon Squeezy setup
- [Invoice Settings](./invoice-settings.md) for invoice generation and seller metadata
- [Referral Settings](./referral-settings.md) if referrals are part of the commercial launch

### 3. Users, access, and support

- [Users and Access](./users-and-access.md) for roles, permissions, and admin boundaries
- [OAuth Providers](./oauth-providers.md) for social login operations
- [Verification Providers](./verification-providers.md) for SMS verification and trial gating
- [Support Playbook](./support-playbook.md) for issue triage after launch

### 4. Content and site operations

- [Content and Site Settings](./content-and-site-settings.md) for the high-level content surface
- [Content Operations](./content-operations.md) for blog, FAQ, announcements, and roadmap workflows
- [Legal Pages and Compliance](./legal-pages-and-compliance.md) for Terms, Privacy, and launch sign-off
- [General Settings](./general-settings.md) for site-wide behavior, analytics, social links, and reCAPTCHA
- [Analytics and Open Graph](./analytics-and-open-graph.md) for tracking and social preview validation

### 5. Integrations overview

- [Providers and Integrations](./providers-and-integrations.md) for the cross-provider map
- [Email Providers](./email-providers.md) for mail delivery configuration and validation

## If you are unsure where to start

- start with [Launch Runbook](./launch-runbook.md) if you are preparing a release
- start with [Support Playbook](./support-playbook.md) if you are handling a live customer issue
- start with [Settings Matrix](./settings-matrix.md) if you know the task is in a settings page but not which one

## Audience boundary

This admin guide explains what operators do in the panel. For implementation details, extension points, and code structure, use the developer sections under Architecture and Guides.
