---
title: 配置系统
description: 说明后台、数据库设置与缓存如何覆盖运行时配置。
---

运行时值来源不清楚时，看这页。

大致流程：

- 初始值来自 `config/*.php` 与 `.env`
- 部分设置可在后台覆盖
- 覆盖值写入数据库
- 运行时读取会走缓存，避免每次请求都访问数据库

很多后台设置页面都依赖这套机制。

## 为什么需要它

这样改设置时不需要每次重新部署。

典型场景包括：

- email provider credentials
- invoice metadata
- legal page content
- provider-specific settings
- site-level behavior exposed through admin pages

## 核心组件

代码中关键组件包括：

- `App\Services\ConfigService`
- `App\Models\Config`
- `App\Constants\ConfigConstants`

它们协同完成：

- decide which keys are overridable
- persist values to the database
- encrypt sensitive settings where required
- cache resolved values for runtime use

## 运行模型

当运营人员在 Filament 中修改设置时：

1. 设置页面或 Livewire 表单调用 `ConfigService::set(...)`
2. 按可覆盖 key 白名单校验该值
3. 将值写入 `configs` 表
4. 刷新运行时缓存值

因此，许多设置无需发版即可即时生效。

## 安全模型

并非所有配置 key 都应允许在后台编辑。

项目通过 `ConfigConstants` 使用白名单模型，只允许预期 key 被修改。敏感值通过加密配置定义单独处理。

这是正确模式。不要把设置系统改成“可写任意配置”的通用入口。

## 开发扩展模式

如果要在后台暴露一个新设置：

1. 在对应 Laravel 配置文件中定义 key
2. 将 key 加入允许覆盖的配置列表
3. 若包含密钥，标记为加密
4. 通过 Filament 页面或 Livewire 表单暴露给后台
5. 在应用代码中通过 Laravel `config` helper 读取

## 运营风险

- 清缓存后若未重新回填设置，可能导致运行时行为异常
- 长生命周期 worker 在重启前可能仍使用旧配置解析结果
- 若团队未定义清晰真值来源，后台凭据可能与 `.env` 漂移

## 推荐团队规则

对每个可配置项，都应明确真值来源是：

- `.env`
- admin-managed settings
- or a hybrid bootstrapping model where `.env` seeds the initial value and admin owns changes afterward

没有这个约定，线上排障会变慢。
