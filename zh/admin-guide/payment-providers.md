---
title: 支付提供商
description: 共享 Admin9 栈中 Stripe、Paddle 与 Lemon Squeezy 的管理端配置与运营检查。
---
当你需要从管理端检查支付路由、凭据或提供商就绪状态时，请使用本指南。

## 适用范围

本页适用于：

- `admin9`
- `admin9-tenancy`

对于 `admin9-tenancy`，请确认提供商凭据与产品映射是全局管理、按租户管理，还是混合模式。

## 支持的提供商

管理资源包含以下提供商的专用设置页：

- Stripe
- Paddle
- Lemon Squeezy

Offline payment support exists at the application level, but the provider-specific admin settings pages currently focus on the hosted providers above.
应用层支持离线支付，但当前提供商专用管理设置页主要覆盖上述托管支付提供商。

## 运营人员应在此管理的内容

- 启用或禁用某个提供商
- 审核提供商记录
- 确认提供商专属配置完整
- 使管理端状态与部署环境变量配置保持一致

## 需要校验的环境变量

### Stripe

```env
STRIPE_SECRET_KEY=""
STRIPE_PUBLISHABLE_KEY=""
STRIPE_WEBHOOK_SIGNING_SECRET=""
```

### Paddle

```env
PADDLE_VENDOR_ID=""
PADDLE_CLIENT_SIDE_TOKEN=""
PADDLE_VENDOR_AUTH_CODE=""
PADDLE_PUBLIC_KEY=""
PADDLE_WEBHOOK_SECRET=""
PADDLE_IS_SANDBOX=true
```

### Lemon Squeezy

```env
LEMON_SQUEEZY_API_KEY=""
LEMON_SQUEEZY_STORE_ID=""
LEMON_SQUEEZY_SIGNING_SECRET=""
LEMON_SQUEEZY_IS_TEST_MODE=false
```

## 运营检查

发布前，对每个已启用提供商确认：

- 凭据有效
- sandbox 与 production 模式设置正确
- webhook secret 已配置
- 存在提供商侧产品或套餐映射
- 成功结账后能返回预期成功路由
- 失败或取消状态行为符合预期

## Webhooks

The webhook endpoints are:

- `/api/payments-providers/stripe/webhook`
- `/api/payments-providers/paddle/webhook`
- `/api/payments-providers/lemon-squeezy/webhook`

当切换域名或环境时，请更新提供商后台配置，确保 webhook 仍投递到正确的公网 URL。

## 发布建议

除非你已完整测试所有下游行为（包括结账、webhook 投递、发票生成和交易入库），否则不建议在生产环境同时启用多个支付提供商。
