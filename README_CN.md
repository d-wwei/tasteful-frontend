# Tasteful Frontend 技能核心

[English Version](README.md) | 中文版

专为生成现代化、生产级别且极具美感的前端 UI 界面 (基于 React, Tailwind CSS, HTML/CSS) 而构建的 AI 原生设计技能 (Skill)。

此技能打破了常见的“AI 默认审美”（如千篇一律的布局、被滥用的默认字体以及糟糕的无障碍体验），采用独创的 **“三层架构体系” (Three-Tier Architecture)**，在确保工程底部严谨性的同时，大幅拉高界面的视觉上限。

## 核心特性

- **第一层：底线层 (Baseline Constraints)**：无障碍优先。强制约束 ARIA 标签、语义化 HTML、键盘焦点捕获以及严格的动效性能限制。
- **第二层：组件基准层 (Component Patterns)**：引入真实生产环境的 SaaS 最佳实践，涵盖表单、数据展示、浮层和导航（例如强制执行 8px 网格、单列排版、按钮标签动词化）。
- **第三层：审美表现层 (Aesthetic Directives)**：通过禁用泛滥的默认字体、强制要求留白构图、用纯粹的强调色取代随意的彩虹色、合理使用现代物理材质（如玻璃拟态 Glassmorphism），全面提升视觉冲击力。
- **设计推演 (Design Thinking)**：强制 AI 在输出任何代码前，先明确大胆的视觉方向和设计的“吸睛点 (Wow factor)”。

## 目录结构

```text
frontend-design/
├── SKILL.md                  # 主技能配置文件 / 核心提示词
├── constraints/
│   ├── accessibility.md      # 底线约束：无障碍设计与性能规范
│   └── components.md         # 交互约束：组件模式与最佳实践
├── README.md                 # 英文使用文档
└── README_CN.md              # 中文使用文档
```

## 使用方法

要应用此技能，请确保您的 AI Agent 工具（如 Cursor, Claude 或其他本地工作流）被正确配置为在生成前端代码时读取 `SKILL.md` 文件。

配置有此技能的 Agent 提示词示例：
> "加载 Tasteful Frontend 技能，帮我构建一个美观的 SaaS 后台设置页面，我想要一种极致的深色模式质感。"

## 设计原则

1. **无障碍设计 (Accessibility) 没有商量余地**。
2. **有主见的审美 (Intentional Aesthetics) 远胜于通用模板**。
3. **通过既定优秀模式确保产品的可用性**。

---
*融合了多个顶尖设计技能精华的终极解决方案。*
