# Brand Guardrails Index

Cross-brand analysis of design guardrails for 66 brands.

## Universal Patterns (Cross-Brand Consensus)

These rules hold across all reference design systems. Any brand-conformant output should satisfy them.

### Typography

1. **Never use weight 700 (bold) on primary typefaces.** Claude caps at 500, Stripe at 300 (body/headlines) / 400 (buttons), Linear at 590, Vercel at 600. None uses bold for their primary font in headlines or body.

2. **OpenType features are non-negotiable.** Every brand has specific OpenType settings that transform a generic font into their typeface identity:
   - Claude: N/A (custom Anthropic typeface family, no special OT features)
   - Stripe: `"ss01"` on all sohne-var
   - Linear: `"cv01", "ss03"` on all Inter Variable
   - Vercel: `"liga"` on all Geist

3. **Negative letter-spacing at display sizes.** All sans-serif-led brands (Stripe, Linear, Vercel) use progressively tighter tracking at large sizes. Claude (serif headlines) uses normal tracking but tight line-heights instead.

4. **Strict weight hierarchy.** Each brand uses 2-3 weights with clear roles. No brand allows arbitrary weight mixing:
   - Claude: 500 (serif headings), 400-500 (sans body/UI)
   - Stripe: 300 (headlines/body), 400 (buttons/links)
   - Linear: 400 (reading), 510 (emphasis), 590 (strong)
   - Vercel: 400 (body), 500 (UI), 600 (headings)

### Color

5. **Never use pure black (`#000000`) for primary headings.** Each brand has a branded near-black:
   - Claude: `#141413` (warm olive-tinted)
   - Stripe: `#061b31` (deep navy)
   - Linear: `#f7f8f8` text on dark bg (the background is near-black: `#08090a`)
   - Vercel: `#171717` (slight warmth)

6. **Brand accent color is reserved for CTAs and high-signal moments only.** Every brand uses a single chromatic accent sparingly:
   - Claude: Terracotta `#c96442`
   - Stripe: Purple `#533afd`
   - Linear: Indigo `#5e6ad2` / `#7170ff`
   - Vercel: Achromatic (black CTA); workflow colors are semantic only

7. **Decorative/secondary accent colors must not appear on interactive elements.** Each brand separates decorative from interactive color:
   - Claude: Illustrations use terracotta/green/black; only terracotta on CTA
   - Stripe: Ruby/Magenta are gradient-only; Purple is interactive
   - Linear: Only indigo is interactive; all else is grayscale
   - Vercel: Workflow colors (Red/Pink/Blue) are semantic, never used as button colors

### Depth & Shadow

8. **Shadow systems are brand-colored and specific, never generic.** Each brand's shadow palette is as distinctive as its color palette:
   - Claude: warm ring shadows (`0px 0px 0px 1px` in warm grays)
   - Stripe: blue-tinted multi-layer (`rgba(50,50,93,0.25)` + neutral)
   - Linear: luminance stepping (background opacity, not shadows)
   - Vercel: multi-layer shadow stacks with inner `#fafafa` ring

9. **No heavy drop shadows.** All four brands use subtle, controlled elevation. No brand exceeds ~0.25 opacity in their shadow system, and most stay well below 0.10 for ambient effects.

### Layout

10. **8px base spacing unit.** All four brands use an 8px grid as the fundamental spacing unit, though each has its own sub-grid variations.

11. **Conservative border-radius, matched to brand identity.** No brand uses arbitrary or inconsistent rounding:
    - Claude: 8-32px range, generous and soft
    - Stripe: 4-8px range, conservative and architectural
    - Linear: 2-22px range, functional with pill options for tags
    - Vercel: 6-12px standard, pills for badges only

---

## Brand-Specific Rules (What Makes Each One Unique)

### Claude -- The Literary Salon
| Unique Rule | Why It Matters |
|---|---|
| Parchment (`#f5f4ed`) page background | The warm cream is the emotional foundation. No other brand uses a non-white, non-dark page canvas. |
| Custom serif headlines (Anthropic Serif, weight 500) | The only brand using serif for headings. This is the core identity differentiator. |
| Light/dark section alternation | Creates a "chapter" reading rhythm. No other brand alternates full sections like this. |
| Warm-only neutrals (yellow-brown undertone on every gray) | No cool grays anywhere. The most chromatic neutral system of the four. |
| Organic, hand-drawn illustrations | The only brand using non-geometric, editorial-style artwork. |

### Stripe -- The Financial Institution Redesigned
| Unique Rule | Why It Matters |
|---|---|
| Weight 300 for headlines | The lightest headline weight among all four brands. "Whisper authority." |
| `"ss01"` on all sohne-var text | The single most impactful OT feature. Without it, Stripe looks like a different company. |
| Blue-tinted shadows (`rgba(50,50,93,0.25)`) | The only brand with chromatically-tinted shadows. Makes elevation feel on-brand. |
| Deep Navy headings (`#061b31`) instead of near-black | The warmest heading color relative to black among all four brands. |
| `"tnum"` for financial data (separate from `"ss01"`) | The only brand with two distinct OT modes for different content types. |

### Linear -- The Precision Engine
| Unique Rule | Why It Matters |
|---|---|
| Dark-mode-native (`#08090a`) | Not a dark theme on a light design. The darkness is the native medium. |
| Weight 510 as signature | A between-weight no other brand uses. Sits exactly between regular and medium. |
| Semi-transparent white borders (`rgba(255,255,255,0.05-0.08)`) | Borders on dark backgrounds use white at near-zero opacity. Unique to dark-native design. |
| Ghost-transparent button backgrounds (`rgba(255,255,255,0.02)`) | Buttons barely exist visually. The most extreme button transparency of any brand. |
| Luminance stacking for elevation (no shadows) | The only brand where depth comes entirely from background opacity, not shadow. |

### Vercel -- The Minified Interface
| Unique Rule | Why It Matters |
|---|---|
| Shadow-as-border (`0px 0px 0px 1px rgba(0,0,0,0.08)`) | Borders live in the shadow layer, not the box model. The most technically sophisticated border approach. |
| Most aggressive letter-spacing (-2.4px to -2.88px at 48px) | Tighter than any other brand. Text feels "minified for production." |
| Four-layer shadow stacks with inner `#fafafa` ring | The inner glow is unique. Cards feel "built, not floating." |
| Achromatic UI with semantic-only color | The only brand where even the CTA is black, not colored. Color exists only in the workflow pipeline. |
| Geist Mono uppercase for technical labels | The "developer console voice" expressed through typography. |

---

## Quick Comparison Matrix

| Dimension | Claude | Stripe | Linear | Vercel |
|---|---|---|---|---|
| **Page Background** | `#f5f4ed` (warm cream) | `#ffffff` (white) | `#08090a` (near-black) | `#ffffff` (white) |
| **Headline Font** | Anthropic Serif | sohne-var | Inter Variable | Geist Sans |
| **Headline Weight** | 500 | 300 | 510 | 600 |
| **Max Weight** | 500 (serif) | 400 (buttons) | 590 | 600 (headings) |
| **Brand Accent** | `#c96442` terracotta | `#533afd` purple | `#5e6ad2` indigo | None (achromatic) |
| **Shadow Signature** | warm ring `0px 0px 0px 1px` | blue-tinted multi-layer | luminance stepping | multi-layer + `#fafafa` glow |
| **Border Radius** | 8-32px (generous) | 4-8px (conservative) | 2-22px (functional) | 6-12px (standard) |
| **OT Features** | N/A | `"ss01"` | `"cv01","ss03"` | `"liga"` |
| **Dark Mode** | Sections only | Brand Dark `#1c1e54` | Native `#08090a` | Not primary |
| **Temperature** | Warm (yellow-brown) | Cool (navy-blue) | Cool (blue-gray) | Neutral (achromatic) |
| **Personality** | Literary salon | Financial luxury | Precision engine | Minified infrastructure |

---

## File Index (66 brands)

### Original Four
- [claude.md](./claude.md) -- Claude (Anthropic)
- [stripe.md](./stripe.md) -- Stripe
- [linear.md](./linear.md) -- Linear
- [vercel.md](./vercel.md) -- Vercel

### AI & LLM Platforms
- [cohere.md](./cohere.md) -- Cohere
- [elevenlabs.md](./elevenlabs.md) -- ElevenLabs
- [minimax.md](./minimax.md) -- Minimax
- [mistral.md](./mistral.md) -- Mistral
- [ollama.md](./ollama.md) -- Ollama
- [opencode-ai.md](./opencode-ai.md) -- OpenCode AI
- [replicate.md](./replicate.md) -- Replicate
- [runwayml.md](./runwayml.md) -- RunwayML
- [together-ai.md](./together-ai.md) -- Together AI
- [voltagent.md](./voltagent.md) -- VoltAgent
- [xai.md](./xai.md) -- xAI

### Developer Tools & IDEs
- [cursor.md](./cursor.md) -- Cursor
- [expo.md](./expo.md) -- Expo
- [lovable.md](./lovable.md) -- Lovable
- [raycast.md](./raycast.md) -- Raycast
- [superhuman.md](./superhuman.md) -- Superhuman
- [warp.md](./warp.md) -- Warp

### Backend, Database & DevOps
- [clickhouse.md](./clickhouse.md) -- ClickHouse
- [composio.md](./composio.md) -- Composio
- [hashicorp.md](./hashicorp.md) -- HashiCorp
- [mongodb.md](./mongodb.md) -- MongoDB
- [posthog.md](./posthog.md) -- PostHog
- [sanity.md](./sanity.md) -- Sanity
- [sentry.md](./sentry.md) -- Sentry
- [supabase.md](./supabase.md) -- Supabase

### Productivity & SaaS
- [calcom.md](./calcom.md) -- Cal.com
- [intercom.md](./intercom.md) -- Intercom
- [mintlify.md](./mintlify.md) -- Mintlify
- [notion.md](./notion.md) -- Notion
- [resend.md](./resend.md) -- Resend
- [zapier.md](./zapier.md) -- Zapier

### Design & Creative Tools
- [airtable.md](./airtable.md) -- Airtable
- [clay.md](./clay.md) -- Clay
- [figma.md](./figma.md) -- Figma
- [framer.md](./framer.md) -- Framer
- [miro.md](./miro.md) -- Miro
- [webflow.md](./webflow.md) -- Webflow

### Fintech & Crypto
- [binance.md](./binance.md) -- Binance
- [coinbase.md](./coinbase.md) -- Coinbase
- [kraken.md](./kraken.md) -- Kraken
- [revolut.md](./revolut.md) -- Revolut
- [wise.md](./wise.md) -- Wise

### E-commerce & Retail
- [airbnb.md](./airbnb.md) -- Airbnb
- [meta.md](./meta.md) -- Meta
- [nike.md](./nike.md) -- Nike
- [shopify.md](./shopify.md) -- Shopify

### Media & Consumer Tech
- [apple.md](./apple.md) -- Apple
- [ibm.md](./ibm.md) -- IBM
- [nvidia.md](./nvidia.md) -- NVIDIA
- [pinterest.md](./pinterest.md) -- Pinterest
- [playstation.md](./playstation.md) -- PlayStation
- [spacex.md](./spacex.md) -- SpaceX
- [spotify.md](./spotify.md) -- Spotify
- [the-verge.md](./the-verge.md) -- The Verge
- [uber.md](./uber.md) -- Uber
- [wired.md](./wired.md) -- WIRED

### Automotive
- [bmw.md](./bmw.md) -- BMW
- [bugatti.md](./bugatti.md) -- Bugatti
- [ferrari.md](./ferrari.md) -- Ferrari
- [lamborghini.md](./lamborghini.md) -- Lamborghini
- [renault.md](./renault.md) -- Renault
- [tesla.md](./tesla.md) -- Tesla
