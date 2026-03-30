---
title: Email Providers
description: Operator guidance for configuring the Email Providers resource inside the ADMIN9 Filament admin panel.
---

Open this guide when outbound email needs to be enabled, repaired, or validated before a release.

## Access requirements

The email provider pages depend on `ConfigService` and the overriding configuration caches. Make sure the Admin Settings feature is enabled before touching this area:

```env
ADMIN_SETTINGS_ENABLED=true
```

If the setting is disabled, the Filament pages for providers, SMTP, and other admin settings reject access.

## Email provider list

The `EmailProviderResource` renders:

- a list of locked provider records (name and slug)
- inline icons pulled from `public/images/email-providers/<slug>.svg`
- an edit action that opens provider-specific settings pages

Operators configure the built-in providers here. They do not create or delete provider records from this screen.

## Provider-specific settings

Each provider has a dedicated Livewire form that writes through `ConfigService::set(...)`, which in turn persists values via `App\Models\Config` and caches them for the runtime config.

### SMTP

`SmtpSettings` exposes the host, port, username, and password fields stored under the `mail.mailers.smtp.*` config keys. These values override whichever SMTP mailer is currently configured in `config/mail.php`, so verify that `mail.default` matches the provider you want to use.

### Mailgun

`MailgunSettings` covers:

- `services.mailgun.domain`
- `services.mailgun.secret` (encrypted)
- `services.mailgun.endpoint`

### Amazon SES

`AmazonSesSettings` manages:

- `services.ses.key`
- `services.ses.secret` (encrypted)
- `services.ses.region`

### Postmark

`PostmarkSettings` manages `services.postmark.token`.

### Resend

`ResendSettings` manages `services.resend.key`.

Each settings form runs simple `TextInput` fields and calls `ConfigService::set(...)`, so the values are persisted in the `configs` table and immediately available through the Laravel config helper.

## Persistence and caching

`ConfigService::set` checks `ConfigConstants::OVERRIDABLE_CONFIGS` before saving to `App\Models\Config` and caching the new value (`cache()->forever`). Sensitive secrets are encrypted; the same service uses `ConfigConstants::ENCRYPTED_CONFIGS` when reading and writing to preserve confidentiality.

Because the service writes to the cache as well as the DB, operators do not need to restart the application after updating provider credentials, but confirm that the value appears in the Filament UI and in `config('services.<provider>')` before relying on it.

## Operational checklist

- verify each enabled provider has valid credentials and webhook secrets (where applicable)
- check that the `services.<provider>.*` entries in the environment and the admin UI match
- send a test email from the app, then verify `mail_mailer` logs or `mail.php` output to ensure deliverability
- confirm templates (password resets, notifications, invoices) render with the selected provider
- backup the `configs` table or export the entries if you are migrating environments
