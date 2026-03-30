---
title: 应用 Starter
description: 公开 starter 仓库与参考应用。
---

要找可直接运行的仓库，就看这页。

## admin9-api

- 仓库：[`admin9-labs/admin9-api`](https://github.com/admin9-labs/admin9-api)
- 主要语言：PHP
- 许可证：MIT

`admin9-api` 是一个 Laravel 12 REST API 脚手架，聚焦大多数商业应用在早期就会遇到的后端共性问题：

- JWT 认证
- 角色与权限管理
- 服务层架构
- 审计事件
- 开箱即用的测试覆盖

如果你要一个后端优先的 starter，可以从它开始。

## admin9-web

- 仓库：[`admin9-labs/admin9-web`](https://github.com/admin9-labs/admin9-web)
- 主要语言：Vue
- 许可证：MIT

`admin9-web` 是 `admin9-api` 对应的前端 SPA 项目。当你希望采用独立前端应用而非单体架构时，它会更合适。

这些场景适合用它：

- API 后端 + SPA 前端
- 前端独立部署
- 多客户端共享认证与 API 契约

## admin9-docs

- 仓库：[`admin9-labs/admin9-docs`](https://github.com/admin9-labs/admin9-docs)

该仓库是文档站的 Mintlify 源码。要更新产品文档或运维手册，就在这里改。

## 应该从哪个 starter 开始

- 如果你需要后端优先的 Laravel 基础，请从 `admin9-api` 开始
- 如果你需要与 API 后端配套的独立 SPA 前端，请从 `admin9-web` 开始
- 如果你要完善产品文档、管理手册或公共文档，请从 `admin9-docs` 开始
