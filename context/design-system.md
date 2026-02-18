# AI for All — Design System

## Fonts

- **Headings:** Fraunces (variable, optical size 9-144, weights 400/600/700)
- **Body:** Commissioner (weights 400/500/600)
- **Google Fonts import:** `https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,400;9..144,600;9..144,700&family=Commissioner:wght@400;500;600&display=swap`

## Colors

### Core Palette
| Token | Value | Usage |
|-------|-------|-------|
| `--ink` | `#1c1917` | Primary text, nav background, footer background |
| `--paper` | `#fafaf9` | Page background |
| `--cream` | `#f5f5f0` | Section backgrounds, secondary button bg |
| `--accent` | `#0f766e` | Primary brand color (teal), links, buttons, stat numbers |
| `--accent-light` | `#ccfbf1` | Highlight boxes, tags |
| `--accent-dark` | `#134e4a` | Hover states, dark accent text |
| `--warm-gray` | `#78716c` | Secondary text |
| `--warm-gray-light` | `#a8a29e` | Tertiary text |
| `--border` | `#e7e5e4` | Card borders, dividers |
| `--highlight` | `#fef3c7` | Warning boxes, warning tags |
| `--highlight-dark` | `#f59e0b` | Warning accents |

### Status Colors
| Token | Value | Usage |
|-------|-------|-------|
| `--success` / `--success-light` | `#16a34a` / `#dcfce7` | Confirmed status |
| `--warning` / `--warning-light` | `#ca8a04` / `#fef9c3` | Pending/caution |
| `--error` / `--error-light` | `#dc2626` / `#fee2e2` | Error states |

### Extended Colors (used in planning/hub pages)
| Token | Value | Usage |
|-------|-------|-------|
| `--blue` / `--blue-light` | `#2563eb` / `#dbeafe` | Info highlights |
| `--yellow` / `--yellow-light` | `#f59e0b` / `#fef3c7` | Warning/attention |
| `--green` / `--green-light` | `#16a34a` / `#dcfce7` | Success/confirmed |
| `--coral` | `#e45a3b` | Accent/alert |

## Spacing Scale
| Token | Value |
|-------|-------|
| `--space-xs` | 4px |
| `--space-sm` | 8px |
| `--space-md` | 16px |
| `--space-lg` | 24px |
| `--space-xl` | 40px |
| `--space-2xl` | 60px |

## Border Radius
| Token | Value |
|-------|-------|
| `--radius-sm` | 4px |
| `--radius-md` | 8px |
| `--radius-lg` | 12px |
| `--radius-full` | 9999px (pills/tags) |

## Shadows
| Token | Value |
|-------|-------|
| `--shadow-sm` | `0 1px 2px rgba(0,0,0,0.05)` |
| `--shadow-md` | `0 4px 12px rgba(0,0,0,0.08)` |
| `--shadow-lg` | `0 8px 25px rgba(0,0,0,0.12)` |

## Typography Scale
| Element | Size | Weight | Font |
|---------|------|--------|------|
| h1 | 2.5em | 700 | Fraunces |
| h2 | 1.8em | 600 | Fraunces |
| h3 | 1.3em | 600 | Fraunces |
| h4 | 1.1em | 600 | Fraunces |
| body | 15px | 400 | Commissioner |
| nav logo | 1.4em | 600 | Fraunces |
| nav links | 0.95em | 500 | Commissioner |

## Component Patterns

### Navigation
- Dark (`--ink`) sticky top bar
- Logo left, links right
- Max-width 1200px container
- White text, opacity 0.8 on hover

### Hero Sections
- Gradient background: `linear-gradient(135deg, var(--ink) 0%, #292524 100%)`
- White text, centered
- Max 700px paragraph width

### Cards
- White background, `--border` border, `--radius-lg` corners
- Hover: translateY(-2px) + `--shadow-md`
- `.card-accent`: 4px left border in `--accent`

### Buttons
- `.btn-primary`: `--accent` bg, white text, `--accent-dark` hover
- `.btn-secondary`: `--cream` bg, `--ink` text, `--border` hover

### Footer
- `--ink` background, white text, centered
- Three lines: bold title, subtitle, muted copyright

## CSS Architecture

- `styles.css` at repo root contains the shared design tokens and base component styles
- Public pages (`index.html`, `calendar.html`, `survey.html`) link `styles.css`
- Hub and planning pages currently use inline `<style>` blocks with duplicated vars
- Future goal: migrate hub/planning pages to use shared `styles.css` too

## Aesthetic Direction

- Clean, professional, minimal — not colorful or playful
- Desktop-focused layouts for business stakeholders
- Warm neutral palette (stone/warm-gray family)
- Teal accent for brand identity
- No emojis in UI, no excessive decoration
