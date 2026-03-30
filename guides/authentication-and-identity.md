---
title: Authentication and Identity
description: Authentication, social login, verification flows, two-factor auth, and token-related behavior in the shared Admin9 stack.
---

Authentication changes should start here whenever they touch login, verification, identity state, or token behavior.

## Applies to

This identity guide is shared by:

- `admin9`
- `admin9-tenancy`

For `admin9-tenancy`, add [Admin9 Tenancy Supplement](/guides/admin9-tenancy) when login boundaries, tenant membership, or tenant-scoped access rules affect the flow.

## Main auth building blocks

- Laravel authentication routes through `Auth::routes()`
- email verification with `MustVerifyEmail`
- social login through Laravel Socialite
- two-factor authentication through `laragear/two-factor`
- API token support through Sanctum

## User model capabilities

The `User` model implements:

- Filament panel access
- email verification
- role and permission assignment
- one-time passwords
- two-factor authentication

This makes the user model the center of both back-office access and customer authentication flows.

## Social login

The public web routes expose:

- `/auth/{provider}/redirect`
- `/auth/{provider}/callback`

The current allowed providers are:

- Google
- GitHub
- Facebook
- Twitter OAuth 2
- LinkedIn OpenID
- Bitbucket
- GitLab

The callback controller persists provider-related metadata onto the user record as config-style values, including provider id, token, refresh token, avatar, nickname, and expiry data when available.

## Email and phone verification

The web layer includes:

- email verification notice and signed verification link flow
- phone verification routes and dedicated verification views

Before release, verify that your registration flow, post-registration redirect behavior, and any verification gating rules match product expectations.

## Two-factor authentication

Two-factor support is exposed in the customer dashboard Filament panel.

Relevant dashboard pages include:

- `TwoFactorAuth`
- `EnableTwoFactorAuth`
- `ConfirmTwoFactorAuth`
- `RecoveryCodes`

The dashboard panel only exposes the 2FA menu item when `config('app.two_factor_auth_enabled')` is enabled.

## OIDC-related configuration note

The current repository includes an `OIDC_ISSUER` environment variable in `.env.example`, but the default route list does not expose `/oauth/*` authorization-server endpoints and `composer.json` does not directly require `laravel/passport`.

Treat OAuth2 / OpenID Connect provider behavior as something to verify in the specific application deployment before documenting it as a shipped capability.

## Operational checklist

- verify login and logout
- verify email verification
- verify each enabled social provider end-to-end
- verify 2FA enrollment and recovery codes
- verify admin access rules separately from dashboard access rules
- verify any external identity-provider integration only after confirming the deployed app actually exposes the required endpoints

For `admin9-tenancy`, also verify how users are associated with tenants and whether authentication redirects preserve the intended tenant context.
