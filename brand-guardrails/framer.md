# Framer -- Design Guardrails

## Do's (10 items)

1. **Use `#0a0a0a` (Canvas Black) as the primary page background.**
   This near-black canvas is the foundational surface of the Framer visual identity -- it represents the infinite workspace of a design tool. Every other color in the system is calibrated against this darkness.
   Verify: page `background-color` is `#0a0a0a` or within the `#0a0a0a`-`#0d0d0d` range. Never a lighter gray, never white.

2. **Reserve Framer Blue (`#0099ff`) exclusively for primary CTAs, active states, and interactive accents.**
   It is the only chromatic color in the system and derives its power from extreme restraint. Blue means "this is interactive" -- nothing else.
   Verify: `#0099ff` appears only on primary action buttons, active toolbar icons, selection highlights, focus rings, and linked text -- never as a background fill, section tint, or decorative element.

3. **Apply spring-physics easing to all meaningful transitions.**
   Framer is a motion design tool; its own interface must demonstrate motion excellence. The signature curve is `cubic-bezier(0.2, 0.9, 0.3, 1.0)` -- a slight overshoot that communicates physical spring behavior.
   Use this for hover transforms, panel reveals, element entrances, and any interaction with visual feedback.
   Verify: transition timing functions use the spring bezier or `cubic-bezier(0.16, 1, 0.3, 1)` ease-out. Never `linear`, never basic `ease`.

4. **Use Inter as the exclusive font family across all text.**
   Framer's typography is clean, functional, and uniform. No serif fonts, no decorative typefaces, no multi-family mixing.
   Verify: every text element renders in Inter (with `-apple-system, BlinkMacSystemFont, sans-serif` fallback).
   Exception: monospace code blocks use SF Mono, Fira Code, or ui-monospace.

5. **Use semi-transparent white borders (`rgba(255,255,255,0.05)` to `rgba(255,255,255,0.12)`) instead of solid dark borders.**
   These whisper-thin borders create structure without visual noise on dark surfaces. They subtly reveal the surface beneath rather than drawing hard lines.
   Three tiers: `0.05` subtle, `0.08` standard, `0.12` prominent (interactive elements).
   Verify: card and container borders use `rgba(255,255,255,...)` at low opacity, never solid hex border colors like `#333` or `#444`.

6. **Apply glassmorphic treatment to navigation and floating toolbars.**
   The navbar and canvas toolbars use `backdrop-filter: blur(12px)` over semi-transparent backgrounds (`rgba(10,10,10,0.85)` or similar). This creates the creative-tool studio atmosphere where tools float above the canvas.
   Verify: sticky navigation elements have both `backdrop-filter` and semi-transparent `background`.
   Fallback: for browsers without backdrop-filter support, use a solid `#141414` background.

7. **Use weight 700 for display headlines, 600 for section headings, 500 for UI labels, 400 for body text.**
   The weight hierarchy creates clear visual structure with four distinct tiers:
   - 700: Display (48px+) -- bold, punchy, creative tool confidence
   - 600: Section/Heading (20-36px) -- authoritative but not overpowering
   - 500: UI/Nav/Labels (11-14px) -- readable emphasis for interface chrome
   - 400: Body/Description (16-18px) -- comfortable reading weight
   Verify: no heading renders at 400, no body text renders at 700. Each tier stays in its lane.

8. **Apply negative letter-spacing at display sizes.**
   Headlines at 48px+ use `-0.96px` tracking, 24-36px use `-0.48px`. This tight tracking gives headlines their punchy, modern feel.
   Below 20px, tracking returns to normal. Below 14px, tracking may be slightly positive (0.2px) for legibility at small sizes.
   Verify: display headlines have proportionally negative `letter-spacing`, never positive or zero.

9. **Use the blue glow (`rgba(0,153,255,0.15)`) sparingly for featured elements.**
   The faint blue ambient glow behind hero elements, active buttons, and featured cards is Framer's energy signature -- the visual equivalent of the tool's motion DNA.
   Apply as `box-shadow: 0 0 20px rgba(0,153,255,0.15)` on featured elements, or as a subtle `radial-gradient(ellipse, rgba(0,153,255,0.06) 0%, transparent 70%)` behind hero sections.
   Verify: at most one or two glow sources per viewport. Glow is always faint (0.06-0.15 opacity), never saturated or opaque.

10. **Use hover animations with subtle scale transforms on interactive elements.**
    Buttons scale to `1.02` on hover with the spring bezier. Cards shift border opacity from `0.08` to `0.12` and may gain a faint blue glow.
    Links transition color from `#999999` to `#ffffff` over 150ms.
    Verify: primary buttons include `transform: scale(1.02)` on hover, and the transition uses the spring easing curve, not a static color swap alone.

## Don'ts (10 items)

1. **Do not use light backgrounds for primary surfaces.**
   The dark canvas is Framer's core identity as a creative tool. Every element in the design system -- transparent borders, blue glow, panel shadows -- is calibrated for dark surfaces and breaks on light ones.
   Violation: `background-color: #ffffff`, `#f5f5f5`, `#e0e0e0`, or any gray lighter than `#1c1c1c` on the main page wrapper, body, or primary sections.

2. **Do not apply Framer Blue (`#0099ff`) as a decorative surface color.**
   Flooding cards, sections, or backgrounds with the accent color destroys the signal-to-noise ratio that makes it meaningful as an interactive indicator.
   Violation: `background-color: #0099ff` on cards, section backgrounds, hero fills, or decorative containers. The only permitted blue surfaces are `rgba(0,153,255,0.08)` tints for selected/active states.

3. **Do not use solid opaque borders on dark surfaces.**
   Borders like `#333333` or `#2a2a2a` look heavy and flat on dark backgrounds. The system requires semi-transparent white borders that subtly reveal the surface beneath and scale with background changes.
   Violation: any `border: 1px solid` with a solid hex color (e.g., `#333`, `#444`, `#555`) on dark-background elements.

4. **Do not use serif fonts, script fonts, or any typeface other than Inter.**
   Framer's typographic identity is mono-family: Inter only. Adding decorative fonts contradicts the clean tool aesthetic.
   Violation: any element rendering in Georgia, Times New Roman, Playfair Display, or any serif/display/script typeface.
   Note: this applies to both marketing pages and UI components. The tool identity is uniform.

5. **Do not use `linear` or basic `ease` timing functions for transitions.**
   Framer is a motion design tool. Its own transitions must demonstrate spring-physics sophistication. Using browser defaults tells users the tool does not care about motion quality.
   Violation: `transition-timing-function: linear`, `ease`, or `ease-in-out` on any interactive animation.
   Exception: opacity-only fades may use `ease` as a fallback for performance-constrained contexts.

6. **Do not introduce additional chromatic colors into the UI chrome.**
   The palette is strictly achromatic (black/white/gray) plus the single blue accent. This discipline creates the tool's clean, professional appearance.
   Status colors (`#ff3b30` red, `#30d158` green, `#ff9f0a` amber) are permitted only for their semantic purpose (errors, success, warnings).
   Violation: purple, teal, magenta, warm orange, pink, or any non-blue hue used decoratively in backgrounds, borders, or text styling.

7. **Do not use invisible shadows on dark surfaces.**
   On dark backgrounds, shadows need sufficient opacity (0.3+) to register visually. Light-colored shadows or low-opacity black shadows are effectively invisible.
   Violation: `box-shadow` with `rgba(0,0,0,0.05)`, `rgba(0,0,0,0.08)`, or any opacity below 0.2 on dark surfaces.
   Correct: use `rgba(0,0,0,0.3)` minimum for level-1 shadows, scaling to `rgba(0,0,0,0.5)` for modal-level elevation.

8. **Do not use positive letter-spacing on display text.**
   Inter at large sizes always runs tight. Positive or zero tracking at 24px+ makes headlines look loose and amateurish.
   Violation: `letter-spacing: 0`, `0.5px`, `1px`, or any positive value on any text 24px or larger.
   Exception: the `micro` label tier (11px) uses `+0.2px` for legibility at tiny sizes.

9. **Do not skip hover/focus states on interactive elements.**
   Every clickable element must signal interactivity through visual feedback. This is especially critical for a tool brand that sells interaction design.
   Buttons need hover color shifts and focus rings. Links need hover color transitions. Cards need border-opacity shifts.
   Violation: interactive elements with no `:hover` or `:focus-visible` styling, or elements that change cursor but show no visual transition.

10. **Do not use `border-radius: 0` on buttons, cards, or input fields.**
    The Framer aesthetic uses functional rounding at every tier: 4px for tags, 6px for buttons/inputs, 8px for cards, 12px for panels, 16px+ for hero containers.
    Sharp 90-degree corners feel foreign to the tool identity and suggest unfinished design.
    Violation: `border-radius: 0` or `2px` on any button, card, or input element.

## Critical Violations (5 items)

1. **Light-mode page background instead of Canvas Black (`#0a0a0a`).**
   The dark canvas IS Framer's identity as a creative workspace. Rendering a Framer-branded page on white or light gray fundamentally misrepresents the product.
   The entire visual system -- transparent borders, blue glow, panel elevation, glassmorphic navigation -- is engineered for dark surfaces and collapses completely on light backgrounds. Semi-transparent white borders become invisible on white. Blue glow becomes garish on white. The depth model inverts.
   This is not a theme preference; it is a structural dependency.

2. **Framer Blue (`#0099ff`) used as decorative surface fill.**
   The accent's power comes from scarcity. When blue floods backgrounds, card fills, or section tints, it stops signaling "interactive" and becomes visual noise.
   The achromatic canvas with surgical blue highlights is the brand's visual signature -- the design equivalent of a surgeon's precise instrument in a sterile environment. Spreading blue everywhere is like flooding an operating room with colored lights.

3. **Static, lifeless transitions (linear timing or no animation).**
   Framer sells motion. Its own interface using `transition: linear` or having no hover/enter animations is equivalent to a car company's website showing broken images of their cars.
   Spring-physics easing (`cubic-bezier(0.2, 0.9, 0.3, 1.0)`) is mandatory on all meaningful interactions. The spring overshoot is the physical signature of the brand -- it says "we understand real motion physics, not just fade-in/fade-out."

4. **Serif or decorative fonts replacing Inter.**
   The mono-family Inter system communicates "modern creative tool." Introducing Georgia, Playfair, or any serif/display font transforms the identity from tool to editorial -- wrong genre entirely.
   Inter at four weights (400, 500, 600, 700) provides all the hierarchy needed. The uniformity is the point: one tool, one typeface, total focus on the work.

5. **Solid opaque borders or missing glassmorphic treatment on navigation.**
   The semi-transparent, blur-backed navigation and toolbars create the "floating tool palette above infinite canvas" experience. This is how professional creative tools present themselves -- tools that hover above your work, ready to assist without dominating.
   Replacing them with solid opaque backgrounds (`#141414` without blur, without transparency) destroys the depth illusion and makes the interface feel like a generic dark-mode website rather than a design studio.
