# Penpot Adapter — Bidirectional Design Token Sync

Penpot is the primary visual design tool for this workflow. It natively supports W3C DTCG design tokens (first design tool to do so), has a Plugin API with full token operations (since v2.14), and an official MCP server. This adapter provides three executable capability paths, detected and selected automatically.

## Capability Detection

Run detection in order. Use the first path that passes.

```
1. Path A — Penpot MCP Server
   Test: MCP tool `high_level_overview` is available and responds.
   Requires: Penpot MCP Server (port 4401) + WebSocket Server (port 4402) + Penpot MCP Plugin installed in the project.
   Result: Full bidirectional automation via `execute_code`.

2. Path B — Penpot REST API
   Test: `curl -s -H "Authorization: Token $PENPOT_ACCESS_TOKEN" https://<instance>/api/rpc/command/get-profile` returns 200.
   Requires: PENPOT_ACCESS_TOKEN env var.
   Result: File-level operations only. NO token operations (tokens are embedded in file data via undocumented transit encoding).

3. Path C — Manual Fallback
   Test: Always available.
   Requires: User can open Penpot UI.
   Result: Manual token import/export via Penpot Tokens panel. AI performs diff and validation.
```

---

## Path A: Penpot MCP Server (Preferred)

### Setup

The Penpot MCP server lives at `penpot/penpot/tree/develop/mcp`. Documentation: https://help.penpot.app/mcp/

Architecture:
- **MCP Server** — port 4401 (Claude connects here via MCP protocol)
- **WebSocket Server** — port 4402 (bridges MCP to the Penpot Plugin)
- **Penpot MCP Plugin** — installed in the Penpot project (runs in-browser, executes JS via Plugin API)

The primary tool is **`execute_code`** — it runs arbitrary JavaScript inside the Penpot Plugin API context. All token, library, and shape operations go through this tool.

Other available tools:
| Tool | Purpose |
|------|---------|
| `high_level_overview` | Get current page structure, shapes, and selection |
| `penpot_api_info` | Look up Plugin API documentation for a specific topic |
| `export_shape` | Export a shape as PNG/SVG |
| `import_image` | Import an image into the project |

### Push: Spec → Penpot

#### Create Token Sets and Tokens

Given a DTCG `tokens.json`, push tokens into Penpot:

```javascript
// Tool: execute_code
// Step 1: Create a token set
const catalog = penpot.library.local.tokens;
const set = catalog.addSet({ name: "core" });
set.toggleActive(); // activate the set

// Step 2: Add color tokens
set.addToken({ type: "color", name: "color.accent", value: "#e76f51" });
set.addToken({ type: "color", name: "color.surface", value: "#faf9f6" });
set.addToken({ type: "color", name: "color.text-primary", value: "#1a1a1a" });

// Step 3: Add spacing tokens (dimension type)
set.addToken({ type: "spacing", name: "spacing.sm", value: "8" });
set.addToken({ type: "spacing", name: "spacing.md", value: "16" });
set.addToken({ type: "spacing", name: "spacing.lg", value: "24" });

// Step 4: Add typography tokens
set.addToken({ type: "fontFamilies", name: "font.display", value: "Space Grotesk" });
set.addToken({ type: "fontSizes", name: "fontSize.base", value: "16" });
set.addToken({ type: "fontWeights", name: "fontWeight.regular", value: "400" });
set.addToken({ type: "fontWeights", name: "fontWeight.bold", value: "700" });

// Step 5: Add border-radius tokens
set.addToken({ type: "borderRadius", name: "radius.sm", value: "4" });
set.addToken({ type: "borderRadius", name: "radius.md", value: "8" });

// Step 6: Add shadow tokens
set.addToken({ type: "shadow", name: "shadow.card", value: "0 2 8 0 rgba(0,0,0,0.08)" });

// Token references use curly-bracket syntax:
set.addToken({ type: "spacing", name: "spacing.section", value: "calc({spacing.lg} * 2)" });
```

**Batch strategy**: The `execute_code` tool can run multi-statement scripts. Push all tokens for one set in a single call. If the spec has multiple groups, use one `execute_code` call per token set.

#### Create Token Themes

```javascript
// Tool: execute_code
const catalog = penpot.library.local.tokens;
const lightTheme = catalog.addTheme({ group: "mode", name: "light" });
const darkTheme = catalog.addTheme({ group: "mode", name: "dark" });
```

#### Create Library Colors

```javascript
// Tool: execute_code
const lib = penpot.library.local;
const accent = lib.createColor();
accent.name = "accent";
accent.color = "#e76f51";
accent.opacity = 1;

const surface = lib.createColor();
surface.name = "surface";
surface.color = "#faf9f6";
surface.opacity = 1;
```

#### Create Library Typographies

```javascript
// Tool: execute_code
const lib = penpot.library.local;
const heading = lib.createTypography();
heading.name = "heading";
heading.fontId = "gfont-space-grotesk";
heading.fontSize = "32";
heading.fontWeight = "700";

const body = lib.createTypography();
body.name = "body";
body.fontId = "gfont-space-grotesk";
body.fontSize = "16";
body.fontWeight = "400";
```

#### Create Layout Frames

```javascript
// Tool: execute_code
// Create a board (frame) with flex layout
const page = penpot.createBoard();
page.name = "Page Shell";
page.resize(1440, 900);
const flex = page.addFlexLayout();
flex.dir = "row";
flex.gap = 0;

// Create sidebar frame
const sidebar = penpot.createBoard();
sidebar.name = "Sidebar";
sidebar.resize(280, 900);
page.appendChild(sidebar);

// Create main content frame
const main = penpot.createBoard();
main.name = "Main Content";
main.resize(1160, 900);
const mainFlex = main.addFlexLayout();
mainFlex.dir = "column";
mainFlex.gap = 24;
page.appendChild(main);
```

### Pull: Penpot → Spec

#### Read All Token Sets and Tokens

```javascript
// Tool: execute_code
const catalog = penpot.library.local.tokens;
const sets = catalog.sets;
const result = [];
for (const s of sets) {
  const tokens = s.tokens;
  const tokenData = tokens.map(t => ({
    name: t.name,
    type: t.type,
    value: t.resolvedValueString,
    description: t.description
  }));
  result.push({ set: s.name, tokens: tokenData });
}
JSON.stringify(result, null, 2);
```

The returned JSON is then mapped to DTCG format by the AI (see mapping table below).

#### Read Library Colors

```javascript
// Tool: execute_code
const colors = penpot.library.local.colors;
const result = colors.map(c => ({ name: c.name, color: c.color, opacity: c.opacity }));
JSON.stringify(result, null, 2);
```

#### Read Library Typographies

```javascript
// Tool: execute_code
const typos = penpot.library.local.typographies;
const result = typos.map(t => ({
  name: t.name,
  fontId: t.fontId,
  fontSize: t.fontSize,
  fontWeight: t.fontWeight,
  lineHeight: t.lineHeight,
  letterSpacing: t.letterSpacing
}));
JSON.stringify(result, null, 2);
```

#### Read Current Page Shapes

```javascript
// Tool: execute_code
const shapes = penpot.currentPage.findShapes({});
const result = shapes.map(s => ({ id: s.id, name: s.name, type: s.type }));
JSON.stringify(result, null, 2);
```

Use `findShapes` with filters:
- `{ name: "Sidebar" }` — exact name match
- `{ nameLike: "Card" }` — partial name match
- `{ type: "frame" }` — by shape type

#### Apply a Token to Shapes

```javascript
// Tool: execute_code
// Apply a token to the currently selected shapes
const catalog = penpot.library.local.tokens;
const sets = catalog.sets;
const coreSet = sets.find(s => s.name === "core");
const accentToken = coreSet.tokens.find(t => t.name === "color.accent");
// Apply to selected shapes as fill color
accentToken.applyToSelected(["fill"]);
```

Or apply to shapes found by name:

```javascript
// Tool: execute_code
const catalog = penpot.library.local.tokens;
const coreSet = catalog.sets.find(s => s.name === "core");
const radiusToken = coreSet.tokens.find(t => t.name === "radius.md");
const cards = penpot.currentPage.findShapes({ nameLike: "Card" });
radiusToken.applyToShapes(cards, ["borderRadius"]);
```

### Sync Workflow (Path A)

```
Spec (tokens.json)                          Penpot Project
       │                                          │
       │  ── Push ──────────────────────────────→  │
       │     execute_code: create sets + tokens    │
       │     execute_code: create library colors   │
       │     execute_code: create frames           │
       │                                          │
       │           [Designer works in Penpot]      │
       │                                          │
       │  ←── Pull ──────────────────────────────  │
       │     execute_code: read all tokens         │
       │     AI maps to DTCG, runs diff            │
       │     AI runs consistency checks            │
       │     AI updates tokens.json                │
       │                                          │
       └──────────── Repeat ──────────────────────┘
```

---

## Path B: Penpot REST API

### When to Use

Use Path B **only** for file-level operations: checking if a project exists, reading file metadata, or creating new project files. Path B **cannot** manipulate tokens, library colors, or typographies — those are embedded in Penpot's internal file data structure using undocumented transit encoding. Do not attempt to use `update-file` for token operations.

If you need token operations, use Path A (MCP) or Path C (Manual).

### Authentication

```bash
# Set access token (generate in Penpot: Profile → Access Tokens)
export PENPOT_ACCESS_TOKEN="penpot_..."
```

All requests use:
```
Authorization: Token $PENPOT_ACCESS_TOKEN
```

Base URL pattern: `https://<instance>/api/rpc/command/<command>`

### Available Operations

#### Get Profile (connection test)

```bash
curl -s -H "Authorization: Token $PENPOT_ACCESS_TOKEN" \
  "https://design.penpot.app/api/rpc/command/get-profile"
```

#### Get File

```bash
curl -s -H "Authorization: Token $PENPOT_ACCESS_TOKEN" \
  "https://design.penpot.app/api/rpc/command/get-file?id=<file-id>"
```

Returns file metadata, pages, and component info. Token data is present in the response but encoded in Penpot's internal transit format — not suitable for direct manipulation.

#### Create File

```bash
curl -s -X POST \
  -H "Authorization: Token $PENPOT_ACCESS_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"project-id": "<project-id>", "name": "New Design File"}' \
  "https://design.penpot.app/api/rpc/command/create-file"
```

#### Get Page

```bash
curl -s -H "Authorization: Token $PENPOT_ACCESS_TOKEN" \
  "https://design.penpot.app/api/rpc/command/get-page?file-id=<file-id>&id=<page-id>"
```

### Limitations

- **No token endpoint.** Token data is embedded in the file data structure using transit encoding. The `update-file` command exists but uses an undocumented internal change format. Attempting to write tokens via REST will break file integrity.
- **No library color/typography endpoints.** Same limitation — embedded in file data.
- **Shape manipulation is fragile.** While `update-file` can theoretically modify shapes, the change format is internal and undocumented.
- **Use case is narrow.** Path B is suitable for: verifying project existence, reading file metadata, creating empty files, and scripting project-level workflows. For anything inside a file, use Path A or C.

---

## Path C: Manual Fallback

When neither MCP nor REST API is available, use manual token exchange through Penpot's built-in Tokens panel.

### Push: Spec → Penpot

1. Open the Penpot project
2. Open the **Tokens** panel (left sidebar, Tokens tab)
3. Click **Import** (or menu, Import tokens)
4. Select the generated `tokens.json` file
5. Penpot creates token sets matching the JSON groups (color, typography, spacing, etc.)
6. Apply tokens to design elements through the Tokens panel

### Layout Setup

Use `layout-spec.yaml` as reference to manually create:
1. **Frames** matching `layout.structure` (sidebar frame, main frame)
2. **Components** matching `pages[].sections[].children` types
3. **Auto-layout** settings matching breakpoints and spacing tokens

Penpot uses native CSS Flexbox and Grid — the layout-spec's responsive rules map directly.

### Pull: Penpot → Spec

1. In Penpot, open the **Tokens** panel
2. Click **Export** (or menu, Export tokens)
3. Select **DTCG / W3C format** (Penpot's native format)
4. Save as `tokens-modified.json`
5. Provide the file to the AI: "Here are my Penpot token changes" or "Sync from Penpot"

---

## DTCG <> Penpot Token Type Mapping

Penpot defines 17 token types. This table maps each to its DTCG `$type` equivalent.

| Penpot TokenType | DTCG `$type` | Notes |
|---|---|---|
| `color` | `color` | Direct match. Penpot accepts hex, RGBA. |
| `dimension` | `dimension` | Generic dimension (px, rem). |
| `spacing` | `dimension` | DTCG has no `spacing` type — use `dimension`. |
| `sizing` | `dimension` | DTCG has no `sizing` type — use `dimension`. |
| `borderWidth` | `dimension` | Map to `dimension` with semantic naming. |
| `borderRadius` | `dimension` | DTCG has no `borderRadius` — use `dimension`. |
| `opacity` | `number` | DTCG `number` (0-1 range). |
| `number` | `number` | Direct match. |
| `rotation` | `number` | Degrees. Map to `number`. |
| `fontFamilies` | `fontFamily` | Direct match. |
| `fontSizes` | `dimension` | DTCG uses `dimension` for font sizes. |
| `fontWeights` | `fontWeight` | Direct match. |
| `letterSpacing` | `dimension` | DTCG uses `dimension` for letter spacing. |
| `shadow` | `shadow` | Direct match. Value format differs (see below). |
| `textCase` | `string` | No DTCG equivalent — use custom `$type: "textCase"` or `string`. |
| `textDecoration` | `string` | No DTCG equivalent — use custom `$type: "textDecoration"` or `string`. |
| `typography` | `typography` | Composite type. Contains fontFamily, fontSize, fontWeight, etc. |

**Shadow value format**: Penpot uses space-separated `"offsetX offsetY blur spread color"`. DTCG uses an object: `{ "offsetX": "0px", "offsetY": "2px", "blur": "8px", "spread": "0px", "color": "#00000014" }`. Convert between formats during push/pull.

**Token references**: Penpot uses `{tokenName}` curly-bracket syntax for references. DTCG uses `{path.to.token}` with dot-separated paths. Both use the same curly-bracket wrapper — paths may need adjustment if nesting structure differs.

**Calc expressions**: Penpot supports `calc()` inside token values, e.g., `calc({spacing.lg} * 2)`. DTCG has no `calc()` equivalent — resolve computed values during pull.

---

## Diff: Token Comparison

When the AI receives modified tokens (from any path), it runs deep JSON comparison:

- Walk both token trees in parallel
- For each token: compare `$value` fields
- Ignore `$description` changes (informational only)
- Report `$type` changes as warnings (likely a mistake)
- New tokens: listed as "added"
- Missing tokens: listed as "removed" (warn — may break layout-spec references)

### Consistency Checks

**Color changes**:
- Calculate contrast ratio of new accent against surface
- If < 4.5:1, suggest adjusted value that meets WCAG AA
- Check if any new colors match banned patterns (pure purple-blue gradient palette)

**Typography changes**:
- Check against banned font list: Arial, Inter, Roboto, system-ui
- If banned font detected, warn and suggest alternatives

**Spacing changes**:
- Verify all values are multiples of 8px (the grid unit)
- If not aligned, suggest nearest 8px-aligned value

**Motion changes**:
- Verify durations are within recommended ranges (150-400ms)

### Report Format

```
Token Sync Report
-----------------
Source: Penpot MCP (Path A) | REST API (Path B) | Manual export (Path C)
Changes detected: {N}

  color.accent: #e76f51 -> #2563eb (contrast: 5.1:1 -- OK)
  typography.font-display: "Space Grotesk" -> "Inter" (BANNED -- suggest "Instrument Serif")
  spacing.lg: 24px -> 32px (8px grid -- OK)

1 issue requires attention. Apply changes?
```

User confirms -> AI updates `tokens.json` and creates version snapshot in `.design-history/`.

---

## Recommended Workflow

```
1. AI generates spec (tokens.json + layout-spec.yaml)
2. Preview with html-preview adapter (quick direction check)
3. Detect capability path (A > B > C)

Path A (MCP available):
  4a. execute_code: create token sets + push all tokens
  5a. execute_code: create library colors + typographies
  6a. execute_code: create layout frames (guided by layout-spec)
  7a. Designer adjusts in Penpot visually
  8a. execute_code: read all tokens back
  9a. AI diffs, runs consistency checks, updates tokens.json
  10a. Repeat 7a-9a until design approved

Path B (REST only):
  4b. Create project/file via REST API if needed
  5b. Fall through to Path C for all token operations

Path C (Manual):
  4c. User imports tokens.json via Penpot Tokens panel
  5c. User builds layout using layout-spec as reference
  6c. User adjusts tokens visually in Penpot
  7c. User exports modified tokens (DTCG format)
  8c. AI diffs, runs consistency checks, updates tokens.json
  9c. Repeat 6c-8c until design approved

All paths:
  11. Hand off final spec to design-to-code-runner
```

---

## Limits

- **Path A requires plugin installation.** The Penpot MCP Plugin must be installed in each project. Without it, the MCP server has no bridge to the Plugin API.
- **Path B cannot do token operations.** The REST API has no dedicated token endpoint. Token data is embedded in file data using undocumented transit encoding. Do not attempt `update-file` for tokens.
- **Layout sync is asymmetric.** Push creates frames from layout-spec. Pull reads tokens but does not reverse-engineer layout-spec from frame structure. Describe layout changes to the AI in text.
- **Shadow value conversion.** Penpot's space-separated shadow format must be converted to/from DTCG's object format during sync. Automated conversion is straightforward but must not be skipped.
- **Calc resolution on pull.** Penpot `calc()` expressions have no DTCG equivalent. Resolve to computed values when pulling. This loses the expression — document the original expression in `$description`.
- **Export format.** Penpot exports DTCG-compatible JSON but may omit `$description` fields.
- **Penpot cloud** (free) has no API rate limits — significant advantage over Figma for AI-driven workflows.
