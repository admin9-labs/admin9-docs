---
title: 管理后台总览
description: 面向运营人员、产品经理与维护者的共享 Admin9 管理端操作地图。
---
当你需要先定位运营任务、再深入具体指南时，可将本页视为 `/admin` 的操作地图。

Admin9 主管理面板挂载在：

```text
/admin
```

本章节面向通过 Filament 管理应用、而非通过代码操作的运营人员与维护者。

## 适用范围

本指南作为以下产品的共享管理基线：

- `admin9`
- `admin9-tenancy`

如果你在运行多租户版本，请将本指南作为默认地图，并确认哪些职责属于平台运营方、哪些属于租户管理员。

## 何时使用本章节

当你需要以下内容时，请使用管理指南：

- 了解哪些运营任务发生在 `/admin`
- 找到发布或支持流程对应的正确页面
- 区分运营职责与开发实现细节

## 从任务开始

<CardGroup cols={2}>
  <Card title="准备发布" href="/zh/admin-guide/launch-runbook">
    检查与发布相关的关键项，包括计费、内容、访问控制、基础设施与支持准备度。
  </Card>
  <Card title="找到正确设置页" href="/zh/admin-guide/settings-matrix">
    当你知道任务属于 `/admin` 但不确定归属页面时，使用设置地图快速定位。
  </Card>
  <Card title="管理目录与计费" href="/zh/admin-guide/products-and-pricing">
    直接进入产品、套餐、交易、提供商、发票和推荐相关配置。
  </Card>
  <Card title="处理用户与支持" href="/zh/admin-guide/support-playbook">
    从支持流程入手，处理线上问题分诊、访问边界与验证相关问题。
  </Card>
</CardGroup>

## 管理面板覆盖内容

管理面板支持：

- 营收监控与 SaaS 指标
- 产品与套餐管理
- 一次性商品管理
- 折扣与优惠码
- 订阅、交易、订单、余额与余额流水
- 用户与角色管理
- 博客、公告、FAQ 与路线图条目
- 支付提供商、邮件提供商、OAuth 提供商与验证提供商配置
- 法务、发票、推荐与 Open Graph 设置

对于 `admin9-tenancy`，其中部分职责可能会在平台级管理与租户级管理之间拆分。

## 主要导航分组

面板提供方定义了以下顶级分组：

- Revenue
- Product Management
- User Management
- Content
- Roadmap
- Settings

## 相关管理页面

管理面板还包含若干独立设置页：

- Dashboard
- General Settings
- Invoice Settings
- Legal Pages Settings
- Open Graph Image Settings
- Referral Settings

## 本指南组织方式

管理指南按运营流程分组，而非按代码结构分组：

- `Start Here`：用于了解全局、准备发布和定位设置
- `Catalog & Revenue`：用于产品、计费、发票与推荐
- `Users & Access`：用于角色、登录提供商、验证与支持分诊
- `Content & Site Operations`：用于公开内容、法务文案、品牌与分析
- `Integrations`：用于提供商接入与邮件投递配置

## 推荐阅读顺序

### 1. Start Here

- [Overview](/zh/admin-guide/overview)：查看管理面板的操作地图
- [Launch Runbook](/zh/admin-guide/launch-runbook)：用于首次发布准备
- [Settings Matrix](/zh/admin-guide/settings-matrix)：快速定位独立设置页面

### 2. 目录与营收运营

- [Products and Pricing](/zh/admin-guide/products-and-pricing)：用于目录、套餐、折扣与计费实体
- [Subscriptions and Transactions](/zh/admin-guide/subscriptions-and-transactions)：用于日常计费运营与审计轨迹
- [Payment Providers](/zh/admin-guide/payment-providers)：用于 Stripe、Paddle、Lemon Squeezy 配置
- [Invoice Settings](/zh/admin-guide/invoice-settings)：用于发票生成与卖方元数据
- [Referral Settings](/zh/admin-guide/referral-settings)：当推荐计划属于商业发布范围时阅读

### 3. 用户、访问与支持

- [Users and Access](/zh/admin-guide/users-and-access)：用于角色、权限与管理边界
- [OAuth Providers](/zh/admin-guide/oauth-providers)：用于社交登录运营
- [Verification Providers](/zh/admin-guide/verification-providers)：用于短信验证与试用门槛
- [Support Playbook](/zh/admin-guide/support-playbook)：用于上线后的问题分诊

### 4. 内容与站点运营

- [Content and Site Settings](/zh/admin-guide/content-and-site-settings)：用于高层内容面配置
- [Content Operations](/zh/admin-guide/content-operations)：用于博客、FAQ、公告与路线图流程
- [Legal Pages and Compliance](/zh/admin-guide/legal-pages-and-compliance)：用于服务条款、隐私政策与发布签核
- [General Settings](/zh/admin-guide/general-settings)：用于全站行为、分析、社交链接与 reCAPTCHA
- [Analytics and Open Graph](/zh/admin-guide/analytics-and-open-graph)：用于追踪与社交预览校验

### 5. 集成总览

- [Providers and Integrations](/zh/admin-guide/providers-and-integrations)：用于支付、邮件、OAuth 与验证配置
- [Email Providers](/zh/admin-guide/email-providers)：用于邮件投递配置与校验

## 如果你不确定从哪里开始

- 如果你在准备发布，从 [Launch Runbook](/zh/admin-guide/launch-runbook) 开始
- 如果你在处理线上客户问题，从 [Support Playbook](/zh/admin-guide/support-playbook) 开始
- 如果你知道任务属于设置页但不清楚具体页面，从 [Settings Matrix](/zh/admin-guide/settings-matrix) 开始

## 读者边界

本管理指南解释运营人员在面板中做什么。实现细节、扩展点与代码结构请查看 Architecture 和 Guides 下的开发者章节。

如果某个流程依赖租户作用域、租户品牌或租户级权限，请先阅读 [Admin9 Tenancy Supplement](/zh/guides/admin9-tenancy)，再直接套用运营步骤。
