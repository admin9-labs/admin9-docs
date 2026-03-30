---
title: Admin9 产品变体
description: 说明 Admin9 单租户与多租户产品的关系，以及哪些文档同时适用。
---

当你需要判断某篇文档适用于 `admin9`、`admin9-tenancy` 还是两者都适用时，请先阅读本页。

## 产品地图

Admin9 Labs 当前维护两个高度相关的应用产品：

- `admin9`：单租户版本
- `admin9-tenancy`：多租户版本

它们共享相同的核心技术栈、绝大多数产品概念，以及整体一致的文档结构。

## 共用内容

除非页面明确说明，否则以下内容默认适用于两个变体：

- 安装与本地开发流程
- 架构与应用结构
- 认证与身份流程
- 支付、计费、服务商与 Webhook
- 本地化、主题与配置模式
- 后台运营、发布检查与参考资料

## 差异点

两者最核心的差异是租户模型：

- `admin9` 作为单租户应用运行
- `admin9-tenancy` 增加了租户感知的应用行为与运营关注点

这些多租户差异记录在 [Admin9 多租户补充说明](/zh/guides/admin9-tenancy) 中。

## 阅读路径

如果你在 `admin9` 上工作：

1. 从 [安装](/zh/getting-started/installation) 开始。
2. 按标准 Admin9 文档标签继续阅读。

如果你在 `admin9-tenancy` 上工作：

1. 同样从 [安装](/zh/getting-started/installation) 开始。
2. 阅读相同的 Admin9 共享文档。
3. 凡是涉及租户边界、租户开通或租户运营的部分，补读 [Admin9 多租户补充说明](/zh/guides/admin9-tenancy)。

## 权威来源

涉及运行时行为时，请以对应产品仓库实现为准：

- 单租户行为以 `admin9` 仓库为准
- 多租户专有行为以 `admin9-tenancy` 仓库为准
