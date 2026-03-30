---
title: Feature Systems
description: Practical notes on the main cross-cutting features developers are likely to configure or extend.
---

This page gives you the cross-cutting platform view before you narrow down into a single feature area.

## Applies to

This feature overview is shared by:

- `admin9`
- `admin9-tenancy`

Use it as the default baseline, then layer in [Admin9 Tenancy Supplement](/guides/admin9-tenancy) if a feature becomes tenant-aware in the multi-tenant product.

## Filament panels

ADMIN9 ships two Filament panels:

- admin panel at `/admin`
- customer dashboard at `/dashboard`

The panel providers also define:

- panel-specific colors
- middleware stacks
- user menu actions
- discovered resources, pages, and widgets

In `admin9-tenancy`, also verify whether panel access, panel navigation, and panel data queries are tenant-scoped.

## Theme switching

The application supports DaisyUI theme switching and synchronizes that theme state with Filament dark mode behavior.

Key characteristics documented in the codebase:

- theme persistence through local storage
- `data-theme` on the root HTML element
- brand-oriented ADMIN9 color palette centered on `#f53003`

When making frontend changes, keep the public site and Filament styling behavior aligned.

## Localization

Localization is powered by `mcamara/laravel-localization`.

Expected routing behavior:

- default locale hidden in URLs
- non-default locales prefixed, for example `/zh/about`

There is already an internal note in the main project docs about hiding the default locale in URLs. If this behavior regresses, inspect `config/laravellocalization.php` first.

## Authentication and verification

The application supports:

- classic email/password auth
- social login redirects and callbacks
- email verification
- phone verification
- two-factor authentication
- API token support through Sanctum

Notable route areas:

- `/auth/{provider}/redirect`
- `/auth/{provider}/callback`
- `/email/verify`
- `/phone/verify`

The default route list does not expose `/oauth/*` authorization-server routes. Verify any OAuth2 / OIDC provider behavior in the deployment you are working with before relying on it.

## Payments and checkout

The commerce layer supports:

- subscription checkout
- subscription plan changes
- local subscription conversion
- one-time product purchases
- balance top-up flows
- provider-specific payment links and webhooks

Review these layers together when debugging billing:

- checkout controllers
- services under `app/Services`
- webhook controllers
- transaction and invoice services

For `admin9-tenancy`, verify whether billing ownership lives at platform scope, tenant scope, or both.

## Content systems

The codebase includes first-party support for:

- blog
- roadmap
- announcements
- FAQs
- legal pages

These are useful both as shipped features and as examples of how ADMIN9 models editable content.

## Extension rule of thumb

When adding a new system, prefer extending an existing pattern already present in the application rather than introducing a parallel architecture. ADMIN9 already has recognizable conventions for services, providers, Filament resources, Livewire components, and domain events.
