---
title: Users and Access
description: Admin-side responsibilities for users, roles, permissions, and account support workflows.
---

Use this guide when the task involves account access, role assignment, permission review, or staff-side user support.

## Core resources

- Users
- Roles

These resources are backed by the application user model and Spatie Permission.

## Typical admin responsibilities

### User management

Use the users resource to:

- inspect user accounts
- review associated subscriptions and orders
- support account troubleshooting
- manage account state where required

The user edit flow also interacts with two-factor-related state when that feature is enabled.

### Role management

Use roles to define operational access boundaries inside the application.

Typical responsibilities:

- create roles for staff or support functions
- assign permissions according to least privilege
- review which users should have admin access

## Access model to keep in mind

ADMIN9 has more than one access surface:

- public authentication
- user dashboard at `/dashboard`
- admin panel at `/admin`

Do not assume customer access and operator access are interchangeable. Verify role assignment carefully before launch.

## Recommended checks before release

- verify admin-only users can reach `/admin`
- verify normal users are limited to `/dashboard`
- verify permissions align with operational duties
- verify 2FA expectations for staff accounts
- verify support staff can inspect billing data without unnecessary destructive access
