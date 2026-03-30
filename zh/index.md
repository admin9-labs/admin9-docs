---
title: 概览
description: 安装、开发、运营与查阅 Admin9。
---

## 目录

<CardGroup cols={2}>
  <Card title="安装 Admin9" href="/zh/getting-started/installation">
    安装环境并启动项目。
  </Card>
  <Card title="本地开发" href="/zh/getting-started/local-development">
    查看日常命令和开发环境。
  </Card>
  <Card title="后台运营" href="/zh/admin-guide/overview">
    查看 `/admin` 里的常见操作。
  </Card>
  <Card title="开源项目" href="/zh/open-source/overview">
    查看相关仓库和 starter 项目。
  </Card>
</CardGroup>

## 技术栈

- PHP 8.2+
- Laravel 12
- Livewire 4
- Filament 5
- Tailwind CSS 4
- DaisyUI 5
- Vite 7
- Laravel Sanctum（API Token）
- Laravel Horizon（Redis 队列）

## 阅读顺序

1. 先读 [安装](/zh/getting-started/installation) 与 [本地开发](/zh/getting-started/local-development)。
2. 再读 [架构](/zh/architecture/overview)。
3. 再看 [命令与端点](/zh/reference/commands-and-endpoints) 与 [发布检查清单](/zh/deployment/release-checklist)。

如果你主要在 `/admin` 工作，直接看 [管理后台](/zh/admin-guide/overview)。

如果你主要看仓库，直接看 [开源仓库](/zh/open-source/overview)。

## 其他页面

- [认证与身份](/zh/guides/authentication-and-identity)
- [支付与计费](/zh/guides/payments-and-billing)
- [本地化与主题](/zh/guides/localization-and-theming)
- [配置系统](/zh/guides/configuration-system)
- [支付 Webhook 与本地测试](/zh/guides/payment-webhooks-and-local-testing)
- [事件与扩展点](/zh/guides/events-and-extension-points)

如果文档描述与产品实际行为不一致，请以对应产品仓库实现为准。
