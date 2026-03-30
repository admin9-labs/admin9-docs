---
title: 发票设置
description: 控制发票生成、卖方元数据与发布校验。
---
检查发票设置时，看这页。

## 页面位置

该页面实现为 `App\Filament\Admin\Pages\InvoiceSettings`，位于 **Settings** 导航分组下。访问要求：

- the `update settings` permission
- `ConfigService::isAdminSettingsEnabled()` returning `true`

若任一门禁不满足，则该页面及其 Livewire 表单不可访问。

## 主要控制项

`App\Livewire\Filament\InvoiceSettings` 中的 Livewire 表单通过 `ConfigService::set` 写入配置，因此变更会立即持久化，并用于运行时缓存。

常用字段：

- `Enable invoice generation`（开关）：开启后，系统会为每笔成功交易生成发票，并可通过 `/invoice/preview` 与 `/invoice/generate/{transactionUuid}` 访问。
- `Invoice number prefix`：定义 `invoices.serial_number.series`（默认 `INV`），作为每个发票编号的前缀。
- 卖方元数据文本输入项：
  - company name
  - company code
  - company address
  - company tax/VAT number
  - company phone

这些值存储在 `invoices.seller.attributes.*` 下，发票服务（`App\Services\InvoiceService`）在通过 `LaravelDaily\Invoices` 生成 PDF 或 HTML 发票时会读取并渲染这些字段。

## 预览

设置页面内置预览动作，会携带当前表单值打开 `/invoice/preview`。在提交变更前，使用它校验布局、语言区域和元数据是否正确。

## 运营检查清单

1. 在生产启用发票前，确认 sandbox 环境的 webhook、支付与开票流程均正常。
2. 设置发票编号前缀以匹配现有财务流水，或避免与历史发票编号冲突。
3. 填写准确的企业元数据；这些信息会显示在每张发票上，供客户和监管方查看。
4. 保存前使用预览动作检查布局与文案。
5. 保存后验证 `/invoice/generate/{transactionUuid}` 仍能为已完成交易生成 PDF（可选用测试交易 UUID）。
6. 如果执行了数据填充或部署新实例，确认配置缓存已刷新（`ConfigService` 会自动处理缓存，但长期运行的 worker 可能仍需重启）。
