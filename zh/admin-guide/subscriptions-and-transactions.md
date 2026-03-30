---
title: 订阅与交易
description: 管理端中的订阅、订单、交易与余额操作。
---
计费排查通常从这里开始。

## 订阅

`Subscriptions` 资源提供以下列表、查看、编辑与动作处理能力：

- `ListSubscriptions`
- `ViewSubscription`
- `AddDiscount`
- `ChangeSubscriptionPlan`
- `CancelSubscription`
- `ConfirmCancelSubscription`
- `DiscardSubscriptionCancellation`

可以用这个资源：

- 验证每位客户的套餐层级、定价与功能可见性
- 查看订阅时间线（开始、试用、取消、续费等事件）
- 在需要人工干预时从管理界面应用折扣或变更套餐
- 对问题订阅执行取消或撤销取消操作

## 订单

`OrderResource` 及其页面允许运营人员：

- 查看所有客户订单（订阅与一次性购买）
- 检查履约细节
- 查看关联交易

在与外部财务系统对账前，使用订单详情确认发票号、支付状态和关联交易。

## 交易

`Transactions` 资源包括：

- `ListTransactions`
- a transaction detail view page

该资源展示交易状态、提供商数据和金额。在排查支付失败或核对报表时，这里是查看支付提供商数据与交易上下文的首要入口。

## 余额

`BalanceResource` 和 `BalanceTransactionResource` 对应站内余额。

管理员通常会：

- 使用余额列表监控客户信用余额
- 使用余额流水列表排查手工调整、充值或退款
- 在处理用户反馈的余额问题时，将交易记录与余额历史交叉核对

## 运营检查清单

1. 部署后定期监控 `Subscriptions`、`Orders` 和 `Transactions`，及时发现异常失败。
2. 仅在完成对账后使用 `BalanceTransactions` 做手工调整，并记录每次修改以备审计。
3. 当支付提供商 webhook 报错时，先确认交易记录、检查关联订单行，再通过 `ViewSubscription` 查看生命周期后再修复。
4. 支持套餐变更或取消后，检查关联余额历史，确保没有遗留无效额度。
