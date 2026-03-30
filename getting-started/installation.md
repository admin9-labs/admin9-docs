---
title: Installation
description: Fresh setup instructions for running ADMIN9 from source.
---

# Installation

This guide assumes you are working from the main application repository at `admin9`.

## Requirements

- PHP 8.2 or newer
- Composer
- Node.js and npm
- MySQL 8
- Redis
- Mailpit or another local SMTP sink

The repository also includes a Docker Compose setup based on Laravel Sail, which is the fastest path for a reproducible local environment.

## Clone and install

```bash
git clone git@github.com:admin9-labs/admin9.git
cd admin9

composer install
npm install
cp .env.example .env
php artisan key:generate
```

## Configure environment

The default `.env.example` expects the Docker Compose service names:

```env
DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=sail
DB_PASSWORD=password

REDIS_HOST=redis
MAIL_HOST=mailpit
MAIL_PORT=1025
QUEUE_CONNECTION=sync
```

If you are not using Docker Compose, replace those hostnames with your local services.

## Prepare the database

```bash
php artisan migrate:fresh --seed
```

The default database seeder currently loads:

- intervals
- currencies
- OAuth login providers
- payment providers
- roles and permissions
- email providers
- verification providers
- FAQs
- legal pages

## Start the application

For a native local setup:

```bash
npm run dev
php artisan serve
```

For the Laravel Sail workflow:

```bash
./vendor/bin/sail up -d
./vendor/bin/sail artisan migrate:fresh --seed
./vendor/bin/sail npm run dev
```

## First URLs to verify

- `/` for the marketing site
- `/admin` for the Filament admin panel
- `/dashboard` for the authenticated user dashboard
- `/blog`
- `/roadmap`

If those routes load, the core HTTP layer is functioning.
