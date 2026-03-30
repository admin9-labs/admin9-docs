---
title: 设置矩阵
description: Admin9 主要管理设置页及其职责范围。
---
知道要改设置，但不知道在哪个页面时，就看这页。

## 访问限制

这些设置页面都受同一套访问限制控制：

- 必须通过 `ConfigService::isAdminSettingsEnabled()` 启用管理设置
- 管理员用户必须具备 `update settings` 权限

如果某个设置页在生产环境中缺失，请先检查这两个条件。

## 设置页面

### General Settings

- 全站行为配置
- 与分析相关的设置
- 注册或登录相关开关
- reCAPTCHA 相关设置
- 社交链接及类似公开元数据

另见：[General Settings](/zh/admin-guide/general-settings)

### Invoice Settings

- 发票生成行为
- 发票展示要求
- 生成发票上必须出现的企业信息

另见：[Invoice Settings](/zh/admin-guide/invoice-settings)

### Legal Pages Settings

- `/terms-of-service`
- `/privacy-policy`

另见：[Legal Pages and Compliance](/zh/admin-guide/legal-pages-and-compliance)

### Open Graph Image Settings

- 社交预览素材
- 发布品牌一致性
- 分享卡片展示效果

这在首次发布前尤其重要，因为社交预览通常是外部用户对产品的第一印象之一。

另见：[Analytics and Open Graph](/zh/admin-guide/analytics-and-open-graph)

### Referral Settings

- 推荐激励
- 运营上线策略
- 推荐规则与公开沟通的一致性

另见：[Referral Settings](/zh/admin-guide/referral-settings)

## 推荐运营流程

1. 在 staging 环境复查所有设置页面。
2. 确认没有页面仍保留测试值或占位值。
3. 验证每个设置页面都与 `.env` 及对外行为一致。
4. 记录发布后每个设置域的负责人。

## 相关指南

- [General Settings](/zh/admin-guide/general-settings)
- [Invoice Settings](/zh/admin-guide/invoice-settings)
- [Legal Pages and Compliance](/zh/admin-guide/legal-pages-and-compliance)
- [Analytics and Open Graph](/zh/admin-guide/analytics-and-open-graph)
- [Referral Settings](/zh/admin-guide/referral-settings)
- [Launch Runbook](/zh/admin-guide/launch-runbook)
