---
title: Settings Matrix
description: A quick map of the main Admin9 admin settings pages and what each one is responsible for.
---

Use this page when the task clearly belongs to a settings screen but the destination is still unclear.

## Access model

The current settings pages share the same access pattern:

- admin settings must be enabled through `ConfigService::isAdminSettingsEnabled()`
- the current admin user must have the `update settings` permission

If a settings page is missing in production, check those two conditions first.

## Settings pages

### General Settings

Broad site-wide operational and presentation settings.

Typical areas:

- global site behavior
- analytics-related settings
- registration or login related toggles
- reCAPTCHA-related settings
- social links and similar public metadata

See also: [General Settings](/admin-guide/general-settings)

### Invoice Settings

Invoice-related configuration and output checks.

Typical areas:

- invoice generation behavior
- invoice presentation requirements
- business details that must appear on generated invoices

See also: [Invoice Settings](/admin-guide/invoice-settings)

### Legal Pages Settings

Public legal documents rendered on:

- `/terms-of-service`
- `/privacy-policy`

See also: [Legal Pages and Compliance](/admin-guide/legal-pages-and-compliance)

### Open Graph Image Settings

Social-sharing image defaults and generated OG image behavior.

Typical areas:

- social preview assets
- release branding consistency
- share-card presentation

See also: [Analytics and Open Graph](/admin-guide/analytics-and-open-graph)

### Referral Settings

Referral program behavior and reward tuning.

Typical areas:

- referral incentives
- operational rollout choices
- alignment between referral rules and public communication

See also: [Referral Settings](/admin-guide/referral-settings)

## Recommended operator workflow

1. Review all settings pages in staging before launch.
2. Confirm no page still contains test or placeholder values.
3. Verify that each settings page aligns with both `.env` and public-facing behavior.
4. Record which teammate owns each settings area after launch.

## Related guides

- [General Settings](/admin-guide/general-settings)
- [Invoice Settings](/admin-guide/invoice-settings)
- [Legal Pages and Compliance](/admin-guide/legal-pages-and-compliance)
- [Analytics and Open Graph](/admin-guide/analytics-and-open-graph)
- [Referral Settings](/admin-guide/referral-settings)
- [Launch Runbook](/admin-guide/launch-runbook)
