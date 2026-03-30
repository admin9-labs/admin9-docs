---
title: Support Playbook
description: Operational steps for support staff to triage user, order, subscription, and transaction issues via Filament.
---

# Support Playbook

This is a playbook for support and operations teams resolving customer issues through the ADMIN9 Filament admin panel.

## Preparation

- confirm you have an admin role with the necessary permissions (`view users`, `view subscriptions`, `view transactions`).
- keep the expected environment hostnames handy (`/admin`, `/dashboard`, API/webhook URLs).
- reproduce the customer context (user email, order ID, subscription UUID) before touching data.

## Step-by-step triage

1. **User verification** – open the `Users` resource, find the account, review the `Orders` and `Subscriptions` relation managers, and check whether `two-factor` or `email_verified_at` flags align with the customer report.
2. **Order review** – use `OrderResource` to check the order status, provider metadata, and linked transaction (`ViewOrder` page). Confirm invoice number or balance adjustments before escalating.
3. **Subscription health** – inspect the `Subscriptions` resource, use action handlers like `AddDiscount`, `ChangeSubscriptionPlan`, and check lifecycle dates (trial_end, canceled_at, next_cycle_at). Use `DiscardSubscriptionCancellation` if cancellation was accidental.
4. **Transaction inspection** – open the `Transactions` resource, review the transaction detail page if webhook data is needed, and verify payment status, provider data, signature, and amounts. If a webhook failed, note the timestamp for correlating with provider logs.
5. **Balance context** – if the customer mentions credits, use `BalanceResource` and `BalanceTransactionResource` to trace manual adjustments, top-ups, or refunds. Ensure totals match the reported credit.

## Common remediation tasks

- update order notes if fulfillment or invoice issues arise, documenting findings before communicating with finance.
- use `AddDiscount` or `ChangeSubscriptionPlan` only when you have documented approval.
- cancel or resume subscriptions via the provided actions rather than editing database fields directly.
- log webhook failures separately so engineering can analyze retries.
- avoid editing users or transactions unless the change is audit-logged and approved (Filament already records admin activity).

## Post-triage checks

- reproduce any front-end failure to verify the fix. For login issues, confirm `/dashboard` access and 2FA prompts.
- rerun webhook delivery if required and confirm `Transactions` updates.
- ensure the admin user exits the Filament session before notifying the customer (to avoid hanging locks).

## Escalation paths

- if you cannot reconcile payments, escalate to the billing owner with the transaction UUID, webhook timestamp, and provider name.
- for subscription math issues, include the affected plan, discount state, and lifecycle dates.
- for legal or documentation conflicts, reference the Launch Runbook and Legal Pages content to keep messaging consistent.
