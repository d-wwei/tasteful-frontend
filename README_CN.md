# Tasteful Frontend

[English Version](README.md) | 中文版

专为 **Web 和移动端** 构建现代化、生产级、高视觉冲击力界面的 AI 原生设计技能。支持 React、Next.js、Vue、Svelte、Tailwind CSS、SwiftUI、React Native 和 Flutter。

此技能专治"AI 设计泡沫" — 千篇一律的布局、被滥用的默认字体、糟糕的无障碍体验 — 采用独创的 **三层架构体系**，在确保工程底线的同时大幅拉高视觉上限。

## v1.0 更新内容

此版本由 [tasteful-frontend](https://github.com/d-wwei/tasteful-frontend)（审美哲学）和 [ui-ux-pro-max](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill)（全面 UX 规则体系）合成而来，使用 [Remix](https://github.com/d-wwei/remix) 工具驱动。

- **10 大规则优先级体系**（CRITICAL → LOW）— 系统化设计决策
- **移动端平台支持** — iOS（SwiftUI / Apple HIG）、Android（Material Design）、React Native、Flutter
- **约束文件大幅扩展** — 无障碍规则 34 → 74 行，组件模式 36 → 78 行
- **预交付检查清单** — 视觉质量、交互、无障碍、布局、代码质量
- **深度覆盖** — 触控目标、手势安全、骨架屏加载、安全区域、弹簧物理曲线、语义色彩 Token、屏幕阅读器支持

## 核心特性

### 三层架构体系

- **第一层：底线约束层** — 无障碍、触控交互、性能。没有商量余地。强制 ARIA 标签、44pt 触控目标、焦点捕获、动效性能、懒加载、屏幕阅读器兼容。
- **第二层：组件模式层** — 来自生产环境的最佳实践：表单、导航、数据展示、浮层、响应式布局。8px 网格、单列表单、动词化按钮标签、空状态 CTA、自适应导航。
- **第三层：审美表现层** — 此技能的灵魂。禁用被滥用的字体（Inter、Roboto、Arial），强制大胆的色彩哲学（一个主色 + 一个强调色），要求有意识的空间构图，应用现代材质效果（玻璃拟态、颗粒感、氛围背景）。

### 设计推演优先

强制 AI 在输出任何代码前，先明确大胆的视觉方向、平台上下文和设计的"吸睛点（Wow Factor）"。

### 规则优先级系统

10 大规则类别按影响级别排序（CRITICAL → LOW），参考 Apple HIG、Material Design 和 WCAG 标准。

### 反 AI 泡沫反模式清单

明确列出通用 AI 审美陷阱、工程失误、UX 错误和移动端特有问题。

## 目录结构

```text
frontend-design/
├── SKILL.md                  # 主技能入口文件（240 行）
├── constraints/
│   ├── accessibility.md      # 无障碍、触控、性能、屏幕阅读器规则
│   └── components.md         # 组件模式、导航、表单、图表、图标
├── README.md                 # 英文文档
└── README_CN.md              # 中文文档
```

## 使用方法

### Claude Code

将技能放置在 `~/.claude/skills/` 下即可自动识别。调用方式：

```
/tasteful-frontend
```

或自然语言引用：

> "帮我构建一个 SaaS 后台设置页面，要深色模式的质感。"

### 其他 AI Agent（Cursor、Windsurf 等）

配置 Agent 在生成前端代码时读取 `SKILL.md` 作为系统提示词或上下文文件。

### 示例提示词

- "为一个金融科技产品做着陆页，我要奢华的编辑杂志风。"
- "做一个 iOS 移动端引导流程，SwiftUI，简约温暖的感觉。"
- "重新设计这个仪表盘的表格，加上合理的空状态和加载骨架屏。"
- "审查这个 React 组件的无障碍性和触控目标合规性。"

## 设计原则

1. **无障碍设计没有商量余地** — 每条规则背后都有真实用户的需求。
2. **有主见的审美远胜通用模板** — 大胆选择，而不是安全默认值。
3. **平台感知** — 尊重 iOS HIG、Material Design 和 Web 惯例。
4. **行动指南，而非百科全书** — 可执行的规则，而不是参考手册。

## 致谢

合成自：
- [tasteful-frontend](https://github.com/d-wwei/tasteful-frontend) — 审美哲学与三层架构
- [ui-ux-pro-max](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill) — 全面的 UI/UX 规则体系与移动端平台规范
- [Anthropic 前端设计指南](https://docs.anthropic.com) — 反 AI 泡沫设计思维

使用 [Remix](https://github.com/d-wwei/remix) 构建 — 通用 artifact 重构工具。

---

MIT 许可证
