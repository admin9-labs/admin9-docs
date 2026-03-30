---
title: Payments and Billing
description: Payment providers, billing flows, checkout routes, and webhook considerations for ADMIN9.
---

Checkout and billing code changes should start here before dropping into provider-specific implementation.

## Supported payment providers

The codebase includes payment provider controllers and environment configuration for:

- Stripe
- Paddle
- Lemon Squeezy
- offline payments

The provider layer is abstracted behind service interfaces so the rest of the application does not need to know SDK-level details.

## Main billing services

Key services involved in billing include:

- `PaymentService`
- `CheckoutService`
- `SubscriptionService`
- `SubscriptionDiscountService`
- `TransactionService`
- `InvoiceService`
- `OrderService`
- `BalanceTopupService`

When debugging billing issues, review service orchestration before changing controller code.

## Subscription flows

Main subscription routes:

- `/checkout/plan/{planSlug}`
- `/checkout/convert-subscription/{subscriptionUuid}`
- `/checkout/subscription/success`
- `/checkout/convert-subscription-success`
- `/subscription/{subscriptionUuid}/change-plan/{planSlug}`

These flows cover:

- initial subscription signup
- converting local subscriptions
- post-checkout success handling
- changing an existing subscription plan

## One-time product flows

Relevant routes:

- `/buy/product/{productSlug}/{quantity?}`
- `/checkout/product`
- `/checkout/product/success`

These are separate from subscription flows and should be tested independently.

## Balance top-up

Balance management is a first-class concept in the codebase.

Relevant routes:

- `/dashboard/balance`
- `POST /dashboard/balance/topup`
- `/dashboard/balance/topup/success`
- `/dashboard/balance/topup/cancel`

There is also a dedicated `BalanceTopup` service namespace and a dashboard balance page that hosts the top-up workflow.

## Webhooks

The webhook endpoints are:

- `/api/payments-providers/stripe/webhook`
- `/api/payments-providers/paddle/webhook`
- `/api/payments-providers/lemon-squeezy/webhook`

Before production release:

- configure webhook signing secrets
- make sure the public URL is reachable from the provider
- verify queue behavior for downstream side effects
- replay sample webhooks from each enabled provider

For local development workflows and provider callback testing, read [Payment Webhooks and Local Testing](./payment-webhooks-and-local-testing.md).

## Environment configuration

Examples from `.env.example`:

```env
STRIPE_SECRET_KEY=""
STRIPE_PUBLISHABLE_KEY=""
STRIPE_WEBHOOK_SIGNING_SECRET=""

PADDLE_VENDOR_ID=""
PADDLE_CLIENT_SIDE_TOKEN=""
PADDLE_VENDOR_AUTH_CODE=""
PADDLE_PUBLIC_KEY=""
PADDLE_WEBHOOK_SECRET=""
PADDLE_IS_SANDBOX=true

LEMON_SQUEEZY_API_KEY=""
LEMON_SQUEEZY_STORE_ID=""
LEMON_SQUEEZY_SIGNING_SECRET=""
LEMON_SQUEEZY_IS_TEST_MODE=false
```

## Recommended release validation

- create a checkout session for each enabled provider
- confirm a successful payment creates the expected subscription or order state
- verify invoice generation
- verify transaction records
- verify discount application
- verify plan change behavior
- verify cancellation or failure handling
