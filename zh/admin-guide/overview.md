---
title: 管理后台
description: Admin9 管理端页面与常见操作。
---
先看这页，再进入具体操作。

Admin9 主管理面板挂载在：

```text
/admin
```

这部分主要写给通过 Filament 管理应用的运营和维护人员。

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

## 常见内容

- 营收监控与 SaaS 指标
- 产品与套餐管理
- 一次性商品管理
- 折扣与优惠码
- 订阅、交易、订单、余额与余额流水
- 用户与角色管理
- 博客、公告、FAQ 与路线图条目
- 支付提供商、邮件提供商、OAuth 提供商与验证提供商配置
- 法务、发票、推荐与 Open Graph 设置

## 导航分组

- Revenue
- Product Management
- User Management
- Content
- Roadmap
- Settings

## 其他页面

- Dashboard
- General Settings
- Invoice Settings
- Legal Pages Settings
- Open Graph Image Settings
- Referral Settings

## 阅读顺序

### 1. Start Here

- [Overview](/zh/admin-guide/overview)：管理后台
- [Launch Runbook](/zh/admin-guide/launch-runbook)：首次发布准备
- [Settings Matrix](/zh/admin-guide/settings-matrix)：定位独立设置页面

### 2. 目录与营收运营

- [Products and Pricing](/zh/admin-guide/products-and-pricing)：目录、套餐、折扣与计费实体
- [Subscriptions and Transactions](/zh/admin-guide/subscriptions-and-transactions)：日常计费运营与审计轨迹
- [Payment Providers](/zh/admin-guide/payment-providers)：Stripe、Paddle、Lemon Squeezy 配置
- [Invoice Settings](/zh/admin-guide/invoice-settings)：发票生成与卖方元数据
- [Referral Settings](/zh/admin-guide/referral-settings)：推荐计划相关设置

### 3. 用户、访问与支持

- [Users and Access](/zh/admin-guide/users-and-access)：角色、权限与管理边界
- [OAuth Providers](/zh/admin-guide/oauth-providers)：社交登录运营
- [Verification Providers](/zh/admin-guide/verification-providers)：短信验证与试用门槛
- [Support Playbook](/zh/admin-guide/support-playbook)：上线后的问题分诊

### 4. 内容与站点运营

- [Content and Site Settings](/zh/admin-guide/content-and-site-settings)：高层内容面配置
- [Content Operations](/zh/admin-guide/content-operations)：博客、FAQ、公告与路线图流程
- [Legal Pages and Compliance](/zh/admin-guide/legal-pages-and-compliance)：服务条款、隐私政策与发布签核
- [General Settings](/zh/admin-guide/general-settings)：全站行为、分析、社交链接与 reCAPTCHA
- [Analytics and Open Graph](/zh/admin-guide/analytics-and-open-graph)：追踪与社交预览校验

### 5. 集成

- [Providers and Integrations](/zh/admin-guide/providers-and-integrations)：支付、邮件、OAuth 与验证配置
- [Email Providers](/zh/admin-guide/email-providers)：邮件投递配置与校验

## 不确定先看哪页

- 如果你在准备发布，从 [Launch Runbook](/zh/admin-guide/launch-runbook) 开始
- 如果你在处理线上客户问题，从 [Support Playbook](/zh/admin-guide/support-playbook) 开始
- 如果你知道任务属于设置页但不清楚具体页面，从 [Settings Matrix](/zh/admin-guide/settings-matrix) 开始

实现细节、扩展点与代码结构请看 Architecture 和 Guides。
