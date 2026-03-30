---
title: OAuth Providers
description: Admin-side management of social login providers and release checks for provider callbacks.
---

# OAuth Providers

ADMIN9 includes an `Oauth Login Providers` resource for managing social login availability.

## Supported providers

The current admin-side provider settings pages cover:

- Google
- GitHub
- Facebook
- Twitter OAuth 2
- LinkedIn
- Bitbucket
- GitLab

These match the public route constraints used by the authentication controller.

## Public auth routes

Social login currently uses:

- `/auth/{provider}/redirect`
- `/auth/{provider}/callback`

If a provider is enabled in admin but not properly configured in the provider console or environment, the user flow will fail at redirect or callback time.

## What operators should manage

- which providers are visible to users
- whether a provider is actually approved for production use
- whether callback URLs are aligned with the deployed domain
- whether branding and legal requirements have been completed in the upstream provider dashboard

## Configuration alignment

The deployment environment must match the enabled provider list.

Examples from `.env.example` include:

- `GOOGLE_CLIENT_ID`
- `GOOGLE_CLIENT_SECRET`
- `GITHUB_CLIENT_ID`
- `GITHUB_CLIENT_SECRET`
- `FACEBOOK_CLIENT_ID`
- `FACEBOOK_CLIENT_SECRET`

There are also provider-specific entries in `config/services.php`, including Twitter OAuth 2 callback configuration.

## Pre-launch checks

- disable any provider you are not ready to support publicly
- verify redirect URI registration in each provider console
- verify successful account creation for first-time users
- verify successful login for returning users
- verify email handling when a provider does not return the expected user profile fields

## Operator note

Only enable providers that have been tested end-to-end in the target environment. Social login issues are highly visible during launch and usually caused by callback mismatch or incomplete provider-app setup.
