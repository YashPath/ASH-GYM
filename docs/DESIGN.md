# Design notes

## Concept

**"Rise from the ash."** The page opens cold: ash-grey ground, white type, grey photos. As the visitor scrolls, it heats up. A glow rises from the bottom of the screen, embers speed up, photos warm into colour, and the accent shifts toward ember orange. The scroll itself is the story of a workout: cold start, building heat, full burn at the join form.

The one signature moment is the **barbell section**. Plates in real competition colours slide onto a 20 kg Olympic bar as you scroll, and the counter reads the true total. It is a detail only a gym would have.

## Colour tokens

| Token | Hex | Use |
|---|---|---|
| `--ash` | `#1d1b1a` | Page background, warm charcoal rather than pure black |
| `--soot` | `#2a2725` | Cards, table header, form panels |
| `--cinder` | `#a39c95` | Secondary text |
| `--bone` | `#efe9e2` | Primary text |
| `--ember` | `#ff5a1f` | Accent, buttons, highlighted plan |
| `--glow` | `#ffb347` | Hot highlights, numbers, peak hours |
| `--line` | `#3a3633` | Borders and dividers |

The site deliberately commits to a single dark look. It sets `color-scheme: dark` and does not switch with the system theme.

### Barbell plate colours (IWF competition standard)

| Plate | Colour |
|---|---|
| 25 kg | Red `#d7263d` |
| 20 kg | Blue `#1e5bd8` |
| 15 kg | Yellow `#f2c230` |
| 10 kg | Green `#2f9e44` |
| 5 kg | White `#efe9e2` |

Loaded total: 20 kg bar + 2 × (25 + 20 + 15 + 10 + 5) = **170 kg**.

## Typography

| Role | Font | Notes |
|---|---|---|
| Display | Big Shoulders Display 800/900 | Condensed industrial face; used large and tight |
| Body | Archivo 400/500/700 | Sturdy grotesque that stays readable on dark backgrounds |

Fallbacks: `Impact, Arial Narrow` for display and `Helvetica Neue, Arial` for body.

Scale (fluid with `clamp`):
- Hero word: 140 px to 460 px
- Section titles: 50 px to 112 px
- Card titles: 40 px to 80 px
- Body: 16 px, intro paragraphs 17 px to 21 px

## Layout

- Max content width 1180 px, side gutter at least 16 px (safe-area aware)
- Section spacing `clamp(72px, 10vw, 112px)`
- Breakpoints: 1000 px (plans 4 → 2 columns), 860 px (facilities panel hidden), 760 px (mobile animation mode), 640 px (gallery 3 → 2 columns)

## Animation map

All scroll animations use GSAP ScrollTrigger with `scrub`, so motion follows the scroll position instead of playing once.

| Section | Trigger | Pinned (desktop) | Pinned (mobile) |
|---|---|---|---|
| Hero letters, embers, background | hero top → hero bottom | No | No |
| Programs horizontal track | section top, length = track width | Yes | No (cards reveal vertically) |
| Barbell plates + counter | section top, +1200 px (+700 on mobile) | Yes | Yes |
| Facilities lines + photo panel | each line at 60 % of viewport | No (sticky panel) | No |
| Coach card stack | section top, +650 px per card (+380 on mobile) | Yes | Yes |
| 12-week timeline | section top, +900 px | Yes | No (vertical timeline) |
| Photo "heat" (grey to colour) | each photo, 95 % → 40 % of viewport | No | No |
| Gallery parallax | gallery enter → leave | No | No |

Pinned ScrollTriggers are created in page order and sorted with `ScrollTrigger.sort()` so pin spacing stays correct.

### Reduced motion

With `prefers-reduced-motion: reduce`, GSAP is skipped entirely. The barbell shows its full 170 kg, videos show their poster image, and the BMI calculator, FAQ and join form still work.

## Media treatment

- Photos are resized to 1000 px wide (hero 1800 px) and saved as WebP at quality 68
- Videos are trimmed to about 9 seconds, scaled to 540 px wide, H.264 CRF 30, audio removed, with a WebP poster frame
- Photos showing another gym's logo, or bright outdoor scenes that clash with the dark palette, were left out
