---
title: 分析与 Open Graph
description: 发布前在管理后台完成分析追踪与社交预览配置的操作指引。
---

本指南用于发布与市场检查阶段，重点确认追踪行为与链接预览是否已完成最终校验。

## 分析追踪

代码库显示可通过后台设置与环境变量实现 Google Analytics 风格追踪，例如：

- `GOOGLE_TRACKING_ID`
- `TRACKING_SCRIPTS`

发布前：

- 确认 tracking ID 为生产值
- 清理测试用分析属性 ID
- 审查自定义追踪脚本的安全性与必要性

分析配置错误在开发期很容易被忽略，因此请将其作为明确的发布清单项。

## Open Graph

ADMIN9 提供了 `Open Graph Image Settings` 页面及相关 Open Graph 配置文件。

该区域决定链接在以下平台中的分享展示效果：

- X
- Facebook
- LinkedIn
- chat apps that consume OG metadata

发布前：

- 确认默认 OG 图片使用真实品牌资产
- 确认首页与主要公开页面生成的预览符合预期
- 确认 staging/测试品牌素材未泄漏到生产内容

在发布流程中至少安排一次手工社交预览检查。即使技术上线成功，若 OG 资源或分析设置错误，整体观感仍会显得未完成。
