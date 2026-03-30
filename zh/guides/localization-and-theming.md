---
title: 本地化与主题
description: 共享 Admin9 技术栈如何处理本地化 URL、翻译支持、DaisyUI 主题与 Filament 主题同步。
---

涉及语言区域的 UI 工作与主题相关改动，都应汇总到本页。

## 本地化模型

应用使用 `mcamara/laravel-localization` 实现基于 URL 的本地化。

当前文档化行为：

- 默认语言不显示在 URL 中
- 非默认语言带前缀

示例：

- 默认语言：`/about`
- 中文语言：`/zh/about`

该行为在内部项目说明 `admin9/docs/i18n-hide-default-locale.md` 中已有记录。

## 本地化改动时需检查

- `config/laravellocalization.php`
- 本地化路由生成
- 浏览器语言重定向行为
- session 语言持久化
- Blade 与 Filament 页面中生成的链接

## 语言覆盖范围

根据项目整体指引，当前应用内置：

- 英语
- 简体中文

新增语言时请：

- 在本地化配置中启用该 locale
- 增加翻译资源
- 验证前端 URL 与语言切换行为

## 主题系统

前端使用 DaisyUI 主题切换，Admin9 品牌色以 `#f53003` 为中心。

结合代码库与项目指引，关键特性如下：

- 主题状态会在本地持久化
- 通过 HTML 根节点 `data-theme` 属性切换主题
- Filament 主题行为与前台主题系统保持同步

## Filament 主题集成

两个面板 Provider 都引用了专用 Vite 主题资源：

- `resources/css/filament/admin/theme.css`
- `resources/css/filament/dashboard/theme.css`

这意味着品牌、色阶或主题语义的改动都应在以下区域验证：

- 前台 Blade 页面
- 管理面板
- 用户 Dashboard

## 回归检查清单

- 验证默认语言页面不带 locale 前缀
- 验证非默认语言页面使用正确前缀
- 验证语言切换器输出
- 验证主题切换在刷新后仍可保持
- 验证 Filament 面板仍使用预期色阶
- 验证深色模式样式在前台与面板之间无偏差
