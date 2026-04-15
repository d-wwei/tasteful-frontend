# Domain Pattern Library

Maps product domains to aesthetic strategies + content design strategies. Loaded in Phase 0 (domain identification), Phase 2 (style tile generation), and Phase 4 (content design layer).

**Why this exists**: In A/B blind tests, Skill lost 4/5 against vanilla AI because aesthetic patterns were extracted from tech brands and misfired on games, cultural brands, blogs, and dev tools. Vanilla AI freely adapts green accents for dev tools, gold+dark for games, and Japanese characters for tea brands. This file provides the domain-specific knowledge Skill was missing.

---

## How to Use

1. **Phase 0 (Anchor)**: Read the brief. Match product description against trigger keywords below. Set `domain` in brief.yaml.
2. **Phase 2 (Search)**: Load this file. Use the domain's recommended aesthetic patterns AND content design strategy to generate style tiles with domain-appropriate character.
3. **Phase 4 (Compose)**: Apply the domain's content design elements. These are the decorative, atmospheric, and cultural elements that make pages feel alive -- the layer above tokens.

If a project spans multiple domains (e.g., a SaaS product for the gaming industry), pick the domain that best matches the **end user's expectation**, not the product category.

---

## Domain 1: SaaS / Productivity Tool

**Trigger keywords**: "SaaS", "dashboard", "productivity", "workflow", "project management", "CRM", "analytics", "B2B", "enterprise", "platform"

**Aesthetic pattern recommendations**:
- Chromatic Restraint (Pattern 8) -- ONE accent color, clean UI chrome
- Shadow as Architecture (Pattern 5) -- structured card elevation for dashboard panels
- Compression as Identity (Pattern 3, gentle) -- professional density in headlines
- Depth Hierarchy (Pattern 9) -- clear layering for panels, modals, sidebars

**Content design strategy**:
- **Product visualization**: Dashboard mockups, data visualizations, metric cards with realistic numbers
- **Social proof elements**: Customer logos, usage statistics, team avatars
- **Feature demonstration**: Before/after comparisons, workflow diagrams, integration icons
- **Atmosphere**: Clean, organized, trustworthy. Whitespace signals control. Subtle background patterns (dot grids, faint lines) suggest precision without clutter
- **Typography mood**: Professional but not boring. Medium-weight sans-serif headlines. Tabular figures in data contexts

**Domain anti-patterns**:
- Do NOT use Warmth as Humanity -- parchment tones feel off-brand for productivity tools
- Do NOT use playful or decorative typography -- users expect efficiency, not personality
- Do NOT use extreme compression -- readability matters more than visual density in tools people use daily
- Avoid dark mode as the default surface unless the product is developer-facing

**Tone shift from generic**: The difference between a generic SaaS page and a good one is realistic product UI in the hero, not abstract gradient shapes.

---

## Domain 2: Developer Tool / CLI / Infrastructure

**Trigger keywords**: "developer", "CLI", "API", "SDK", "infrastructure", "deployment", "CI/CD", "devops", "code", "terminal", "open source", "framework", "compiler", "runtime"

**Aesthetic pattern recommendations**:
- Darkness as Canvas (Pattern 2) -- developers expect dark surfaces
- Compression as Identity (Pattern 3, standard to maximum) -- engineering precision
- The Signature Weight (Pattern 10) at 500-600 -- confident, technical headings
- Ring as Border (Pattern 6, dark variant) -- translucent containment on dark backgrounds

**Content design strategy**:
- **Code snippets**: Real syntax-highlighted code blocks in the hero and feature sections. Use the product's actual syntax. Monospace font (JetBrains Mono, Fira Code, or IBM Plex Mono) for code, proportional for prose
- **Terminal/CLI mockups**: Simulated terminal windows with actual commands. Green/cyan text on dark backgrounds for output. Cursor blink animations
- **API response previews**: JSON/YAML output blocks showing real response structures
- **Status indicators**: Green dots for "passing", deployment status bars, latency metrics
- **Atmosphere**: The page should feel like an extension of the developer's IDE. Dark surfaces, monospace accents, syntax-colored highlights. Background: subtle code watermark or grid pattern
- **Accent color strategy**: Green (CI passing, success), blue-violet (brand distinction from GitHub's blue), or orange/amber (warmth in a technical context, like Rust/Cloudflare)

**Domain anti-patterns**:
- Do NOT use Lightness as Luxury -- weight 300 headlines feel insubstantial for infrastructure products
- Do NOT use serif typography -- developers read monospace and sans-serif; serifs signal "editorial", not "technical"
- Do NOT use warm cream backgrounds -- parchment is for literary products, not engineering
- Do NOT use purple-to-blue gradient CTAs -- this is the most overused pattern in developer marketing

**Tone shift from generic**: A developer tool page without code snippets is like a restaurant menu without food photos. The code IS the hero content.

---

## Domain 3: E-commerce / Consumer Brand

**Trigger keywords**: "e-commerce", "shop", "store", "brand", "retail", "fashion", "product", "marketplace", "DTC", "direct to consumer", "consumer"

**Aesthetic pattern recommendations**:
- Lightness as Luxury (Pattern 1) -- premium feel through weight restraint
- Shadow as Architecture (Pattern 5) -- product cards need structured depth
- Chromatic Restraint (Pattern 8) -- brand color discipline
- Polish Pass (Pattern 11) -- e-commerce demands pixel-perfect interaction states

**Content design strategy**:
- **Product photography placeholders**: Large, high-quality product image zones. Specify aspect ratios (1:1 for grid, 16:9 for hero, 4:5 for mobile). Use gradient placeholder colors that match the product category
- **Price typography**: Prominent pricing with currency symbols, strikethrough for sales, size hierarchy (price > product name > description)
- **Trust signals**: Shipping badges, return policy icons, payment method logos, star ratings, review counts
- **Category navigation**: Visual category cards with lifestyle imagery, not just text links
- **Atmosphere**: Aspirational but accessible. Photography-driven layouts. Generous product image spacing. Subtle hover zoom on product cards
- **CTA strategy**: "Add to Cart" must be the most prominent element on product pages. Use the brand's strongest accent color exclusively for purchase actions

**Domain anti-patterns**:
- Do NOT use Darkness as Canvas as the primary surface -- e-commerce needs bright, honest product presentation
- Do NOT use Compression as Identity at extreme levels -- product names need legibility
- Do NOT use monospace typography -- it signals "developer", not "consumer"
- Avoid information-dense layouts -- e-commerce is about desire, not data

**Tone shift from generic**: Product images carry 80% of the visual weight. Token design supports the photography, not the other way around.

---

## Domain 4: Game / Interactive Entertainment

**Trigger keywords**: "game", "gaming", "interactive", "play", "score", "level", "arcade", "puzzle", "RPG", "typing game", "leaderboard", "tournament", "esports"

**Aesthetic pattern recommendations**:
- Amplify Impact (Pattern 13) -- games demand visual drama and energy
- Darkness as Canvas (Pattern 2) -- dark backgrounds are native to gaming interfaces
- The Signature Weight (Pattern 10) at 700-900 -- bold, high-energy headings
- Depth Hierarchy (Pattern 9, dark surface model) -- layered UI for game chrome

**Content design strategy**:
- **Dynamic color palette**: Vibrant, saturated accent colors. Gold/amber for achievements and scores. Neon-adjacent highlights for interactive elements. Dark background with bright foreground creates focus
- **Scoreboard/stats typography**: Large, bold numerals. Tabular figures. Monospace or display fonts for scores. Animated number transitions
- **Game state visualization**: Progress bars, XP meters, rank badges, streak counters. These ARE the decoration -- game UI is inherently decorative
- **Particle/glow effects**: Subtle glow on active elements. Spark effects on achievements. Gradient overlays on hero sections (but NOT purple-to-blue)
- **Atmosphere**: High energy, reward-focused. Dark surfaces with vibrant accents create the "arena" feeling. Sound-design-adjacent visual feedback (bright flash on score, screen shake metaphor through motion)
- **Typography mood**: Display fonts with character -- condensed, extended, or geometric. NOT the same clean sans-serif you'd use for a SaaS dashboard

**Domain anti-patterns**:
- Do NOT use Lightness as Luxury -- weight 300 headlines feel lifeless for games
- Do NOT use Warmth as Humanity -- parchment and terracotta are wrong for gaming energy
- Do NOT use Chromatic Restraint (warm monochrome model) -- games need vibrant color to signal reward and progress
- Do NOT use gentle, editorial spacing -- games benefit from tighter, denser UI chrome
- Avoid "calm" or "minimal" aesthetics -- games should feel exciting even when idle

**Tone shift from generic**: The A/B test loss on the typing game happened because Skill applied its default "composed professional" aesthetic. Games need controlled chaos, not quiet authority.

---

## Domain 5: Event / Promotional / Festival

**Trigger keywords**: "event", "conference", "festival", "promotion", "launch", "countdown", "campaign", "seasonal", "concert", "meetup", "hackathon", "sale"

**Aesthetic pattern recommendations**:
- Amplify Impact (Pattern 13) -- promotional pages live or die by visual drama
- Color Strategy (Pattern 14) -- bold, intentional color with clear hierarchy
- Shadow as Architecture (Pattern 5, Stripe model) -- dramatic depth for pricing cards
- Compression as Identity (Pattern 3, moderate) -- dense headlines with urgency

**Content design strategy**:
- **Countdown/date typography**: Large, dramatic date displays. Countdown timers with animated digits. Event date as a hero-level visual element, not metadata
- **Speaker/lineup grids**: Circular or rounded portrait images. Name + title + talk topic cards. Staggered grid for visual rhythm
- **Pricing tier comparison**: Clear visual hierarchy between tiers. Highlight the recommended tier. Price as the largest text in each card
- **Location/venue**: Map embed placeholder, venue photography, travel info cards
- **Atmosphere**: Urgency + aspiration. Bold colors, large type, clear CTAs. The page should feel like an invitation, not a brochure. Gradient backgrounds (multi-stop, brand-specific) are appropriate here
- **Scarcity signals**: "X seats remaining", early-bird pricing strikethrough, social proof ("500+ attendees registered")

**Domain anti-patterns**:
- Do NOT use subtle, understated aesthetics -- events need to generate excitement
- Do NOT use dark developer-tool aesthetics unless the event IS a developer conference (and even then, add energy)
- Avoid information overload -- promotional pages need one clear CTA per viewport
- Do NOT use multiple competing accent colors -- one bold color for all CTAs

**Tone shift from generic**: Skill won the A/B test on the promotional page. This domain aligns well with structured visual hierarchy. Lean into it: pricing comparison, headline impact, CTA guidance.

---

## Domain 6: Editorial / Blog / Personal Site

**Trigger keywords**: "blog", "editorial", "magazine", "journal", "personal", "portfolio", "writing", "essay", "newsletter", "author", "publication"

**Aesthetic pattern recommendations**:
- Warmth as Humanity (Pattern 4) -- literary tone through warm neutrals and serif headlines
- Typography as Brand DNA (Pattern 7) -- the typeface IS the personality
- The Signature Weight (Pattern 10) at 400-500 -- readable, authoritative, not loud
- Chromatic Restraint (Pattern 8, warm monochrome) -- minimal color, maximum typography focus

**Content design strategy**:
- **Reading-first layout**: Single-column content at 65-75 characters per line. Generous line-height (1.6-1.8). No sidebar competing with content. Article title as the dominant visual element
- **Typography as decoration**: Drop caps, pull quotes, typographic dividers (ornamental rules, centered dots, small fleurons). The type itself creates visual rhythm without images
- **Author identity**: Author photo, bio, social links. Personal sites need a human face
- **Minimal navigation**: Top nav with 3-5 items max. No mega-menus. The blog A/B loss happened because Skill over-structured what should have been simple
- **Atmosphere**: Quiet confidence. Whitespace is the primary design element. Reading experience trumps visual spectacle. Subtle background textures (paper grain, light noise) add warmth without distraction
- **Image strategy**: Full-width hero images for feature articles. Modest inline images that don't interrupt reading flow. No decorative imagery -- every image must earn its place

**Domain anti-patterns**:
- Do NOT use Compression as Identity -- compressed tracking fights reading comfort
- Do NOT use Darkness as Canvas as default -- most readers prefer light backgrounds for long-form text
- Do NOT use complex navigation patterns -- blogs are inherently linear
- Do NOT over-structure -- the A/B blog loss came from too many visual layers. Simple hierarchy (title > subtitle > body) is correct here
- Avoid loud accent colors -- editorial sites use muted, tasteful accents (deep blue, wine, forest green)

**Tone shift from generic**: The blog A/B test loss: vanilla AI produced "fewer layers, prominent title, minimal color -- better for reading." That IS the correct answer. The skill's instinct to add structure hurt here.

---

## Domain 7: Cultural / Luxury / Heritage Brand

**Trigger keywords**: "cultural", "heritage", "artisan", "luxury", "traditional", "ceremony", "craft", "museum", "gallery", "haute couture", "boutique", "Japanese", "Chinese", "Korean", "French", "Italian", "wabi-sabi", "zen"

**Aesthetic pattern recommendations**:
- Warmth as Humanity (Pattern 4) -- cultural brands need organic warmth
- Lightness as Luxury (Pattern 1) -- restraint communicates refinement
- Ring as Border (Pattern 6, warm variant) -- gentle containment, not hard edges
- Chromatic Restraint (Pattern 8, warm monochrome) -- natural palette derived from the culture

**Content design strategy**:
- **Native language typography**: Use decorative text in the brand's cultural language. Japanese brands: large kanji/hiragana as hero decoration (e.g., "一期一会", "侘寂", "美"). Chinese brands: calligraphic headers. The A/B test on the tea brand was lost because Skill had no mechanism to introduce Japanese decorative characters
- **Cultural color palette**: Derive colors from the culture, not from tech brands. Japanese: indigo (ai-iro), persimmon (kaki-iro), matcha green, washi white. Chinese: vermillion, gold, jade. French luxury: noir, creme, gold. Italian: terracotta, olive, ivory
- **Material texture references**: Paper grain (washi), fabric weave, stone texture, wood grain -- rendered as subtle CSS backgrounds or described as atmosphere
- **Asymmetric, breathing layouts**: Inspired by the culture's design principles. Japanese: ma (negative space), asymmetric balance. European luxury: centered, symmetrical, gold-ratio proportions
- **Atmosphere**: The page should evoke a physical space (gallery, workshop, garden, salon). Slow motion transitions (400-600ms). Scroll-triggered reveals. Generous whitespace that feels intentional, not empty
- **Product presentation**: Artisan products need large, reverent image spaces. Tight crops. Process shots (hands making, ingredients, tools). The product story is as important as the product image

**Domain anti-patterns**:
- Do NOT use tech-dark-mode aesthetics -- dark-on-dark luminance stepping feels digital, not cultural
- Do NOT use Compression as Identity -- cultural brands need breathing room, not engineering density
- Do NOT use monospace typography -- it signals technology, not craft
- Do NOT use standard SaaS card layouts -- cultural brands need bespoke compositions
- Do NOT ignore the specific culture -- a Japanese tea brand and a French perfume brand require fundamentally different approaches. "Cultural" is not one category

**Tone shift from generic**: The tea brand A/B loss is the defining example. Vanilla AI added "一期一会" and "侘/寂" decorative characters plus product gradient simulation. These cultural details made the page feel authentic. Tokens alone cannot achieve this -- you need content design.

---

## Domain 8: Finance / Fintech

**Trigger keywords**: "finance", "fintech", "banking", "payment", "trading", "investment", "crypto", "wallet", "insurance", "stock", "portfolio"

**Aesthetic pattern recommendations**:
- Lightness as Luxury (Pattern 1) -- authority through restraint, not weight
- Shadow as Architecture (Pattern 5) -- structured card depth for financial data
- Chromatic Restraint (Pattern 8, cool accent) -- trust through color discipline
- Typography as Brand DNA (Pattern 7) -- tabular figures, proper number formatting

**Content design strategy**:
- **Number-first hierarchy**: Financial products live by their numbers. Large, clear account balances. Tabular figures everywhere. Proper currency formatting. Percentage change indicators with directional color (green up, red down)
- **Trust architecture**: Security badges, regulatory compliance logos, encryption indicators. Bank-grade visual weight -- the page must feel like a vault, not a startup
- **Data visualization**: Portfolio charts, performance graphs, transaction history. These are content, not decoration. Clean, well-labeled axes. No gratuitous 3D or animation on charts
- **Transaction flows**: Step indicators, progress bars, confirmation screens. Financial actions need clear, multi-step UX with explicit confirmation
- **Atmosphere**: Quiet authority. Deep navy, charcoal, slate -- not trendy colors. White/light surfaces for data-heavy sections. Dark accents for emphasis. The page communicates "your money is safe here"
- **Typography mood**: Professional serif for headings (trustworthy), clean sans for data (legible). Generous spacing between data rows. Never sacrifice legibility for style in financial interfaces

**Domain anti-patterns**:
- Do NOT use playful or casual aesthetics -- finance users need to trust the interface
- Do NOT use Warmth as Humanity (parchment tones) -- warm surfaces feel informal for finance
- Do NOT use vibrant, saturated accent colors -- they signal "startup", not "bank"
- Do NOT use extreme compression on financial data -- numbers need room to breathe
- Do NOT use dark mode as default for consumer finance -- professional traders want dark, retail customers want light

**Tone shift from generic**: Finance pages that look like SaaS dashboards fail because they lack the visual weight of trust. A bank website should feel heavier than a project management tool.

---

## Domain 9: Health / Wellness / Education

**Trigger keywords**: "health", "wellness", "medical", "fitness", "education", "learning", "course", "school", "university", "therapy", "mindfulness", "nutrition"

**Aesthetic pattern recommendations**:
- Warmth as Humanity (Pattern 4) -- approachable, human-centered
- Chromatic Restraint (Pattern 8) with calming accent -- blue-green, sage, warm coral
- Ring as Border (Pattern 6, warm variant) -- soft containment
- Polish Pass (Pattern 11) -- accessibility is non-negotiable in health/education

**Content design strategy**:
- **Human imagery placeholders**: Diverse, authentic people. Not stock-photo-perfect athletes. Real patients, real students, real practitioners
- **Progress/achievement elements**: Course progress bars, health metrics, milestone badges. Positive reinforcement through visual design
- **Trust signals (medical)**: Provider credentials, certifications, HIPAA compliance badges, clinical evidence citations
- **Accessibility-first**: Larger base font (18px), extra-generous line height (1.8), high contrast defaults. Health and education content must be maximally accessible
- **Atmosphere**: Calm, supportive, non-judgmental. Soft rounded corners. Gentle color transitions. Illustrations preferred over photography in sensitive health contexts. Green and blue tones for calm; warm tones for community
- **Content structure**: Clear information hierarchy. Short paragraphs. Scannable headers. FAQs for common concerns. No information overwhelm

**Domain anti-patterns**:
- Do NOT use Darkness as Canvas -- dark interfaces feel clinical or intimidating in health contexts
- Do NOT use Compression as Identity -- health/education content must breathe
- Do NOT use aggressive CTAs -- "BUY NOW" energy is wrong for health decisions
- Do NOT use cold, technical aesthetics -- even medical tools benefit from warmth
- Avoid small text -- health/education audiences span wide age ranges

**Tone shift from generic**: Health and education pages should feel like a trusted advisor, not a product pitch. Slower pace, warmer tone, more breathing room than any other domain.

---

## Domain 10: Media / Entertainment / Music

**Trigger keywords**: "media", "entertainment", "music", "video", "streaming", "podcast", "radio", "news", "content platform", "social", "creator"

**Aesthetic pattern recommendations**:
- Darkness as Canvas (Pattern 2) -- media consumption native on dark surfaces
- Amplify Impact (Pattern 13) -- content thumbnails need visual punch
- Color Strategy (Pattern 14) -- content-adaptive color (album art, video thumbnails inform the palette)
- Depth Hierarchy (Pattern 9) -- layered UI for player controls, overlays, content grids

**Content design strategy**:
- **Content-forward grids**: Large thumbnails, minimal text overlay. The content IS the visual design. Aspect ratios: 16:9 for video, 1:1 for album art, 2:3 for movie posters
- **Player/control UI**: Persistent player bars, progress sliders, playback controls. These need to feel tactile and responsive. High contrast controls on dark backgrounds
- **Genre/mood coloring**: Dynamic accent colors pulled from content (album art dominant color, show poster palette). The UI adapts to what's playing
- **Creator profiles**: Large avatar/banner, follower count, content grid. Social proof through numbers
- **Atmosphere**: Immersive. The interface should disappear and let content dominate. Blurred backdrop of current content. Smooth transitions between content items. Cinematic feeling
- **Typography**: Clean sans-serif for UI. Bold, condensed for titles/show names. Small, muted metadata

**Domain anti-patterns**:
- Do NOT use bright/white surfaces as the default -- media content looks best on dark
- Do NOT use Warmth as Humanity (parchment) -- media platforms need neutral backgrounds that don't color-shift content
- Do NOT use heavy borders or shadows around content thumbnails -- they compete with the content
- Do NOT use serif typography for UI -- media platforms need fast, scannable navigation
- Avoid information density -- browsing is a leisure activity, not a work task

**Tone shift from generic**: Media platforms succeed when the UI becomes invisible and content fills the viewport. The best design decision is often "show more content, show less chrome."

---

## Cross-Domain Decision Matrix

When the domain is unclear or spans categories, use this matrix to resolve conflicts:

| Signal in Brief | Primary Domain | Secondary Influence |
|----------------|---------------|-------------------|
| "Developer tool for game studios" | Developer Tool | Game (accent color, energy level) |
| "Luxury e-commerce" | E-commerce | Cultural/Luxury (typography, restraint) |
| "Health tech dashboard" | SaaS/Productivity | Health (warmth, accessibility emphasis) |
| "Music education platform" | Education | Media (dark surface option, content grids) |
| "Financial gaming app" | Finance | Game (achievement elements, dynamic color) |
| "Cultural festival website" | Event/Promotional | Cultural (native language, cultural palette) |

**Resolution rule**: The primary domain determines the surface strategy (light vs dark), layout density, and typography mood. The secondary domain contributes content design elements and accent color strategy.

---

## Integration with aesthetic-patterns.md

This file does NOT replace aesthetic-patterns.md. The relationship:

- **aesthetic-patterns.md**: Token-level directives. HOW to implement a visual choice (exact shadow values, weight numbers, letter-spacing formulas).
- **domain-patterns.md**: Domain-level strategy. WHICH visual choices to make and what content elements to add for a given product category.

Phase 2 workflow:
1. Identify domain from brief (this file)
2. Load recommended aesthetic patterns (aesthetic-patterns.md)
3. Apply domain's content design strategy to style tile generation
4. Check domain anti-patterns before finalizing each tile
