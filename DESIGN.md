# Design System — TTAndrei Portfolio

## Color Strategy: Committed

One dominant accent (cobalt) carries 35–40% of prominent surfaces. Amber reserved exclusively for numeric metrics and data values. Neither appears together in the same element.

### Palette

```
--bg:              oklch(11% 0.01 250)   /* near-black, blue-tinted */
--surface:         oklch(16% 0.012 250)  /* project sections */
--surface-accent:  oklch(14% 0.02 250)   /* featured project section */
--border:          oklch(22% 0.015 250)
--text:            oklch(91% 0.008 250)  /* primary text */
--text-secondary:  oklch(60% 0.01 250)   /* descriptions, labels */
--accent:          oklch(65% 0.19 250)   /* cobalt — radar scope blue */
--accent-dim:      oklch(55% 0.18 250)   /* accent on hover */
--accent-subtle:   oklch(65% 0.19 250 / 0.12) /* accent backgrounds */
--amber:           oklch(74% 0.14 60)    /* metrics and data only */
--amber-subtle:    oklch(74% 0.14 60 / 0.10)
```

### Usage Rules

- `--accent` on borders, nav, active states, project numbers, links, decorative elements
- `--amber` ONLY on numeric metric values. Never on headings or body copy.
- Never mix `--accent` and `--amber` in the same compound element
- No `#000` or `#fff` — all neutrals tinted toward `h=250`

## Typography

### Fonts

- **Display:** Chakra Petch 600, 700 — headings, project titles, hero name
- **Body:** Source Sans 3 400, 600 — descriptions, labels, nav links, body copy
- **Mono:** Source Code Pro 400, 500 — numeric metrics, tech tags, file paths, code

Google Fonts import: `Chakra+Petch:wght@600;700|Source+Code+Pro:wght@400;500|Source+Sans+3:wght@400;600`

### Scale

Fluid with `clamp()`, ratio ≥ 1.3 between adjacent steps.

```
hero-name:    clamp(3.5rem, 9vw, 7.5rem)   Chakra Petch 700
hero-sub:     clamp(1rem, 2.5vw, 1.5rem)    Source Sans 3 400
section-h2:   clamp(1.75rem, 4vw, 3rem)     Chakra Petch 700
project-h3:   clamp(1.25rem, 2vw, 1.6rem)   Chakra Petch 600
metric-val:   clamp(1.75rem, 3.5vw, 2.5rem) Source Code Pro 500
body:         clamp(0.9375rem, 1.5vw, 1.0625rem) Source Sans 3 400
label:        0.6875rem                      Source Code Pro 500
```

Line-height on dark: body 1.7, headings 1.1, metrics 1.0

### Body Width

Max 65ch on prose. Never full-width text.

## Elevation / Depth

No `box-shadow` with spread. Only diffuse ambient glow where needed:
- Project card hover: `0 0 0 1px var(--border), 0 8px 32px oklch(65% 0.19 250 / 0.08)`
- No blur-glass (glassmorphism banned)

## Layout

- Max site width: 1200px, centered, `padding-inline: clamp(1.5rem, 5vw, 4rem)`
- Sections: vertical rhythm via `padding-block: clamp(5rem, 10vw, 9rem)`
- Featured project: 2-col (content left, screenshots right), `gap: clamp(2rem, 5vw, 5rem)`
- Supporting projects: full-width 2-col for Drones, then 2-col grid for PGTA pair
- No nested cards. No icon-heading-text card grid.

## Motion

- Entrance: `opacity 0→1 + translateY 24px→0`, `0.6s cubic-bezier(0.16, 1, 0.3, 1)`
- Stagger: `0.1s` delay per sibling
- Hover transitions: `0.2s ease-out`
- Radar sweep: `3.8s linear infinite` rotate
- No bounce. No elastic. No layout-property animation.

## Components

### Tech Tag
Small pill. Border: `1px solid var(--border)`. Text: `var(--text-secondary)`, `Source Code Pro 500`, `0.6875rem`. Padding: `0.25rem 0.625rem`. No background fill.

### Project Number
`Source Code Pro 500`, `var(--accent)`, `0.75rem`, tracked uppercase. Example: `01 / FEATURED`.

### Metric Block
Value: `Source Code Pro 500`, `var(--amber)`, metric-val scale. Label below: `Source Code Pro 500`, `var(--text-secondary)`, `label` scale, uppercase, tracked.

### Image Slot (placeholder state)
`aspect-ratio: 16/9`. Border: `1px dashed var(--accent)`. Background: `var(--surface)`. When missing: amber monospace label showing filename.

## Bans (active)

- No side-stripe borders (border-left accent)
- No gradient text
- No glassmorphism
- No hero-metric template (big number + gradient accent card)
- No identical card grid for all 4 projects
- No em dash
- No `#000` or `#fff`
