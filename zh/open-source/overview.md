---
title: 开源总览
description: Admin9 Labs 维护的公开开源项目及其相互关系。
---

如果你在选择 starter、package 或配套项目前需要先看公开仓库全景，请先阅读本页。

## 如何使用本节

- 若你想先了解哪些仓库属于产品、可复用包或支撑基础设施，从这里开始。
- 若你在评估完整 starter kit 或参考应用，请看 [Application Starters](/zh/open-source/application-starters)。
- 若你需要认证、OIDC、UI 或 API 文档相关可复用包，请看 [Laravel Packages](/zh/open-source/laravel-packages)。

## 项目组合地图

<CardGroup cols={2}>
  <Card title="应用 Starter" href="/zh/open-source/application-starters">
    可直接克隆并扩展的完整仓库，覆盖 API、Web 与文档层面。
  </Card>
  <Card title="Laravel 包" href="/zh/open-source/laravel-packages">
    用于 OpenID Connect、DaisyUI Blade 组件与 Scramble 扩展的可复用包。
  </Card>
</CardGroup>

## 仓库地图

### 产品与 Starter 仓库

- [`admin9-api`](https://github.com/admin9-labs/admin9-api)：Laravel 12 REST API 脚手架，内置 JWT 认证、RBAC、服务层结构、审计事件与测试。
- [`admin9-web`](https://github.com/admin9-labs/admin9-web)：基于 Vue 的前端 SPA starter，设计上与 `admin9-api` 搭配使用。
- [`admin9-docs`](https://github.com/admin9-labs/admin9-docs)：Admin9 Labs 文档站的 Mintlify 文档源码仓库。

### Laravel 包

- [`laravel-oidc-client`](https://github.com/admin9-labs/laravel-oidc-client)：Laravel 的 OIDC 客户端包，支持 Authorization Code Flow 与 PKCE。
- [`laravel-oidc-server`](https://github.com/admin9-labs/laravel-oidc-server)：面向 Laravel Passport 部署场景的 OIDC 服务器端包。
- [`laravel-scramble-extensions`](https://github.com/admin9-labs/laravel-scramble-extensions)：用于业务响应型 API 的 OpenAPI 文档辅助扩展。
- [`blade-daisyui`](https://github.com/admin9-labs/blade-daisyui)：DaisyUI 5 的 Blade 封装组件。
