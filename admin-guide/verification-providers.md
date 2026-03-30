---
title: Verification Providers
description: Setting up Twilio-based SMS verification and related gating controls from the admin UI before launch.
---

# Verification Providers

ADMIN9 includes a `Verification Providers` resource in the **Settings** navigation group to keep SMS verification and trial gating operational without touching code.

## Twilio provider

The codebase ships with a dedicated Twilio provider implementation (`App\Services\VerificationProviders\TwilioProvider`) that:

- reads `services.twilio.sid`, `services.twilio.token`, and `services.twilio.from`
- uses the Twilio PHP SDK to send SMS via the configured credentials
- logs exceptions and returns `false` on failure so the calling logic can surface verification errors

The admin-specific `TwilioSettings` Livewire form writes these values through `ConfigService::set(...)`, so updates persist in the `configs` table and refresh the runtime `config(...)` helper without waiting for a deploy.

## Required environment/configuration items

Operators should ensure the following configuration keys exist and are accurate:

```env
TWILIO_SID=""
TWILIO_TOKEN=""
TWILIO_FROM=""
```

These map to `services.twilio.sid`, `services.twilio.token`, and `services.twilio.from` inside `config/services.php`. The admin form writes to the same keys via `ConfigService`, so the environment values and database-backed config should be kept in sync.

## Access requirements

The resource is protected by:

- `ConfigService::isAdminSettingsEnabled()` (check whether admin settings UI is allowed)
- Filament permissions (`update settings`)

If either is false in production, the verification provider settings will be unreachable, which blocks updating Twilio credentials.

## Trial gating and SMS verification flows

Twilio verification supports:

- user phone verification
- trial gating with `TRIAL_WITHOUT_PAYMENT_SMS_VERIFICATION_ENABLED=false` (see `.env.example`)

Before launch, operators should decide whether SMS verification is required for:

- new registrations
- trial starts that should block usage without confirmation
- checkout flows that rely on verified phone numbers for compliance or throttling

## Operational checklist

1. Confirm Twilio credentials in the admin UI and `.env` match the production Twilio project.
2. Send test verification SMS to ensure Twilio accepts the `from` number and message payload.
3. Verify error handling: force a Twilio failure (invalid token) and confirm the log/notification surface enough detail for support.
4. Double-check that `ConfigConstants::OVERRIDABLE_CONFIGS` includes the Twilio keys used by the form so they stay editable through the admin UI.
5. If you plan to skip phone verification for launch, make sure `TRIAL_WITHOUT_PAYMENT_SMS_VERIFICATION_ENABLED` matches that choice and is recorded in the launch runbook.
