---
title: General Settings
description: Site-wide admin settings to review before the first public release.
---

Reach for this page when the change is site-wide and does not clearly belong to billing, legal, referral, or content operations.

## What this page controls

Review this page for broad application behavior such as:

- site-level presentation settings
- registration and login related toggles
- analytics-related settings
- reCAPTCHA-related settings
- social link configuration

The codebase specifically shows reCAPTCHA controls and references to documentation links from this settings area.

## Release-critical items to review

Before launch, confirm:

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
