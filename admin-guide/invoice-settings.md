---
title: Invoice Settings
description: Admin guidance for controlling invoice generation, seller metadata, and release validation in ADMIN9.
---

# Invoice Settings

The `Invoice Settings` page inside `/admin` exposes the controls that determine whether invoices are generated, how invoice numbers are formatted, and what seller metadata appears on every document.

## Access and location

The page is implemented as `App\Filament\Admin\Pages\InvoiceSettings` under the **Settings** navigation group. Access requires:

- the `update settings` permission
- `ConfigService::isAdminSettingsEnabled()` returning `true`

If either gate is false, the page and its Livewire form are inaccessible.

## Primary controls

The Livewire form at `App\Livewire\Filament\InvoiceSettings` writes values through `ConfigService::set`, so changes are persisted immediately and cached for runtime.

Key fields you operate on:

- `Enable invoice generation` (toggle) – when true, the system issues invoices for each successful transaction and makes them available at `/invoice/preview` and `/invoice/generate/{transactionUuid}`.
- `Invoice number prefix` – defines `invoices.serial_number.series` (default `INV`). It prefixes every generated invoice ID.
- Seller metadata text inputs for:
  - company name
  - company code
  - company address
  - company tax/VAT number
  - company phone

These values are stored under `invoices.seller.attributes.*` and are rendered by the invoice service (`App\Services\InvoiceService`) when composing PDF or HTML invoices through `LaravelDaily\Invoices`.

## Preview workflow

The settings page includes an inline preview action that opens `/invoice/preview` with the current form values. Use it to validate layout, locale, and metadata before committing to a change.

## Operational checklist

1. Confirm sandbox webhook, payment, and invoicing flows are working before enabling invoices in production.
2. Set the invoice number prefix to match any existing accounting sequence or remove collisions from previous invoices.
3. Provide accurate company metadata; these values are visible to customers and regulators on each invoice.
4. Use the preview action to check layout and text before saving.
5. After saving, verify `/invoice/generate/{transactionUuid}` still produces a PDF for a completed transaction (choose a test transaction UUID).
6. Ensure cached config values are refreshed if you seed the database or deploy new instances (`ConfigService` handles caching automatically, but long-lived workers may need a reboot).
