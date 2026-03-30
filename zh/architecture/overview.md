---
title: 架构总览
description: 共享 Admin9 应用架构的高层认知模型，涵盖面板、服务、事件与用户侧流程。
---

在深入模块、路由或服务之前，先读本页把系统全貌建立起来。

## 适用范围

本架构总览是以下两个产品的共享基线：

- `admin9`
- `admin9-tenancy`

对于多租户变体，请将本页作为默认系统地图，并结合 [Admin9 多租户补充说明](/zh/guides/admin9-tenancy) 理解租户边界。

## 运行时入口面

### 公共 Web 应用

Web 层提供：

- marketing pages
- authentication and verification flows
- subscription checkout
- one-time product checkout
- blog and roadmap pages
- invoice generation and preview

这些路由主要定义在 `routes/web.php`。

### 管理后台

管理后台由 `App\Providers\Filament\AdminPanelProvider` 注册，路径为：

```text
/admin
```

它是营收、产品、用户、内容、路线图与系统设置的运营入口。

### 用户仪表盘

用户仪表盘由 `App\Providers\Filament\DashboardPanelProvider` 注册，路径为：

```text
/dashboard
```

它承载面向客户的账户区域、订阅操作、推荐、余额管理与资料功能。

## 多租户说明

在 `admin9-tenancy` 中，这些运行入口通常会叠加租户感知路由、租户作用域数据访问，以及更明确的平台级与租户级管理边界。

## 架构模式

### 服务层

大部分业务逻辑位于 `app/Services`，从而让控制器、Livewire 组件和 Filament Resource 保持轻量。

Key examples:

- `CheckoutService`
- `SubscriptionService`
- `OrderService`
- `InvoiceService`
- `MetricsService`
- `TransactionService`
- `UserService`
- `ConfigService`
- `PaymentService`

### 事件驱动副作用

领域事件按业务关注点放在 `app/Events`，对应监听器放在 `app/Listeners`。

当前事件覆盖领域包括：

- balance
- order
- referral
- subscription
- user

这里是扩展通知、记账与非阻塞副作用的首选位置。

需要实操化的扩展指导，请阅读 [事件与扩展点](/zh/guides/events-and-extension-points)。

### Provider 抽象

支付与验证服务商通过接口抽象实现，避免将服务商 SDK 细节扩散到应用其他层。

主要抽象接口：

- `PaymentProviderInterface`
- `VerificationProviderInterface`
- `BalanceTopupProviderInterface`

## 主要平台能力

### 商业能力

- subscription billing
- one-time purchases
- discounts and discount codes
- invoices
- transactions
- balance top-ups

### 身份与访问

- Laravel 认证脚手架
- 邮箱验证
- 手机验证
- 社交登录
- 双因素认证
- 通过 Spatie Permission 管理角色与权限

### 内容与用户触达

- blog
- roadmap
- announcements
- FAQs
- legal pages

### 产品展示层

- DaisyUI 主题切换
- 本地化 URL
- SEO 与站点地图支持

## 版本说明

部分历史文档仍提到 Livewire 3 与 Filament 4。当前代码依赖显示为 Livewire 4 与 Filament 5，请以依赖清单为准。
