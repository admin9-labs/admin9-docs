---
title: General Settings
description: Site-wide admin settings to review before the first public release of ADMIN9.
---

# General Settings

The admin panel includes a `General Settings` page intended for site-wide operational and presentation settings.

## What this page likely controls

Based on the codebase and related settings integrations, this page is the place to review broad application behavior such as:

- site-level presentation settings
- registration and login related toggles
- analytics-related settings
- reCAPTCHA-related settings
- social link configuration

The codebase specifically shows reCAPTCHA controls and references to documentation links from this settings area.

## Release-critical items to review

Before first public release, confirm:

- branding and basic site metadata are correct
- analytics configuration is intentional
- tracking scripts are production-safe
- social profile links point to real destinations
- reCAPTCHA is either fully configured or intentionally disabled

## reCAPTCHA

The environment file includes:

```env
RECAPTCHA_SITE_KEY=""
RECAPTCHA_SECRET_KEY=""
RECAPTCHA_SKIP_IP=""
```

If you enable reCAPTCHA in admin settings, make sure these values are also correct in the deployment environment.

## Analytics and tracking

The environment file also includes:

- `GOOGLE_TRACKING_ID`
- `TRACKING_SCRIPTS`

Treat custom tracking script support as a production-risk area. Only add scripts that have been reviewed and are necessary for launch.

## Suggested operator workflow

1. Review the page in staging.
2. Compare each setting with the deployment environment.
3. Validate the public registration and login forms.
4. Verify no test or placeholder values remain.
