---
title: 发布运行手册
description: 面向运营人员的首次发布运行手册，用于在共享 Admin9 产品栈对外开放前完成最终检查。
---
在将新部署对外开放前，使用本运行手册协调管理端的最终检查。

## 适用范围

本运行手册是以下产品的共享发布基线：

- `admin9`
- `admin9-tenancy`

对于 `admin9-tenancy`，请将本手册作为默认运营检查清单，并补充租户专属发布检查项，如租户开通、租户域名、租户品牌以及平台与租户的职责边界。

## 何时使用本运行手册

当出现以下场景时使用本页：

- 你正在准备某个部署的首次公开发布
- 你需要对管理设置、内容和基础设施进行最终跨职能复核
- 你希望用一份统一发布清单串联运营任务

## 本运行手册范围

本运行手册默认前提：

- 核心实现工作已完成
- 提供商凭据已可用或即将配置
- 当前工作目标是验证上线就绪度，而不是从零设计功能

## 1. 冻结范围

在发布窗口前：

- 停止添加非关键功能
- 明确发布时支持的单一支付提供商或提供商组合
- 明确发布时支持的社交登录提供商
- 明确生产凭据与回滚决策的责任人

## 2. 完成管理配置

在 `/admin` 中，复核：

- products and plans
- one-time products if enabled
- discounts
- payment providers
- email providers
- OAuth providers
- verification providers
- general settings
- legal pages settings
- invoice settings
- referral settings
- Open Graph settings

## 3. 完成公开内容

确认：

- 首页文案与链接
- FAQ 内容
- 若用于发布，博客内容是否就绪
- 路线图可见性
- 公告
- 服务条款
- 隐私政策

## 4. 验证关键用户流程

在类生产环境中测试：

- registration
- email verification
- social login
- 2FA if enabled
- subscription checkout
- one-time purchase checkout
- payment webhook delivery
- invoice generation
- dashboard access
- admin access

## 5. 验证基础设施

- 已配置数据库备份
- 如队列依赖 Redis，则 Redis 正在运行
- Horizon 或队列 worker 正在运行
- 邮件投递已验证
- 已强制 HTTPS
- 公网回调 URL 正确

## 6. 验证可观测性

- 日志可访问
- 失败任务有监控
- 支付失败可被诊断
- 支持团队知道如何查看用户、订阅、订单和交易

## 7. 上线决策

仅在以下条件满足时发布：

- 所有发布关键流程全部通过
- 提供商凭据已确认
- 法务内容已就绪
- 不再存在占位品牌内容
- 责任人已就首个发布窗口的支持覆盖达成一致

## 相关指南

- [Products and Pricing](/zh/admin-guide/products-and-pricing)
- [Payment Providers](/zh/admin-guide/payment-providers)
- [Users and Access](/zh/admin-guide/users-and-access)
- [Support Playbook](/zh/admin-guide/support-playbook)
- [Content and Site Settings](/zh/admin-guide/content-and-site-settings)
- [Settings Matrix](/zh/admin-guide/settings-matrix)
