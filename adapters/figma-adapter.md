# Figma Adapter — Bidirectional Design Token Sync

Figma integration for tasteful-frontend design specs. Uses Figma Tokens Studio plugin for DTCG import/export, or Figma MCP server for API-driven workflows (paid plans only).

## Push: Spec → Figma

### Via Tokens Studio Plugin (Recommended)

1. Install [Tokens Studio for Figma](https://tokens.studio/) plugin
2. Open the plugin in your Figma file
3. Go to Settings → Token Format → select **W3C DTCG**
4. Import the generated `tokens.json` file
5. Tokens appear in the plugin panel, organized by group (color, typography, spacing, etc.)
6. Apply tokens to design elements via the plugin interface

### Via Figma MCP Server (Pro+ Plans Only)

Requires Figma Professional plan or higher. See [Figma MCP docs](https://developers.figma.com/docs/figma-mcp-server/plans-access-and-permissions/).

Rate limits by plan:
| Plan | MCP Calls | Cost |
|------|-----------|------|
| Starter (Free) | 6/month | $0 |
| Professional (Full seat) | 200/day | $15+/mo |
| Organization | 200/day | $25+/mo |
| Enterprise | 600/day | $75+/mo |

**Free tier (6 calls/month) is effectively unusable for AI-driven workflows.**

### Layout Setup

Use `layout-spec.yaml` as reference to create frames and components in Figma manually. Figma uses Auto Layout (not CSS Flexbox/Grid like Penpot), so some translation is needed:
- layout-spec `gap` → Auto Layout spacing
- layout-spec `breakpoints` → separate frames per viewport size
- layout-spec component types → Figma components/variants

## Pull: Figma → Spec

### Token Export via Tokens Studio

1. In Tokens Studio plugin, click Export
2. Select **W3C DTCG format**
3. Save as `tokens-modified.json`
4. Provide to AI: "Here are my Figma token changes" or "Sync from Figma"

### Token Export via Figma Variables (Native)

Figma Variables can also be exported, but they use Figma's proprietary format, not DTCG. Use Tokens Studio for standard-compliant export.

### AI Readback Process

Identical to Penpot adapter:
1. **Diff**: Compare modified JSON against current `tokens.json`
2. **Consistency checks**: Contrast ratios, banned fonts, 8px grid alignment, motion ranges
3. **Report**: List changes with pass/warn status
4. **Confirm**: User approves → AI updates `tokens.json` + version snapshot

## Diff: Token Comparison

Same deep JSON comparison as Penpot adapter:
- Compare `$value` fields for each token
- Ignore `$description` changes
- Warn on `$type` changes
- List added/removed tokens

## Limits

### MCP Rate Limits (Critical)
- **Free tier: 6 MCP calls per month** — not viable for iterative AI workflows
- Pro tier: 200 calls/day — workable but requires paid subscription
- Rate limits apply to all REST API tools that read data from Figma
- If rate-limited, fall back to Tokens Studio plugin (manual but unlimited)

### Plugin Dependencies
- Tokens Studio is a **third-party plugin**, not native Figma
- Plugin must be installed per-file by each team member
- Token format conversion (legacy ↔ DTCG) may introduce inconsistencies

### API Changes
- Figma updated OAuth requirements (Nov 2025) — public apps require review
- REST API rate limit structure changed — `X-Figma-Rate-Limit-Type` headers determine tier
- Dev Mode features moved behind paid seats

### Format Differences
- Figma Variables use a proprietary format (not DTCG-compatible natively)
- Tokens Studio provides the DTCG bridge, but adds a dependency layer
- Color format may differ (Figma uses RGBA objects, DTCG uses hex strings) — Tokens Studio handles conversion

### vs. Penpot
| Aspect | Figma | Penpot |
|--------|-------|--------|
| DTCG native support | No (via plugin) | Yes (built-in) |
| API rate limits | Strict (plan-based) | None (free cloud) |
| Layout system | Auto Layout (proprietary) | CSS Flexbox/Grid (standard) |
| Self-hosting | Not possible | Fully supported |
| Cost for AI workflow | $15+/mo minimum | Free |

## Recommended Workflow

```
1. AI generates spec (tokens.json + layout-spec.yaml)
2. Preview with html-preview adapter (quick direction check)
3. Install Tokens Studio plugin in Figma file
4. Import tokens via Tokens Studio (DTCG format)
5. Build layout in Figma using tokens (manual)
6. Adjust token values in Tokens Studio or Figma Variables
7. Export modified tokens via Tokens Studio (DTCG format)
8. AI syncs changes (diff + consistency check + version snapshot)
9. Repeat 6-8 until design approved
10. Hand off final spec to design-to-code-runner
```

**Note**: If you're choosing between Figma and Penpot for this workflow, Penpot has significant advantages for AI-driven design: native DTCG support, no API rate limits, CSS-native layout system, and free cloud hosting. Consider Figma primarily when team/organization already uses it.
