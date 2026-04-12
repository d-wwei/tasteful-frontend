# Pencil MCP Adapter — Programmatic Design Generation

Pencil MCP is a programmatic design tool for `.pen` files. Unlike Penpot and Figma, it operates through MCP tool calls (batch_get, batch_design, set_variables) rather than a human-editable GUI. Best suited for **AI-autonomous design generation** where the AI creates visual artifacts without human intervention.

## Push: Spec → Pencil

### Token → Variables

Convert tokens.json to Pencil MCP variables using the `set_variables` tool:

```
# Map token groups to Pencil variables
color.surface     → variable "color-surface" (color type)
color.accent      → variable "color-accent" (color type)
typography.font-display → variable "font-display" (string type)
spacing.md        → variable "spacing-md" (number type)
# ... for all tokens
```

Use `mcp__pencil__set_variables` to push variables into the .pen file.

### Layout → Frames

Convert layout-spec.yaml to Pencil frame structure using `batch_design`:

1. Create root frame matching `layout.structure`
2. Create sidebar frame (if specified) with `layout.sidebar.width`
3. Create main content frame with `layout.main.max_width`
4. For each `pages[].sections`:
   - Create a frame with appropriate layout (vertical/horizontal/grid)
   - Set gap from token reference (`{spacing.lg}` → resolved value)
5. For each component in `children`:
   - Create component frames matching the abstract type
   - Apply token variables for colors, typography, spacing

### Component Mapping

| layout-spec type | Pencil implementation |
|-----------------|----------------------|
| `header` | Text node with font-display, scale-2xl |
| `card` | Frame with surface-subtle fill, radius-md, padding |
| `form-field` | Frame with label text + input rectangle |
| `button` | Frame with accent fill, text, radius-md |
| `table` | Grid frame with header row + data rows |
| `nav-item` | Frame with icon placeholder + label text |

## Pull: Pencil → Spec

### Reading Back Variables

Use `mcp__pencil__get_variables` to read current variable values from the .pen file, then reverse-map to tokens.json format.

### Reading Back Structure

Use `mcp__pencil__batch_get` to read frame structure:
1. Get top-level frames → infer layout.structure
2. Get child frames → infer page sections
3. Read properties (fill, font, spacing) → compare against token values

### AI Diff Process

1. Read variables from .pen file
2. Map back to DTCG token format
3. Diff against current tokens.json
4. Run standard consistency checks (contrast, banned fonts, 8px grid)
5. Report changes and request confirmation

## Diff: Property Comparison

- Read node properties via `batch_get` with relevant patterns
- Compare against expected values from tokens.json
- Properties checked: fillColor, textColor, fontSize, fontFamily, gap, padding, cornerRadius
- Use `search_all_unique_properties` to find deviations from token values

## Limits

### No Human-Friendly GUI
- Pencil operates through MCP API calls only
- Humans cannot visually edit .pen files with drag-and-drop, color pickers, etc.
- For human-in-the-loop design iteration, use Penpot or Figma adapter instead
- Best use case: AI generates complete design autonomously, exports as image for review

### Programmatic Only
- All operations are batch_design/batch_get/set_variables calls
- No real-time visual preview during generation (use get_screenshot to check)
- Complex layouts require many operations (aim for ≤25 per batch_design call)

### Format Differences
- Pencil uses its own .pen format (not SVG, not Figma, not standard)
- Token mapping is one-way translation (DTCG → Pencil variables)
- Pencil variables don't have $type metadata — type is inferred from usage

### Export Capabilities
- Export nodes to PNG/JPEG/WEBP/PDF via `export_nodes`
- Useful for generating design preview images for review
- No direct DTCG token export (reverse mapping required)

## Recommended Workflow

```
1. AI generates spec (tokens.json + layout-spec.yaml)
2. AI opens/creates .pen file via Pencil MCP
3. AI pushes tokens as variables (set_variables)
4. AI creates frame structure (batch_design)
5. AI takes screenshot for visual verification (get_screenshot)
6. AI exports as PNG for human review (export_nodes)
7. Human reviews exported image
8. Human provides text feedback → AI updates spec → repeat from step 3
9. When approved, hand off spec to design-to-code-runner
```

## When to Use This Adapter

| Scenario | Recommended? |
|----------|-------------|
| AI-autonomous design generation (no human editing needed) | **Yes** — primary use case |
| Quick design mockup for review as image | **Yes** — export to PNG |
| Human wants to visually edit the design | **No** — use Penpot/Figma |
| Bidirectional token sync with human edits | **No** — use Penpot/Figma |
| Generating design system documentation | **Yes** — programmatic generation |
