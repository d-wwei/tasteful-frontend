# Tasteful Frontend

[中文版](README_CN.md) | English Version

An AI-native **design spec generator** for web and mobile. Six-phase workflow outputs three-layer W3C DTCG design tokens + layout specifications instead of code. Supports bidirectional sync with Penpot, Figma, and other visual design tools.

This skill fights generic "AI slop" — predictable palettes, overused fonts, poor accessibility — with opinionated design thinking, 66+ brand reference libraries, and a human-in-the-loop exploration phase.

## What's New in v3.0

Major workflow redesign: **six-phase design process with three-layer tokens**.

- **Six-phase workflow** — Anchor (understand) -> Frame (structure) -> Search (explore visuals) -> Systematize (build token system) -> Compose (assemble spec) -> Verify (quality check)
- **Style Tile exploration** — Phase 2 generates 3-5 visual direction options for human selection before committing to a direction
- **Three-layer token architecture** — Primitive (raw values) -> Semantic (purpose mapping) -> Component (UI binding). Change a primitive, the entire system updates.
- **Project `.design/` directory** — Structured output directory with progressive population across phases
- **66+ brand reference libraries** — Real-world brand tokens, guardrails, and agent prompts as vocabulary source
- **Constraint timing** — Loose in exploration (Phase 0-2), strict in execution (Phase 3-5). Creativity before precision.

### Why Three Layers?

Single-layer tokens create a brittle system: renaming "accent" means updating every reference. Three layers create indirection — primitives define what exists, semantics define what things mean, components define where things go. Changing a brand color means updating one semantic token; the entire component layer follows automatically.

## Six-Phase Workflow

```
Phase 0: Anchor    -> Understand problem, create brief.yaml
Phase 1: Frame     -> Information architecture, layout skeleton
Phase 2: Search    -> 3-5 Style Tiles, human selects direction  [HUMAN CHECKPOINT]
Phase 3: Systematize -> Three-layer tokens + component specs
Phase 4: Compose   -> Complete spec + push to design tools
Phase 5: Verify    -> Utility / Usability / Beauty quality check
```

## Design Spec Output

The skill outputs into a project's `.design/` directory:

1. **Three-layer tokens** (W3C DTCG v2025.10)
   - `primitive.tokens.json` — Raw values: colors by shade, font families, spacing scale
   - `semantic.tokens.json` — Purpose mapping: surface, accent, text-primary (references primitives)
   - `component.tokens.json` — UI binding: button-primary-bg, card-border (references semantics)
2. **layout-spec.yaml** — Page structure, component tree, responsive rules, interaction patterns
3. **preview.html** — Optional self-contained style guide preview

## Adapter System

| Adapter | Direction | Best For |
|---------|-----------|----------|
| HTML Preview | Push only | Quick visual validation in any browser |
| Penpot | Bidirectional | Primary tool — native DTCG, free, no API limits |
| Figma | Bidirectional | Teams already using Figma (paid plans recommended) |
| Pencil MCP | Bidirectional | AI-autonomous design generation |

## Directory Structure

```text
frontend-design/
├── SKILL.md                          # Core: six-phase workflow + design philosophy
├── spec-schema.yaml                  # Three-layer token schema + layout-spec format
├── project-dir-spec.md               # .design/ directory structure specification
├── aesthetic-patterns.md             # 10+ encodable visual patterns from brand analysis
├── constraints/
│   ├── accessibility.md              # Design-level a11y, touch, performance rules
│   ├── components.md                 # Component patterns, navigation, layout
│   ├── component-visual-specs.md     # Component behavior + visual spec templates
│   ├── component-css-specs.md        # CSS-level component implementation
│   ├── responsive-strategies.md      # Breakpoint behavior, collapse rules
│   ├── opentype-rules.md             # OpenType feature usage guide
│   └── code-rules.md                 # Code-level rules (for design-to-code-runner)
├── brand-tokens/                     # 66+ brand reference token libraries
│   └── {brand}.tokens.json
├── brand-guardrails/                 # Brand-specific do's / don'ts
│   └── {brand}.md
├── brand-previews/                   # Visual token preview per brand
│   └── {brand}-preview.html
├── agent-prompts/                    # Brand-specific component generation prompts
│   └── {brand}.md
├── adapters/
│   ├── html-preview-adapter.md       # Browser preview generation
│   ├── penpot-adapter.md             # Penpot bidirectional sync
│   ├── figma-adapter.md              # Figma bidirectional sync
│   └── pencil-adapter.md             # Pencil MCP programmatic design
├── examples/
│   └── saas-dashboard/
│       ├── primitive.tokens.json     # Example primitive layer
│       ├── semantic.tokens.json      # Example semantic layer
│       ├── component.tokens.json     # Example component layer
│       └── layout-spec.yaml          # Example layout specification
├── README.md
└── README_CN.md
```

## How to Use

### Claude Code

```
/tasteful-frontend
```

Or reference naturally:

> "Design a SaaS dashboard with a dark, minimal aesthetic. Output the design spec."

### Design-to-Code Handoff

After the design spec is finalized in Phase 5:
1. The `.design/handoff/` directory contains frozen tokens + layout-spec
2. Use **design-to-code-runner** with handoff artifacts + `constraints/code-rules.md`
3. It outputs production code in your target framework (React/SwiftUI/Flutter/etc.)

### Example Prompts

- "Generate a design spec for a fintech landing page. Luxury editorial feel."
- "Create tokens and layout for an iOS settings screen. SwiftUI, minimal."
- "Show me 5 style tile options for a developer tools dashboard."
- "Sync my Penpot changes back into the spec."
- "Review this design spec for accessibility compliance."

## Principles

1. **Accessibility is non-negotiable** — every constraint exists because real users need it.
2. **Explore before committing** — generate options, let humans choose direction.
3. **Three layers, not one** — primitive -> semantic -> component indirection enables systematic change.
4. **Intentional aesthetics over generic templates** — bold choices, not safe defaults.
5. **Spec before code** — lock down every visual decision before implementation begins.
6. **Platform-aware** — respect iOS HIG, Material Design, and web conventions.
7. **Tool-agnostic** — adapters let you use whatever design tool you prefer.

## Credits

Synthesized from:
- [tasteful-frontend](https://github.com/d-wwei/tasteful-frontend) — aesthetic philosophy and three-tier architecture
- [ui-ux-pro-max](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill) — comprehensive UI/UX rule system
- [awesome-design-md](https://github.com/VoltAgent/awesome-design-md) — 66+ brand design reference
- [W3C Design Tokens Community Group](https://www.designtokens.org/) — DTCG v2025.10 specification

Built with [Remix](https://github.com/d-wwei/remix) — universal artifact reconstruction tool.

---

MIT License
