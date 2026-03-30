---
title: Laravel 软件包
description: 由 Admin9 Labs 发布的可复用 Laravel 软件包。
---
当你需要来自 Admin9 Labs 的可复用软件包，而不是完整的 starter 应用时，更适合查看本页。

## 身份与认证

### laravel-oidc-client

- Repository: [`admin9-labs/laravel-oidc-client`](https://github.com/admin9-labs/laravel-oidc-client)
- 主语言：PHP
- 许可证：MIT

该软件包为 Laravel 实现了一个支持授权码流程与 PKCE 的 OpenID Connect 客户端。当你的 Laravel 应用需要通过标准 OIDC 流程对接外部身份提供方认证时，它非常合适。

### laravel-oidc-server

- Repository: [`admin9-labs/laravel-oidc-server`](https://github.com/admin9-labs/laravel-oidc-server)
- 主语言：PHP
- 许可证：MIT

该软件包为 Laravel Passport 部署增加 OpenID Connect 服务端能力，包含 discovery 以及 JWKS、UserInfo、token introspection、token revocation、RP-initiated logout 等配套端点。

## UI 与开发体验

### blade-daisyui

- Repository: [`admin9-labs/blade-daisyui`](https://github.com/admin9-labs/blade-daisyui)
- 主语言：Blade
- 许可证：MIT

该软件包为 DaisyUI 5 组件提供了 Laravel 友好的 Blade 封装。对于希望复用 UI 基础组件、但不想从零自建 Blade 组件的团队很有帮助。

### laravel-scramble-extensions

- Repository: [`admin9-labs/laravel-scramble-extensions`](https://github.com/admin9-labs/laravel-scramble-extensions)
- 主语言：PHP
- 许可证：MIT

该软件包扩展了基于 Scramble 的 API 文档工作流，面向 business-response 风格 API。公开说明重点包括：

- response envelope 生成
- 基于 scene 的 form request 提取
- 过滤类 query 参数提取
