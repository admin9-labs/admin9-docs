---
title: Open Source Overview
description: Public open source projects maintained by Admin9 Labs and how they fit together.
---

# Open Source Overview

Admin9 Labs maintains a small but focused set of public repositories around Laravel SaaS infrastructure, OpenID Connect, frontend starters, and developer tooling.

This section gives you a stable map of the public projects linked from the `admin9-labs` GitHub organization.

## How to use this section

- Start here if you want to understand which repositories are products, reusable packages, or support infrastructure.
- Use [Application Starters](./application-starters.md) if you are evaluating full starter kits or reference apps.
- Use [Laravel Packages](./laravel-packages.md) if you want reusable packages for auth, OIDC, UI, or API documentation.

This tab is intentionally separate from the main ADMIN9 implementation docs so product documentation and organization discovery do not compete for the same navigation space.

## Portfolio map

<CardGroup cols={2}>
  <Card title="Application Starters" href="/open-source/application-starters">
    Full repositories you can clone and extend, including API, web, and documentation surfaces.
  </Card>
  <Card title="Laravel Packages" href="/open-source/laravel-packages">
    Reusable packages for OpenID Connect, DaisyUI Blade components, and Scramble extensions.
  </Card>
</CardGroup>

## Repository map

### Product and starter repositories

- [`admin9-api`](https://github.com/admin9-labs/admin9-api): Laravel 12 REST API scaffold with JWT auth, RBAC, service-layer structure, audit events, and tests.
- [`admin9-web`](https://github.com/admin9-labs/admin9-web): Vue-based frontend SPA starter intended to pair with `admin9-api`.
- [`admin9-docs`](https://github.com/admin9-labs/admin9-docs): Mintlify documentation source for the ADMIN9 documentation site.

### Laravel packages

- [`laravel-oidc-client`](https://github.com/admin9-labs/laravel-oidc-client): OIDC client package for Laravel with Authorization Code Flow and PKCE.
- [`laravel-oidc-server`](https://github.com/admin9-labs/laravel-oidc-server): OIDC server package built for Laravel Passport deployments.
- [`laravel-scramble-extensions`](https://github.com/admin9-labs/laravel-scramble-extensions): OpenAPI documentation helpers for business-response APIs.
- [`blade-daisyui`](https://github.com/admin9-labs/blade-daisyui): Blade wrapper components for DaisyUI 5.

### Organization infrastructure

- [`.github`](https://github.com/admin9-labs/.github): Shared organization profile and GitHub-level metadata.

## How this section is intended to work

- use this tab as the portfolio index for repositories that do not yet need their own standalone documentation site
- keep product-level ADMIN9 documentation in the main docs tabs so implementation guidance stays separate from organization discovery
- link out to package-specific or project-specific docs when an individual repository grows beyond overview-level coverage
