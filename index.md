---
title: Overview
description: Install, develop, operate, and reference Admin9.
---

## Directory

<CardGroup cols={2}>
  <Card title="Install Admin9" href="/getting-started/installation">
    Install the project and get it running.
  </Card>
  <Card title="Local Development" href="/getting-started/local-development">
    Daily commands and local environment notes.
  </Card>
  <Card title="Admin Docs" href="/admin-guide/overview">
    Common `/admin` tasks and settings.
  </Card>
  <Card title="Open Source" href="/open-source/overview">
    Public repositories and starters.
  </Card>
</CardGroup>

## Stack

- PHP 8.2+
- Laravel 12
- Livewire 4
- Filament 5
- Tailwind CSS 4
- DaisyUI 5
- Vite 7
- Laravel Sanctum for API tokens
- Laravel Horizon for Redis-backed queues

## Reading Order

1. Read [Installation](/getting-started/installation) and [Local Development](/getting-started/local-development).
2. Read [Architecture](/architecture/overview).
3. Then read [Commands and Endpoints](/reference/commands-and-endpoints) and [Release Checklist](/deployment/release-checklist).

If you work mainly in `/admin`, go to [Admin Overview](/admin-guide/overview).

If you mainly care about repositories, go to [Open Source](/open-source/overview).

## Other Pages

- [Authentication and Identity](/guides/authentication-and-identity)
- [Payments and Billing](/guides/payments-and-billing)
- [Localization and Theming](/guides/localization-and-theming)
- [Configuration System](/guides/configuration-system)
- [Payment Webhooks and Local Testing](/guides/payment-webhooks-and-local-testing)
- [Events and Extension Points](/guides/events-and-extension-points)

If prose and product behavior ever disagree, treat the relevant product repository as authoritative.
