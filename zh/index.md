---
title: Admin9 Labs 文档
description: Admin9 通用文档、产品变体、后台运营与开源仓库的组织级入口。
---

从这里开始，先选择适合你的 Admin9 Labs 文档路径，再进入产品部署、后台运营或仓库探索。

## 选择你的路径

<CardGroup cols={2}>
  <Card title="Admin9 产品变体" href="/zh/products/admin9-variants">
    对比单租户产品 `admin9` 与多租户变体 `admin9-tenancy`，了解哪些文档是共享的。
  </Card>
  <Card title="共享文档" href="/zh/getting-started/installation">
    使用主文档完成安装、架构、指南与发布工作，这些内容适用于两个变体。
  </Card>
  <Card title="多租户补充说明" href="/zh/guides/admin9-tenancy">
    当涉及租户边界、租户开通或租户级运营时，请阅读多租户补充文档。
  </Card>
  <Card title="开源项目总览" href="/zh/open-source/overview">
    浏览 Admin9 Labs 维护的公开仓库、starter 项目与可复用包。
  </Card>
</CardGroup>

## 文档结构

本站分为三大文档区域：

- Docs：共享的产品安装、开发、架构、指南与发布流程
- Admin Docs：面向运营人员的后台面板工作流
- Open Source：公开仓库与可复用包文档

在主文档中，`admin9` 是单租户变体，`admin9-tenancy` 是多租户变体。大多数页面共用；仅多租户差异集中在补充说明中。

## 主文档覆盖内容

- 发布带管理后台和用户仪表盘的订阅制 SaaS
- 管理产品、套餐、定价、折扣、发票与交易
- 支持 Stripe、Paddle、Lemon Squeezy 与线下支付流程
- 提供认证、验证与社交登录流程
- 提供多语言、可换肤的前端页面与内置运营工具

## 快速开始

<CardGroup cols={2}>
  <Card title="确认产品变体" href="/zh/products/admin9-variants">
    在使用共享指南前，先确认你在单租户还是多租户产品上工作。
  </Card>
  <Card title="安装产品" href="/zh/getting-started/installation">
    基于当前 Laravel、Livewire、Filament 技术栈，从源码搭建 Admin9。
  </Card>
  <Card title="本地运行" href="/zh/getting-started/local-development">
    启动 MySQL、Redis、Vite、队列以及应用主要入口。
  </Card>
  <Card title="阅读多租户说明" href="/zh/guides/admin9-tenancy">
    在租户边界影响架构或运营时，按补充说明应用多租户差异。
  </Card>
</CardGroup>

## 当前技术栈

当前代码库依赖：

- PHP 8.2+
- Laravel 12
- Livewire 4
- Filament 5
- Tailwind CSS 4
- DaisyUI 5
- Vite 7
- Laravel Sanctum（API Token）
- Laravel Horizon（Redis 队列）

## 共享平台能力

- 位于 `/admin` 的管理后台，用于产品、内容、营收与设置管理
- 位于 `/dashboard` 的用户仪表盘
- 订阅结账与一次性购买结账
- Stripe、Paddle、Lemon Squeezy 与线下支付流程
- OAuth 社交登录
- 双因素认证
- 角色与权限管理
- 博客、路线图、公告、FAQ、法律页面
- 带本地化 URL 的多语言前端路由
- DaisyUI 主题切换与 Filament 状态同步

## 推荐阅读顺序

1. 先读 [Admin9 产品变体](/zh/products/admin9-variants)，确认你在单租户还是多租户产品上工作。
2. 再读 [安装](/zh/getting-started/installation) 与 [本地开发](/zh/getting-started/local-development)。
3. 接着阅读 [架构总览](/zh/architecture/overview) 与共享指南。
4. 如果你使用 `admin9-tenancy`，凡是涉及租户边界的实现都补读 [Admin9 多租户补充说明](/zh/guides/admin9-tenancy)。
5. 发布前使用 [命令与端点](/zh/reference/commands-and-endpoints) 与 [发布检查清单](/zh/deployment/release-checklist)。

如果你主要在 `/admin` 工作，完成安装流程后可转到 [后台概览](/zh/admin-guide/overview)。

如果你的目标是评审开源仓库而不是部署 Admin9 产品，请转到 [开源总览](/zh/open-source/overview)。

## 核心指南

- [认证与身份](/zh/guides/authentication-and-identity)
- [支付与计费](/zh/guides/payments-and-billing)
- [本地化与主题](/zh/guides/localization-and-theming)
- [配置系统](/zh/guides/configuration-system)
- [支付 Webhook 与本地测试](/zh/guides/payment-webhooks-and-local-testing)
- [事件与扩展点](/zh/guides/events-and-extension-points)

如果文档描述与产品实际行为不一致，请以对应产品仓库实现为准。
