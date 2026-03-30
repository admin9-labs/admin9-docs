---
title: OAuth 提供商
description: 在管理后台维护社交登录提供商，并检查回调配置。
---

要启用、检查或修复社交登录时，看这页。

## 支持的提供商

管理侧提供商设置页包括：

- Google
- GitHub
- Facebook
- Twitter OAuth 2
- LinkedIn
- Bitbucket
- GitLab

这些与认证控制器在公开路由上允许的 provider 范围保持一致。

## 公开认证路由

社交登录使用：

- `/auth/{provider}/redirect`
- `/auth/{provider}/callback`

如果在后台启用了某个 provider，但其开发者平台或运行环境配置不完整，用户流程通常会在 redirect 或 callback 阶段失败。

## 检查项

- 哪些 provider 对用户可见
- 某个 provider 是否已获准用于生产环境
- callback URL 是否与部署域名一致
- 上游 provider 控制台中的品牌与合规项是否已完成

## 配置一致性

部署环境必须与后台启用的 provider 列表一致。

`.env.example` 中的示例变量包括：

- `GOOGLE_CLIENT_ID`
- `GOOGLE_CLIENT_SECRET`
- `GITHUB_CLIENT_ID`
- `GITHUB_CLIENT_SECRET`
- `FACEBOOK_CLIENT_ID`
- `FACEBOOK_CLIENT_SECRET`

`config/services.php` 中也有 provider 级配置项，包括 Twitter OAuth 2 的 callback 配置。

## 上线前检查

- 关闭尚未准备好对外支持的 provider
- 在各 provider 控制台核对 redirect URI 注册配置
- 验证首次登录用户能成功创建账户
- 验证已有用户可成功登录
- 验证当 provider 未返回预期用户字段时的邮箱处理逻辑

只启用在目标环境完成端到端验证的 provider。发布期社交登录问题可见性极高，常见根因是 callback 不匹配或 provider 应用配置不完整。
