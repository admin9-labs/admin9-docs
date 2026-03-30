---
title: Configuration
description: Environment variables, service configuration, and the main toggles developers need before shipping.
---

Start here for the broad configuration picture before tracing a narrower service or subsystem.

## Core application settings

From `.env.example`:

```env
APP_NAME=ADMIN9
APP_ENV=local
APP_DEBUG=true
APP_URL=http://localhost
APP_TIMEZONE=UTC
```

You should treat `APP_URL` as a high-impact setting because it also influences generated URLs and the default OIDC issuer.

## Database, session, queue, cache

```env
DB_CONNECTION=mysql
CACHE_DRIVER=file
QUEUE_CONNECTION=sync
SESSION_DRIVER=file
REDIS_HOST=redis
```

For production, validate whether `file` and `sync` defaults are still appropriate for your environment. In most real deployments you will want Redis-backed queues and cache.

## Mail

```env
MAIL_MAILER=smtp
MAIL_HOST=mailpit
MAIL_PORT=1025
MAIL_FROM_ADDRESS="hello@example.com"
```

Mail provider support in the codebase includes Mailgun, Postmark, Amazon SES, and Resend-related dependencies. Ensure the selected mailer and credentials are aligned with `config/mail.php` and `config/services.php`.

## Social login

Available environment slots include:

- `GOOGLE_CLIENT_ID`
- `GOOGLE_CLIENT_SECRET`
- `GITHUB_CLIENT_ID`
- `GITHUB_CLIENT_SECRET`
- `FACEBOOK_CLIENT_ID`
- `FACEBOOK_CLIENT_SECRET`

The default database seeder also initializes OAuth login provider records.

## Payments

Configured provider variable groups currently include:

- Stripe
- Paddle
- Lemon Squeezy
- offline payments through the application domain model

Examples from `.env.example`:

```env
STRIPE_SECRET_KEY=""
STRIPE_PUBLISHABLE_KEY=""
STRIPE_WEBHOOK_SIGNING_SECRET=""

PADDLE_VENDOR_ID=""
PADDLE_CLIENT_SIDE_TOKEN=""
PADDLE_WEBHOOK_SECRET=""
PADDLE_IS_SANDBOX=true

LEMON_SQUEEZY_API_KEY=""
LEMON_SQUEEZY_STORE_ID=""
LEMON_SQUEEZY_SIGNING_SECRET=""
LEMON_SQUEEZY_IS_TEST_MODE=false
```

## Verification and anti-abuse

The application also supports:

- reCAPTCHA
- Twilio-based SMS verification
- optional trial gating based on SMS verification

Relevant variables:

```env
RECAPTCHA_SITE_KEY=""
RECAPTCHA_SECRET_KEY=""
TWILIO_SID=""
TWILIO_TOKEN=""
TWILIO_FROM=""
TRIAL_WITHOUT_PAYMENT_SMS_VERIFICATION_ENABLED=false
```

## Analytics and social links

The environment file includes:

- `GOOGLE_TRACKING_ID`
- `TRACKING_SCRIPTS`
- social profile URLs for Facebook, X, Instagram, LinkedIn, YouTube, GitHub, and Discord

## Important config files to review before release

- `config/app.php`
- `config/auth.php`
- `config/services.php`
- `config/queue.php`
- `config/horizon.php`
- `config/mail.php`
- `config/laravellocalization.php`
- `config/filament.php`
- `config/two-factor.php`
- `config/permission.php`

## Admin-managed settings

Some application behavior is managed in Filament instead of hard-coded config.

Notable admin settings pages include:

- General settings
- Invoice settings
- Legal pages settings
- Open Graph image settings
- Referral settings

Document your deployment process so operators know which settings are expected to be configured through the UI versus `.env`.

## Related reading

If you are extending or debugging the settings mechanism itself, read [Configuration System](/guides/configuration-system).
