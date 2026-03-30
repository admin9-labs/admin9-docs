# ADMIN9 Docs

This repository contains the Mintlify source content for the ADMIN9 documentation site.

It is a standalone documentation repository for the `admin9` product and should be maintained alongside the main application codebase.

## Purpose

This repository is intended to hold:

- developer documentation
- admin and operations documentation
- release and deployment guidance
- Mintlify configuration for the public docs site

It is not the ADMIN9 application repository itself.

## Structure

- `mint.json` - Mintlify configuration
- `index.md` - docs homepage
- `getting-started/` - installation and local development
- `architecture/` - system and codebase structure
- `guides/` - developer-focused feature and integration guides
- `admin-guide/` - admin and operations documentation
- `reference/` - commands and quality references
- `deployment/` - release and deployment checklists

## Local checks

Broken-link validation:

```bash
mintlify broken-links
```

If Mintlify CLI is not installed locally:

```bash
npm install -g mintlify
```

## CI

This repository includes a GitHub Actions workflow that runs Mintlify broken-link checks on:

- pushes to `main`
- pull requests

## Relationship to the main product repository

The source of truth for product behavior remains the main `admin9` application repository.

When updating docs, prefer to verify details against:

- `composer.json`
- `package.json`
- `.env.example`
- `routes/*.php`
- `app/Filament/*`
- `app/Services/*`

## Maintenance notes

- Documentation content should track the current `admin9` codebase.
- When product behavior changes, update docs from the codebase rather than from older marketing material or inherited docs.
- Keep Mintlify navigation in `mint.json` aligned with the actual file structure.
