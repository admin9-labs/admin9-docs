---
title: 提供商与集成
description: 管理后台中支付、邮件、OAuth 与验证提供商的配置入口总览。
---

本页是 `/admin` 的集成索引，帮助你在进入具体 provider 配置前，先把任务分流到正确的 provider 类型。

## 支付提供商

后台包含 `Payment Providers` 资源，且为以下 provider 提供专属设置页：

- Stripe
- Paddle
- Lemon Squeezy

该区域可用于：

- 启用或禁用 provider
- 审查 provider 记录
- 配置 provider 专属设置页
- 对齐后台配置与 `.env` 中的值

上线前：

- 核对 API 凭据
- 核对 webhook 密钥
- 核对沙箱与生产模式配置
- 对每个启用 provider 验证端到端结账流程

另见：[支付提供商](/zh/admin-guide/payment-providers)

## 邮件提供商

后台包含 `Email Providers` 资源，并提供以下专属设置页：

- SMTP
- Mailgun
- Postmark
- Amazon SES
- Resend

该区域应与实际邮件投递策略和 DNS 配置保持一致。

发布前：

- 核对发件身份
- 验证外发可达性
- 验证关键邮件模板渲染结果

另见：[邮件提供商](/zh/admin-guide/email-providers)

## OAuth 登录提供商

后台包含 `Oauth Login Providers` 资源，提供以下设置页：

- Google
- GitHub
- Facebook
- Twitter OAuth 2
- LinkedIn
- Bitbucket
- GitLab

使用本节控制公开认证页面可用的社交登录 provider。

发布前：

- 核对已启用 provider 与你的策略一致
- 核对 callback URL
- 核对各 provider 平台上的品牌与应用审批要求

另见：[OAuth 提供商](/zh/admin-guide/oauth-providers)

## 验证提供商

后台包含 `Verification Providers` 资源，并支持 Twilio 设置。

当你的发布方案包含手机验证或短信门控试用时，请使用本节。

另见：[验证提供商](/zh/admin-guide/verification-providers)

## 运营建议

建议维护内部 runbook，记录以下内容：

- 哪些设置保存在 `.env`
- 哪些设置保存在管理后台
- 凭据轮换由谁负责
- webhook 变更在生产发布前如何测试

## 使用顺序

1. 先用本页识别 provider 类型与责任模型。
2. 再进入对应 provider 页面执行字段级配置与校验。
3. 将最终生产值记录到发布 runbook 或内部凭据台账。
