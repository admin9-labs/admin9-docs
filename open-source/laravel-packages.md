---
title: Laravel Packages
description: Reusable Laravel packages published by Admin9 Labs.
---

# Laravel Packages

Admin9 Labs also publishes reusable Laravel packages that can be adopted independently of the full starter repositories.

## Identity and authentication

### laravel-oidc-client

- Repository: [`admin9-labs/laravel-oidc-client`](https://github.com/admin9-labs/laravel-oidc-client)
- Primary language: PHP
- License: MIT

This package implements an OpenID Connect client for Laravel with Authorization Code Flow and PKCE. It is the fit when your Laravel application needs to authenticate against an external identity provider with standard OIDC flows.

### laravel-oidc-server

- Repository: [`admin9-labs/laravel-oidc-server`](https://github.com/admin9-labs/laravel-oidc-server)
- Primary language: PHP
- License: MIT

This package adds OpenID Connect server capabilities to Laravel Passport deployments, including discovery and supporting endpoints such as JWKS, UserInfo, token introspection, token revocation, and RP-initiated logout.

## UI and developer experience

### blade-daisyui

- Repository: [`admin9-labs/blade-daisyui`](https://github.com/admin9-labs/blade-daisyui)
- Primary language: Blade
- License: MIT

This package provides Laravel-friendly Blade wrappers around DaisyUI 5 components, which is useful for teams that want reusable UI primitives without building custom Blade components from scratch.

### laravel-scramble-extensions

- Repository: [`admin9-labs/laravel-scramble-extensions`](https://github.com/admin9-labs/laravel-scramble-extensions)
- Primary language: PHP
- License: MIT

This package extends Scramble-based API documentation workflows for business-response APIs. The public description highlights:

- response envelope generation
- scene-based form request extraction
- filter query parameter extraction

## Documentation recommendation

At the current organization size, grouping packages together on one page is the right tradeoff:

- the navigation stays compact
- users can compare related packages quickly
- you can later split individual packages into dedicated pages if installation guides or API references become larger
