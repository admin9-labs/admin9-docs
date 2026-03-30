---
title: 本地开发
description: 日常开发流程、服务要求与常见环境任务。
---

安装完成后，本页将作为你日常本地命令、服务与环境预期的工作参考。

## 适用范围

本页由两个产品变体共享，可作为默认工作流：

- `admin9`
- `admin9-tenancy`

如果租户解析、租户域名或租户作用域任务影响你的本地环境，请补读 [Admin9 多租户补充说明](/zh/guides/admin9-tenancy)。

## 默认 Docker Compose 拓扑

仓库内置的 `docker-compose.yml` 包含以下服务：

- `laravel.test`
- `mysql`
- `mailpit`
- `redis`
- `ngrok`

`.env.example` 中相关端口映射：

- App: `APP_PORT=8080`
- Vite: `VITE_PORT=5173`
- MySQL: `FORWARD_DB_PORT=3306`
- Mailpit SMTP: `FORWARD_MAILPIT_PORT=1025`
- Mailpit UI: `FORWARD_MAILPIT_DASHBOARD_PORT=8025`
- Redis: `FORWARD_REDIS_PORT=6379`
- ngrok UI: `FORWARD_NGROK_PORT=4040`

## 日常命令

前端：

```bash
npm run dev
npm run build
```

后端：

```bash
php artisan serve
php artisan migrate
php artisan queue:work
php artisan horizon
```

测试与质量检查：

```bash
vendor/bin/phpunit
vendor/bin/phpstan analyse
vendor/bin/pint
```

## 当前代码库的开发前提

- `.env.example` 中队列默认是 `sync`，但已经安装了可用于 Redis worker 的 Horizon。
- 邮件默认使用 Mailpit。
- 支付、社交登录、Twilio 与 reCAPTCHA 凭据默认均为空，测试这些流程前需显式配置。
- `.env.example` 包含 `OIDC_ISSUER`，但在依赖 OAuth2 / OIDC 集成前应先确认服务端端点可用。

## 推荐本地启动顺序

1. 启动数据库、Redis 和邮件服务。
2. 执行 `php artisan migrate:fresh --seed`。
3. 启动 Vite。
4. 启动 Laravel 应用服务。
5. 登录 `/admin`，确认货币、服务商与法律内容等种子数据已存在。

## 常见开发检查项

修改支付或认证逻辑后：

- 确认 Web 路由仍可解析
- 确认 Webhook 端点在本地可达
- 确认队列驱动的副作用仍正常
- 确认 `/admin` 和 `/dashboard` 均可访问

修改本地化或前端导航后：

- 检查默认语言路由（无前缀）
- 检查非默认语言路由（带 `/zh/...`）
- 确认主题切换仍可正确更新 `data-theme` 状态
