# Tasteful Frontend

[English Version](README.md) | 中文版

面向 **Web 和移动端** 的 AI 原生 **设计规约生成器**。六阶段工作流输出三层 W3C DTCG 设计令牌 + 布局规约，而非代码。支持与 Penpot、Figma 等可视化设计工具的双向同步。

此技能专治"AI 设计泡沫" — 千篇一律的配色、被滥用的默认字体、糟糕的无障碍体验 — 采用有主见的设计思维、66+ 品牌参考库，以及人机协作的视觉探索阶段。

## v3.0 更新内容

重大工作流重构：**六阶段设计流程 + 三层令牌架构**。

- **六阶段工作流** — 锚定(Anchor) -> 定框(Frame) -> 探索(Search) -> 系统化(Systematize) -> 组合(Compose) -> 校验(Verify)
- **Style Tile 视觉探索** — 第 2 阶段生成 3-5 个视觉方向选项，供人工选择后再确定方向
- **三层令牌架构** — 原始层(Primitive) -> 语义层(Semantic) -> 组件层(Component)。修改一个原始值，整个系统自动更新。
- **项目 `.design/` 目录** — 结构化输出目录，随阶段渐进填充
- **66+ 品牌参考库** — 真实品牌令牌、护栏规则和 Agent 提示词，作为视觉词汇来源
- **约束时序** — 探索阶段(Phase 0-2)保持松散，执行阶段(Phase 3-5)严格收紧。先创意，后精确。

### 为什么要三层？

单层令牌系统脆弱：重命名"accent"意味着更新所有引用。三层创造了间接层 — 原始层定义"有什么"，语义层定义"意味着什么"，组件层定义"用在哪里"。更换品牌色只需修改一个语义令牌，整个组件层自动跟随。

## 六阶段工作流

```
Phase 0: 锚定 (Anchor)      -> 理解问题，创建 brief.yaml
Phase 1: 定框 (Frame)       -> 信息架构，布局骨架
Phase 2: 探索 (Search)      -> 3-5 个 Style Tile，人工选方向  [人工检查点]
Phase 3: 系统化 (Systematize) -> 三层令牌 + 组件规约
Phase 4: 组合 (Compose)     -> 完整规约 + 推入设计工具
Phase 5: 校验 (Verify)      -> 实用性 / 易用性 / 美感 三层质检
```

## 设计规约输出

技能输出到项目的 `.design/` 目录：

1. **三层令牌** (W3C DTCG v2025.10)
   - `primitive.tokens.json` — 原始值：按色阶的颜色、字体族、间距刻度
   - `semantic.tokens.json` — 语义映射：surface、accent、text-primary（引用原始层）
   - `component.tokens.json` — 组件绑定：button-primary-bg、card-border（引用语义层）
2. **layout-spec.yaml** — 页面结构、组件树、响应式规则、交互模式
3. **preview.html** — 可选的自包含样式指南预览

## 适配器系统

| 适配器 | 方向 | 适用场景 |
|--------|------|----------|
| HTML 预览 | 仅推送 | 在浏览器中快速验证方向 |
| Penpot | 双向 | 主力工具 — 原生 DTCG、免费、无 API 限制 |
| Figma | 双向 | 团队已在使用 Figma（建议付费版） |
| Pencil MCP | 双向 | AI 自主设计生成 |

## 目录结构

```text
frontend-design/
├── SKILL.md                          # 核心：六阶段工作流 + 设计哲学
├── spec-schema.yaml                  # 三层令牌 Schema + 布局规约格式
├── project-dir-spec.md               # .design/ 目录结构规范
├── aesthetic-patterns.md             # 10+ 可编码视觉模式（品牌分析提炼）
├── constraints/
│   ├── accessibility.md              # 设计层无障碍、触控、性能规则
│   ├── code-rules.md                 # 代码级规则（供 design-to-code-runner 使用）
│   ├── color-deep.md                 # 色彩系统深度知识
│   ├── component-css-specs.md        # CSS 级组件实现
│   ├── component-visual-specs.md     # 组件行为 + 视觉规格模板
│   ├── components.md                 # 组件模式、导航、布局
│   ├── motion-deep.md                # 动效时序、缓动、编排
│   ├── motion-performance.md         # 动效渲染、FLIP、层提升
│   ├── opentype-rules.md             # OpenType 特性使用指南
│   ├── responsive-strategies.md      # 断点行为、折叠规则
│   └── typography-deep.md            # 排版系统深度知识
├── brand-tokens/                     # 66+ 品牌参考令牌库
│   └── {brand}.tokens.json
├── brand-guardrails/                 # 品牌级规则护栏
│   └── {brand}.md
├── brand-previews/                   # 品牌令牌可视化预览
│   └── {brand}-preview.html
├── agent-prompts/                    # 品牌专属组件生成提示词
│   └── {brand}.md
├── adapters/
│   ├── html-preview-adapter.md       # 浏览器预览生成
│   ├── penpot-adapter.md             # Penpot 双向同步
│   ├── figma-adapter.md              # Figma 双向同步
│   └── pencil-adapter.md             # Pencil MCP 程序化设计
├── examples/
│   └── saas-dashboard/
│       ├── primitive.tokens.json     # 示例原始层
│       ├── semantic.tokens.json      # 示例语义层
│       ├── component.tokens.json     # 示例组件层
│       └── layout-spec.yaml          # 示例布局规约
├── README.md
└── README_CN.md
```

## 使用方法

### Claude Code

```
/tasteful-frontend
```

或自然语言引用：

> "为 SaaS 仪表盘生成设计规约，深色极简风格。"

### 设计到代码的交接

Phase 5 完成后：
1. `.design/handoff/` 目录包含冻结的令牌 + 布局规约
2. 使用 **design-to-code-runner** 技能加载交接产物 + `constraints/code-rules.md`
3. 输出目标框架的生产代码（React/SwiftUI/Flutter 等）

### 示例提示词

- "为金融科技着陆页生成设计规约，奢华编辑杂志风。"
- "为 iOS 设置页创建令牌和布局，SwiftUI，极简。"
- "给我展示 5 个开发者工具仪表盘的 Style Tile 方向选项。"
- "将 Penpot 的修改同步回规约。"
- "审查这份设计规约的无障碍合规性。"

## 设计原则

1. **无障碍没有商量余地** — 每条约束背后都有真实用户的需求。
2. **探索先于承诺** — 生成选项，让人类选择方向。
3. **三层而非一层** — 原始 -> 语义 -> 组件的间接层实现系统化变更。
4. **有主见的审美远胜通用模板** — 大胆选择，而不是安全默认值。
5. **先规约后代码** — 实现前锁定每个视觉决策。
6. **平台感知** — 尊重 iOS HIG、Material Design 和 Web 惯例。
7. **工具无关** — 适配器让你使用任何偏好的设计工具。

## 致谢

合成自：
- [tasteful-frontend](https://github.com/d-wwei/tasteful-frontend) — 审美哲学与三层架构
- [ui-ux-pro-max](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill) — 全面的 UI/UX 规则体系
- [awesome-design-md](https://github.com/VoltAgent/awesome-design-md) — 66+ 品牌设计参考
- [W3C Design Tokens Community Group](https://www.designtokens.org/) — DTCG v2025.10 规范

使用 [Remix](https://github.com/d-wwei/remix) 构建 — 通用 artifact 重构工具。

---

MIT 许可证
