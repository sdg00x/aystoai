# Brand

What AYSTO looks and sounds like, so new pages, sections and posts match.

## Look

Dark, calm and a bit futuristic. Deep navy background, one electric blue that marks the thing you want people to see, and a faint grid behind the dark sections.

## Colour

### Dark sections (clinic homepage, blog hero)

| Token | Hex | Use |
| --- | --- | --- |
| `--bg` | `#05070C` | Page background |
| `--bg-2` | `#090D16` | Raised sections |
| `--text` | `#E9EEF8` | Body and headings |
| `--muted` | `#8B97AE` | Secondary text |
| `--blue` | `#1FA8FF` | Primary buttons, key highlights |
| `--teal` | `#3EE6C1` | Gradient start, success states |
| `--indigo` | `#7C8CFF` | Gradient end |
| `--red` | `#FF6B6B` | Missed call, cost figures |
| `--amber` | `#FFC46B` | Warnings, founding offer |

Headline gradient: `linear-gradient(90deg, #3EE6C1 0%, #1FA8FF 45%, #7C8CFF 100%)`, applied to one phrase per headline at most.

### Light sections

| Token | Hex | Use |
| --- | --- | --- |
| `--l-bg` | `#F5F7FB` | Light section background |
| `--l-card` | `#FFFFFF` | Cards |
| `--l-line` | `#E3E8F0` | Borders |
| `--l-text` | `#0B1020` | Text |
| `--l-muted` | `#5B6478` | Secondary text |

### `/business` page

The local business page uses a lighter, friendlier palette so it reads as a separate offer:

| Token | Hex |
| --- | --- |
| `--text` | `#0E1A1C` |
| `--teal` | `#178A7A` |
| `--mint` | `#5EE0C6` |
| `--navy` | `#0B1A3A` |
| `--blue` | `#2563EB` |
| `--soft` | `#F4F7F6` |

## Type

| Role | Font | Weights |
| --- | --- | --- |
| Headings | Space Grotesk | 500, 600, 700 |
| Body | Inter | 400, 500, 600 |
| Labels, eyebrows, numbers | JetBrains Mono | 400, 500 |

Headings are tight: `letter-spacing: -0.03em`, `line-height: 1.06`. Eyebrow labels are mono, uppercase, spaced out, in a soft blue.

## Logo

"Node A": an A drawn as a single stroked path, in electric blue on the dark background. The wordmark is AYSTO in Space Grotesk, spaced.

## Voice

- Lead with time and money saved, not with the AI.
- Plain, spoken words. Short sentences.
- Specific numbers over adjectives ("live in 14 days", "from £950").
- Honest about what AI should and shouldn't do, especially around medical advice.
- No hype words, no fake urgency, no em dashes.

## Motion

Subtle and purposeful: sections fade up as they scroll in, the hero phone animates a live call, buttons lift slightly on hover. Everything respects `prefers-reduced-motion`.
