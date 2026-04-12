# Penpot Adapter — Bidirectional Design Token Sync

Penpot is the primary visual design tool for this workflow. It natively supports W3C DTCG design tokens (first design tool to do so). This adapter handles bidirectional sync between the design spec and Penpot.

## Push: Spec → Penpot

### Token Import (Current: Manual)

1. Open your Penpot project
2. Open the **Tokens** panel (left sidebar → Tokens tab)
3. Click the **Import** button (or menu → Import tokens)
4. Select the generated `tokens.json` file
5. Penpot will create token sets matching the JSON groups (color, typography, spacing, etc.)
6. Apply tokens to your design elements through the Tokens panel

### Token Import (Future: Plugin API)

When [penpot/penpot#7916](https://github.com/penpot/penpot/issues/7916) is resolved:

```
# Pseudocode for future automation
penpot.tokens.import("tokens.json")
penpot.tokens.apply_to_selection(token_name)
```

### Layout Setup (Current: Manual)

Use `layout-spec.yaml` as a reference to manually create:
1. **Frames** matching `layout.structure` (sidebar frame, main frame)
2. **Components** matching `pages[].sections[].children` types
3. **Auto-layout** settings matching breakpoints and spacing tokens

Penpot uses native CSS Flexbox and Grid — the layout-spec's responsive rules map directly.

## Pull: Penpot → Spec

### Token Export

1. In Penpot, open the **Tokens** panel
2. Click **Export** (or menu → Export tokens)
3. Select **DTCG / W3C format** (this is Penpot's native format)
4. Save as `tokens-modified.json`
5. Provide the file to the AI: "Here are my Penpot token changes" or "Sync from Penpot"

### AI Readback Process

When the user provides a modified token file, the AI executes:

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
   ─────────────────
   Changes detected: {N}

   ✅ color.accent: #e76f51 → #2563eb (contrast: 5.1:1 — OK)
   ⚠️  typography.font-display: "Space Grotesk" → "Inter" (BANNED — suggest "Instrument Serif")
   ✅ spacing.lg: 24px → 32px (8px grid — OK)

   1 issue requires attention. Apply changes?
   ```

4. **User confirms** → AI updates `tokens.json` and creates version snapshot in `.design-history/`

## Diff: Token Comparison

The diff process uses deep JSON comparison:
- Walk both token trees in parallel
- For each token: compare `$value` fields
- Ignore `$description` changes (informational only)
- Report `$type` changes as warnings (likely a mistake)
- New tokens: listed as "added"
- Missing tokens: listed as "removed" (warn — may break layout-spec references)

## Limits

- **Token Plugin API not yet available** ([penpot/penpot#7916](https://github.com/penpot/penpot/issues/7916)) — push/pull is manual file exchange for now
- **No MCP server** — Penpot has REST API and Plugin API, but no official MCP integration yet
- **Layout sync is one-directional** — layout-spec → Penpot frames is manual; Penpot frame changes don't auto-sync back to layout-spec (describe changes to AI in text)
- **Large projects** may have performance issues in Penpot compared to Figma
- **Export format**: Penpot exports DTCG-compatible JSON, but may omit `$description` fields
- **Penpot cloud** (free) has no API rate limits — advantage over Figma

## Recommended Workflow

```
1. AI generates spec (tokens.json + layout-spec.yaml)
2. Preview with html-preview adapter (quick direction check)
3. Import tokens into Penpot (manual)
4. Build layout in Penpot using tokens (manual, guided by layout-spec)
5. Adjust token values visually in Penpot (color picker, font selector, etc.)
6. Export modified tokens from Penpot
7. AI syncs changes (diff + consistency check + version snapshot)
8. Repeat 5-7 until design is approved
9. Hand off final spec to design-to-code-runner
```
