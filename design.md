# Design System — Bamboo Sushi Bar & Hibachi Express

**Version 2.** Supersedes the first draft, which documented a light/dark theme pair. That was wrong — see "Theme history" below.

This file exists so any future session editing or extending this site uses the **real** tokens below instead of inventing new colors, fonts, or components. Treat every value here as a constraint, not a suggestion. If a task calls for something not covered here, ask before improvising.

---

## Theme history — read this before touching color

The original `index.html` contained **two** `:root` blocks defining the same variable names: a light "paper" theme and a dark "charcoal" theme. There was no toggle — no `data-theme` attribute, no `prefers-color-scheme` query, no class switch, no `localStorage`. Nothing in the codebase ever selected between them.

Because the dark block appeared later in the source, it won the cascade unconditionally. **The light theme was dead code that never rendered for a single visitor.** The site has always been dark; that was an accident of source order rather than a decision.

The client subsequently said they wanted a dark site with light type that pops — which is a description of what was already live. So v2 makes it deliberate:

- **One theme. Dark.** The light tokens are deleted, not commented out.
- **Do not add a theme toggle** unless the client explicitly asks. For a restaurant site it's real ongoing cost (every new component needs testing in two palettes, forever) for a feature approximately zero diners will click.

---

## Brand Overview

- **Name:** Bamboo Sushi Bar & Hibachi Express
- **Mascot mark:** "Bomb Squad" — a scowling chef head biting chopsticks inside a red circle badge, flanked by two hanging banner flags reading "SAKE" and "BOMBERS." Used as the icon-only mark (nav, favicon, footer) alongside the wordmark.
- **Category:** Family-owned Japanese restaurant — sushi, hibachi, ramen. Three Emerald Coast locations. Founded October 2007 by Joe Rice and Danny Ledford, starting with a 45-seat room in Crestview.
- **Positioning:** Fresh ingredients, fair prices, counter-service speed with full-service care. Confident and a little playful (roll names like Godzilla, Sasquatch, King Kong, TNT) without tipping into cartoonish — the type and layout stay editorial, the roll names carry the personality.

---

## The Content Principle (the most important thing in this file)

**This restaurant has two distinct houses, and the design must keep them separate.**

| | The Bar | The Line |
|---|---|---|
| **What it is** | Sushi bar, out front | Hibachi Express, closed kitchen in back |
| **Visible?** | Yes — customers watch every roll get cut | No — nobody sees the cooking |
| **The promise** | Craft, hand work, theater | Speed, fired to order, out fast |
| **Copy verbs** | rolled, cut, hand-pressed, made in front of you | fired, griddled, out fast, to order |

The v1 site blurred these into one generic "grill" story — the H1 said *"Fun on the grill,"* the menu section said *"hot off the grill,"* and the story said *"the same family running the grills."* All three pointed the customer's attention at the one station they can never see, and away from the one they can.

**Rules that follow from this:**

- Never imply tableside or theatrical hibachi cooking. There is no teppanyaki chef performing at the table. Hibachi Express is a closed back kitchen.
- Never describe sushi as "sizzling," "hot off the grill," or anything thermal. (The v1 hero literally said sushi was *"served sizzling hot."*)
- The sushi bar is the strongest untapped asset on the site. Sell it. "Best seat in the house, same price as a table" is a real, free differentiator.
- "Best sushi on the Emerald Coast" is only usable **attributed** — they won Community's Choice "Finest on the Emerald Coast: Best Sushi" in 2023 and 2024. Unattributed it's a hollow brag everyone makes.

---

## Verified Facts (single source of truth)

Hours were wrong on the v1 site — listed as a 9:00am open in both the visible copy and the JSON-LD structured data Google reads. Corrected and confirmed by the client:

- **Mon–Thu, Sun:** 11:00am – 8:30pm
- **Fri–Sat:** 11:00am – 9:30pm
- Same at all three locations.

| Location | Address | Phone | Notes |
|---|---|---|---|
| Crestview | 2505 S Ferdon Blvd, Crestview, FL 32536 | (850) 689-1391 | Original, est. 2007. Dine-in, takeout, curbside |
| Fort Walton Beach | 9 Eglin Pkwy NE, Fort Walton Beach, FL 32548 | (850) 200-4250 | **Drive-thru** |
| Niceville | 117 W John Sims Pkwy, Niceville, FL 32578 | (850) 678-0771 | **Drive-thru** |

Instagram: `@bamboo_crestview`, `@bamboo_fwb`, `@bambooniceville`

**Still unverified — do not publish without checking:** catering lead time (currently vague), the three review-summary cards (unverified paraphrase, not real quotes), and the rating figures (4.5 Google / 4.3 Tripadvisor / 4.2 Yelp).

---

## Color System

One theme. The site's own CSS comment explains the two-red decision: *"Logo is 56% red, mean #D62D34. Brand red kept as-is. Two reds by necessity: #D8262A is only 3.56:1 on charcoal (WCAG large-text only), so small text uses `--red-lite` at 5.36:1."*

| Token | Hex | Use |
|---|---|---|
| `--paper` | `#1A1817` | Page background — warm charcoal, never cool gray |
| `--card` | `#232020` | Elevated surfaces |
| `--void` | `#100E0E` | Deepest accent band (dark contrast sections) |
| `--ink` | `#F2EDE4` | Primary text — warm cream, 15.17:1 |
| `--ash` | `#B9AFA4` | Secondary text, 8.20:1 |
| `--ash-dim` | `#8A8078` | Tertiary/quiet text |
| `--rule` | `#332E2C` | Borders, dividers |
| `--seam` | `#2A2624` | Subtle fills (badges, placeholders) |
| `--red` | `#D8262A` | Logo red — **large text, fills and buttons only** |
| `--red-lite` | `#F25A53` | **Small text and links** — the accessible substitute |
| `--red-hover` | `#E8433F` | Hover state |
| `--red-deep` | `#7A1215` | Deep red for gradients |
| `--red-tint` | `rgba(216,38,42,.12)` | Wash (notices, active pills) |
| `--gold` | `#C9962F` | Sparingly — awards, location pins |

**The one rule people break:** never use `--red` for small body text. Use `--red-lite`. This is a deliberate WCAG fix, not an inconsistency.

Two variants push the background darker for a more gallery-like feel — `#141211` (Itamae) and `#0D0B0B` (Bomb Squad). Both are legitimate; the token relationships stay identical.

---

## Typography

Three families, each with exactly one job:

| Family | Role | Weights | Notes |
|---|---|---|---|
| **Fraunces** (serif) | Display — headlines, section titles, dish names, pull quotes | 300–600, italic 300–600 | Italic is an emphasis/color device, not for whole sentences |
| **Inter** (sans) | Body copy, buttons, paragraphs | 300–700 | 16px base, 1.6 line-height |
| **IBM Plex Mono** | Eyebrows, labels, nav, badges, stats | 400–600 | Always uppercase, always letter-spaced `.06em`–`.22em`. Never body paragraphs |

Never substitute a system sans for headlines — Fraunces carries the editorial feel. Never use Inter for the small tracked labels — the monospace is what makes the "order ticket" motif read.

---

## Spacing & Shape

- **Page gutter:** `clamp(20px, 5vw, 64px)` — fluid, never fixed.
- **Section rhythm:** `clamp(64px, 10vw, 128px)` vertical padding. Editorial variants go up to `150px`.
- **Radius scale** — nothing outside this set:
  - `100px` pill — buttons, tags, badges
  - `20–26px` — feature panels, hero media
  - `14–18px` — cards
  - `50%` — circular icon buttons
  - `2px` — permitted only in the editorial variant, where near-square corners are the point

Never sharp corners on an interactive element. No stray `4px` or `8px` radii.

---

## Motion

- **Easing:** `cubic-bezier(.16,.9,.28,1)` (or `.16,1,.3,1` in the effects build). One curve per document — don't mix.
- **Scroll reveal:** fade + rise 22–28px, staggered via a `--d` delay variable in ms.
- **Hover lift:** `-1px` to `-4px`. Never more.
- **Image zoom:** `1.04–1.09` scale, `.6–1.4s`.
- **`prefers-reduced-motion: reduce` is non-negotiable.** Every animation must check it. The builds disable animation, transition and smooth-scroll globally when it's set.

---

## Effects Catalogue (v2)

Available in the effects build. All vanilla — no libraries. Every one is gated on `prefers-reduced-motion`; pointer-driven ones additionally on `(pointer:fine)` so touch devices never pay for them.

| Effect | What it does | Notes |
|---|---|---|
| **Film grain** | Inline SVG `feTurbulence` noise, animated with `steps(6)` | No image request. This is what stops a flat dark page reading as dead black plastic. `opacity:.055` |
| **Hairline grid** | Fixed background grid with a radial `mask-image` fade | Structure without noise |
| **Cursor glow** | Radial red glow trailing the pointer across the hero | Lerped at `0.12`; the rAF loop stops itself once caught up — no idle loop |
| **Magnetic buttons** | Button translates toward the cursor | `0.16` x / `0.26` y multipliers |
| **Card tilt** | 3D perspective rotate on pointer move | **Max 5°.** More reads as a gimmick |
| **Animated counters** | Count up with ease-out-quart | Zeroed on load, fires once at 60% visibility |
| **Clip-path drawer** | Mobile menu wipes open via `inset(0 0 100% 0)` → `inset(0)` | Nicer than a translate |
| **Glow shadows** | `color-mix(in srgb, var(--red) N%, transparent)` | Ties every glow to the accent token |
| **Scroll readout** | Fixed corner showing scroll % + current section | rAF-throttled, passive listener |

**Deliberately rejected** (from the same reference material): terminal boot sequences and text-scramble effects. Both are software-agency conceits — a restaurant homepage that appears to boot a fake terminal reads as a broken page, not as craft. Don't add them.

---

## Component Patterns (don't reinvent these)

- **Buttons:** pill radius, ~14px/26px padding, 600 weight. Variants: solid red (primary), ghost-dark, ghost-light (over photos). The effects build adds a `::before` fill that slides up on hover.
- **Eyebrow tags:** mono, uppercase, small red `●` before the text, dashed bottom border. The recurring "order ticket" motif — introduces every major section. **This is the site's strongest structural device. Keep it.**
- **Marquee:** infinite horizontal strip, red or ink background, mono uppercase, `✻`/`◆` separators. Track must be duplicated in JS for a seamless `-50%` loop.
- **Dark contrast band:** near-black with a radial red/gold glow. Use once, for a genuine content peak — not decoration.
- **Cards:** `--card` surface, 1px `--rule` border, red border + lift on hover. No heavy default shadows.
- **Location pin badge:** small gold-bordered pill. Location cards only.
- **Live open/closed status:** colored dot + label, green pulse when open, muted when closed. Driven by the hours table above. Don't repurpose for anything but real-time status.

---

## Photography & Imagery

- Warm grade, `object-fit: cover` by default. `object-fit: contain` only for award certificates and trophies, so nothing gets cropped.
- Hero images get a layered gradient scrim (vertical dark-to-paper + horizontal dark-to-transparent) so white headline text stays legible without a flat overlay box.
- Rounded containers per the radius scale — never edge-to-edge square crops.
- Asset paths are relative and stable: `images/brand/`, `images/food/`, `images/gallery/`, `images/menu/`. Keep them.

---

## Voice & Copy Tone

Short, concrete, occasionally wry. Never generic "delicious and fresh" filler. Real examples from the live copy:

- *"Miso Soup — starts almost every table's order."*
- *"Panko Fried Shrimp — the most-mentioned starter in our reviews."*
- *"Uni — market price, when we can get it right."*
- *"Order direct. It's cheaper."*

Keep new copy in that register: specific, a little dry, never over-selling. Specificity beats adjectives — "45-seat room" does more work than any amount of "cozy."

**Lines worth protecting in any redesign:** "Full-service care, counter-service speed." · "Order direct. It's cheaper." · the counter-service explainer paragraph · "From a 45-seat room in Crestview…" · "Come in as a customer and leave as a friend."

---

## Accessibility Constraints

- Focus states: 2–2.5px solid red outline, 3px offset. Never remove or replace with the browser default.
- Contrast is pre-computed (ratios in the color table). New text-on-background pairings must be checked, not eyeballed.
- `prefers-reduced-motion` respected globally.
- Every interactive element is a real `<button>` or `<a>`. Lightboxes trap focus and close on `Escape`, returning focus to the trigger.

---

## Hard Constraints (what NOT to do)

- No second theme. No light mode. No toggle.
- No pure black or pure white as a text/background pair — always the warm tokens.
- No system-default sans for headlines. Fraunces only.
- No sharp corners on buttons, tags, or cards.
- No easing curves or radii outside what's documented above.
- No stock Bootstrap-style card shadows or generic SaaS gradients. The only gradients here are the documented red/gold radial glows and the hero scrim.
- Never `--red` for small text — use `--red-lite`.
- Never imply theatrical hibachi. Never call sushi hot.
- No terminal-boot or text-scramble effects.
