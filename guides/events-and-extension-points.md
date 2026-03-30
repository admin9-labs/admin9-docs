---
title: Events and Extension Points
description: Where to hook custom behavior into the shared Admin9 stack using domain events, listeners, and service boundaries.
---

Customization work should start here if the goal is to extend the shared Admin9 stack cleanly instead of patching core flows inline.

## Event areas in the codebase

The application has dedicated event directories for:

- balance
- order
- referral
- subscription
- user

Listeners are grouped under `app/Listeners` by the same business areas.

## What belongs in an event listener

Good listener responsibilities:

- sending notifications
- triggering post-payment side effects
- synchronizing external systems
- analytics or bookkeeping actions
- provisioning or deprovisioning domain resources

Bad listener responsibilities:

- core validation logic
- primary transaction control flow
- business rules that must execute synchronously to keep data consistent

## Practical examples

Common event-driven customization points include:

- registration
- subscription created, renewed, or cancelled
- order completion
- payment failure
- user verification

This is a good mental model when deciding where to extend the product.

## Preferred extension order

When adding custom behavior, review options in this order:

1. existing service method extension
2. event listener
3. provider implementation swap or new provider
4. controller override as a last resort

This keeps customizations consistent with the rest of the application.

## Other extension seams

Beyond events, ADMIN9 already exposes useful boundaries through:

- `app/Services`
- `app/Services/PaymentProviders`
- `app/Services/VerificationProviders`
- Filament resources and pages
- Livewire components

## Recommended documentation habit

Whenever you introduce a new event or hook:

- name it after a business action
- document when it fires
- document the guaranteed payload
- document whether it fires before or after persistence

That discipline makes future integrations much easier.
