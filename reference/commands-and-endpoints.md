---
title: Commands and Endpoints
description: Quick reference for common development commands, panel paths, and application endpoints.
---

Use this page as a quick lookup for commands, routes, and panel paths.

## Common commands

### Frontend

```bash
npm run dev
npm run build
npm run format
npm run format:check
```

### Backend

```bash
php artisan serve
php artisan migrate
php artisan migrate:fresh --seed
php artisan queue:work
php artisan horizon
```

### Quality

```bash
vendor/bin/phpunit
vendor/bin/phpstan analyse
vendor/bin/pint
```

### Deployment

```bash
php dep deploy
```

## Panel routes

- `/admin`
- `/dashboard`

## Public routes

Notable routes defined in `routes/web.php`:

- `/`
- `/blog`
- `/blog/category/{slug}`
- `/blog/{slug}`
- `/roadmap`
- `/roadmap/i/{itemSlug}`
- `/roadmap/suggest`
- `/terms-of-service`
- `/privacy-policy`

## Authentication and verification routes

- `/email/verify`
- `/email/verify/{id}/{hash}`
- `/email/verification-notification`
- `/phone/verify`
- `/phone/verified`
- `/registration/thank-you`
- `/auth/{provider}/redirect`
- `/auth/{provider}/callback`

Provider values currently allowed by the route constraints:

- `google`
- `github`
- `facebook`
- `twitter-oauth-2`
- `linkedin-openid`
- `bitbucket`
- `gitlab`

## Checkout and subscription routes

- `/checkout/plan/{planSlug}`
- `/checkout/convert-subscription/{subscriptionUuid}`
- `/checkout/subscription/success`
- `/checkout/convert-subscription-success`
- `/subscription/{subscriptionUuid}/change-plan/{planSlug}`
- `/already-subscribed`

## One-time purchase and balance routes

- `/buy/product/{productSlug}/{quantity?}`
- `/checkout/product`
- `/checkout/product/success`
- `/dashboard/balance`
- `POST /dashboard/balance/topup`
- `/dashboard/balance/topup/success`
- `/dashboard/balance/topup/cancel`

## Invoice routes

- `/invoice/generate/{transactionUuid}`
- `/invoice/preview`

## Payment provider routes

Browser route:

- `/payment-provider/paddle/payment-link`

Webhook API routes from `routes/api.php`:

- `/api/payments-providers/stripe/webhook`
- `/api/payments-providers/paddle/webhook`
- `/api/payments-providers/lemon-squeezy/webhook`

Note the current path segment is `payments-providers` in the codebase. Preserve that exact path unless you intentionally perform a breaking route change.
