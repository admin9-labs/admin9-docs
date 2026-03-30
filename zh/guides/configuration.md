---
title: 配置
description: 发布前开发者需要掌握的环境变量、服务配置与关键开关。
---

在追踪某个具体服务或子系统前，先用本页建立完整配置视图。

## 适用范围

本页描述以下产品的共享配置基线：

- `admin9`
- `admin9-tenancy`

在多租户变体中，请将本页视为平台级默认配置，并额外确认哪些设置支持按租户覆盖。相关边界请阅读 [Admin9 多租户补充说明](/zh/guides/admin9-tenancy)。

## 核心应用设置

来自 `.env.example`：

```env
APP_NAME=ADMIN9
APP_ENV=local
APP_DEBUG=true
APP_URL=http://localhost
APP_TIMEZONE=UTC
```

`APP_URL` 是高影响配置，它会影响 URL 生成以及默认 OIDC issuer。

对于 `admin9-tenancy`，还要确认租户域名、租户子域名或租户级 URL 生成是否在默认 `APP_URL` 之外再增加一层逻辑。

## 数据库、会话、队列、缓存

```env
DB_CONNECTION=mysql
CACHE_DRIVER=file
QUEUE_CONNECTION=sync
SESSION_DRIVER=file
REDIS_HOST=redis
```

在生产环境中，请评估 `file` 与 `sync` 默认值是否仍然适用。大多数真实部署会使用 Redis 队列与缓存。

## 邮件

```env
MAIL_MAILER=smtp
MAIL_HOST=mailpit
MAIL_PORT=1025
MAIL_FROM_ADDRESS="hello@example.com"
```

代码库支持的邮件服务商包括 Mailgun、Postmark、Amazon SES 以及与 Resend 相关依赖。请确保所选 mailer 与凭据和 `config/mail.php`、`config/services.php` 保持一致。

## 社交登录

可用环境变量包括：

- `GOOGLE_CLIENT_ID`
- `GOOGLE_CLIENT_SECRET`
- `GITHUB_CLIENT_ID`
- `GITHUB_CLIENT_SECRET`
- `FACEBOOK_CLIENT_ID`
- `FACEBOOK_CLIENT_SECRET`

默认数据库 seeder 也会初始化 OAuth 登录服务商记录。

## 支付

当前已配置的服务商变量分组包括：

- Stripe
- Paddle
- Lemon Squeezy
- 通过应用领域模型支持的线下支付

`.env.example` 示例：

```env
STRIPE_SECRET_KEY=""
STRIPE_PUBLISHABLE_KEY=""
STRIPE_WEBHOOK_SIGNING_SECRET=""

PADDLE_VENDOR_ID=""
PADDLE_CLIENT_SIDE_TOKEN=""
PADDLE_WEBHOOK_SECRET=""
PADDLE_IS_SANDBOX=true

LEMON_SQUEEZY_API_KEY=""
LEMON_SQUEEZY_STORE_ID=""
LEMON_SQUEEZY_SIGNING_SECRET=""
LEMON_SQUEEZY_IS_TEST_MODE=false
```

## 验证与反滥用

应用还支持：

- reCAPTCHA
- Twilio-based SMS verification
- optional trial gating based on SMS verification

相关变量：

```env
RECAPTCHA_SITE_KEY=""
RECAPTCHA_SECRET_KEY=""
TWILIO_SID=""
TWILIO_TOKEN=""
TWILIO_FROM=""
TRIAL_WITHOUT_PAYMENT_SMS_VERIFICATION_ENABLED=false
```

## 分析与社交链接

环境文件中包含：

- `GOOGLE_TRACKING_ID`
- `TRACKING_SCRIPTS`
- social profile URLs for Facebook, X, Instagram, LinkedIn, YouTube, GitHub, and Discord

## 发布前重点检查的配置文件

- `config/app.php`
- `config/auth.php`
- `config/services.php`
- `config/queue.php`
- `config/horizon.php`
- `config/mail.php`
- `config/laravellocalization.php`
- `config/filament.php`
- `config/two-factor.php`
- `config/permission.php`

## 后台可管理设置

部分应用行为通过 Filament 管理，而不是写死在配置文件中。

主要后台设置页面包括：

- General settings
- Invoice settings
- Legal pages settings
- Open Graph image settings
- Referral settings

请在部署文档中写清哪些设置应通过 UI 配置，哪些应通过 `.env` 配置，方便运营侧执行。

对于 `admin9-tenancy`，还应标注哪些设置是平台全局，哪些由租户管理。

## 相关阅读

如果你要扩展或排查设置机制本身，请阅读 [配置系统](/zh/guides/configuration-system)。
