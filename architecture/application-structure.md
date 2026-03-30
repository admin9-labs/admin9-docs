---
title: Application Structure
description: Directory-level map of the ADMIN9 application and where to extend each concern.
---

# Application Structure

This page is a practical map of the codebase for developers adding features or debugging production issues.

## Top-level directories

### `app/`

The main application namespace.

- `Client/` external service clients
- `Console/Commands/` custom Artisan commands
- `Constants/` application enums and constant values
- `Dto/` transport and state objects
- `Events/` domain events grouped by business area
- `Exceptions/` domain or transport exceptions
- `Filament/` admin and dashboard resources, pages, and widgets
- `Http/Controllers/` route controllers
- `Http/Middleware/` custom HTTP middleware
- `Listeners/` event listeners
- `Livewire/` frontend interaction components
- `Mail/` mailables
- `Mapper/` mapping helpers
- `Models/` Eloquent models
- `Notifications/` notifications
- `Policies/` authorization policies
- `Providers/` service providers and panel providers
- `Services/` business logic
- `Support/` shared support helpers
- `Validator/` custom validation logic
- `View/Components/` Blade view components

### `config/`

Operational configuration for:

- auth
- cache
- cookie consent
- CORS
- database
- filesystems
- Filament
- Horizon
- invoices
- localization
- mail
- permission
- queue
- Sanctum
- services
- session
- Telescope
- two-factor auth

### `database/seeders/`

Contains both baseline seeders and special-purpose seeders:

- production-safe baseline seeders in the root
- demo seeders under `Demo/`
- testing seeders under `Testing/`

### `resources/`

Frontend assets and Blade templates.

Important areas:

- `resources/css/`
- `resources/js/`
- `resources/views/`

### `routes/`

- `web.php` for browser routes
- `api.php` for webhook-style API routes
- `channels.php`
- `console.php`

### `tests/`

Automated tests for critical application behavior.

## Where to add new functionality

### Add a new admin management feature

Typical touch points:

- `app/Filament/Admin/Resources`
- `app/Filament/Admin/Pages`
- `app/Services`
- `app/Models`
- `database/migrations`

### Add a new customer-facing dashboard capability

Typical touch points:

- `app/Filament/Dashboard`
- `app/Livewire`
- `app/Services`
- `resources/views`

### Add a new payment or verification provider

Typical touch points:

- `app/Services/PaymentProviders`
- `app/Services/VerificationProviders`
- `app/Http/Controllers/PaymentProviders`
- `config/services.php`
- `.env`
- seeders if the provider should exist by default

### Add a new public content section

Typical touch points:

- `routes/web.php`
- `app/Http/Controllers`
- `resources/views`
- admin-side Filament resources if the content is editable

## Guiding rule

If a change includes both orchestration and provider-specific SDK code, keep the orchestration in a service and isolate the provider specifics behind an interface or dedicated implementation.
