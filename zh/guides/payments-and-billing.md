---
title: 支付与计费
description: 支付提供商、计费流程、结账路由与 Webhook 注意事项。
---

涉及结账和计费时，先看这页。

## 支持的支付提供商

代码库已包含以下支付提供商的控制器与环境配置：

- Stripe
- Paddle
- Lemon Squeezy
- 线下支付

提供商层通过服务接口抽象，应用其他部分不需要关心 SDK 细节。

## 主要计费服务

计费相关关键服务包括：

- `PaymentService`
- `CheckoutService`
- `SubscriptionService`
- `SubscriptionDiscountService`
- `TransactionService`
- `InvoiceService`
- `OrderService`
- `BalanceTopupService`

排查计费问题时，先检查服务层，再看控制器。

## 订阅流程

核心订阅路由：

- `/checkout/plan/{planSlug}`
- `/checkout/convert-subscription/{subscriptionUuid}`
- `/checkout/subscription/success`
- `/checkout/convert-subscription-success`
- `/subscription/{subscriptionUuid}/change-plan/{planSlug}`

这些流程覆盖：

- 初次订阅开通
- 本地订阅转换
- 结账成功后的处理
- 已有订阅套餐变更

## 一次性商品流程

相关路由：

- `/buy/product/{productSlug}/{quantity?}`
- `/checkout/product`
- `/checkout/product/success`

该流程与订阅流程相互独立，应分别测试。

## 余额充值

余额管理是代码库里的核心功能之一。

相关路由：

- `/dashboard/balance`
- `POST /dashboard/balance/topup`
- `/dashboard/balance/topup/success`
- `/dashboard/balance/topup/cancel`

此外还包含专门的 `BalanceTopup` 服务命名空间，以及承载充值流程的 Dashboard 余额页面。

## Webhook

Webhook 端点如下：

- `/api/payments-providers/stripe/webhook`
- `/api/payments-providers/paddle/webhook`
- `/api/payments-providers/lemon-squeezy/webhook`

上线前请确认：

- 已配置 webhook 签名密钥
- 提供商可访问公开回调 URL
- 队列处理可正确执行后续副作用
- 对每个启用的提供商回放样例 webhook

关于本地开发与提供商回调测试，请参考 [Payment Webhooks and Local Testing](/zh/guides/payment-webhooks-and-local-testing)。

## 环境配置

以下示例来自 `.env.example`：

```env
STRIPE_SECRET_KEY=""
STRIPE_PUBLISHABLE_KEY=""
STRIPE_WEBHOOK_SIGNING_SECRET=""

PADDLE_VENDOR_ID=""
PADDLE_CLIENT_SIDE_TOKEN=""
PADDLE_VENDOR_AUTH_CODE=""
PADDLE_PUBLIC_KEY=""
PADDLE_WEBHOOK_SECRET=""
PADDLE_IS_SANDBOX=true

LEMON_SQUEEZY_API_KEY=""
LEMON_SQUEEZY_STORE_ID=""
LEMON_SQUEEZY_SIGNING_SECRET=""
LEMON_SQUEEZY_IS_TEST_MODE=false
```

## 建议验证项

- 为每个启用提供商创建结账会话
- 确认支付成功后生成预期的订阅或订单状态
- 验证发票生成
- 验证交易记录
- 验证折扣应用
- 验证套餐变更行为
- 验证取消或失败场景处理
