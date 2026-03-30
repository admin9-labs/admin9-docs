---
title: Overview
description: Developer-focused introduction to the ADMIN9 codebase, platform capabilities, and documentation map.
---

# ADMIN9 Overview

ADMIN9 is a Laravel-based SaaS starter kit for teams that want to ship subscription products without building the standard commercial stack from scratch.

This documentation is written for developers, operators, and maintainers working from the current codebase. It focuses on implementation, operations, and release readiness rather than marketing copy.

## Pick your path

<CardGroup cols={2}>
  <Card title="Developer setup" href="/getting-started/installation">
    Install ADMIN9, run the local stack, and verify the main application surfaces.
  </Card>
  <Card title="Operator workflows" href="/admin-guide/overview">
    Use the Admin Guide for launch prep, settings ownership, and day-to-day panel operations.
  </Card>
  <Card title="Release validation" href="/deployment/release-checklist">
    Run the pre-release checks for configuration, billing, auth, content, and quality gates.
  </Card>
  <Card title="Open source portfolio" href="/open-source/overview">
    See how ADMIN9 relates to the broader Admin9 Labs repositories and reusable packages.
  </Card>
</CardGroup>

Use the cards above if you already know your role. If you are evaluating the product itself, continue with the overview below and then branch into the section that matches your workflow.

## What you can do with this codebase

- launch a subscription SaaS with an admin panel and user dashboard
- manage products, plans, pricing, discounts, invoices, and transactions
- support Stripe, Paddle, Lemon Squeezy, or offline payment flows
- ship authentication, verification, and social login flows for customer-facing products
- ship localized, themeable frontend pages with built-in operational tooling

## Fast path

<CardGroup cols={2}>
  <Card title="Install the project" href="/getting-started/installation">
    Set up ADMIN9 from source with the current Laravel, Livewire, and Filament stack.
  </Card>
  <Card title="Run locally" href="/getting-started/local-development">
    Bring up MySQL, Redis, Vite, queues, and the main application surfaces.
  </Card>
  <Card title="Understand the architecture" href="/architecture/overview">
    Learn how the panels, services, events, and provider abstractions fit together.
  </Card>
  <Card title="Prepare for release" href="/deployment/release-checklist">
    Validate configuration, billing flows, auth flows, and release quality gates.
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

## What ADMIN9 already includes

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

## Read this documentation in order

1. Start with [Installation](./getting-started/installation.md) if you need a fresh environment.
2. Continue with [Local Development](./getting-started/local-development.md) for daily workflow.
3. Read [Architecture Overview](./architecture/overview.md) to understand the main subsystems.
4. Use [Configuration](./guides/configuration.md) and [Feature Systems](./guides/feature-systems.md) when enabling or extending specific capabilities.
5. Use [Commands and Endpoints](./reference/commands-and-endpoints.md) and [Release Checklist](./deployment/release-checklist.md) before shipping.

If you work primarily in `/admin`, switch to the [Admin Overview](./admin-guide/overview.md) after the installation flow.

If you are reviewing the open source portfolio rather than deploying ADMIN9 itself, switch to [Open Source Overview](./open-source/overview.md) instead of continuing through the developer setup path.

## Core guides

- [Authentication and Identity](./guides/authentication-and-identity.md)
- [Payments and Billing](./guides/payments-and-billing.md)
- [Localization and Theming](./guides/localization-and-theming.md)
- [Configuration System](./guides/configuration-system.md)
- [Payment Webhooks and Local Testing](./guides/payment-webhooks-and-local-testing.md)
- [Events and Extension Points](./guides/events-and-extension-points.md)

## Source of truth

For product behavior and version-sensitive details, treat these files in the main `admin9` application repository as the source of truth:

- `admin9/composer.json` for PHP and backend package versions
- `admin9/package.json` for frontend tooling versions
- `admin9/routes/*.php` for public and API endpoints
- `admin9/app/Providers/Filament/*PanelProvider.php` for panel paths and panel behavior
- `admin9/.env.example` for documented environment variables

If the repository changes, update the docs from those files first. If prose and code disagree, treat the codebase as authoritative.
