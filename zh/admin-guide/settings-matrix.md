---
title: 设置矩阵
description: Admin9 主要管理设置页及其职责范围的快速地图。
---
当任务目标明确但不清楚该去哪个页面时，可将本页视为管理设置的归属表。

## 适用范围

本设置地图适用于：

- `admin9`
- `admin9-tenancy`

对于 `admin9-tenancy`，在分配责任前请先判断每个设置页是平台全局、租户专属还是继承配置。

## 何时使用本页

当出现以下场景时使用本页：

- 你知道改动属于某个设置页面，但不确定具体是哪一个
- 你需要在发布评审前快速确认设置归属
- 你想确认任务属于内容、计费、法务还是推荐设置

## 访问模型

当前设置页面共享同一访问模式：

- 必须通过 `ConfigService::isAdminSettingsEnabled()` 启用管理设置
- 当前管理员用户必须具备 `update settings` 权限

如果某个设置页在生产环境中缺失，请先检查这两个条件。

## 设置页面

### General Settings

本页用于全站级的运营与展示配置。

常见范围：

- 全站行为配置
- 与分析相关的设置
- 注册或登录相关开关
- reCAPTCHA 相关设置
- 社交链接及类似公开元数据

另见：[General Settings](/zh/admin-guide/general-settings)

### Invoice Settings

本页用于发票相关配置与输出检查。

常见范围：

- 发票生成行为
- 发票展示要求
- 生成发票上必须出现的企业信息

另见：[Invoice Settings](/zh/admin-guide/invoice-settings)

### Legal Pages Settings

本页用于配置以下地址展示的公开法务文档：

- `/terms-of-service`
- `/privacy-policy`

另见：[Legal Pages and Compliance](/zh/admin-guide/legal-pages-and-compliance)

### Open Graph Image Settings

本页用于社交分享图默认配置或生成式 OG 图片行为。

常见范围：

- 社交预览素材
- 发布品牌一致性
- 分享卡片展示效果

这在首次发布前尤其重要，因为社交预览通常是外部用户对产品的第一印象之一。

另见：[Analytics and Open Graph](/zh/admin-guide/analytics-and-open-graph)

### Referral Settings

本页用于推荐计划行为与奖励参数调整。

常见范围：

- 推荐激励
- 运营上线策略
- 推荐规则与公开沟通的一致性

另见：[Referral Settings](/zh/admin-guide/referral-settings)

## 推荐运营流程

1. 发布前在 staging 环境复查所有设置页面。
2. 确认没有页面仍保留测试值或占位值。
3. 验证每个设置页面都与 `.env` 及对外行为一致。
4. 记录发布后每个设置域的负责人。

在 `admin9-tenancy` 中，还应记录职责归属是平台团队还是租户管理员。

## 相关指南

- [General Settings](/zh/admin-guide/general-settings)
- [Invoice Settings](/zh/admin-guide/invoice-settings)
- [Legal Pages and Compliance](/zh/admin-guide/legal-pages-and-compliance)
- [Analytics and Open Graph](/zh/admin-guide/analytics-and-open-graph)
- [Referral Settings](/zh/admin-guide/referral-settings)
- [Launch Runbook](/zh/admin-guide/launch-runbook)
