---
title: Subscriptions and Transactions
description: Admin procedures for monitoring and resolving subscription, order, transaction, and balance data.
---

Billing investigations usually start here, especially when you need to reconcile customer activity with what `/admin` shows.

## Tracking subscription health

The `Subscriptions` resource exposes list, view, edit, and action handlers for:

- `ListSubscriptions`
- `ViewSubscription`
- `AddDiscount`
- `ChangeSubscriptionPlan`
- `CancelSubscription`
- `ConfirmCancelSubscription`
- `DiscardSubscriptionCancellation`

Use this resource to:

- verify plan tiers, pricing, and feature visibility for each customer
- inspect subscription timelines (start, trial, cancel, renew events)
- apply discounts or change plans from the admin interface when manual intervention is required
- cancel or undo cancellation attempts for problematic subscriptions

## Reviewing orders

`OrderResource` and its pages allow operators to:

- review every customer order (subscriptions and one-time purchases)
- inspect fulfillment details
- view related transactions

Use the order view to confirm invoice numbers, payment status, and linked transactions before reconciling with external accounting.

## Transactions and audit trails

The `Transactions` resource includes:

- `ListTransactions`
- a transaction detail view page

It surfaces transaction state, provider data, and amounts. When investigating failed payments or reconciling reports, this is the primary place to inspect payment-provider data and related transaction context.

## Balances and balance transactions

`BalanceResource` and `BalanceTransactionResource` represent on-platform credit balances.

Admins should:

- use the balances list to monitor customer credits
- use the balance transactions list to investigate manual adjustments, top-ups, or refunds
- cross-reference transactions with balance history when troubleshooting user-reported credits

## Operational checklist

1. Regularly monitor `Subscriptions`, `Orders`, and `Transactions` after deployment to catch unexpected failures.
2. Use `BalanceTransactions` only for reconciled manual adjustments; document each manual change in case of audit review.
3. When a payment provider webhook shows a failure, confirm the transaction record, review related order lines, and use `ViewSubscription` to see the lifecycle before applying fixes.
4. After supporting plan changes or cancellations, check the associated balance history to make sure no stale credits remain.
