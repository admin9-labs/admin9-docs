---
title: Admin9 Labs Documentation
description: Organization-level entry point for Admin9 Labs product docs, product variants, and open source repositories.
---

Start here to choose the right Admin9 Labs documentation path before jumping into product setup, admin operations, or repository exploration.

## Pick your path

<CardGroup cols={2}>
  <Card title="Admin9 variants" href="/products/admin9-variants">
    Compare the single-tenant `admin9` product with the multi-tenant `admin9-tenancy` variant and see which docs are shared.
  </Card>
  <Card title="Shared product docs" href="/getting-started/installation">
    Use the Admin9 docs for installation, architecture, guides, admin operations, and release work shared by both variants.
  </Card>
  <Card title="Tenancy supplement" href="/guides/admin9-tenancy">
    Read the multi-tenant addendum when tenant scoping, provisioning, or tenant-level operations matter.
  </Card>
  <Card title="Open source portfolio" href="/open-source/overview">
    Explore the public repositories, starters, and reusable packages maintained by Admin9 Labs.
  </Card>
</CardGroup>

## Documentation structure

This site is organized by documentation type:

- product docs for product positioning and variant boundaries
- usage docs for installation, development, architecture, reference, and release workflows
- admin docs for operator-facing panel workflows
- open source docs for public repositories and reusable packages

Within the product docs, `admin9` is the single-tenant variant and `admin9-tenancy` is the multi-tenant variant. Most pages are shared; multi-tenant-only differences are collected in the tenancy supplement.

## What the Admin9 product docs cover

- launch a subscription SaaS with an admin panel and user dashboard
- manage products, plans, pricing, discounts, invoices, and transactions
- support Stripe, Paddle, Lemon Squeezy, or offline payment flows
- ship authentication, verification, and social login flows for customer-facing products
- ship localized, themeable frontend pages with built-in operational tooling

## Fast path

<CardGroup cols={2}>
  <Card title="Review variants" href="/products/admin9-variants">
    Decide whether you are working in the single-tenant or multi-tenant product before applying the shared guides.
  </Card>
  <Card title="Install the product" href="/getting-started/installation">
    Set up the shared Admin9 stack from source with the current Laravel, Livewire, and Filament stack.
  </Card>
  <Card title="Run locally" href="/getting-started/local-development">
    Bring up MySQL, Redis, Vite, queues, and the main application surfaces.
  </Card>
  <Card title="Read tenancy notes" href="/guides/admin9-tenancy">
    Apply the multi-tenant differences where tenant boundaries affect architecture or operations.
  </Card>
</CardGroup>

## Current stack

The current codebase depends on:

- PHP 8.2+
- Laravel 12
- Livewire 4
- Filament 5
- Tailwind CSS 4
- DaisyUI 5
- Vite 7
- Laravel Sanctum for API tokens
- Laravel Horizon for Redis-backed queues

## What the shared Admin9 platform includes

- Admin panel at `/admin` for product, content, revenue, and settings management
- User dashboard at `/dashboard`
- Subscription checkout and one-time purchase checkout
- Stripe, Paddle, Lemon Squeezy, and offline payment flows
- OAuth social login providers
- Two-factor authentication
- Role and permission management
- Blog, roadmap, announcement, FAQ, and legal page support
- Multi-language frontend routing with localized URLs
- Theme switching with DaisyUI themes and Filament synchronization

## Recommended reading order

1. Start with [Admin9 Product Variants](/products/admin9-variants) to identify whether you are working on the single-tenant or multi-tenant product.
2. Continue with [Installation](/getting-started/installation) and [Local Development](/getting-started/local-development).
3. Read [Architecture Overview](/architecture/overview) and the shared guides.
4. If you are on `admin9-tenancy`, add [Admin9 Tenancy Supplement](/guides/admin9-tenancy) anywhere tenant concerns affect the implementation.
5. Use [Commands and Endpoints](/reference/commands-and-endpoints) and [Release Checklist](/deployment/release-checklist) before shipping.

If you work primarily in `/admin`, switch to the [Admin Overview](/admin-guide/overview) after the installation flow.

If you are reviewing the public repository portfolio rather than deploying an Admin9 product, switch to [Open Source Overview](/open-source/overview).

## Core guides

- [Authentication and Identity](/guides/authentication-and-identity)
- [Payments and Billing](/guides/payments-and-billing)
- [Localization and Theming](/guides/localization-and-theming)
- [Configuration System](/guides/configuration-system)
- [Payment Webhooks and Local Testing](/guides/payment-webhooks-and-local-testing)
- [Events and Extension Points](/guides/events-and-extension-points)

If prose and product behavior ever disagree, treat the relevant product repository as authoritative.
