---
title: 命令与端点
description: 常用开发命令、面板路径与应用端点。
---

不想翻完整文档时，可以直接查这页。

## 常用命令

### 前端

```bash
npm run dev
npm run build
npm run format
npm run format:check
```

### 后端

```bash
php artisan serve
php artisan migrate
php artisan migrate:fresh --seed
php artisan queue:work
php artisan horizon
```

### 质量检查

```bash
vendor/bin/phpunit
vendor/bin/phpstan analyse
vendor/bin/pint
```

### 部署

```bash
php dep deploy
```

## 面板路由

- `/admin`
- `/dashboard`

## 公共路由

`routes/web.php` 中定义的重点路由：

- `/`
- `/blog`
- `/blog/category/{slug}`
- `/blog/{slug}`
- `/roadmap`
- `/roadmap/i/{itemSlug}`
- `/roadmap/suggest`
- `/terms-of-service`
- `/privacy-policy`

## 认证与验证路由

- `/email/verify`
- `/email/verify/{id}/{hash}`
- `/email/verification-notification`
- `/phone/verify`
- `/phone/verified`
- `/registration/thank-you`
- `/auth/{provider}/redirect`
- `/auth/{provider}/callback`

路由约束允许的 provider 值：

- `google`
- `github`
- `facebook`
- `twitter-oauth-2`
- `linkedin-openid`
- `bitbucket`
- `gitlab`

## 结账与订阅路由

- `/checkout/plan/{planSlug}`
- `/checkout/convert-subscription/{subscriptionUuid}`
- `/checkout/subscription/success`
- `/checkout/convert-subscription-success`
- `/subscription/{subscriptionUuid}/change-plan/{planSlug}`
- `/already-subscribed`

## 一次性购买与余额路由

- `/buy/product/{productSlug}/{quantity?}`
- `/checkout/product`
- `/checkout/product/success`
- `/dashboard/balance`
- `POST /dashboard/balance/topup`
- `/dashboard/balance/topup/success`
- `/dashboard/balance/topup/cancel`

## 发票路由

- `/invoice/generate/{transactionUuid}`
- `/invoice/preview`

## 支付提供商路由

浏览器路由：

- `/payment-provider/paddle/payment-link`

`routes/api.php` 中的 Webhook API 路由：

- `/api/payments-providers/stripe/webhook`
- `/api/payments-providers/paddle/webhook`
- `/api/payments-providers/lemon-squeezy/webhook`

注意：代码库里的路径段是 `payments-providers`。除非你明确要做破坏性路由变更，否则不要改。
