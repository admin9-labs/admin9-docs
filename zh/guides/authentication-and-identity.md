---
title: 认证与身份
description: Admin9 中的认证、社交登录、验证流程、双因素认证与令牌相关行为。
---

涉及登录、验证、身份状态或令牌时，先看这页。

## 认证核心构件

- 基于 `Auth::routes()` 的 Laravel 认证路由
- 基于 `MustVerifyEmail` 的邮箱验证
- 基于 Laravel Socialite 的社交登录
- 基于 `laragear/two-factor` 的双因素认证
- 基于 Sanctum 的 API Token 支持

## User 模型

`User` 模型实现了：

- Filament 面板访问控制
- 邮箱验证
- 角色与权限分配
- 一次性密码
- 双因素认证

`User` 模型同时用于后台访问和用户侧认证。

## 社交登录

公开 Web 路由提供：

- `/auth/{provider}/redirect`
- `/auth/{provider}/callback`

支持的提供商包括：

- Google
- GitHub
- Facebook
- Twitter OAuth 2
- LinkedIn OpenID
- Bitbucket
- GitLab

回调控制器会把提供商相关元数据以配置式字段写入用户记录，包括 provider id、token、refresh token、avatar、nickname 以及可用时的过期时间信息。

## 邮箱与手机号验证

Web 层包含：

- 邮箱验证提示与签名验证链接流程
- 手机号验证路由与专用验证视图

要确认注册流程、注册后跳转行为以及各类验证门禁规则与产品预期一致。

## 双因素认证

双因素认证在 Dashboard 的 Filament 面板中提供。

相关 Dashboard 页面包括：

- `TwoFactorAuth`
- `EnableTwoFactorAuth`
- `ConfirmTwoFactorAuth`
- `RecoveryCodes`

只有在 `config('app.two_factor_auth_enabled')` 开启时，Dashboard 面板才会显示 2FA 菜单项。

## OIDC 配置

仓库在 `.env.example` 中包含 `OIDC_ISSUER` 环境变量，但默认路由并未暴露 `/oauth/*` 授权服务器端点，且 `composer.json` 也未直接依赖 `laravel/passport`。

因此，OAuth2 / OpenID Connect 的提供方行为需要先在部署环境里验证。

## 运维检查清单

- 验证登录与登出
- 验证邮箱验证流程
- 对每个已启用社交提供商做端到端验证
- 验证 2FA 开通与恢复码
- 将 admin 访问规则与 dashboard 访问规则分开验证
- 仅在确认部署应用确实暴露所需端点后，再验证外部身份提供方集成
