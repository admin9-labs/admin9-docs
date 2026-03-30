# Admin9 Labs Docs

This repository contains the Mintlify source content for the Admin9 Labs documentation site.

## Purpose

This repository holds:

- product documentation for `admin9`
- developer documentation
- admin and operations documentation
- release and deployment guidance
- open source portfolio pages
- Mintlify configuration for the public docs site

It is not the application repository.

## Structure

- `docs.json` - Mintlify configuration
- `index.md` - docs homepage
- `getting-started/` - installation and local development
- `architecture/` - system and codebase structure
- `guides/` - developer-focused feature and integration guides
- `admin-guide/` - admin and operations documentation
- `reference/` - commands and quality references
- `deployment/` - release and deployment checklists
- `open-source/` - public repository pages

## Local checks

Preview the site locally:

```bash
mintlify dev
```

Broken-link validation:

```bash
mintlify broken-links
```

If Mintlify CLI is not installed locally:

```bash
npm install -g mintlify
```

If you prefer not to install it globally:

```bash
npx mintlify dev
npx mintlify broken-links
```

## CI

This repository includes a GitHub Actions workflow that runs Mintlify broken-link checks on:

- pushes to `main`
- pull requests

It also runs markdown link validation across the repository so broken external links and moved internal references are caught before merge.

## Relationship to the product repository

The source of truth for product behavior remains the application repository:

- `admin9`

When updating docs, prefer to verify details against:

- `composer.json`
- `package.json`
- `.env.example`
- `routes/*.php`
- `app/Filament/*`
- `app/Services/*`

Recommended verification order for fact-sensitive pages:

1. confirm package and framework versions in `composer.json` and `package.json`
2. confirm user-facing paths in `routes/web.php` and `routes/api.php`
3. confirm panel paths, navigation groups, and theme assets in `app/Providers/Filament/*PanelProvider.php`
4. confirm documented environment variables in `.env.example`
5. confirm service behavior in the relevant files under `app/Services/*`

Pages most likely to drift and should be checked first:

- `getting-started/installation.md`
- `getting-started/local-development.md`
- `reference/commands-and-endpoints.md`
- `guides/authentication-and-identity.md`
- `guides/payments-and-billing.md`
- `admin-guide/*` pages that describe Filament settings or provider configuration

## Maintenance notes

- Documentation content should track the current product repositories.
- When product behavior changes, update docs from the relevant codebase rather than from older marketing material or inherited docs.
- Keep Mintlify navigation in `docs.json` aligned with the actual file structure.
- Keep `index.md`, section landing pages, and `README.md` aligned with the actual repo structure.
