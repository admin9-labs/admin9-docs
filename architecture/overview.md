---
title: Architecture Overview
description: High-level mental model for ADMIN9, including panels, services, events, and user-facing flows.
---

# Architecture Overview

ADMIN9 is a monolithic Laravel application with a clear service-layer bias and two main Filament surfaces.

## Runtime surfaces

### Public web application

The web layer provides:

- marketing pages
- authentication and verification flows
- subscription checkout
- one-time product checkout
- blog and roadmap pages
- invoice generation and preview

These routes are defined primarily in `routes/web.php`.

### Admin panel

The admin panel is registered by `App\Providers\Filament\AdminPanelProvider` and lives at:

```text
/admin
```

It is the operational surface for revenue, product, user, content, roadmap, and settings management.

### User dashboard

The user dashboard is registered by `App\Providers\Filament\DashboardPanelProvider` and lives at:

```text
/dashboard
```

It contains the customer-facing account area, subscription operations, referrals, balance management, and profile features.

## Architectural patterns

### Service layer

Most business logic is organized under `app/Services`. This keeps controllers, Livewire components, and Filament resources relatively thin.

Key examples:

- `CheckoutService`
- `SubscriptionService`
- `OrderService`
- `InvoiceService`
- `MetricsService`
- `TransactionService`
- `UserService`
- `ConfigService`
- `PaymentService`

### Event-driven side effects

Domain events are grouped by concern under `app/Events`, with listeners under `app/Listeners`.

Current event areas include:

- balance
- order
- referral
- subscription
- user

This is the right extension point for notifications, bookkeeping, and non-blocking side effects.

For practical customization guidance, read [Events and Extension Points](../guides/events-and-extension-points.md).

### Provider abstraction

Payment providers and verification providers are implemented behind interfaces. This keeps provider-specific SDK logic out of the rest of the application.

Notable abstractions:

- `PaymentProviderInterface`
- `VerificationProviderInterface`
- `BalanceTopupProviderInterface`

## Main platform capabilities

### Commerce

- subscription billing
- one-time purchases
- discounts and discount codes
- invoices
- transactions
- balance top-ups

### Identity and access

- Laravel auth scaffolding
- email verification
- phone verification
- social login
- two-factor authentication
- OAuth2 / OIDC provider support through Passport
- roles and permissions through Spatie Permission

### Content and engagement

- blog
- roadmap
- announcements
- FAQs
- legal pages

### Product presentation

- DaisyUI theme switching
- localized URLs
- SEO and sitemap support

## Version note

Some older project documents still describe Livewire 3 and Filament 4. The current codebase dependencies indicate Livewire 4 and Filament 5. Treat the package manifest as the authoritative version reference.
