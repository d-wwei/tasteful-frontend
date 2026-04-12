# Zapier -- Design Guardrails

## Do's (10 items)

1. **Use Bridal Heath (`#fffdf9`) as the primary page background.**
   This warm near-white with a peach undertone is the emotional foundation of Zapier's visual identity.
   Automation should feel warm and inviting, not sterile or clinical. The peach warmth communicates
   "friendly tool" before a single word is read, differentiating Zapier from cold SaaS dashboards.
   Verify: page `background-color` must be `#fffdf9`, never cold `#ffffff` or any blue-tinted white.

2. **Use Degular at weight 600-700 for all headlines.**
   Degular is Zapier's custom brand typeface by Oh No Type Co, self-hosted at fonts.zapier.com.
   Display headings use weight 700 for maximum presence with -0.02em letter-spacing. Section
   headings use weight 600. This rounded, confident sans-serif carries the brand's friendly
   authority -- punchy enough for marketing, approachable enough for product UI.
   Verify: every heading element renders Degular, not Inter or system fonts. No weight below 600.

3. **Use Zap Orange (`#ff4f00`) exclusively for primary CTAs, active states, and link text.**
   This International Orange (NASA heritage) is the single highest-energy color in the system.
   It signals "action" and "connection" -- the core Zapier promise. Its power comes from scarcity:
   appearing only at moments where the user should act or where automation is alive and running.
   Verify: `#ff4f00` appears only on buttons, links, active step indicators, and connection pulses.
   Never as a section background, decorative fill, or large-area surface color.

4. **Keep every neutral warm-toned with a brown/peach undertone.**
   The grays are `#594a42` (Warm Brown), `#8c7b72` (Taupe), `#a3927f` (Khaki) -- never blue-gray
   or cool-gray variants. This warm neutral family is what makes the orange feel at home rather
   than pasted on. Even borders (`#f0e6d8`) and subtle backgrounds (`#fff3e6`) carry warmth.
   Verify: no color in the neutral range has a blue, green, or cool undertone. Hue channel
   should fall in the 15-35 degree range (orange-brown family).

5. **Use Serenade (`#fff3e6`) for secondary surfaces and icon backgrounds.**
   This warm cream with orange glow creates the layering system. Cards float on the Bridal Heath
   canvas in white (`#ffffff`). Icon containers and tag backgrounds sit on Serenade. Interactive
   surfaces use Light Peach (`#ffecd2`). Each layer steps warmer, creating depth through warmth.
   Verify: secondary containers, tag backgrounds, and icon areas use `#fff3e6`, not `#f5f5f5`.

6. **Apply the warm shadow system based on `rgba(32,21,21,...)`.**
   Every shadow in the system uses Zapier Earth (`#201515`) as the shadow color base, tinting
   shadows warm to match the cream canvas. Level 1 (cards): 0.06 opacity. Level 2 (hover): 0.08.
   Level 3 (modals): 0.12. The orange glow shadow (`rgba(255,79,0,0.15)`) is reserved for
   active automation states and featured CTAs.
   Verify: no shadow uses `rgba(0,0,0,...)` -- all use `rgba(32,21,21,...)` at appropriate opacities.

7. **Maintain the Degular/Inter typographic hierarchy strictly.**
   Degular carries authority and brand presence for headlines -- Display through Card Title level.
   Inter carries clarity and utility for all functional text: buttons, labels, nav links, body
   paragraphs, captions, and overline text. The split is clean and absolute. Mixing them
   erodes the visual hierarchy that guides the user's eye from headline to action.
   Verify: no headline uses Inter; no button, label, nav link, or body text uses Degular.

8. **Set body text line-height to 1.55.**
   Zapier's friendly, approachable personality extends to generous text spacing. Body text
   breathes with room. This spacing communicates "easy" and "low friction" -- core to the
   automation promise. Headings use 1.10-1.30 for tight, punchy presence. Captions use 1.43.
   Verify: body paragraphs have `line-height: 1.55` or equivalent.

9. **Use the workflow visual language for any sequential content.**
   Zapier's signature UI pattern is the step-by-step Zap flow: numbered circles (Zap Orange
   background, white text) connected by dashed lines (`2px dashed #e0d1c2`). Active steps
   pulse in Zap Orange; completed steps show Java Teal (`#13d0ab`) with a soft glow ring;
   inactive steps use muted `#e0d1c2`. This is the brand's strongest visual differentiator.
   Verify: any multi-step process uses the step-connector pattern, not generic numbered lists.

10. **Apply border-radius 8px for standard elements, 12px for cards, 16px for featured containers.**
    Zapier's geometry is consistently rounded and approachable. The radius hierarchy:
    - 6px: badges, tags, small compact elements
    - 8px: buttons, inputs, small cards
    - 12px: content cards, icon backgrounds, dropdown menus
    - 16px: Zap Builder panels, hero containers, modal dialogs
    - 24px: marketing hero sections, featured landing page containers
    - 9999px (pill): status badges, toggle switches, app icon containers
    Verify: no interactive element has radius below 6px; no card has radius below 8px.

## Don'ts (10 items)

1. **Do not use cold white (`#ffffff`) as a page background.**
   The warm Bridal Heath (`#fffdf9`) canvas is core identity. Pure white makes Zapier look
   like every other SaaS product -- indistinguishable from a Tailwind default. Use `#ffffff`
   only for cards, inputs, and modals that need to float above the warm canvas.
   Violation: `background-color: #ffffff` or `white` on `<body>` or main page wrapper.

2. **Do not use cool blue-grays anywhere in the neutral palette.**
   Every gray must carry a brown/peach undertone. Cool neutrals destroy the warm ecosystem
   that makes Zap Orange feel intentional rather than arbitrary. A single `#6b7280` border
   or `#94a3b8` text color breaks the warmth of the entire page.
   Violation: any color with a blue or violet hue (e.g., `#6b7280`, `#94a3b8`, `#64748b`,
   `#71717a`, `#9ca3af`) in backgrounds, text, or borders.

3. **Do not apply Zap Orange as a decorative surface fill or section background.**
   The orange's power comes from signal scarcity. Flooding the page with `#ff4f00` backgrounds
   destroys the signal-to-noise ratio that makes CTAs and active states pop. When orange is
   everywhere, it guides nowhere -- the eye has no focal point.
   Violation: any container, section, or card with `background-color: #ff4f00`. Exception:
   small badges (<40px), step number circles, and button surfaces.

4. **Do not use sharp corners (< 6px radius) on buttons, cards, or containers.**
   Zapier's identity is rounded and friendly. Sharp corners create an aggressive, technical
   feeling that contradicts the "automation is easy" brand promise. Even input fields and
   small interactive elements should have soft corners.
   Violation: `border-radius: 0`, `2px`, or `4px` on any interactive element or card.

5. **Do not use Inter for headlines or Degular for UI text.**
   The typographic split is the brand's voice architecture. Inter headlines look generic and
   lose the confident personality that Degular brings. Degular on buttons looks overstylized
   and reduces readability at small sizes. The separation is what creates visual rhythm.
   Violation: any `<h1>` through `<h6>` rendering in Inter; any button, label, or nav element
   rendering in Degular.

6. **Do not use heavy drop shadows or material-design-style elevation.**
   Zapier's depth comes from warm-tinted shadows at low opacity (0.04-0.12), not dramatic
   floating effects. Heavy shadows feel corporate and rigid -- the opposite of Zapier's
   friendly, lightweight personality. The design should feel grounded and approachable.
   Violation: `box-shadow` with blur > 24px at opacity > 0.12, or any shadow stack that
   creates a prominent floating effect.

7. **Do not use Zapier Earth (`#201515`) as text color for body passages.**
   Reserve the darkest brand color for headlines and short labels where its intensity is
   appropriate. Body text uses Warm Brown (`#594a42`) for comfortable sustained reading on
   the cream canvas. The contrast of `#201515` on `#fffdf9` is too harsh for paragraphs.
   Violation: paragraphs of 3+ lines set in `#201515`.

8. **Do not use status colors (Teal, Blue, Gold, Red) as decorative accents.**
   These carry functional meaning in the automation context: Java Teal (`#13d0ab`) means
   connected/active; Picton Blue (`#499df3`) means info/pending; Sunglow (`#ffc43e`) means
   warning/attention; Warm Red (`#d4351c`) means error/disconnected. Using them decoratively
   erodes their signal value and confuses users reading automation status.
   Violation: `#13d0ab`, `#499df3`, `#ffc43e`, or `#d4351c` on non-functional elements.

9. **Do not reduce body line-height below 1.40.**
   The generous spacing supports Zapier's friendly, low-friction personality. Tight text
   feels like effort, which contradicts the "automation makes life easy" message. Even
   compact UI contexts (dashboards, tables) should maintain at least 1.40.
   Violation: `line-height` of 1.2 or 1.3 on any paragraph or body text element.

10. **Do not mix rounded and sharp border-radius within the same component.**
    Consistency in corner rounding is essential for the approachable feel. A card with 12px
    corners containing buttons with 2px radius creates visual dissonance -- the brain reads
    it as two different design systems fighting. Internal elements should use the same or
    smaller (but still rounded) radius as their container.
    Violation: mixing radius values that differ by more than 8px within a single component.

## Critical Violations (5 items)

1. **Cold white page background instead of Bridal Heath (`#fffdf9`).**
   The warm cream canvas IS Zapier. It communicates "friendly automation" before a single
   word is read. A cold white background makes the page indistinguishable from every generic
   SaaS landing page. This single color change collapses the entire brand atmosphere into
   commodity territory. Every warm neutral, every shadow tint, every orange accent was
   designed to harmonize with this canvas -- change it and the whole system breaks.

2. **Cool blue-gray neutrals anywhere in the palette.**
   Zapier's warmth depends on every neutral carrying a brown/peach undertone. A single
   cool-gray text color or border instantly breaks the warm spell and makes the design
   feel like a Tailwind default with orange buttons pasted on. The warm neutrals are not
   aesthetic preference -- they are the structural foundation that makes Zap Orange feel
   native rather than foreign. Fix by replacing with nearest warm equivalent from the palette.

3. **Zap Orange (`#ff4f00`) used as a large surface fill.**
   The orange is a signal flare -- bright, energetic, scarce. Applying it as a section
   background, full-width banner, or large card fill destroys its meaning and overwhelms
   the user visually. The user's eye should snap to Zap Orange because it appears in
   focused, intentional moments: CTAs, active indicators, connection pulses. When it covers
   large areas, it guides nowhere and creates visual fatigue.

4. **Inter headlines replacing Degular.**
   Degular is the first thing that distinguishes Zapier's visual voice from a generic SaaS
   product. Its rounded, confident letterforms carry brand personality that Inter cannot
   replicate. Removing Degular makes the page anonymous -- interchangeable with any other
   product using Inter + colored buttons. This is the typographic equivalent of removing
   the logo. If Degular is unavailable, fall back to system-ui, never to Inter.

5. **Automation visual language absent from sequential content.**
   Any multi-step process, workflow, or feature breakdown should use Zapier's signature
   step-connector pattern: numbered circles in Zap Orange, dashed connection lines, status
   color indicators (Teal for active, orange pulse for running, gray for inactive). Rendering
   these as plain ordered lists or generic cards wastes Zapier's strongest UI differentiator --
   the visual language of automation itself. This pattern is what makes Zapier screenshots
   instantly recognizable.
