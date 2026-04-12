# Project `.design/` Directory Specification

Every project using tasteful-frontend maintains a `.design/` directory at its root. This directory is the single source of truth for all design decisions and artifacts. It is progressively populated across the six workflow phases.

## Directory Structure

```
{project}/.design/
├── brief.yaml                        <- Phase 0: Anchor
├── layout-spec.yaml                  <- Phase 1-4: progressive fill
├── exploration/                      <- Phase 2: Search
│   ├── style-tile-1.html
│   ├── style-tile-2.html
│   ├── style-tile-3.html
│   └── selected.yaml
├── tokens/                           <- Phase 3: Systematize
│   ├── primitive.tokens.json
│   ├── semantic.tokens.json
│   └── component.tokens.json
├── components/                       <- Phase 3-4: component specs
│   ├── button.yaml
│   ├── card.yaml
│   ├── input.yaml
│   └── ...
├── history/                          <- Version snapshots
│   ├── v1/
│   │   ├── tokens/
│   │   └── layout-spec.yaml
│   └── v2/
│       ├── tokens/
│       └── layout-spec.yaml
└── handoff/                          <- Phase 5: Verify -> design-to-code-runner
    ├── tokens/
    │   ├── primitive.tokens.json
    │   ├── semantic.tokens.json
    │   └── component.tokens.json
    ├── layout-spec.yaml
    └── adapter-output/               <- Penpot/Figma/HTML preview artifacts
```

## File Lifecycle

### Phase 0: Anchor

| File | Action | Description |
|------|--------|-------------|
| `brief.yaml` | **Created** | Project brief: name, platform, audience, pain points, success criteria |

### Phase 1: Frame

| File | Action | Description |
|------|--------|-------------|
| `layout-spec.yaml` | **Created (skeleton)** | Meta, layout structure, pages, navigation. No token references yet. |

### Phase 2: Search

| File | Action | Description |
|------|--------|-------------|
| `exploration/style-tile-*.html` | **Created** | 3-5 self-contained HTML Style Tiles for visual direction comparison |
| `exploration/selected.yaml` | **Created** | User's selection: which tile (or combination), rationale, any requested modifications |

### Phase 3: Systematize

| File | Action | Description |
|------|--------|-------------|
| `tokens/primitive.tokens.json` | **Created** | All raw values — colors, fonts, spacing, radii, shadows, motion |
| `tokens/semantic.tokens.json` | **Created** | Purpose-mapped references to primitives |
| `tokens/component.tokens.json` | **Created** | Component-scoped references to semantics |
| `components/*.yaml` | **Created** | Component specs with states, variants, token bindings |

### Phase 4: Compose

| File | Action | Description |
|------|--------|-------------|
| `layout-spec.yaml` | **Updated (complete)** | Token references filled in, interaction section added |
| adapter output | **Created** | preview.html, Penpot file, Figma sync, etc. |

### Phase 5: Verify

| File | Action | Description |
|------|--------|-------------|
| `handoff/` | **Created** | Frozen copy of final tokens + layout-spec for code runner |
| `history/v{n}/` | **Created** | Snapshot of current state before handoff |

## File Format References

- **brief.yaml**: See `brief_schema` in `spec-schema.yaml`
- **layout-spec.yaml**: See `layout_spec_schema` in `spec-schema.yaml`
- **tokens/*.json**: See `tokens_schema` in `spec-schema.yaml` (W3C DTCG v2025.10)
- **components/*.yaml**: Component-specific, follows the structure in `constraints/component-visual-specs.md`
- **selected.yaml**: Freeform YAML with required fields `chosen_tile`, `rationale`, and optional `modifications`

## Versioning Rules

1. **On first creation**: No history snapshot needed.
2. **On sync readback** (user edits in Penpot/Figma and syncs back): Snapshot current state to `history/v{n}/` before applying changes.
3. **On handoff**: Always snapshot to `history/v{n}/` and copy final state to `handoff/`.
4. **Version numbering**: Sequential integers starting at 1. Never reuse a version number.

## Gitignore Recommendations

Projects should track `.design/` in version control with these exceptions:

```gitignore
# Large adapter outputs (regenerable)
.design/handoff/adapter-output/
# Exploration tiles (ephemeral)
.design/exploration/style-tile-*.html
```

Everything else — tokens, layout-spec, brief, selected.yaml, component specs, history — should be committed. These are design decisions, not build artifacts.
