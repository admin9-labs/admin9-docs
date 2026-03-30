---
title: 安装
description: 从源码启动共享 Admin9 应用技术栈的全新安装说明。
---

全新环境请从这里开始；当技术栈跑起来后，日常请以本地开发指南为主。

## 适用范围

本页是以下两个产品的共享安装基线：

- `admin9`（单租户）
- `admin9-tenancy`（多租户）

如果你安装的是多租户变体，请先完成本页步骤，再阅读 [Admin9 多租户补充说明](/zh/guides/admin9-tenancy) 了解租户特有差异。

## 环境要求

- PHP 8.2 或更新版本
- Composer
- Node.js 与 npm
- MySQL 8
- Redis
- Mailpit 或其他本地 SMTP 接收器

仓库还提供基于 Laravel Sail 的 Docker Compose 方案，这是获得可复现本地环境的最快路径。

## 克隆并安装

```bash
git clone git@github.com:admin9-labs/admin9.git
cd admin9

composer install
npm install
cp .env.example .env
php artisan key:generate
```

如果你使用多租户仓库，请替换为对应的 `admin9-tenancy` 克隆地址与工作目录。

## 配置环境变量

默认 `.env.example` 使用 Docker Compose 服务名：

```env
DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=sail
DB_PASSWORD=password

REDIS_HOST=redis
MAIL_HOST=mailpit
MAIL_PORT=1025
QUEUE_CONNECTION=sync
```

如果你不使用 Docker Compose，请将这些主机名改为你的本地服务地址。

## 准备数据库

```bash
php artisan migrate:fresh --seed
```

默认 seeder 当前会初始化：

- intervals
- currencies
- OAuth login providers
- payment providers
- roles and permissions
- email providers
- verification providers
- FAQs
- legal pages

## 启动应用

原生本地运行：

```bash
npm run dev
php artisan serve
```

Laravel Sail 流程：

```bash
./vendor/bin/sail up -d
./vendor/bin/sail artisan migrate:fresh --seed
./vendor/bin/sail npm run dev
```

## 首批验证 URL

- `/`：官网营销站点
- `/admin`：Filament 管理后台
- `/dashboard`：已登录用户仪表盘
- `/blog`
- `/roadmap`

如果这些路由都能正常访问，说明核心 HTTP 层工作正常。
