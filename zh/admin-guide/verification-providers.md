---
title: 验证提供商
description: 在发布前通过管理后台配置基于 Twilio 的短信验证及相关门控策略。
---

短信验证配置和发布前校验都应通过本页完成。

## Twilio 提供商

代码库内置了专用 Twilio provider 实现（`App\Services\VerificationProviders\TwilioProvider`），其行为包括：

- 读取 `services.twilio.sid`、`services.twilio.token` 和 `services.twilio.from`
- 使用配置好的凭据通过 Twilio PHP SDK 发送短信
- 失败时记录异常并返回 `false`，供调用方向上抛出验证错误

管理侧 `TwilioSettings` Livewire 表单通过 `ConfigService::set(...)` 写入这些值，因此更新会持久化到 `configs` 表，并即时刷新运行时 `config(...)`，无需等待重新部署。

## 必要环境变量/配置项

运营人员应确保以下配置键存在且正确：

```env
TWILIO_SID=""
TWILIO_TOKEN=""
TWILIO_FROM=""
```

这些会映射到 `config/services.php` 中的 `services.twilio.sid`、`services.twilio.token`、`services.twilio.from`。管理表单通过 `ConfigService` 写入同一组键，因此环境变量与数据库配置应保持一致。

## 访问要求

该资源受以下条件保护：

- `ConfigService::isAdminSettingsEnabled()`（检查是否允许访问后台设置 UI）
- Filament 权限（`update settings`）

如果在生产环境中任一条件不满足，验证提供商设置页将不可访问，Twilio 凭据也无法更新。

## 试用门控与短信验证流程

Twilio 验证支持：

- 用户手机号验证
- 通过 `TRIAL_WITHOUT_PAYMENT_SMS_VERIFICATION_ENABLED=false` 控制试用门槛（见 `.env.example`）

发布前应明确以下场景是否强制短信验证：

- 新用户注册
- 未完成验证就应阻止继续使用的试用开通流程
- 因合规或限流需要依赖已验证手机号的结账流程

## 运营检查清单

1. 确认管理后台与 `.env` 中的 Twilio 凭据都指向生产 Twilio 项目。
2. 发送测试验证码短信，确认 Twilio 接受 `from` 号码与消息负载。
3. 验证错误处理：主动制造 Twilio 失败（如无效 token），确认日志/通知提供了足够的支持排障信息。
4. 复核 `ConfigConstants::OVERRIDABLE_CONFIGS` 已包含表单使用的 Twilio 键，确保可在后台持续编辑。
5. 若首发计划不启用手机验证，确认 `TRIAL_WITHOUT_PAYMENT_SMS_VERIFICATION_ENABLED` 与该决策一致，并记录进发布 runbook。
