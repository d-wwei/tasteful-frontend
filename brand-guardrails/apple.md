# Apple -- Design Guardrails

## Do's (10 items)

1. **Use SF Pro Display at 20px+ and SF Pro Text below 20px.** Respect the optical sizing boundary -- the font changes its DNA based on size context. Verify: no SF Pro Display below 20px, no SF Pro Text at 20px or above.

2. **Apply negative letter-spacing at ALL text sizes.** The scale: -0.28px at 56px, -0.374px at 17px, -0.224px at 14px, -0.12px at 12px, -0.08px at 10px. Verify: every text element has negative `letter-spacing` appropriate to its size.

3. **Use Apple Blue (`#0071e3`) ONLY for interactive elements.** Buttons, links, focus rings. It is the singular chromatic accent. Verify: `#0071e3`, `#0066cc`, and `#2997ff` appear only on clickable/focusable elements.

4. **Alternate between black (`#000000`) and light gray (`#f5f5f7`) section backgrounds.** This creates cinematic pacing. Verify: product pages contain alternating dark/light sections, each near full-viewport height.

5. **Use 980px pill radius for "Learn more" and "Shop" CTA links.** This signature capsule shape is immediately recognizable as Apple. Verify: text CTA links that stand alone use `border-radius: 980px`.

6. **Keep product imagery on solid-color fields.** No gradients, textures, or busy backgrounds behind products. Verify: hero product photography sits on `#000000` or `#f5f5f7` with no competing visual elements.

7. **Apply the translucent glass effect for sticky navigation.** `background: rgba(0,0,0,0.8)` + `backdrop-filter: saturate(180%) blur(20px)`. Verify: the nav bar uses this exact combination, never an opaque background.

8. **Compress headline line-heights to 1.07-1.14.** Apple headlines are famously tight. Verify: display headlines (56px) use `line-height: 1.07`, section headings (40px) use `1.10`.

9. **Use `#1d1d1f` (near-black, not `#000000`) for text on light backgrounds.** Slightly warmer for comfortable reading. Verify: body and heading text on light sections uses `#1d1d1f`.

10. **Use `#2997ff` (Bright Blue) for links on dark backgrounds instead of `#0066cc`.** Higher luminance ensures contrast. Verify: links on black sections use `#2997ff`, links on light sections use `#0066cc`.

## Don'ts (10 items)

1. **Do not introduce additional accent colors.** The entire chromatic budget is one blue. Violation: any hue other than blue (`#0071e3` / `#0066cc` / `#2997ff`) used on interactive elements.

2. **Do not use heavy shadows or multiple shadow layers.** Apple's system is one soft diffused shadow or nothing. Violation: multiple `box-shadow` layers, or any shadow with blur < 20px paired with opacity > 0.15.

3. **Do not use visible borders on cards or containers.** Apple almost never uses borders. Violation: `border: 1px solid` on cards, product tiles, or content sections.

4. **Do not apply wide letter-spacing to SF Pro.** The font is designed to run tight at every size. Violation: `letter-spacing` > 0.3px on any SF Pro text (except small tile headings which use 0.196-0.231px as designed).

5. **Do not use weight 800 or 900.** Maximum is 700 (bold), and even that is rare. Violation: `font-weight: 800`, `900`, or `bold` used prominently.

6. **Do not add textures, patterns, or gradients to backgrounds.** Solid colors only for all surfaces. Violation: gradient or pattern backgrounds on any section or container.

7. **Do not make the navigation opaque.** The glass blur effect is essential. Violation: `background: #000000` or `background: rgba(0,0,0,1)` on the sticky navigation bar.

8. **Do not center-align body text.** Apple body copy is left-aligned; only headlines center. Violation: `text-align: center` on paragraph or body text blocks.

9. **Do not use rounded corners larger than 12px on rectangular elements.** 980px is for pill links only. Violation: `border-radius: 20px` or `border-radius: 32px` on standard rectangular cards or containers.

10. **Do not use `#ffffff` as a page section background.** Light sections use `#f5f5f7`, which has a blue-gray tint that prevents sterility. Violation: `background: #ffffff` on a major page section.

## Critical Violations (5 items)

1. **Additional accent colors beyond Apple Blue.** Every interactive element in the system uses blue. Adding orange, green, or purple for different buttons destroys the monochromatic discipline that makes Apple Blue so powerful.

2. **Opaque navigation bar.** The translucent `rgba(0,0,0,0.8)` + `backdrop-filter: saturate(180%) blur(20px)` glass effect is the most recognizable depth element on Apple's website. An opaque nav feels heavy and removes the floating quality.

3. **Products on busy backgrounds.** Apple treats products as sculptures in a gallery. Placing them on gradients, textures, or lifestyle photos undermines the "reverence for the object" philosophy that defines Apple's visual identity.

4. **Positive letter-spacing on SF Pro text.** SF Pro is engineered for negative tracking at every size. Positive spacing makes it look wrong at a fundamental level -- like wearing the font incorrectly.

5. **Light-mode section where dark is needed (and vice versa).** The alternating black/`#f5f5f7` rhythm creates cinematic pacing. Using all-light or all-dark destroys the "scenes in a film" quality of Apple product pages.
