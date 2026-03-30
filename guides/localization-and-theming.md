---
title: Localization and Theming
description: How Admin9 handles localized URLs, translation support, DaisyUI themes, and Filament theme synchronization.
---

Locale-aware UI work and theme-related changes both converge here.

## Localization model

The application uses `mcamara/laravel-localization` for URL-based localization.

Current documented behavior:

- default locale is hidden from the URL
- non-default locales are prefixed

Examples:

- default locale: `/about`
- Chinese locale: `/zh/about`

There is already an internal project note describing this behavior in `admin9/docs/i18n-hide-default-locale.md`.

## What to review when localization changes

- `config/laravellocalization.php`
- localized route generation
- browser language redirect behavior
- session locale persistence
- links generated in Blade and Filament surfaces

## Translation footprint

The broader project guidance indicates the app currently ships with:

- English
- Simplified Chinese

When adding another language:

- enable the locale in localization config
- add translation resources
- verify frontend URLs and language switching behavior

## Theme system

The frontend uses DaisyUI theme switching with the Admin9 brand palette centered around `#f53003`.

Important characteristics from the codebase and project guidance:

- theme state is persisted locally
- the HTML root `data-theme` attribute is the switching mechanism
- Filament theme behavior is synchronized with the public-facing theme system

## Filament theme integration

Both panel providers reference dedicated Vite theme assets:

- `resources/css/filament/admin/theme.css`
- `resources/css/filament/dashboard/theme.css`

This means changes to brand, color scale, or theme semantics should be validated in:

- public Blade pages
- admin panel
- user dashboard

## Regression checklist

- verify default locale pages without a locale prefix
- verify non-default locales with the correct prefix
- verify language switcher output
- verify theme changes persist across reloads
- verify Filament panels still use the expected color scale
- verify dark-mode-related styling does not diverge between public and panel surfaces
