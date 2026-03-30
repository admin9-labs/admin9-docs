---
title: Application Starters
description: Public starter repositories and reference applications published by Admin9 Labs.
---

# Application Starters

These repositories are the most relevant entry points if you want a clone-and-build starting point instead of an installable package.

## admin9-api

- Repository: [`admin9-labs/admin9-api`](https://github.com/admin9-labs/admin9-api)
- Primary language: PHP
- License: MIT

`admin9-api` is positioned as a production-ready Laravel 12 REST API scaffold. It focuses on common backend concerns that most commercial applications need early:

- JWT authentication
- role and permission management
- service-layer architecture
- audit events
- test coverage out of the box

Use it when you want a backend-first starter that already includes opinionated structure for admin and business APIs.

## admin9-web

- Repository: [`admin9-labs/admin9-web`](https://github.com/admin9-labs/admin9-web)
- Primary language: Vue
- License: MIT

`admin9-web` is the frontend SPA counterpart to `admin9-api`. It is useful when you want a separate frontend application instead of a monolith.

Use it when your delivery model is:

- API backend plus SPA frontend
- independent frontend deployment
- shared auth and API contracts across multiple clients

## admin9-docs

- Repository: [`admin9-labs/admin9-docs`](https://github.com/admin9-labs/admin9-docs)
- Documentation site: [admin9.dev/docs](https://admin9.dev/docs)

This repository is the Mintlify source for the current documentation site. It should remain the source of truth for portfolio-level docs until individual projects outgrow shared documentation.

## Suggested positioning on the docs site

For this tab, the starter repos work best as:

- the first content group after the overview
- the place where new users understand the relationship between API, web, and docs
- the bridge between the ADMIN9 product and the broader Admin9 Labs open source portfolio
