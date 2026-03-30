---
title: 功能系统
description: 开发者常会碰到的几类核心功能。
---

先看这页，再看具体功能。

## Filament 面板

Admin9 内置两个 Filament 面板：

- `/admin` 管理后台
- `/dashboard` 用户仪表盘

面板提供者还定义了：

- panel-specific colors
- middleware stacks
- user menu actions
- discovered resources, pages, and widgets

## 主题切换

应用支持 DaisyUI 主题切换，并将主题状态与 Filament 暗色模式行为同步。

主要实现：

- 通过 local storage 持久化主题
- 在根 HTML 元素使用 `data-theme`
- 以 `#f53003` 为中心的 ADMIN9 品牌色板

调整前端时，请保持公共站点与 Filament 样式行为一致。

## 本地化

本地化由 `mcamara/laravel-localization` 提供。

路由规则：

- 默认语言不显示在 URL 中
- 非默认语言带前缀，例如 `/zh/about`

如果这条规则回归，先检查 `config/laravellocalization.php`。

## 认证与验证

应用支持：

- classic email/password auth
- social login redirects and callbacks
- email verification
- phone verification
- two-factor authentication
- API token support through Sanctum

关键路由区域：

- `/auth/{provider}/redirect`
- `/auth/{provider}/callback`
- `/email/verify`
- `/phone/verify`

默认路由列表没有暴露 `/oauth/*` 授权服务器路由。依赖 OAuth2 / OIDC 行为前，先在部署环境验证。

## 支付与结账

商业层支持：

- subscription checkout
- subscription plan changes
- local subscription conversion
- one-time product purchases
- balance top-up flows
- provider-specific payment links and webhooks

排查计费问题时，先看这几层：

- checkout controllers
- services under `app/Services`
- webhook controllers
- transaction and invoice services

## 内容系统

代码库内置支持：

- blog
- roadmap
- announcements
- FAQs
- legal pages

这些模块既可以直接用，也可以拿来参考可编辑内容的建模方式。

## 扩展经验法则

新增系统时，优先沿用现有模式，不要另起一套并行架构。Admin9 在 services、providers、Filament resources、Livewire 组件和领域事件上已经有明确约定。
