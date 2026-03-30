---
title: 支持团队操作手册
description: 支持人员通过 Filament 排查用户、订单、订阅和交易问题的操作步骤。
---

当需要在 `/admin` 中排查用户、订单、订阅或交易问题时，现场支持流程应统一按本手册执行。

## 准备工作

- 确认你具备管理员角色及必要权限（`view users`、`view subscriptions`、`view transactions`）。
- 预先准备环境主机信息（`/admin`、`/dashboard`、API/webhook URL）。
- 在动数据前先还原用户上下文（用户邮箱、订单 ID、订阅 UUID）。

## 分步排查

1. **用户核验**：打开 `Users` 资源，定位账户，查看 `Orders` 与 `Subscriptions` 关联管理器，并核对 `two-factor`、`email_verified_at` 状态是否与用户反馈一致。
2. **订单复核**：使用 `OrderResource` 检查订单状态、provider 元数据及关联交易（`ViewOrder` 页面）。升级处理前先确认发票号或余额调整信息。
3. **订阅健康度检查**：查看 `Subscriptions` 资源，按需使用 `AddDiscount`、`ChangeSubscriptionPlan` 等动作，并检查生命周期时间点（trial_end、canceled_at、next_cycle_at）。若为误取消，可使用 `DiscardSubscriptionCancellation`。
4. **交易排查**：打开 `Transactions` 资源，必要时查看交易详情页中的 webhook 数据，核对支付状态、provider 数据、签名及金额。若 webhook 失败，记录时间戳以便关联 provider 日志。
5. **余额上下文**：如用户提到积分/余额，使用 `BalanceResource` 与 `BalanceTransactionResource` 追踪手动调整、充值或退款，确保汇总结果与用户反馈一致。

## 常见修复动作

- 出现履约或发票问题时先补充订单备注，记录结论后再与财务沟通。
- 仅在有明确审批记录时使用 `AddDiscount` 或 `ChangeSubscriptionPlan`。
- 通过系统动作取消或恢复订阅，避免直接改数据库字段。
- 单独记录 webhook 失败事件，便于工程团队分析重试链路。
- 除非变更已获批准且可审计，否则不要直接修改用户或交易数据（Filament 已记录管理员操作）。

## 排查后检查

- 复现前端失败场景确认修复结果。登录问题需额外验证 `/dashboard` 访问与 2FA 提示。
- 如有需要，重放 webhook 并确认 `Transactions` 已更新。
- 通知用户前确保管理员退出 Filament 会话，避免遗留锁定或占用。

## 升级路径

- 若无法对齐支付结果，向计费负责人升级并附上交易 UUID、webhook 时间戳和 provider 名称。
- 若是订阅金额计算问题，附上受影响套餐、折扣状态及生命周期时间点。
- 若涉及法务或文档冲突，引用 Launch Runbook 与 Legal Pages 内容，确保对外口径一致。
