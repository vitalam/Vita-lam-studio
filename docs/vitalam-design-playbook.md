# VITA LAM — AI-Ready Design Playbook v1
*Extracted from the Modern Design demo (moderndesign.demo.carboncopy.one) and applied to vitalam.org. This document is also a live sample of the「AI-ready 設計手冊」deliverable sold on the site: hand it to any AI tool or developer and the design carries on.*

## 1. Identity in one line
Swiss-brutalist editorial on a black drafting grid: engineering precision, one electric accent, statements set in massive Chinese display type. Serious surfaces, confident voice.

## 2. Colour

| Token | Value | Use |
|---|---|---|
| `--bg` | `#0A0A09` | page background |
| `--ink` | `#F2F2EE` | primary text |
| `--ink-2` | `#B9B9B2` | secondary text |
| `--ink-3` | `#83837C` | tertiary/labels |
| `--accent` | `#D9FF3F` | THE accent — CTAs, highlights, one word per headline max |
| `--accent-2` | `#C4EC2D` | accent hover |
| `--violet` | `#A78BFA` | rare secondary (category chips only, ≤1 use per viewport) |
| panel | `#101010` | card/panel fill |
| line | `#282826` | all borders, 1px |

Text on accent is always `#0C0D04`. Never place accent text on panel fills below 1rem (contrast).

## 3. Background
Fixed full-page drafting grid: 72px repeating hairlines at `rgba(242,242,238,.045)`, both axes, plus two faint glows (lime top-left ~6%, violet bottom-right ~5%). No photos, no gradients as decoration, no glass blur.

## 4. Type
- Latin: Inter. Chinese: Noto Sans TC.
- Display (h1/h2): ZH weight 900, EN weight 800, tight leading (1.04–1.2). Scale: h1 `clamp(2.6rem, 6.2vw, 4.7rem)`.
- Stacked-statement pattern for heroes: line 1 white, line 2 (or key phrase) solid `--accent`. Optionally a mid-line in `--ink-3` for three-step stacks (white → grey → lime).
- Kickers: `.78rem`, uppercase, letter-spacing `.18em`, weight 700, accent colour, auto-numbered `01 ·` `02 ·` … on section heads (CSS counter).
- Body: 17px/1.62, `--ink-2`.

## 5. Shape & surface
- Radius: 6px panels, 3–4px buttons/chips/inputs. Nothing rounder. No pills.
- Panels: `#101010` fill + 1px `#282826` border. No shadows at rest.
- Hover grammar (uniform everywhere): translate(−3px,−3px) + border turns accent + hard offset shadow `6px 6px 0 rgba(217,255,63,.16)` — a print-block "lift", never a soft glow.
- Brand mark: 【VITA LAM】 — CJK corner brackets in accent around the wordmark.

## 6. Components
- **Buttons:** primary = solid accent, black text, sharp; secondary = 1px border ghost; WhatsApp = accent-outlined ghost that fills on hover. Hover = translate(−2px,−2px) + hard shadow.
- **Icon chips:** 54px square, 4px radius, `#141412` fill, hairline border, accent stroke icon (hand-drawn SVG sprite, stroke 2.2).
- **Marquee ticker:** hairline-bordered strip, uppercase ZH+EN service words separated by accent `✳`, 40s linear loop, paused under reduced-motion. One per page.
- **Chips/filters:** rectangular ghost; active = solid accent.
- **Tables:** hairline row rules, first column `--ink` 600, prices in accent.
- **Forms:** `#0E0E0D` fields, hairline borders, accent focus ring.
- **Floating action:** 56px accent square (WhatsApp), hard-shadow hover.

## 7. Motion
Scroll-reveal only: 22px rise + fade, .7s cubic-bezier(.2,.6,.2,1), once. Marquee drift. Pulse ring (accent) for wayfinding highlights. Everything stops under `prefers-reduced-motion`. No parallax, no cursor effects.

## 8. Voice (copy rules travel with the design)
Precise, punchy, professional-humorous. Fragments allowed. One dry joke per section max. Statements over descriptions: 「設計是一門學科，不是服務。」 Cantonese-flavoured 書面語; second-person outcomes; first-person buttons.

## 9. Hard rules for any AI tool continuing this design
1. One accent. Lime `#D9FF3F` earns its power by scarcity — if everything is lime, nothing is.
2. Hairlines everywhere; soft shadows nowhere. Depth comes from the hover block-lift only.
3. Type does the hierarchy. If a layout needs decoration to read clearly, fix the type scale instead.
4. The grid background is the canvas signature — never remove it, never busy it.
5. Both languages always in the DOM; ZH is default; ZH display type is always weight 900.
6. Never describe the AI Logic Firewall mechanism; benefit language only.
