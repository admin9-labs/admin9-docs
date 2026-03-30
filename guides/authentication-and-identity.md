---
title: Authentication and Identity
description: Authentication, social login, two-factor auth, and OAuth2 / OIDC behavior in ADMIN9.
---

# Authentication and Identity

ADMIN9 includes several identity-related layers: Laravel session auth, social login, email and phone verification, two-factor authentication, and OAuth2 / OpenID Connect provider capabilities.

## Main auth building blocks

- Laravel authentication routes through `Auth::routes()`
- email verification with `MustVerifyEmail`
- social login through Laravel Socialite
- two-factor authentication through `laragear/two-factor`
- OAuth2 provider flows through Laravel Passport
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

## OAuth2 / OpenID Connect provider role

The project documentation and environment file indicate that ADMIN9 can act as an OAuth2 / OpenID Connect provider.

Important points:

- Passport supplies `/oauth/*` endpoints
- `OIDC_ISSUER` defaults to `APP_URL`
- PKCE support is part of the intended external client flow

When deploying ADMIN9 as an identity provider:

- ensure `APP_URL` is the public canonical URL
- ensure `OIDC_ISSUER` is correct
- validate HTTPS and callback URLs carefully
- test authorization code and token flows with a real client

## Operational checklist

- verify login and logout
- verify email verification
- verify each enabled social provider end-to-end
- verify 2FA enrollment and recovery codes
- verify admin access rules separately from dashboard access rules
- verify OAuth2 client integration if ADMIN9 is serving external apps
