# Cursor -- Design Guardrails

## Do's (10 items)

1. **Use `#14120b` (Obsidian) as the primary page background.**
   This warm near-black with brown undertone is the actual Cursor dark theme background from cursor.com.
   It separates Cursor from generic dark themes that use neutral `#0d0d0d` or `#1a1a1a`.
   Verify: page `background-color` must be `#14120b`.
   For frosted nav bars use `rgba(20,18,11,0.85)` with `backdrop-filter: blur(12px)`.

2. **Use Cursor Gothic for all display and UI text.**
   Cursor commissioned a custom typeface -- Cursor Gothic -- for headlines, body, labels, nav, and buttons.
   It is the primary brand font across the marketing site and product chrome.
   Verify: every non-code text element uses `'Cursor Gothic', -apple-system, sans-serif` as its font stack.
   If Cursor Gothic is unavailable, degrade to system sans-serif but never silently substitute Inter.

3. **Use Berkeley Mono for all code, terminal, and inline-code contexts.**
   Berkeley Mono is the official monospace face, paired with Cursor Gothic to create the IDE-meets-brand tension.
   This pairing is the typographic identity of the product.
   Verify: every `<code>`, `<pre>`, terminal output, and chat code block uses `'Berkeley Mono', 'JetBrains Mono', monospace`.

4. **Reserve `#4c9df3` (Cursor Blue) for AI interaction accents, active states, and primary CTAs.**
   This blue is the intelligence signal -- it marks where the AI is working, what is focused, and the primary action.
   It should be scarce and high-signal, appearing only at decisive interaction points.
   Verify: `#4c9df3` appears only on buttons, focused inputs, active tabs, AI indicators, and link hover states.
   Never use it as a decorative background or large surface fill.

5. **Keep all grays warm-tinted with brown/amber undertone.**
   The neutral palette carries intentional warmth: `#d7d6d5` (primary text), `#8a8884` (secondary), `#5c5a56` (tertiary), `#26241e` (elevated surfaces).
   This warm cast makes Cursor's dark theme feel crafted rather than default.
   Verify: no gray in the design has a blue or neutral cast.
   Reject `#808080`, `#666666`, `#e0e0e0`, `#333333` -- these are NOT in the Cursor palette.

6. **Use hairline borders at `rgba(255,255,255,0.07)` for panel separation.**
   IDE aesthetics rely on near-invisible borders that structure space without visual weight.
   Prominent borders at `rgba(255,255,255,0.12)` are reserved for emphasized elements like cards and inputs.
   Verify: borders use the brand's specific alpha values, not solid colors like `#333`, `#444`, or `#2a2a2a`.
   The two-tier border system (0.07 hairline, 0.12 prominent) must be respected.

7. **Maintain developer-dense spacing with 4px base grid.**
   Cursor signals professionalism through compact, efficient layouts.
   Card padding is 24px (not 32px). Nav height is 56px (not 64px). Base text is 14px (not 16px).
   Verify: spacing values are multiples of 4px.
   Components should feel tool-like rather than marketing-generous.
   Only hero sections on marketing pages use generous spacing (120px+).

8. **Use heavy shadows for dark-surface elevation.**
   On Obsidian backgrounds, light shadows are completely invisible.
   Level-1 needs `rgba(0,0,0,0.25)`, modals need `rgba(0,0,0,0.40)`.
   The only colored shadow is the accent glow: `0 0 12px rgba(76,157,243,0.20)`.
   Verify: no shadow on dark surfaces uses opacity below 0.20.
   The accent glow appears only on focused inputs and AI-active indicators.

9. **Apply the accent-muted wash `rgba(76,157,243,0.12)` for selected and active states.**
   This blue-tinted ghost background marks selected list items, active tab backgrounds, and focused tree items.
   It communicates "AI-selected" or "user-focused" without flooding the UI with solid blue.
   Verify: selection/active states use the translucent wash, not solid `#4c9df3` backgrounds.
   AI suggestion lines use the lighter `rgba(76,157,243,0.08)` wash with a 2px left border.

10. **Use `#f14c4c` for errors and `#73c991` for success, consistent with IDE diagnostics.**
    These semantic colors are drawn from code editor convention -- red squiggly underlines, green diff markers.
    Warning amber is `#e5c07b` for linter warnings and caution states.
    Verify: error states are `#f14c4c`, success states `#73c991`, warning states `#e5c07b`.
    No other red, green, or yellow variants should appear in the design.
    Diff backgrounds use translucent washes: added `rgba(115,201,145,0.15)`, removed `rgba(241,76,76,0.15)`.

## Don'ts (10 items)

1. **Do not use neutral dark backgrounds (`#0d0d0d`, `#1a1a1a`, `#121212`, `#000000`).**
   These lack the warm undertone that defines Cursor's dark palette.
   The warm-dark differentiation separates Cursor from VS Code's default dark theme and generic Tailwind dark.
   Use `#14120b` (surface), `#1b1913` (subtle), `#26241e` (elevated), `#201e18` (overlay) instead.
   Even `#1a1a1a` is too neutral -- it must be `#1b1913` with its brown cast.

2. **Do not use `#4c9df3` as a surface fill or background color.**
   Cursor Blue is a signal, not a surface.
   Using it for section backgrounds, hero fills, or card backgrounds drowns out the accent's meaning.
   Maximum opacity for blue backgrounds is 0.12 (the accent-muted wash).
   Solid blue is for text, icons, borders, and small interactive elements (buttons, badges) only.

3. **Do not use Inter, system-ui, or generic sans-serif as the primary UI font.**
   Cursor has a custom typeface (Cursor Gothic) and this is core to brand recognition.
   Falling back to Inter makes the design indistinguishable from any dark SaaS template.
   Use Cursor Gothic with system font fallbacks in the stack.
   The only exception: if building a prototype where custom fonts cannot load, document the substitution.

4. **Do not use monospace for non-code UI text.**
   Berkeley Mono is strictly for code contexts: code blocks, inline code, terminal, file paths, git hashes.
   Using it for labels, headings, nav links, or badge text breaks the type pairing hierarchy.
   The Gothic-for-UI / Mono-for-code split must be maintained across every component.

5. **Do not use Cursor Gothic for code blocks or terminal output.**
   Proportional fonts in code contexts destroy readability and the IDE authenticity.
   Every character in a code block must be monospace for alignment.
   Verify: no `<pre>` or `<code>` element renders in Cursor Gothic or any sans-serif face.

6. **Do not use border-radius above 12px on standard components.**
   Cursor's geometry is crisp, not bubbly -- it communicates precision and developer tooling.
   Standard buttons get 6px, cards get 8px, featured containers get 12px.
   Only pill badges use 9999px.
   Rounded corners above 12px (16px, 24px, 32px) make the design feel consumer-app instead of developer-tool.
   Verify: no card, button, or container uses radius greater than 12px (except pill badges).

7. **Do not use light or medium-weight headlines.**
   Headlines in Cursor use weight 700 with tight letter-spacing (-0.02em) to create density and authority.
   Weight 400 or 500 headlines feel tentative and lose the technical confidence.
   Body text is 400, labels/buttons are 500, headlines are 700 -- no overlap.
   Verify: all `<h1>` through `<h3>` elements use `font-weight: 700`.

8. **Do not apply marketing-generous spacing in tool-density contexts.**
   32px card padding, 80px section gaps, and 64px nav heights belong to marketing landing pages only.
   When building app-like interfaces (chat panels, settings, sidebars), use the compact scale.
   App context: 12-24px padding, 48px headers, 8-16px gaps.
   Marketing context: 24-32px padding, 80px section gaps, 56-64px headers.
   Mixing marketing spacing into tool UI makes the product feel sluggish and wasteful.

9. **Do not use warm or colored tints on text.**
   Text colors in the Cursor palette are desaturated warm grays: `#d7d6d5`, `#8a8884`, `#5c5a56`.
   Do not introduce amber-tinted, green-tinted, or blue-tinted body text.
   The only colored text permitted: `#4c9df3` for links/active states, `#f14c4c` for error messages, `#73c991` for success messages, `#e5c07b` for warnings.
   White `#ffffff` is reserved for text-on-accent (buttons with blue background).

10. **Do not introduce gradients on surfaces or buttons.**
    Cursor's surfaces are flat, solid colors -- the depth system relies on layered surfaces and heavy shadows, not gradients.
    The only gradient allowed: decorative accent line (`linear-gradient(90deg, transparent, #4c9df3, transparent)`) at 1px height, opacity 0.3-0.4.
    Background gradients, button gradients, card gradients, and hero gradient washes are not part of the language.
    If depth is needed, use the surface layer system: `#14120b` -> `#1b1913` -> `#26241e`.

## Critical Violations (5 items)

1. **Neutral dark backgrounds instead of warm-dark Obsidian.**
   Using `#0d0d0d`, `#121212`, or `#1a1a1a` as the page background strips away Cursor's visual identity.
   The warm undertone in `#14120b` is the first and most important differentiator from generic dark UIs.
   Without it, the warm gray text colors (`#d7d6d5`, `#8a8884`) look out of place on neutral surfaces.
   Every downstream color relationship breaks when the surface warmth is wrong.
   Test: place `#14120b` next to `#0d0d0d` -- the brown undertone should be visible.

2. **Missing Cursor Gothic / Berkeley Mono type pairing.**
   The Gothic-for-UI, Mono-for-code split is the typographic identity of the entire brand.
   Replacing either with Inter, system-ui, or generic monospace collapses the design into anonymous dark-theme territory.
   If custom fonts cannot load, the fallback stack must be explicit and the degradation acknowledged.
   Never silently substitute Inter for Cursor Gothic -- it produces a completely different brand impression.

3. **Cursor Blue (`#4c9df3`) used as a surface fill or background.**
   Flooding any component with solid blue destroys the signal-to-noise ratio that makes the accent meaningful.
   Blue is the intelligence accent -- it signals AI activity, focus, and primary action.
   When blue becomes a surface color, nothing feels highlighted anymore and the entire UI flattens.
   Maximum solid blue area: a single button. Maximum blue wash: 0.12 opacity.

4. **Light backgrounds in primary surfaces.**
   Cursor is a dark-first brand built for developers working in dim environments.
   Using white, off-white, or light gray as the page or panel background fundamentally inverts the identity.
   The warm-dark surface IS the brand -- it creates the environment where blue accents glow and code is readable.
   Light variants exist for the marketing site's alternate mode, not for product design language.

5. **Bubbly, consumer-app border-radius (16px+) on standard elements.**
   Cursor communicates precision and developer tooling through crisp, controlled geometry.
   6px buttons, 8px cards, 12px modals -- this scale signals professional software.
   Inflating radii to 16px, 24px, or 32px makes the interface look like a consumer productivity app.
   Pill shapes (9999px) are reserved exclusively for small status badges and toggle tracks.
   The radius scale is a silent but powerful signal of the tool's intended audience.
