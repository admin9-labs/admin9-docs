---
title: Open Source Overview
description: Public open source projects maintained by Admin9 Labs and how they fit together.
---

# Open Source Overview

Admin9 Labs maintains a small but focused set of public repositories around Laravel SaaS infrastructure, OpenID Connect, frontend starters, and developer tooling.

This section gives you a map of the public projects that were visible on the `admin9-labs` GitHub organization as of 2026-03-30.

## How to use this section

- Start here if you want to understand which repositories are products, reusable packages, or support infrastructure.
- Use [Application Starters](./application-starters.md) if you are evaluating full starter kits or reference apps.
- Use [Laravel Packages](./laravel-packages.md) if you want reusable packages for auth, OIDC, UI, or API documentation.

## Portfolio map

<CardGroup cols={2}>
  <Card title="Application Starters" href="/open-source/application-starters">
    Full repositories you can clone and extend, including API, web, and documentation surfaces.
  </Card>
  <Card title="Laravel Packages" href="/open-source/laravel-packages">
    Reusable packages for OpenID Connect, DaisyUI Blade components, and Scramble extensions.
  </Card>
</CardGroup>

## Current public repositories

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

## Recommended navigation model

If this docs site is becoming the canonical documentation hub for the organization, a dedicated `Open Source` tab is the right structure:

- it separates product documentation from organization portfolio content
- it gives external visitors a direct path to public repositories
- it avoids mixing package discovery into the ADMIN9 product docs navigation

If later you publish package-specific docs sites, this tab can stay as the portfolio index and link out to each package's canonical documentation.
