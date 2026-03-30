---
title: 应用结构
description: 共享 Admin9 应用的目录级地图，以及各类关注点应扩展的位置。
---

当你已经知道要改什么，但不清楚对应目录时，本页是最快的代码库定位入口。

## 适用范围

本页可作为以下产品的共享目录地图：

- `admin9`
- `admin9-tenancy`

在多租户变体中，围绕这里描述的共享结构，通常还会有额外的租户相关目录、模型、中间件或服务。

## 顶层目录

### `app/`

主应用命名空间。

- `Client/` 外部服务客户端
- `Console/Commands/` 自定义 Artisan 命令
- `Constants/` 应用枚举与常量
- `Dto/` 传输与状态对象
- `Events/` 按业务域组织的事件
- `Exceptions/` 领域或传输异常
- `Filament/` 管理后台与仪表盘的 Resource、Page、Widget
- `Http/Controllers/` 路由控制器
- `Http/Middleware/` 自定义 HTTP 中间件
- `Listeners/` 事件监听器
- `Livewire/` 前端交互组件
- `Mail/` mailables
- `Mapper/` 映射辅助工具
- `Models/` Eloquent 模型
- `Notifications/` 通知
- `Policies/` 授权策略
- `Providers/` 服务提供者与面板提供者
- `Services/` 业务逻辑
- `Support/` 通用支持工具
- `Validator/` 自定义校验逻辑
- `View/Components/` Blade 视图组件

### `config/`

运行配置目录，包括：

- auth
- cache
- cookie consent
- CORS
- database
- filesystems
- Filament
- Horizon
- invoices
- localization
- mail
- permission
- queue
- Sanctum
- services
- session
- Telescope
- two-factor auth

### `database/seeders/`

同时包含基础种子与专项种子：

- 根目录中的生产可用基础 seeders
- `Demo/` 下的演示 seeders
- `Testing/` 下的测试 seeders

### `resources/`

前端资源与 Blade 模板。

重点目录：

- `resources/css/`
- `resources/js/`
- `resources/views/`

### `routes/`

- `web.php`：浏览器路由
- `api.php`：Webhook 风格 API 路由
- `channels.php`
- `console.php`

### `tests/`

关键应用行为的自动化测试。

## 新功能放在哪里

### 新增后台管理功能

常见改动点：

- `app/Filament/Admin/Resources`
- `app/Filament/Admin/Pages`
- `app/Services`
- `app/Models`
- `database/migrations`

### 新增面向用户的仪表盘能力

常见改动点：

- `app/Filament/Dashboard`
- `app/Livewire`
- `app/Services`
- `resources/views`

### 新增支付或验证服务商

常见改动点：

- `app/Services/PaymentProviders`
- `app/Services/VerificationProviders`
- `app/Http/Controllers/PaymentProviders`
- `config/services.php`
- `.env`
- seeders if the provider should exist by default

### 新增公共内容板块

常见改动点：

- `routes/web.php`
- `app/Http/Controllers`
- `resources/views`
- admin-side Filament resources if the content is editable

## 指导原则

如果一次改动同时包含编排逻辑与服务商 SDK 细节，请将编排留在 service 层，把服务商实现隔离在接口或专用实现后面。

对于 `admin9-tenancy`，同样适用这条规则：租户解析与租户作用域应显式实现，不要把租户判断散落到无关模块中。
