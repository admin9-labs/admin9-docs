---
title: Analytics and Open Graph
description: Admin-side guidance for analytics tracking and social preview configuration before launch.
---

# Analytics and Open Graph

These settings affect how the product is observed externally and how links appear when shared.

## Analytics

The codebase indicates support for Google Analytics-style tracking through admin-managed settings and environment values such as:

- `GOOGLE_TRACKING_ID`
- `TRACKING_SCRIPTS`

Before launch:

- verify tracking IDs are production values
- remove any test analytics property IDs
- review any custom tracking scripts for safety and necessity

Analytics errors are easy to miss during development, so treat this as an explicit launch checklist item.

## Open Graph

ADMIN9 includes an `Open Graph Image Settings` page and an Open Graph-related configuration file.

This area is responsible for how shared links render on:

- X
- Facebook
- LinkedIn
- chat apps that consume OG metadata

Before launch:

- verify the default OG image reflects real brand assets
- verify homepage and major public pages generate the expected preview
- verify staging or test branding is not leaking into production content

Include at least one manual social preview review in your release workflow. A technically correct launch can still look unfinished if OG assets or analytics settings are wrong.
