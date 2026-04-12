# Spotify -- Agent Prompt Guide

Self-contained reference for generating pixel-perfect Spotify-branded components.
Aesthetic: dark immersive music cocoon -- content-first darkness where album art provides color.

---

## 1. Quick Color Reference

```
Surface (page bg):    #121212   Near Black -- deepest background, immersive cocoon
Card surface:         #181818   Dark Surface -- cards, containers, sidebar
Interactive surface:  #1f1f1f   Mid Dark -- button backgrounds, interactive surfaces
Elevated card:        #252525   Dark Card -- elevated card surfaces
Accent:              #1ed760   Spotify Green -- play buttons, active states, CTAs only
Text primary:        #ffffff   White -- primary text on dark
Text secondary:      #b3b3b3   Silver -- muted labels, inactive nav
Error:               #f3727f   Negative Red -- error states
Warning:             #ffa42b   Warning Orange -- caution states
Info:                #539df5   Announcement Blue -- informational
Border:              #4d4d4d   Border Gray -- button borders on dark
Border light:        #7c7c7c   Light Border -- outlined buttons, muted links
```

---

## 2. Quick Typography Reference

```
Section:     SpotifyMixUITitle, CircularSp, sans-serif  | 24px | weight 700 | line-height normal | letter-spacing normal
Feature:     SpotifyMixUI, CircularSp, sans-serif       | 18px | weight 600 | line-height 1.30  | letter-spacing normal
Body Bold:   SpotifyMixUI, CircularSp, sans-serif       | 16px | weight 700 | line-height normal | letter-spacing normal
Body:        SpotifyMixUI, CircularSp, sans-serif       | 16px | weight 400 | line-height normal | letter-spacing normal
Button UC:   SpotifyMixUI, CircularSp, sans-serif       | 14px | weight 700 | line-height 1.00  | letter-spacing 1.4px  | uppercase
Button:      SpotifyMixUI, CircularSp, sans-serif       | 14px | weight 700 | line-height normal | letter-spacing 0.14px
Nav Active:  SpotifyMixUI, CircularSp, sans-serif       | 14px | weight 700 | line-height normal | letter-spacing normal
Nav Inactive:SpotifyMixUI, CircularSp, sans-serif       | 14px | weight 400 | line-height normal | letter-spacing normal
Caption:     SpotifyMixUI, CircularSp, sans-serif       | 14px | weight 400 | line-height normal | letter-spacing normal
Small:       SpotifyMixUI, CircularSp, sans-serif       | 12px | weight 400 | line-height normal | letter-spacing normal
Badge:       SpotifyMixUI, CircularSp, sans-serif       | 10.5px| weight 600| line-height 1.33  | text-transform capitalize
```

Key rules:
- Bold/regular binary: most text is 700 (bold) or 400 (regular), 600 is sparingly used
- Uppercase buttons: button labels use uppercase + wide letter-spacing (1.4px-2px)
- Compact sizing: 10px-24px range, designed for scanning playlists not reading articles
- Global script fallback stack for 180+ markets

---

## 3. Example Component Prompts

### Hero Section

Create a hero section with Spotify visual identity:
- Background: `#121212`
- Container: max-width 1280px, centered, padding 80px 32px
- Headline: "Music for every mood" at 24px SpotifyMixUITitle, weight 700, line-height normal, color `#ffffff`
- Subtitle: 16px SpotifyMixUI, weight 400, line-height normal, color `#b3b3b3`, max-width 600px, margin-top 16px
- CTA button: background `#1ed760`, color `#000000`, 14px SpotifyMixUI weight 700, uppercase, letter-spacing 1.4px, padding 14px 32px, border-radius 9999px (full pill), border: none
- Secondary button: background transparent, color `#ffffff`, 14px weight 700, padding 12px 32px, border: 1px solid `#7c7c7c`, border-radius 9999px
- Button row gap: 16px, margin-top 32px
- On mobile (<576px): headline 20px, buttons stack full-width, padding 48px 20px

### Feature Card

Create a dark card with Spotify visual identity:
- Background: `#181818`
- Border-radius: 8px
- Padding: 16px
- No border (borders are rare in Spotify's system)
- Hover: background lightens to `#252525`, transition 300ms
- Album art: square, border-radius 6px (or 50% for artist circles), margin-bottom 16px
- Title: 16px SpotifyMixUI, weight 700, line-height normal, color `#ffffff`, text-overflow ellipsis
- Description: 14px weight 400, color `#b3b3b3`, line-height normal, max 2 lines
- Box-shadow on hover: `rgba(0,0,0,0.3) 0px 8px 8px`
- On mobile (<576px): padding 12px

### CTA Button Row

Create a CTA button row with Spotify visual identity:
- Layout: flex, gap 16px, align-items center
- Primary button (Green Pill): background `#1ed760`, color `#000000`, font 14px SpotifyMixUI weight 700, text-transform uppercase, letter-spacing 1.4px, padding 14px 32px, border-radius 9999px, border: none, cursor pointer, transition: all 200ms
- Primary hover: background `#1fdf64`, transform scale(1.04)
- Outlined button: background transparent, color `#ffffff`, 14px weight 700, padding 12px 32px, border: 1px solid `#7c7c7c`, border-radius 9999px
- Outlined hover: border-color `#ffffff`
- Dark pill: background `#1f1f1f`, color `#ffffff`, padding 8px 16px, border-radius 9999px
- Circular play: background `#1ed760`, color `#000000`, padding 12px, border-radius 50%
- On mobile (<576px): flex-direction column, buttons full-width

### Navigation Bar

Create a sidebar navigation with Spotify visual identity:
- Background: `#121212`, width 240px, height 100vh, position fixed, left 0
- Logo: Spotify logo in `#ffffff`, padding 24px, margin-bottom 16px
- Nav section: padding 0 12px
- Nav item: display flex, align-items center, gap 16px, padding 8px 12px, border-radius 4px, cursor pointer, transition: all 150ms
- Nav icon: 24px, color `#b3b3b3`
- Active item: color `#ffffff`, icon `#ffffff`, background `rgba(255,255,255,0.1)`
- Inactive item: 14px SpotifyMixUI weight 400, color `#b3b3b3`
- Active text: 14px weight 700, color `#ffffff`
- Hover on inactive: color `#ffffff`
- On mobile (<768px): sidebar becomes bottom bar, horizontal, 56px height

### Data Card / Metric Display

Create a stat display card with Spotify visual identity:
- Background: `#181818`
- Border-radius: 8px
- Padding: 24px
- Overline: 12px SpotifyMixUI weight 700, text-transform uppercase, letter-spacing 2px, color `#b3b3b3`, margin-bottom 8px
- Metric value: 24px SpotifyMixUITitle, weight 700, color `#ffffff`
- Description: 14px SpotifyMixUI weight 400, color `#b3b3b3`, margin-top 8px
- Accent indicator: 4px left border in `#1ed760` for positive metrics
- On mobile (<576px): padding 16px, metric value 20px

### Now Playing Bar (Brand-Specific)

Create a now-playing bar with Spotify visual identity:
- Background: `#181818`, position fixed, bottom 0, left 0, right 0, height 72px, z-index 100
- Border-top: 1px solid `#282828`
- Layout: display grid, grid-template-columns 1fr 2fr 1fr, align-items center, padding 0 16px
- Left (track info): album art 48px square radius 4px, track name 14px weight 400 `#ffffff`, artist 12px weight 400 `#b3b3b3`, gap 12px
- Center (controls): flex, gap 16px, align-items center, justify-content center
- Play button: background `#ffffff`, color `#000000`, border-radius 50%, padding 8px, 16px icon
- Skip buttons: color `#b3b3b3`, hover `#ffffff`, 16px
- Progress bar: height 4px, background `#4d4d4d`, border-radius 2px, fill `#1ed760`, hover: fill height 6px
- Right (volume): volume slider same style as progress, speaker icon `#b3b3b3`
- On mobile (<576px): simplified to track info + play/pause only, height 56px

---

## 4. Iteration Guide

1. **Start with `#121212`.** Everything lives in near-black darkness. The UI recedes so content (album art, playlists) can glow. If a surface looks too bright, darken it.

2. **Spotify Green is functional only.** `#1ed760` appears on play buttons, active states, and primary CTAs. Never use it decoratively or as a background fill. The UI stays achromatic.

3. **Pill everything.** 9999px radius for small buttons, 500px for large, 50% for circular play controls. Square buttons break the Spotify identity completely.

4. **Uppercase + wide tracking on buttons.** Button labels use `text-transform: uppercase` and `letter-spacing: 1.4px-2px`. This creates the systematic "label" voice distinct from content text.

5. **Heavy shadows for dark surfaces.** On `#121212` backgrounds, 0.3-0.5 opacity shadows are needed for visibility. Subtle shadows (0.05-0.1) are invisible on dark backgrounds.

6. **Album art provides all the color.** The interface is deliberately achromatic. If a component needs visual interest, add album art or a playlist image rather than introducing colors.
