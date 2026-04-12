# Figma Adapter — Bidirectional Design Token Sync

Figma integration for tasteful-frontend design specs. Four capability paths, auto-detected by plan tier: MCP Server (Pro+), REST API (Enterprise), Tokens Studio plugin/CLI, or manual fallback. All paths target W3C DTCG as the canonical token format.

## Capability Detection

Run detection in this order. Use the first path that succeeds.

```
1. Check Figma plan tier (determines available paths)
2. If MCP server reachable AND plan >= Professional → Path A
3. If REST API Variables endpoints accessible AND plan = Enterprise → Path B
4. If Tokens Studio plugin installed → Path C
5. Otherwise → Path D (manual fallback)
```

### Plan-Tier Decision Tree

```
Figma Plan?
├── Enterprise (Full seat)
│   ├── Best: Path B (REST API) — full variable CRUD, no MCP rate ceiling
│   ├── Also: Path A (MCP) — 600 calls/day, good for read + screenshot
│   └── Fallback: Path C (Tokens Studio)
├── Organization
│   ├── Best: Path A (MCP) — 200 calls/day
│   ├── Note: Path B unavailable — Variables API requires Enterprise
│   └── Fallback: Path C (Tokens Studio)
├── Professional (Full seat)
│   ├── Best: Path A (MCP) — 200 calls/day
│   ├── Note: Path B unavailable
│   └── Fallback: Path C (Tokens Studio)
├── Starter (Free)
│   ├── Path A: 6 calls/month — unusable for AI workflows
│   ├── Path B: unavailable
│   ├── Best: Path C (Tokens Studio plugin — unlimited, no API)
│   └── Fallback: Path D (manual)
```

---

## Path A: Figma MCP Server

### When to Use

- Figma Professional plan or higher (Full seat required)
- Best for: reading design context, screenshots, writing variables via Plugin API
- Rate limits constrain iteration speed — pair with Path C for high-volume work

| Plan | MCP Calls | Cost |
|------|-----------|------|
| Starter (Free) | 6/month | $0 |
| Professional | 200/day | $15+/mo |
| Organization | 200/day | $25+/mo |
| Enterprise | 600/day | $75+/mo |

MCP server is remote (Figma-hosted). Connect via the standard MCP protocol configuration for your AI client.

### Read: Design Context

#### get_variable_defs

Returns variables and styles for the current selection.

```
Tool: get_variable_defs
Input: (operates on current Figma selection)
```

Response contains variable collections, modes, and resolved values. Use this to audit what exists in Figma before pushing changes.

**KNOWN LIMITATION**: `get_variable_defs` may return resolved (flattened) values instead of alias references. A semantic token `color.accent` that aliases `primitive.blue.600` may appear as the raw hex value `#2563eb` with no trace of the alias chain. You cannot reliably reconstruct primitive-to-semantic token mappings from this output alone.

Workaround: Use `use_figma` with Plugin API to read `variable.valuesByMode` which preserves `VariableAlias` objects.

#### get_metadata

Returns sparse XML with layer IDs, names, types, and bounding-box positions.

```
Tool: get_metadata
Input: (operates on current Figma selection)
```

Useful for understanding layer structure before writing. Does not include variable data.

#### get_screenshot

Captures a screenshot of the selected area. Use for visual verification after pushing tokens.

```
Tool: get_screenshot
Input: (operates on current Figma selection)
```

#### search_design_system

Search components, variables, and styles across libraries.

```
Tool: search_design_system
Input: { "query": "button primary" }
```

Remote MCP only. Returns matching components and variables with metadata.

### Write: Push Tokens via use_figma

`use_figma` executes arbitrary JavaScript against the Figma Plugin API. This is the write path for MCP.

#### Create a Variable Collection

```
Tool: use_figma
Input: {
  "js": "
    const collection = figma.variables.createVariableCollection('design-tokens');
    return { collectionId: collection.id, defaultModeId: collection.modes[0].modeId };
  "
}
```

#### Create a Color Variable

```
Tool: use_figma
Input: {
  "js": "
    const collection = figma.variables.getVariableCollectionById('COLLECTION_ID');
    const variable = figma.variables.createVariable('color/accent', collection.id, 'COLOR');
    variable.setValueForMode(collection.modes[0].modeId, { r: 0.149, g: 0.388, b: 0.92, a: 1 });
    variable.scopes = ['ALL_FILLS'];
    variable.codeSyntax = { WEB: 'var(--color-accent)' };
    return { variableId: variable.id };
  "
}
```

#### Create a Float Variable (Spacing)

```
Tool: use_figma
Input: {
  "js": "
    const collection = figma.variables.getVariableCollectionById('COLLECTION_ID');
    const variable = figma.variables.createVariable('spacing/lg', collection.id, 'FLOAT');
    variable.setValueForMode(collection.modes[0].modeId, 32);
    variable.scopes = ['GAP', 'WIDTH_HEIGHT'];
    variable.codeSyntax = { WEB: 'var(--spacing-lg)' };
    return { variableId: variable.id };
  "
}
```

#### Create an Alias (Semantic → Primitive)

```
Tool: use_figma
Input: {
  "js": "
    const primitiveVar = figma.variables.getVariableById('PRIMITIVE_VARIABLE_ID');
    const semanticVar = figma.variables.getVariableById('SEMANTIC_VARIABLE_ID');
    const collection = figma.variables.getVariableCollectionById(semanticVar.variableCollectionId);
    semanticVar.setValueForMode(collection.modes[0].modeId, figma.variables.createVariableAlias(primitiveVar));
    return { aliasCreated: true };
  "
}
```

#### Batch Write from DTCG Token JSON

```
Tool: use_figma
Input: {
  "js": "
    const tokens = JSON.parse(TOKENS_JSON_STRING);
    const collection = figma.variables.createVariableCollection('design-tokens');
    const modeId = collection.modes[0].modeId;
    const results = [];

    function walkTokens(obj, prefix) {
      for (const [key, val] of Object.entries(obj)) {
        const path = prefix ? prefix + '/' + key : key;
        if (val.$value !== undefined && val.$type) {
          let resolvedType, figmaValue;
          if (val.$type === 'color') {
            resolvedType = 'COLOR';
            // Convert hex to Figma RGBA (0-1 floats)
            const hex = val.$value.replace('#', '');
            figmaValue = {
              r: parseInt(hex.slice(0,2), 16) / 255,
              g: parseInt(hex.slice(2,4), 16) / 255,
              b: parseInt(hex.slice(4,6), 16) / 255,
              a: 1
            };
          } else if (val.$type === 'dimension') {
            resolvedType = 'FLOAT';
            figmaValue = parseFloat(val.$value);
          } else if (val.$type === 'number') {
            resolvedType = 'FLOAT';
            figmaValue = Number(val.$value);
          }
          if (resolvedType) {
            const v = figma.variables.createVariable(path, collection.id, resolvedType);
            v.setValueForMode(modeId, figmaValue);
            v.codeSyntax = { WEB: 'var(--' + path.replace(/\\//g, '-') + ')' };
            results.push({ path, type: resolvedType });
          }
        } else if (typeof val === 'object' && !val.$value) {
          walkTokens(val, path);
        }
      }
    }
    walkTokens(tokens, '');
    return { created: results.length, variables: results };
  "
}
```

Replace `TOKENS_JSON_STRING` with the stringified contents of your `tokens.json`.

### MCP Prompt: figma-generate-library

Available as a built-in MCP prompt/skill. Generates a design system in Figma from an existing codebase. Useful for reverse-engineering tokens from a live project.

### Known Limitations

- **Alias stripping**: `get_variable_defs` returns resolved values, not alias chains. Use `use_figma` Plugin API to read aliases reliably.
- **Rate limits**: Professional/Organization get 200 calls/day. Enterprise gets 600/day. Plan ahead for batch operations.
- **Remote only**: MCP server is Figma-hosted. Requires network access and Figma account session.
- **Free tier unusable**: 6 calls/month makes iterative AI workflows impossible on Starter plan.

---

## Path B: Figma REST API

### Requirements

- **Enterprise plan with Full seats** — Variables API is Enterprise-only
- Authentication: Personal Access Token or OAuth2
- OAuth scopes: `file_variables:read` (GET), `file_variables:write` (POST)
- Base URL: `https://api.figma.com`

### Auth Setup

Personal Access Token (simplest):
```
Header: X-Figma-Token: <personal_access_token>
```

Generate at: Figma → Settings → Personal Access Tokens

### Read Variables

#### GET Local Variables

```bash
curl -s \
  -H "X-Figma-Token: YOUR_TOKEN" \
  "https://api.figma.com/v1/files/FILE_KEY/variables/local"
```

Response structure (abbreviated):
```json
{
  "status": 200,
  "meta": {
    "variableCollections": {
      "VariableCollectionId:1:1": {
        "id": "VariableCollectionId:1:1",
        "name": "design-tokens",
        "modes": [{ "modeId": "1:0", "name": "Default" }],
        "variableIds": ["VariableID:2:1", "VariableID:2:2"]
      }
    },
    "variables": {
      "VariableID:2:1": {
        "id": "VariableID:2:1",
        "name": "color/accent",
        "resolvedType": "COLOR",
        "valuesByMode": {
          "1:0": { "r": 0.149, "g": 0.388, "b": 0.92, "a": 1 }
        },
        "scopes": ["ALL_FILLS"],
        "codeSyntax": { "WEB": "var(--color-accent)" }
      },
      "VariableID:2:2": {
        "id": "VariableID:2:2",
        "name": "color/surface",
        "resolvedType": "COLOR",
        "valuesByMode": {
          "1:0": { "type": "VARIABLE_ALIAS", "id": "VariableID:3:1" }
        },
        "scopes": ["FRAME_FILL"],
        "codeSyntax": { "WEB": "var(--color-surface)" }
      }
    }
  }
}
```

Note: Alias values appear as `{"type": "VARIABLE_ALIAS", "id": "VariableID:..."}` — this preserves the alias chain, unlike MCP's `get_variable_defs`.

Rate limit tier: Tier 2.

#### GET Published Variables

```bash
curl -s \
  -H "X-Figma-Token: YOUR_TOKEN" \
  "https://api.figma.com/v1/files/FILE_KEY/variables/published"
```

Same response structure. Use this to read variables published as a library.

### Write Variables

#### POST Create/Update/Delete Variables

```bash
curl -s -X POST \
  -H "X-Figma-Token: YOUR_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "variableCollections": [
      {
        "action": "CREATE",
        "id": "temp_collection_1",
        "name": "design-tokens"
      }
    ],
    "variableModes": [],
    "variables": [
      {
        "action": "CREATE",
        "id": "temp_color_accent",
        "name": "color/accent",
        "variableCollectionId": "temp_collection_1",
        "resolvedType": "COLOR",
        "scopes": ["ALL_FILLS"],
        "codeSyntax": { "WEB": "var(--color-accent)" }
      },
      {
        "action": "CREATE",
        "id": "temp_spacing_lg",
        "name": "spacing/lg",
        "variableCollectionId": "temp_collection_1",
        "resolvedType": "FLOAT",
        "scopes": ["GAP", "WIDTH_HEIGHT"],
        "codeSyntax": { "WEB": "var(--spacing-lg)" }
      }
    ],
    "variableModeValues": [
      {
        "variableId": "temp_color_accent",
        "modeId": "temp_collection_1:mode_default",
        "value": { "r": 0.149, "g": 0.388, "b": 0.92, "a": 1 }
      },
      {
        "variableId": "temp_spacing_lg",
        "modeId": "temp_collection_1:mode_default",
        "value": 32
      }
    ]
  }' \
  "https://api.figma.com/v1/files/FILE_KEY/variables"
```

Response includes `tempIdToRealId` mapping:
```json
{
  "status": 200,
  "tempIdToRealId": {
    "temp_collection_1": "VariableCollectionId:10:1",
    "temp_color_accent": "VariableID:11:1",
    "temp_spacing_lg": "VariableID:11:2",
    "temp_collection_1:mode_default": "10:0"
  }
}
```

Rate limit tier: Tier 3.

#### Create an Alias via REST API

To make `color/surface` alias `color/bg/light`:

```bash
curl -s -X POST \
  -H "X-Figma-Token: YOUR_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "variableModeValues": [
      {
        "variableId": "VariableID:11:3",
        "modeId": "10:0",
        "value": { "type": "VARIABLE_ALIAS", "id": "VariableID:11:4" }
      }
    ]
  }' \
  "https://api.figma.com/v1/files/FILE_KEY/variables"
```

#### Atomicity

All changes in a single POST are atomic. If any variable, collection, or mode in the request fails validation, the entire request rolls back. No partial writes.

#### Limits

- 5,000 variables per collection
- 40 modes per collection
- Temp IDs allowed only on CREATE actions; response maps them to real IDs

### DTCG to Figma Variable Mapping (POST Body Construction)

To convert a DTCG `tokens.json` into a REST API POST body:

1. Walk the DTCG token tree
2. For each token with `$value` and `$type`:
   - Map `$type` to `resolvedType` using the mapping table below
   - Map `$value` to Figma value format (hex string to `{r,g,b,a}` floats for COLOR, strip `px`/`rem` units to number for FLOAT)
   - Use the DTCG path (dot-separated groups) as the variable `name` with `/` separators
   - Set `scopes` based on the token's semantic role
   - Set `codeSyntax.WEB` to `var(--token-path)`
3. For alias tokens (DTCG value is `"{group.name}"`), set value to `{"type": "VARIABLE_ALIAS", "id": "VariableID:..."}` — requires knowing the target variable's Figma ID (read first, then write aliases)

---

## Path C: Tokens Studio

### Plugin Workflow (Figma ↔ Git)

1. Install [Tokens Studio for Figma](https://tokens.studio/) from Figma Community
2. Open the plugin in your Figma file
3. Go to Settings → Token Format → select **W3C DTCG**
4. **Import**: Load the generated `tokens.json` file. Tokens appear organized by group (color, typography, spacing, etc.)
5. **Apply**: Use plugin interface to bind tokens to design elements
6. **Edit**: Adjust values directly in the plugin or via Figma Variables panel
7. **Export**: Click Export → select W3C DTCG format → save as `tokens-modified.json`

Bidirectional sync with Git (GitHub/GitLab/JSONBin):
- Configure sync target in plugin settings
- Plugin pushes/pulls token files to/from the repository
- Handles format conversion between legacy Tokens Studio format and DTCG

### CLI Workflow (@tokens-studio/sdk)

The CLI (`@tokens-studio/sdk` v2.0.2+) provides platform-to-local pull:

```bash
# Install
npm install -g @tokens-studio/sdk

# Configure API key (Tokens Studio platform account required)
tokensstudio setup

# Pull tokens from Tokens Studio platform to local
tokensstudio pull
```

For full pipeline with code output, pair with Style Dictionary v4+:

```bash
# Pull tokens from platform
tokensstudio pull

# Transform DTCG tokens to platform-specific outputs
npx style-dictionary build --config sd.config.js
```

### Limitations

- **CLI is pull-only**: `tokensstudio pull` downloads tokens from the platform. It does not push back to Figma. Use the plugin for Figma sync.
- **Plugin required for Figma sync**: The CLI alone cannot read or write Figma variables.
- **Platform API key**: CLI requires a Tokens Studio platform account and API key.
- **Format conversion**: Converting between legacy Tokens Studio format and DTCG may introduce minor inconsistencies — always verify after conversion.

---

## Path D: Manual Fallback

When no API access is available (Free plan without Tokens Studio, or air-gapped environment).

### Push: Spec → Figma

1. Open `tokens.json` and the Figma file side by side
2. Manually create Figma local variables matching each token:
   - Use `/` separators for group hierarchy (`color/accent`, `spacing/lg`)
   - Set values by hand, converting formats (hex to Figma color picker, px values to numbers)
3. Use `layout-spec.yaml` as reference for frame and component structure
4. Figma uses Auto Layout (not CSS Flexbox/Grid), so translate:
   - `gap` → Auto Layout spacing
   - `breakpoints` → separate frames per viewport size
   - Component types → Figma components/variants

### Pull: Figma → Spec

1. Open Figma Variables panel, note changed values
2. Manually create `tokens-modified.json` reflecting the changes (or describe changes to AI in text)
3. Provide to AI for diff and consistency check

---

## Figma Variables ↔ DTCG Mapping Table

| Figma resolvedType | Figma Scopes | DTCG $type | Value Conversion |
|-------------------|-------------|-----------|-----------------|
| COLOR | ALL_FILLS, FRAME_FILL, SHAPE_FILL, TEXT_FILL, STROKE_COLOR | color | Hex `#rrggbb` ↔ `{r, g, b, a}` floats (0–1). Example: `#2563eb` ↔ `{r: 0.149, g: 0.388, b: 0.92, a: 1}` |
| FLOAT | GAP, WIDTH_HEIGHT | dimension | `"32px"` ↔ `32` (strip unit) |
| FLOAT | CORNER_RADIUS | dimension | `"8px"` ↔ `8` |
| FLOAT | OPACITY | number | `0.8` ↔ `0.8` (no unit, direct) |
| FLOAT | FONT_SIZE, LINE_HEIGHT, LETTER_SPACING, PARAGRAPH_SPACING | dimension | `"16px"` ↔ `16` |
| FLOAT | STROKE_FLOAT, EFFECT_FLOAT | dimension | `"1px"` ↔ `1` |
| STRING | FONT_FAMILY | fontFamily | `"Space Grotesk"` ↔ `"Space Grotesk"` (direct) |
| STRING | FONT_STYLE | fontStyle | `"italic"` ↔ `"italic"` (direct) |
| BOOLEAN | — | (no DTCG equivalent) | Store in `$extensions.figma.boolean` |

### Alias Mapping

| Direction | Format |
|-----------|--------|
| Figma → DTCG | `{"type": "VARIABLE_ALIAS", "id": "VariableID:123:456"}` → `"{group.token-name}"` |
| DTCG → Figma | `"{color.primitive.blue-600}"` → `{"type": "VARIABLE_ALIAS", "id": "VariableID:..."}` |

Converting DTCG alias references to Figma requires a lookup step: read existing variables first (Path B GET), build a name-to-ID map, then substitute IDs in the POST body.

---

## Pull: Figma → Spec (All Paths)

### AI Readback Process

When the user provides modified tokens (via any export path), the AI executes:

1. **Diff**: Compare `tokens-modified.json` against current `tokens.json`
   - List every changed value with before → after
   - Categorize changes by group (color, typography, spacing, motion)
   - Identify any added or removed tokens

2. **Consistency Checks**:

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
   - Verify durations are within recommended ranges (150–400ms)

3. **Report**:
   ```
   Token Sync Report
   -----------------
   Changes detected: {N}

   OK  color.accent: #e76f51 → #2563eb (contrast: 5.1:1 — OK)
   WARN  typography.font-display: "Space Grotesk" → "Inter" (BANNED — suggest "Instrument Serif")
   OK  spacing.lg: 24px → 32px (8px grid — OK)

   1 issue requires attention. Apply changes?
   ```

4. **User confirms** → AI updates `tokens.json` and creates version snapshot in `.design-history/`

## Diff: Token Comparison

Deep JSON comparison process:
- Walk both token trees in parallel
- For each token: compare `$value` fields
- Ignore `$description` changes (informational only)
- Report `$type` changes as warnings (likely a mistake)
- New tokens: listed as "added"
- Missing tokens: listed as "removed" (warn — may break layout-spec references)

---

## Recommended Workflow

```
1. AI generates spec (tokens.json + layout-spec.yaml)
2. Preview with html-preview adapter (quick direction check)
3. Detect capability (plan tier → Path A/B/C/D)
4. Push tokens to Figma:
   - Path A: use_figma batch write (MCP, Pro+ plans)
   - Path B: POST /v1/files/:key/variables (REST API, Enterprise)
   - Path C: Import via Tokens Studio plugin (any plan)
   - Path D: Manual variable creation (any plan)
5. Build layout in Figma using tokens (manual, guided by layout-spec)
6. Adjust token values in Figma (Variables panel, Tokens Studio, or directly)
7. Export modified tokens:
   - Path A: use_figma read + get_variable_defs (alias caveat applies)
   - Path B: GET /v1/files/:key/variables/local (preserves aliases)
   - Path C: Export via Tokens Studio plugin (DTCG format)
   - Path D: Manual transcription
8. AI syncs changes (diff + consistency check + version snapshot)
9. Repeat 6-8 until design approved
10. Hand off final spec to design-to-code-runner
```

---

## Limits

### MCP Rate Limits (Path A)
- **Free tier: 6 MCP calls per month** — not viable for iterative AI workflows
- Pro/Org tier: 200 calls/day — workable for moderate iteration
- Enterprise tier: 600 calls/day — comfortable for heavy AI use
- `use_figma` each invocation counts as one call regardless of script complexity

### REST API Constraints (Path B)
- **Enterprise plan required** for Variables API endpoints
- Rate limits by tier: `X-Figma-Rate-Limit-Type` header on responses
- Tier 2 (reads): higher allowance. Tier 3 (writes): lower allowance
- All POST mutations are atomic — partial failure rolls back entire request
- OAuth scope requirements: `file_variables:read`, `file_variables:write`

### Plugin Dependencies (Path C)
- Tokens Studio is a **third-party plugin**, not native Figma
- Plugin must be installed per-file by each team member
- Token format conversion (legacy ↔ DTCG) may introduce inconsistencies
- CLI is pull-only — cannot push to Figma

### Format Differences (All Paths)
- Figma Variables use a proprietary format (not DTCG natively)
- Color: Figma uses `{r, g, b, a}` floats (0–1), DTCG uses hex strings
- Units: Figma FLOAT variables are unitless numbers, DTCG dimension tokens include units (`px`, `rem`)
- Boolean: Figma BOOLEAN has no direct DTCG `$type` — use `$extensions`
- Alias chain: REST API GET preserves aliases; MCP `get_variable_defs` may flatten them

### vs. Penpot
| Aspect | Figma | Penpot |
|--------|-------|--------|
| DTCG native support | No (via plugin or conversion) | Yes (built-in) |
| API rate limits | Strict (plan-based) | None (free cloud) |
| Variables API access | Enterprise only (REST) | N/A (token import/export) |
| Layout system | Auto Layout (proprietary) | CSS Flexbox/Grid (standard) |
| Self-hosting | Not possible | Fully supported |
| Cost for AI workflow | $15+/mo minimum | Free |

**Note**: If choosing between Figma and Penpot for this workflow, Penpot has significant advantages for AI-driven design: native DTCG support, no API rate limits, CSS-native layout system, and free cloud hosting. Use Figma primarily when the team already uses it.
