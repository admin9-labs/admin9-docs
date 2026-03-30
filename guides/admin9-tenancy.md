---
title: Admin9 Tenancy Supplement
description: Multi-tenant-specific notes for teams using admin9-tenancy instead of the single-tenant admin9 build.
---

This page documents the main areas where `admin9-tenancy` needs extra attention beyond the shared `admin9` documentation set.

## Scope

Read the standard Admin9 docs as the baseline. Use this supplement only for the parts that change when the application becomes multi-tenant.

## What stays the same

The following areas should generally be read the same way for both variants:

- Laravel, Livewire, Filament, Tailwind, and Vite stack assumptions
- local development workflow
- application structure and service-layer conventions
- billing, identity, content, and provider integration concepts
- admin and operator workflows that are not tenant-bound

## What changes in the multi-tenant variant

When working on `admin9-tenancy`, expect additional design and operational decisions around:

- tenant identification and request scoping
- tenant-aware data isolation
- tenant provisioning and lifecycle management
- tenant-specific domains, branding, and configuration
- tenant-aware billing ownership and reporting boundaries
- super-admin versus tenant-admin responsibilities

## How to read the rest of the docs

Use the shared docs with these interpretation rules:

- treat global settings pages as potentially split between platform-level settings and tenant-level settings
- treat admin workflows as needing a clear boundary between operator actions and tenant administrator actions
- treat routes, queues, jobs, events, and caches as tenant-aware unless the implementation is explicitly platform-global
- treat integrations such as email, OAuth, verification, and payment providers as possibly configured at either platform scope or tenant scope

## Recommended verification points

Before applying any shared Admin9 guide to `admin9-tenancy`, verify the corresponding implementation areas in the multi-tenant repository:

- route and middleware tenant resolution
- tenant model and tenant ownership relationships
- database isolation strategy
- Filament panel boundaries
- configuration storage and tenant overrides
- billing entity ownership and reporting queries

## Documentation convention

If a future page contains important multi-tenant behavior, add a short `admin9-tenancy note` section to that page instead of duplicating the whole document.
