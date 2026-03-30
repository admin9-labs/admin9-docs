---
title: 支付 Webhook 与本地测试
description: 在共享 Admin9 技术栈中，使用 Stripe CLI 与 ngrok 流程进行本地支付 Webhook 测试的方法。
---

如果你的本地计费调试依赖支付提供商回调，本页就是对应的流程参考。

## 适用范围

本 Webhook 流程适用于：

- `admin9`
- `admin9-tenancy`

如果你在测试 `admin9-tenancy`，在认定本地流程有效前，先确认转发回调能解析到正确的租户上下文。

## 当前 Webhook 路由

当前共享应用暴露以下端点：

- `/api/payments-providers/stripe/webhook`
- `/api/payments-providers/paddle/webhook`
- `/api/payments-providers/lemon-squeezy/webhook`

这些路径属于对发布敏感的集成点。

## Stripe 本地流程

最直接的本地方案是用 Stripe CLI 把事件转发到本地应用。

示例：

```bash
stripe listen --forward-to localhost:8080/api/payments-providers/stripe/webhook --skip-verify
```

如果应用不运行在 `localhost:8080`，请按实际主机和端口调整命令。

## Paddle 与 Lemon Squeezy 本地流程

仓库已提供包含 `ngrok` 服务的 Docker Compose 配置。可用它为需要公网回调 URL 的提供商暴露本地 Webhook 端点。

`.env.example` 相关环境变量：

```env
NGROK_AUTHTOKEN=
NGROK_STATIC_DOMAIN=
FORWARD_NGROK_PORT=4040
```

典型流程：

1. 配置 ngrok 凭据
2. 启动 Docker Compose 服务栈
3. 打开 ngrok inspector
4. 将提供商沙箱 webhook 地址指向转发后的公网 URL

## 本地测试需要验证的内容

- webhook 投递能到达预期路由
- 签名校验成功
- 交易记录正确更新
- 订阅或订单状态变更被正确持久化
- 在当前队列配置下，相关副作用仍可正常执行

## 常见失败场景

- 本地端口错误
- 提供商控制台仍指向旧的 ngrok 域名
- webhook 密钥错误
- 副作用依赖队列任务时，queue worker 未运行
- 提供商凭据变更后仍使用旧缓存配置

## 建议测试矩阵

发布前至少模拟：

- 结账成功
- 支付失败
- 订阅续费或等价周期性事件
- 如果发布范围支持，测试退款或取消流程

## 团队规则

计费相关改动在合并前，必须至少通过当前本地环境回放一次真实或沙箱 webhook。
