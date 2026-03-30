---
title: 产品与定价
description: Admin9 运营人员如何在管理面板中管理产品、套餐、定价、折扣、订阅与商业数据。
---
当你需要梳理影响用户可购买内容的商品目录与定价面时，请从本页开始。

## 适用范围

本指南适用于：

- `admin9`
- `admin9-tenancy`

对于 `admin9-tenancy`，在定义运营归属前，请先确认目录实体与计费记录是全局管理、按租户管理，还是混合模式。

## 核心资源

管理面板包含以下资源：

- Products
- Plans
- One-Time Products
- Discounts
- Subscriptions
- Orders
- Transactions
- Balances
- Balance Transactions

## 运营模型

### Products

使用 products 定义站点对外展示的核心商业供给。

典型职责：

- 创建产品基本信息
- 控制产品可见性与展示方式
- 在需要时将产品关联到套餐

### Plans

plans 表示周期性订阅方案。

典型职责：

- 定义套餐层级结构
- 管理定价关系
- 在需要时维护提供商相关的套餐数据

### One-time products

one-time products 用于非周期性购买。

典型职责：

- 维护可独立售卖的商品项
- 管理其定价
- 在需要时维护提供商侧商品标识

### Discounts

discounts 用于促销和留存场景。

discount 资源还通过专用 relation manager 支持优惠码管理。

### Subscriptions and orders

这些资源主要用于复核、支持与运营干预，而不是目录初始化配置。

可用于：

- 查看生命周期状态
- 审查客户行为
- 排查计费问题
- 查看用量或相关交易数据

## 发布前检查清单

- 确认每个对外套餐都配置了正确的价格行
- 确认存在提供商侧套餐与产品映射
- 确认折扣作用范围和生效时间正确
- 验证订阅与一次性商品的测试购买流程
- 验证发票与交易记录按预期生成

对于 `admin9-tenancy`，还需验证目录可见性、定价作用域与交易报表在租户边界下行为正确。
