---
title: Local Development
description: Daily developer workflow, service expectations, and common environment tasks.
---

Use this page for daily local work after installation.

## Docker Compose

`docker-compose.yml` includes these services:

- `laravel.test`
- `mysql`
- `mailpit`
- `redis`
- `ngrok`

Relevant forwarded ports:

- App: `APP_PORT=8080`
- Vite: `VITE_PORT=5173`
- MySQL: `FORWARD_DB_PORT=3306`
- Mailpit SMTP: `FORWARD_MAILPIT_PORT=1025`
- Mailpit UI: `FORWARD_MAILPIT_DASHBOARD_PORT=8025`
- Redis: `FORWARD_REDIS_PORT=6379`
- ngrok UI: `FORWARD_NGROK_PORT=4040`

## Day-to-day commands

Frontend:

```bash
npm run dev
npm run build
```

Backend:

```bash
php artisan serve
php artisan migrate
php artisan queue:work
php artisan horizon
```

Testing and quality:

```bash
vendor/bin/phpunit
vendor/bin/phpstan analyse
vendor/bin/pint
```

## Environment Notes

- Queues default to `sync` in `.env.example`, but Horizon is already installed for Redis-backed workers.
- Mail defaults to Mailpit.
- Payment, social login, Twilio, and reCAPTCHA credentials are empty by default and must be configured before testing.
- `.env.example` includes `OIDC_ISSUER`, but OAuth2 / OIDC provider endpoints should be verified before you rely on that integration path.

## Recommended local bring-up sequence

1. Start database, Redis, and mail services.
2. Run `php artisan migrate:fresh --seed`.
3. Start Vite.
4. Start the Laravel app server.
5. Log into `/admin` and verify seed data exists for currencies, providers, and legal content.

## Common development checks

After changing any payment or auth logic:

- Verify web routes still resolve
- Verify webhook endpoints are reachable in your local setup
- Verify queue-backed side effects still work
- Verify both `/admin` and `/dashboard` still load

After changing localization or frontend navigation:

- Check default locale routes without a prefix
- Check non-default locale routes with `/zh/...`
- Verify theme switching still updates the `data-theme` state correctly
