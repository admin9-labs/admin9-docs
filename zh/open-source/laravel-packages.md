---
title: Laravel 软件包
description: 可复用 Laravel 软件包。
---
要找可复用软件包，而不是 starter 应用时，看这页。

## 身份与认证

### laravel-oidc-client

- Repository: [`admin9-labs/laravel-oidc-client`](https://github.com/admin9-labs/laravel-oidc-client)
- 主语言：PHP
- 许可证：MIT

这个包为 Laravel 提供支持授权码流程和 PKCE 的 OpenID Connect 客户端。Laravel 应用要接外部身份提供方时，可以用它。

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

这个包为 DaisyUI 5 组件提供 Laravel 友好的 Blade 封装。想复用 UI 基础组件时可以直接用。

### laravel-scramble-extensions

- Repository: [`admin9-labs/laravel-scramble-extensions`](https://github.com/admin9-labs/laravel-scramble-extensions)
- 主语言：PHP
- 许可证：MIT

该软件包扩展了基于 Scramble 的 API 文档工作流，面向 business-response 风格 API。公开说明重点包括：

- response envelope 生成
- 基于 scene 的 form request 提取
- 过滤类 query 参数提取
