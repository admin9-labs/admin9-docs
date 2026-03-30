---
title: 功能系统
description: 开发者最常配置或扩展的核心横切能力实操说明。
---

在进入单一功能域前，本页先给出平台级横切视图。

## 适用范围

本功能总览由以下产品共享：

- `admin9`
- `admin9-tenancy`

请先将其作为默认基线；若某能力在多租户产品中变为租户感知，再叠加 [Admin9 多租户补充说明](/zh/guides/admin9-tenancy)。

## Filament 面板

ADMIN9 内置两个 Filament 面板：

- `/admin` 管理后台
- `/dashboard` 用户仪表盘

面板提供者还定义了：

- panel-specific colors
- middleware stacks
- user menu actions
- discovered resources, pages, and widgets

在 `admin9-tenancy` 中，还需确认面板访问、面板导航与面板数据查询是否按租户作用域执行。

## 主题切换

应用支持 DaisyUI 主题切换，并将主题状态与 Filament 暗色模式行为同步。

代码中体现的关键特征：

- 通过 local storage 持久化主题
- 在根 HTML 元素使用 `data-theme`
- 以 `#f53003` 为中心的 ADMIN9 品牌色板

调整前端时，请保持公共站点与 Filament 样式行为一致。

## 本地化

本地化由 `mcamara/laravel-localization` 提供。

预期路由行为：

- 默认语言不显示在 URL 中
- 非默认语言带前缀，例如 `/zh/about`

主项目文档中已记录“默认语言不显示在 URL 中”的规则。如该行为回归，先检查 `config/laravellocalization.php`。

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

默认路由列表未暴露 `/oauth/*` 授权服务器路由。在依赖 OAuth2 / OIDC 行为前，请先在当前部署环境验证服务商行为。

## 支付与结账

商业层支持：

- subscription checkout
- subscription plan changes
- local subscription conversion
- one-time product purchases
- balance top-up flows
- provider-specific payment links and webhooks

排查计费问题时，建议联合检查以下层：

- checkout controllers
- services under `app/Services`
- webhook controllers
- transaction and invoice services

对于 `admin9-tenancy`，请确认计费归属在平台级、租户级，还是两者并存。

## 内容系统

代码库内置支持：

- blog
- roadmap
- announcements
- FAQs
- legal pages

这些模块既可直接使用，也可作为 ADMIN9 可编辑内容建模的参考。

## 扩展经验法则

新增系统时，优先沿用应用中已有模式，而不是另起一套并行架构。ADMIN9 在 services、providers、Filament resources、Livewire 组件和领域事件上已有明确约定。
