---
title: Configuration System
description: How ADMIN9 overrides runtime configuration through the admin panel, database-backed settings, and cached config values.
---

# Configuration System

ADMIN9 uses a configuration override system layered on top of Laravel's normal config files and environment variables.

At a high level:

- baseline values come from `config/*.php` and `.env`
- selected settings can be overridden from the admin panel
- overridden values are stored in the database
- runtime reads are cached so the application does not hit the database on every request

This is one of the most important architectural ideas in the project because many admin settings pages rely on it.

## Why it exists

This system allows operators to change production-facing behavior without redeploying the application for every settings change.

Typical examples include:

- email provider credentials
- invoice metadata
- legal page content
- provider-specific settings
- site-level behavior exposed through admin pages

## Main pieces

The key components referenced by the codebase are:

- `App\Services\ConfigService`
- `App\Models\Config`
- `App\Constants\ConfigConstants`

These work together to:

- decide which keys are overridable
- persist values to the database
- encrypt sensitive settings where required
- cache resolved values for runtime use

## Operational model

When an operator changes a setting in Filament:

1. a settings page or Livewire form calls `ConfigService::set(...)`
2. the value is validated against the list of allowed overridable keys
3. the value is written to the `configs` table
4. the cached runtime value is refreshed

This means many settings become effective immediately without a code deploy.

## Security model

Not every config key should be editable from the admin panel.

The project uses an allowlist model through `ConfigConstants` so only intended keys can be changed. Sensitive values are handled separately through encrypted config definitions.

This is the correct pattern. Do not turn the settings system into a generic write-any-config mechanism.

## Developer extension pattern

If you want to expose a new setting in admin:

1. define the config key in the appropriate Laravel config file
2. add the key to the allowed overridable config list
3. mark it as encrypted if it contains a secret
4. expose it through a Filament page or Livewire form
5. read it through Laravel's config helper in the application code

## Operational risks

- clearing cache without repopulating settings can create confusing runtime behavior
- long-lived workers may continue using older resolved config until restarted
- admin-side credentials can drift away from `.env` if the team does not define a clear source of truth

## Recommended team rule

For every configurable concern, document whether the source of truth is:

- `.env`
- admin-managed settings
- or a hybrid bootstrapping model where `.env` seeds the initial value and admin owns changes afterward

Without that clarity, production debugging becomes slow.
