---
title: Testing and Quality
description: Test execution, static analysis, formatting, and quality expectations for ADMIN9.
---

Before merge or release, this page is the fast reference for the checks that keep the codebase healthy.

## Main commands

Run the application test suite:

```bash
vendor/bin/phpunit
```

Run static analysis:

```bash
vendor/bin/phpstan analyse
```

Run formatting:

```bash
vendor/bin/pint
```

Format or check frontend-oriented source files:

```bash
npm run format
npm run format:check
```

## Build verification

Before release, also run:

```bash
npm run build
```

This catches asset-pipeline issues that do not appear during normal PHP-only checks.

## Testing environment notes

The repository includes `.env.testing`, and the broader Laravel workflow assumes test runs should not share the same database as daily development.

Recommended practice:

- keep a separate testing database
- make sure `.env.testing` points to it
- do not run destructive test flows against your normal local database

## What to test first

For this codebase, prioritize tests around:

- checkout flows
- payment webhooks
- subscription lifecycle changes
- authentication and verification flows
- provider-specific integrations that are enabled for the release

The visible test suite already covers legal pages, referrals, balance handling, top-up flows, and several core services. Webhook-specific and auth-provider regressions still deserve explicit release testing because they are easier to miss.

## Release minimum

A practical first-release quality bar is:

- `vendor/bin/phpunit`
- `vendor/bin/phpstan analyse`
- `vendor/bin/pint`
- `npm run build`

If one of these fails, treat the release as not ready.
