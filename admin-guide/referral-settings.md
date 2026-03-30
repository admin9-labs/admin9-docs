---
title: Referral Settings
description: How admins configure and validate the referral program ahead of launch.
---

Use this page when the referral program needs launch review, policy changes, or reward tuning.

## What the page covers

- referral rewards (amount, currency, payout method)
- eligibility rules (who can refer, referral frequency)
- tracking parameters (UTM, cookies, or referral codes)
- general toggles (enable/disable referral program)

Check the Filament page `App\Filament\Admin\Pages\ReferralSettings` to see the exact fields and validation rules.

## Pre-launch considerations

1. Confirm the referral program is only enabled once all reward mechanisms and accounting implications are understood.
2. Define who gets first access and whether referrals are incentivized per-plan or across the entire catalog.
3. Coordinate with finance to ensure payouts or credits are recorded properly.
4. Align referral terms with the legal copy maintained under `Legal Pages Settings`.

## Operational checklist

- verify referral links appear correctly in customer dashboards or marketing emails
- verify referral credits or discounts are applied in `BalanceTransaction` or `Discount` records
- verify there is monitoring for fraud, multiple accounts, or excessive rewards
- confirm `Launch Runbook` includes referral readiness
