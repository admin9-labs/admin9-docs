---
title: 法务页面与合规
description: 发布前在管理后台维护服务条款、隐私政策与合规内容的操作说明。
---

在发布准备和合规审查阶段请重点使用本页，它覆盖了运营人员需要持续维护的法务文案。

## 入口与访问

该页面注册为 `App\Filament\Admin\Pages\LegalPagesSettings`，在后台导航中归类于 **Settings**。访问受 `update settings` 权限与 `ConfigService::isAdminSettingsEnabled()` 开关共同控制，编辑前需确认两者均为可用状态。

## 发布前需要完成的事项

- 确保种子法务内容准确。默认 `DatabaseSeeder` 会执行 `LegalPagesSeeder`，请审阅初始文案并在后台按需修订。
- 确保服务条款与隐私政策反映真实产品形态，包含正确的主体信息，并覆盖已启用的支付方式、认证方式与数据处理实践。
- 确认区域合规声明（如 GDPR、CCPA）与目标服务地区一致。

## 运营注意事项

- 确保后台文案与法务草案/审批版本同步。若律师批准新措辞，应在后台更新，不要硬编码。
- 编辑前使用 Filament 页面版本能力（若已配置）或先做备份；系统不提供自动回滚。若需审计，请另存旧版本。
- 在 runbook 中记录法务内容 owner，便于后续版本快速拉通责任人。

## 合规验证清单

1. 核对条款与隐私文本准确，且公开路由（`/terms-of-service`、`/privacy-policy`）渲染的是最新文案。
2. 确认驱动这些路由的 `ConfigService` 配置值已填充（例如通过配置服务写入的 `app.legal.terms_of_service`）。
3. 确保新增支付 provider、OAuth 流程或功能开关已在法务文案中体现，使已发布说明与实际功能一致。
4. 确认执行更新的管理员具备所需权限，并且生产环境 `ConfigService::isAdminSettingsEnabled()` 仍为 true。

请将本页纳入发布清单。在正式上线前完成法务内容定稿，获取对应产品/法务负责人签核，并记录当前上线的审批文案版本。
