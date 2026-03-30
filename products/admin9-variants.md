---
title: Admin9 Product Variants
description: How the single-tenant and multi-tenant Admin9 products relate, and which docs apply to both.
---

Use this page when you need to decide whether a document applies to `admin9`, `admin9-tenancy`, or both.

## Product map

Admin9 Labs currently documents two closely related application products:

- `admin9`: the single-tenant version
- `admin9-tenancy`: the multi-tenant version

They share the same core stack, most of the same product concepts, and the same overall documentation structure.

## What is shared

Unless a page explicitly says otherwise, assume these sections apply to both variants:

- installation and local development workflow
- architecture and application structure
- authentication and identity flows
- payments, billing, providers, and webhooks
- localization, theming, and configuration patterns
- admin operations, release checks, and reference material

## What is different

The main product difference is tenancy:

- `admin9` runs as a single-tenant application
- `admin9-tenancy` adds tenant-aware application behavior and operational concerns

Those multi-tenant differences are documented in [Admin9 Tenancy Supplement](/guides/admin9-tenancy).

## Reading path

If you are working on `admin9`:

1. Start with [Installation](/getting-started/installation).
2. Continue through the standard Admin9 docs tabs.

If you are working on `admin9-tenancy`:

1. Start with [Installation](/getting-started/installation).
2. Read the same shared Admin9 docs.
3. Add [Admin9 Tenancy Supplement](/guides/admin9-tenancy) anywhere tenant boundaries, provisioning, or operations matter.

## Source of truth

Treat the relevant product repository as authoritative for runtime behavior:

- use the `admin9` repository for single-tenant behavior
- use the `admin9-tenancy` repository for multi-tenant-specific behavior
