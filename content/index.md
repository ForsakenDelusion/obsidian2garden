---
publish: true
title: 欢迎来到我的主页
created: 2026-08-24T18:19:24.456Z
modified: 2026-09-05T02:30:00.000Z
---

# Changelog

## 2026-09-05

- 新增并接入自定义 **Obsidian Admonition 插件**（`github:ForsakenDelusion/quartz-obsidian-admonition`），通过 `github:` 引用方式加入 `quartz.config.yaml`。支持 `` `ad-<type>` `` 代码块转 callout、`title` / `collapse` / `icon` / `color` / `metadata` 选项，以及用递减反引号写的**嵌套** admonition（外层 5 → 内层 4 → 内内层 3 反引号）。
- 插件以 TypeScript + tsup 开发，预构建 `dist/` 一并提交（避免 npm 全局 `omit=dev` 导致 Quartz 侧无 tsup 而构建失败），Quartz 检测到预构建 dist 直接加载，无需二次构建。
- 本地端到端验证通过：`npx quartz build` 正确渲染出 note / tip(is-collapsible) / warning / danger 四类 callout，含嵌套结构。

## 2026-08-25

- 从 Aura 主题切换回 Quartz 默认主题，因为 Aura 对 Explorer 标题字号的样式覆盖会导致折叠后内容被截断，而默认主题显示正常。

## 2026-08-24

- (早期内容占位)

Hi
