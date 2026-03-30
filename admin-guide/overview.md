---
title: Admin Overview
description: Operational map of the ADMIN9 admin panel for operators, product managers, and maintainers.
---

Treat this as the map for `/admin` when you need to place an operational task before diving into a narrower guide.

The ADMIN9 admin panel is mounted at:

```text
/admin
```

This section is written for operators and maintainers who manage the application through Filament rather than through code.

## When to use this section

Use the admin guide when you need to:

- understand which operational tasks happen in `/admin`
- find the right page for a launch or support workflow
- separate operator responsibilities from developer implementation details

## Start from your task

<CardGroup cols={2}>
  <Card title="Prepare a launch" href="/admin-guide/launch-runbook">
    Review the release-critical checks for billing, content, access, infrastructure, and support readiness.
  </Card>
  <Card title="Find the right settings page" href="/admin-guide/settings-matrix">
    Use the settings map when you know the task belongs in `/admin` but not which page owns it.
  </Card>
  <Card title="Manage catalog and billing" href="/admin-guide/products-and-pricing">
    Jump into products, plans, transactions, providers, invoices, and referral configuration.
  </Card>
  <Card title="Handle users and support" href="/admin-guide/support-playbook">
    Start with the support workflow for live issue triage, access boundaries, and verification problems.
  </Card>
</CardGroup>

## What the admin panel covers

The admin panel supports:

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
- `Integrations` for provider setup and email delivery configuration

## Recommended reading order

### 1. Start Here

- [Overview](/admin-guide/overview) for the operating map of the admin panel
- [Launch Runbook](/admin-guide/launch-runbook) for first-release preparation
- [Settings Matrix](/admin-guide/settings-matrix) for a quick map of standalone settings pages

### 2. Catalog and revenue operations

- [Products and Pricing](/admin-guide/products-and-pricing) for catalog, plans, discounts, and billing entities
- [Subscriptions and Transactions](/admin-guide/subscriptions-and-transactions) for day-to-day billing operations and audit trails
- [Payment Providers](/admin-guide/payment-providers) for Stripe, Paddle, and Lemon Squeezy setup
- [Invoice Settings](/admin-guide/invoice-settings) for invoice generation and seller metadata
- [Referral Settings](/admin-guide/referral-settings) if referrals are part of the commercial launch

### 3. Users, access, and support

- [Users and Access](/admin-guide/users-and-access) for roles, permissions, and admin boundaries
- [OAuth Providers](/admin-guide/oauth-providers) for social login operations
- [Verification Providers](/admin-guide/verification-providers) for SMS verification and trial gating
- [Support Playbook](/admin-guide/support-playbook) for issue triage after launch

### 4. Content and site operations

- [Content and Site Settings](/admin-guide/content-and-site-settings) for the high-level content surface
- [Content Operations](/admin-guide/content-operations) for blog, FAQ, announcements, and roadmap workflows
- [Legal Pages and Compliance](/admin-guide/legal-pages-and-compliance) for Terms, Privacy, and launch sign-off
- [General Settings](/admin-guide/general-settings) for site-wide behavior, analytics, social links, and reCAPTCHA
- [Analytics and Open Graph](/admin-guide/analytics-and-open-graph) for tracking and social preview validation

### 5. Integrations overview

- [Providers and Integrations](/admin-guide/providers-and-integrations) for payment, email, OAuth, and verification setup
- [Email Providers](/admin-guide/email-providers) for mail delivery configuration and validation

## If you are unsure where to start

- start with [Launch Runbook](/admin-guide/launch-runbook) if you are preparing a release
- start with [Support Playbook](/admin-guide/support-playbook) if you are handling a live customer issue
- start with [Settings Matrix](/admin-guide/settings-matrix) if you know the task is in a settings page but not which one

## Audience boundary

This admin guide explains what operators do in the panel. For implementation details, extension points, and code structure, use the developer sections under Architecture and Guides.
