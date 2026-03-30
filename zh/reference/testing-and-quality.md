---
title: 测试与质量
description: 共享 Admin9 代码库的测试执行、静态分析、格式化与质量基线。
---

在合并或发布前，本页可作为保障代码库健康的检查项速查。

## 主要命令

运行应用测试套件：

```bash
vendor/bin/phpunit
```

运行静态分析：

```bash
vendor/bin/phpstan analyse
```

运行格式化：

```bash
vendor/bin/pint
```

格式化或检查前端相关源码：

```bash
npm run format
npm run format:check
```

## 构建验证

发布前还应执行：

```bash
npm run build
```

这能捕获仅做 PHP 检查时不易暴露的前端资源构建问题。

## 测试环境说明

仓库包含 `.env.testing`，且 Laravel 常规实践默认测试运行不应与日常开发共用同一数据库。

推荐实践：

- 维护独立测试数据库
- 确保 `.env.testing` 指向该库
- 不要在日常本地数据库上执行破坏性测试流程

## 优先测试内容

在本代码库中，优先覆盖以下场景：

- 结账流程
- 支付 Webhook
- 订阅生命周期变更
- 认证与验证流程
- 本次发布启用的提供商集成

现有可见测试已覆盖法律页面、推荐返利、余额处理、充值流程和若干核心服务。Webhook 与认证提供商相关回归仍需在发布前显式验证，因为这类问题更容易遗漏。

## 发布最低门槛

首版发布可采用以下质量基线：

- `vendor/bin/phpunit`
- `vendor/bin/phpstan analyse`
- `vendor/bin/pint`
- `npm run build`

以上任一项失败，都应视为发布尚未就绪。
