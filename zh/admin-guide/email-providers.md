---
title: 邮件提供商
description: 在 Admin9 Filament 管理后台配置邮件提供商。
---

启用、修复或验证外发邮件时，看这页。

## 访问条件

邮件提供商页面依赖 `ConfigService` 和可覆盖配置缓存。操作前请确认已启用 Admin Settings 功能：

```env
ADMIN_SETTINGS_ENABLED=true
```

如果该开关关闭，provider、SMTP 和其他后台设置页面都无法访问。

## 提供商列表

`EmailProviderResource` 会渲染：

- 锁定的 provider 记录列表（name 与 slug）
- 来自 `public/images/email-providers/<slug>.svg` 的内联图标
- 可打开 provider 专属设置页的编辑动作

这里配置内置 provider，不在这里创建或删除 provider 记录。

## 各 provider 的设置

每个 provider 都有专用 Livewire 表单，经 `ConfigService::set(...)` 写入，并通过 `App\Models\Config` 持久化，再写入缓存供运行时配置读取。

### SMTP

`SmtpSettings` 暴露 `mail.mailers.smtp.*` 下的 host、port、username、password 字段。这些值会覆盖 `config/mail.php` 当前 SMTP mailer 对应配置，因此请确认 `mail.default` 与目标 provider 一致。

### Mailgun

`MailgunSettings` covers:

- `services.mailgun.domain`
- `services.mailgun.secret` (encrypted)
- `services.mailgun.endpoint`

### Amazon SES

`AmazonSesSettings` manages:

- `services.ses.key`
- `services.ses.secret` (encrypted)
- `services.ses.region`

### Postmark

`PostmarkSettings` manages `services.postmark.token`.

### Resend

`ResendSettings` manages `services.resend.key`.

各设置表单均使用 `TextInput` 字段并调用 `ConfigService::set(...)`，因此值会持久化到 `configs` 表，并可立即通过 Laravel `config(...)` 读取。

## 持久化与缓存

`ConfigService::set` 会先检查 `ConfigConstants::OVERRIDABLE_CONFIGS`，再写入 `App\Models\Config` 并缓存新值（`cache()->forever`）。敏感密钥会被加密；该服务在读写时使用 `ConfigConstants::ENCRYPTED_CONFIGS` 以保证机密性。

该服务同时写入数据库和缓存，更新凭据后通常无需重启应用；但使用前仍要确认新值已在 Filament UI 和 `config('services.<provider>')` 中生效。

## 运营检查清单

- 核对每个已启用 provider 的凭据与 webhook 密钥（如适用）有效
- 核对环境变量与后台 UI 中 `services.<provider>.*` 配置一致
- 从应用发送测试邮件，并检查 `mail_mailer` 日志或 `mail.php` 输出确认可投递性
- 确认密码重置、通知、发票等模板使用所选 provider 渲染正常
- 如需迁移环境，先备份 `configs` 表或导出相关配置项
