# dave&mike.net — Handoff Brief (April 14, 2026)

## Project
Static single-page landing site for David & Mike's personal lifestyle brand. Pure HTML/CSS/JS — no framework, no build step. Target: GitHub Pages.

## File structure (all in one folder)
```
index.html           ← main file, all CSS + JS inline
arm_phone.png        ← 800×1028px, transparent PNG, hand holding iPhone
table_setting.png    ← 896×1168px, hero background photo (Firefly-generated)
FireflyNoLable.png   ← 768×1376px, referenced inside the logo SVG
wine_glass_bottle1.svg ← inline logo (wine glass + bottle + wordmark)
```

## Layout
Left/right split: 52% / 48%, full viewport height, no scroll.

**Left panel:** `table_setting.png` as full-cover background. `arm_phone.png` overlaid, anchored bottom-left, exits the frame at the lower-left corner (no floating elbow). Width: 64% of panel. Rotated 4° clockwise.

**Right panel:** Cream bg `#F0EDE7`. Logo SVG (134px wide) → "esperienze" (italic Cormorant Garamond) → definition line → rule → nav links (Travel, Kitchen, Family) with slate-blue arrows.

## Carousel (built, placeholder content)
A `<div class="phone-screen">` is absolutely positioned over the white screen area of `arm_phone.png`:
- Center: 65% left, 38.6% top of the phone-zone container
- Size: 25% W × 45% H
- Rotation: 15° clockwise (matches phone screen tilt in photo)
- 3 placeholder color slides: slate blue → cream → rust
- Crossfade transition, auto-advances every 4 seconds

**To swap in real photos** — replace each placeholder div with:
```html
<img class="slide" src="photo.jpg" style="object-fit:cover;width:100%;height:100%">
```

## Brand tokens
| Token | Value | Use |
|---|---|---|
| Accent | `#5E82A0` | Slate blue — "&" wordmark, nav arrows |
| BG right | `#F0EDE7` | Warm cream right panel |
| Text | `#1C1A18` | Near-black body |
| Muted | `#8A7F76` | Warm grey definition text |
| Rule | `#D8D2CA` | Thin horizontal divider |

Fonts: **Cormorant Garamond** (esperienze heading) + **DM Sans** (everything else) via Google Fonts.

## What's still open
1. Dave provides real carousel photos (travel + dinner parties) to swap in
2. Visual fine-tune of carousel overlay position once viewed in browser (15° rotation + center position measured from pixel analysis — may need ±1–2° nudge)
3. Nav links are `href="#"` placeholders — need real destinations or section content
4. GitHub repo setup + Pages deploy

## Known issue to watch
The carousel overlay rotation (15°) was computed from pixel-level analysis of arm_phone.png. It should be close but worth a browser check — if the colored rectangle doesn't sit squarely on the white screen, adjust `rotate()` in `.phone-screen` up or down a few degrees.
