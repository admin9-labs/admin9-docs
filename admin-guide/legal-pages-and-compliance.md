---
title: Legal Pages and Compliance
description: Admin instructions for keeping terms, privacy, and compliance-ready content up to date before launch.
---

# Legal Pages and Compliance

The admin panel includes a dedicated `Legal Pages` settings page where operators can maintain Terms of Service, Privacy Policy, and other compliance content without touching code.

## Where this page lives

The page is registered as `App\Filament\Admin\Pages\LegalPagesSettings` and is grouped under **Settings** in the admin navigation. Access is gated by the `update settings` permission and by the `ConfigService::isAdminSettingsEnabled()` flag, so confirm both are true before attempting edits.

## What to do before launching

- make sure the seeded legal content is accurate. The default `DatabaseSeeder` runs `LegalPagesSeeder`, so review the initial content and edit it through the panel if needed.
- verify that the Terms and Privacy copy reflect the real offering, include the correct company details, and mention all enabled payment providers, authentication methods, and data processing practices.
- confirm that any regional compliance statements (e.g., GDPR, CCPA) match the regions you intend to serve.

## Operational considerations

- keep the panel copy in sync with any legal drafts or approvals. If a lawyer approves new wording, update it in the panel instead of hard-coding it.
- use Filament page versioning (if configured) or backups before editing, because there is no automatic rollback. Copy the previous version elsewhere if you need to audit changes.
- document in your runbook which team member owns legal content so future releases know who to loop in.

## Compliance validation checklist

1. Verify Terms and Privacy texts are accurate and public-facing routes (`/terms-of-service`, `/privacy-policy`) render the latest copy.
2. Confirm `ConfigService` values that drive those routes (e.g., `app.legal.terms_of_service` via the config service helper) are populated.
3. Ensure any new payment providers, OAuth flows, or feature toggles are referenced in the legal copy so published documentation matches functionality.
4. Confirm the admin user performing the update has the required permission and that `ConfigService::isAdminSettingsEnabled()` is still true in production.

## Release note

Treat this page as part of the launch checklist—the legal content must be finalized before the `Launch Runbook` section marks your release as “go”. Request sign-off from the responsible product or legal stakeholder and record the approved copy version so the team knows what text is live.
