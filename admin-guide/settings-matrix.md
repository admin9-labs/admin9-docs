---
title: Settings Matrix
description: A quick map of the main ADMIN9 admin settings pages and what each one is responsible for.
---

# Settings Matrix

ADMIN9 exposes several standalone settings pages in the admin panel. This page maps those screens to their intended responsibility so operators know where to make changes.

## Access model

The current settings pages share the same access pattern:

- admin settings must be enabled through `ConfigService::isAdminSettingsEnabled()`
- the current admin user must have the `update settings` permission

If a settings page is missing in production, check those two conditions first.

## Settings pages

### General Settings

Use this page for broad site-wide operational and presentation settings.

Typical areas:

- global site behavior
- analytics-related settings
- registration or login related toggles
- reCAPTCHA-related settings
- social links and similar public metadata

See also: [General Settings](./general-settings.md)

### Invoice Settings

Use this page for invoice-related configuration and output checks.

Typical areas:

- invoice generation behavior
- invoice presentation requirements
- business details that must appear on generated invoices

See also: [Invoice Settings](./invoice-settings.md)

### Legal Pages Settings

Use this page for the public legal documents rendered on:

- `/terms-of-service`
- `/privacy-policy`

See also: [Legal Pages and Compliance](./legal-pages-and-compliance.md)

### Open Graph Image Settings

Use this page for social-sharing image defaults or generated OG image behavior.

Typical areas:

- social preview assets
- release branding consistency
- share-card presentation

This is especially important before first launch because social previews are often one of the first external impressions of the product.

See also: [Analytics and Open Graph](./analytics-and-open-graph.md)

### Referral Settings

Use this page for referral program behavior and reward tuning.

Typical areas:

- referral incentives
- operational rollout choices
- alignment between referral rules and public communication

See also: [Referral Settings](./referral-settings.md)

## Recommended operator workflow

1. Review all settings pages in staging before launch.
2. Confirm no page still contains test or placeholder values.
3. Verify that each settings page aligns with both `.env` and public-facing behavior.
4. Record which teammate owns each settings area after launch.
