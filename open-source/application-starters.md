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

This repository is the Mintlify source for the current documentation site. Use it when you need to update shared product documentation, operator runbooks, or the open-source portfolio index.

## Which starter to begin with

- start with `admin9-api` if you want a backend-first Laravel foundation
- start with `admin9-web` if you need a separate SPA frontend to pair with an API backend
- start with `admin9-docs` if you are improving product docs, admin runbooks, or shared public documentation
