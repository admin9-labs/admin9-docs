---
title: Admin9 多租户补充说明
description: 面向使用 admin9-tenancy 的团队，补充单租户 admin9 之外的多租户特有要点。
---

本页说明 `admin9-tenancy` 相比共享 `admin9` 文档体系需要额外关注的关键区域。

## 范围

标准 Admin9 文档是基础；本补充文档只覆盖应用切换为多租户后发生变化的部分。

## 不变部分

以下内容通常可按同一方式理解：

- Laravel、Livewire、Filament、Tailwind、Vite 技术栈前提
- 本地开发流程
- 应用结构与 service 层约定
- 计费、身份、内容与服务商集成概念
- 不受租户边界影响的后台运营工作流

## 多租户变体的变化点

在 `admin9-tenancy` 中，通常需要额外设计与运营决策的方面包括：

- 租户识别与请求作用域
- 租户感知的数据隔离
- 租户开通与生命周期管理
- 租户级域名、品牌与配置
- 租户感知的计费归属与报表边界
- 平台超级管理员与租户管理员的职责划分

## 其余文档的阅读方式

阅读共享文档时，建议遵循以下解释规则：

- 将“全局设置页面”视为可能拆分为平台级设置与租户级设置
- 将后台流程视为需要明确区分运营方动作与租户管理员动作
- 除非实现明确是平台全局，否则默认路由、队列、任务、事件、缓存都应具备租户感知
- 邮件、OAuth、验证、支付等集成应视为可能在平台级或租户级配置

## 推荐验证点

在将任何共享 Admin9 指南应用到 `admin9-tenancy` 前，请先在多租户仓库确认：

- route and middleware tenant resolution
- tenant model and tenant ownership relationships
- database isolation strategy
- Filament panel boundaries
- configuration storage and tenant overrides
- billing entity ownership and reporting queries

## 文档约定

未来如果某页包含重要多租户行为，优先在该页增加简短的 `admin9-tenancy note` 小节，而不是复制整篇文档。
