# Meta -- Design Guardrails

## Do's (10 items)

1. **Use `#ffffff` white cards on `#f0f2f5` gray page fill as the primary layout pattern.**
   This card-on-gray architecture is the visual foundation of every Meta product --
   Facebook feed, Messenger panels, Instagram web. The gray fill creates separation
   between cards without needing heavy borders.
   Verify: feed-style layouts use `#f0f2f5` as `body` or `main` background, with
   white `#ffffff` cards floating above it.

2. **Use Meta Blue (`#0064e0`) exclusively for primary CTAs, text links, and active navigation states.**
   This is the only primary brand color. Its power comes from restraint -- on a mostly
   white-and-gray canvas, every blue element becomes a focal point.
   Verify: `#0064e0` appears only on clickable elements (buttons, links, active tabs),
   never as a background fill or decorative surface.

3. **Use 15px as the base font size for product UI contexts.**
   Facebook's actual base size is 15px, not 16px. This deliberate choice increases content
   density in feed layouts and is core to the Meta reading experience.
   Verify: standard body text, post content, and button labels render at `font-size: 15px`.
   Marketing/landing pages may use 16-17px body, but feed and social contexts must be 15px.

4. **Apply three-state interaction feedback on all interactive surfaces.**
   Default background, hover (`#f2f3f5`), active (`#e4e6eb`). Every clickable non-blue
   surface -- nav items, action bar buttons, list rows, dropdown options -- must transition
   through these three grays. This tactile feedback loop is what makes Meta interfaces
   feel responsive.
   Verify: hovering any interactive element produces a visible background-color change;
   pressing produces a darker change.

5. **Use `border-radius: 9999px` (pill) for search bars, chip filters, reaction pills, and tokens.**
   The pill shape is Meta's interaction signature. Combined with 8px radius for structural
   containers, this two-radius vocabulary creates the visual grammar.
   Verify: search inputs, tag chips, and status badges use `9999px` radius; cards, dialogs,
   and panels use `8px`.

6. **Set body line-height to 1.34 for feed and product UI contexts.**
   Meta uses tighter-than-standard line-height to maximize content density in the feed.
   This is deliberate, not neglectful.
   Verify: post body text, comments, and standard UI text use `line-height: 1.34`
   (not 1.5 or 1.6). Marketing long-form content may use 1.50.

7. **Apply real elevation shadows to cards on gray backgrounds.**
   Cards on `#f0f2f5` need `box-shadow: 0px 1px 2px rgba(0,0,0,0.10)` to separate from
   the page. Popovers stack shadows for deeper elevation. The shadow communicates z-layer.
   Verify: every white card sitting on a gray surface has a visible shadow; shadow intensity
   increases with z-index (card < popover < modal).

8. **Use Optimistic Display at weight 700 for display and section headlines (32px+).**
   Optimistic Display is the marketing/hero typeface. All headlines 32px and above should
   use the Display optical size at bold weight. Below 32px, switch to Optimistic Text at
   weight 600.
   Verify: no headline below 32px uses Optimistic Display; no headline 32px+ uses
   Optimistic Text.

9. **Render user names in feed at 15px weight 600 with `#050505` color.**
   The user-name-bold / timestamp-muted pairing is the DNA of Meta's social surfaces.
   Names at same size as body text but heavier weight, timestamps at 13px weight 400
   in `#65676b`.
   Verify: post author names are weight 600, never weight 400 or 700; timestamps are
   always 13px `#65676b`.

10. **Use the Facebook notification red (`#e41e3f`) only for notifications, errors, and destructive actions.**
    Red is a high-urgency signal in Meta's system. It appears on notification count badges,
    error states, and delete/remove actions. Using it elsewhere dilutes the signal.
    Verify: `#e41e3f` or similar reds appear only on notification badges, inline error
    messages, and destructive-action buttons -- never as decorative accents.

## Don'ts (10 items)

1. **Do not use a pure white page background for feed-style layouts.**
   The `#f0f2f5` gray fill is not optional decor -- it is the negative space that gives
   cards their visual separation. A white page with white cards creates an undifferentiated
   blob.
   Violation: `body` or `main` background set to `#ffffff` when the layout contains
   multiple floating cards.

2. **Do not flood surfaces with Meta Blue.**
   A blue header, blue sidebar, or blue card background destroys the signal-to-noise ratio
   that makes the accent meaningful. Meta uses blue at roughly 5% of screen area.
   Violation: any surface larger than a button or badge rendered in `#0064e0` or any blue
   variant.

3. **Do not increase feed body text to 16px or loosen line-height to 1.5+ in product UI.**
   This is the most common error when rebuilding Meta-style interfaces. Larger/looser text
   breaks the content density that defines the Meta reading experience.
   Violation: feed post text, comments, or card body text at `font-size: 16px` or
   `line-height: 1.5+` in product (non-marketing) contexts.

4. **Do not use serif fonts anywhere in the Meta design system.**
   Meta's typography is exclusively sans-serif (Optimistic, system-ui, Helvetica). Serifs
   are fundamentally incompatible with Meta's optimistic, forward-looking identity.
   Violation: any `font-family` declaration including Georgia, Times New Roman, or
   any serif face.

5. **Do not use `border-radius: 0` or sharp corners on cards, buttons, or interactive elements.**
   Meta's visual language is rounded and approachable. Zero-radius corners create an
   enterprise/brutalist feel that contradicts the social warmth.
   Violation: `border-radius: 0`, `2px`, or any radius below 4px on a card, button,
   or input.

6. **Do not omit hover and active states on interactive surfaces.**
   A Meta surface without state transitions feels broken. The three-state gray gradient
   (default -> `#f2f3f5` -> `#e4e6eb`) is the minimum for any clickable element.
   Violation: an interactive element that shows no visible change on hover or press.

7. **Do not use heavy or decorative shadows.**
   Meta's shadow system is utilitarian -- it communicates z-index, not decoration. Only
   `rgba(0,0,0,0.10)` at small offsets for standard cards, stacked shadows for elevated
   elements.
   Violation: any shadow with blur > 28px, opacity > 0.15, or visible color tint
   (colored shadows).

8. **Do not use pure black (`#000000`) for text or backgrounds.**
   Meta uses `#050505` for primary text and `#18191a` for dark mode backgrounds -- both
   are slightly softer than pure black. The difference is subtle but measurable in
   readability.
   Violation: `color: #000000` or `background: #000000` anywhere in the UI.

9. **Do not place card borders and card shadows together redundantly.**
   On `#f0f2f5` backgrounds, cards use shadows for separation -- no border needed. On
   `#ffffff` backgrounds, cards use borders for separation -- shadow optional. Doubling
   both creates visual noise.
   Violation: a card with both `border: 1px solid #dadde1` and `box-shadow` when a
   simpler treatment would suffice.

10. **Do not use the three-column feed layout below 992px viewport.**
    The sacred three-column layout (280px nav + 680px feed + 280px sidebar) requires
    1200px+ viewport. Below 992px, the sidebars collapse. The feed column width is fixed
    at ~680px, never stretched.
    Violation: squishing three columns into a narrow viewport, or making the feed column
    fluid/stretchy beyond its 680px constraint.

## Critical Violations (5 items)

1. **White cards on a white background in feed layouts.**
   This single error collapses Meta's entire depth system. Without the `#f0f2f5` gray fill
   creating negative space between cards, the interface becomes an undifferentiated white
   wall. The card-on-gray pattern IS the visual architecture -- removing it removes the
   structure that makes Meta interfaces scannable.

2. **Meta Blue used as a background fill or dominant surface color.**
   Painting headers, sidebars, or card backgrounds in `#0064e0` turns Meta's restrained
   brand language into garish saturation. The power of Meta Blue comes from its scarcity
   on a neutral canvas. Flooding the screen with it is the visual equivalent of SHOUTING
   EVERY WORD. Blue at greater than 10% of screen area is a violation.

3. **Body text at 16px with 1.5+ line-height in feed contexts.**
   This seems harmless but fundamentally changes the content density that defines Meta's
   information architecture. Users see fewer posts per viewport, timestamps and metadata
   feel disproportionately large, and the layout reads as a blog rather than a social feed.
   The 15px/1.34 pairing is load-bearing -- it is the typographic density that enables
   the feed experience.

4. **Missing interactive state transitions on clickable elements.**
   A Meta interface without hover and active state changes on buttons, nav items, and list
   rows feels dead. The three-state gray progression (default -> hover `#f2f3f5` -> active
   `#e4e6eb`) is what creates the sense of a living, responsive surface. Without it, users
   get no feedback that the interface is listening to their input.

5. **Serif typography anywhere in the design.**
   Optimistic is a sans-serif family designed specifically for Meta's brand identity.
   Introducing serif fonts -- even as a "design choice" for headings -- immediately breaks
   the optimistic, modern, social-platform identity and makes it look like a news publisher
   or fintech product. There is no context within Meta's design system where serif text
   is appropriate.
