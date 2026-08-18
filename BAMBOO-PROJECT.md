# Bamboo Sushi — Project Memory

Drop this in the project root next to `index.html`. Any future Claude session that can see this file starts already knowing the project instead of re-deriving it.

Last updated: 18 Aug 2026

---

## What this is

Paid freelance web work. Rob is rebuilding the site for **Bamboo Sushi Bar & Hibachi Express** — a family-owned Japanese restaurant with three locations on Florida's Emerald Coast. Rob works there as a sushi chef, which is where the client relationship came from.

Current state: three design concepts delivered, awaiting the client picking a direction.

---

## Deliverables so far

| File | What it is |
|---|---|
| `bamboo-concept-01-classic.html` | Familiar structure, refined. Closest to what they have now. |
| `bamboo-concept-02-editorial.html` | Editorial layout, large type, generous whitespace. |
| `bamboo-concept-03-immersive.html` | Full motion/texture build — grain, cursor glow, tilt, magnetic buttons. |
| `bamboo-brand-guide.pdf` | **Client-facing.** Presents the system as finished. No process, no before/after. |
| `design.md` | **Internal.** Full technical spec — tokens, effects, constraints. |
| `copy-audit.md` | **Internal only. Never send to the client.** |

**Naming rule:** files that reach the client must not carry internal codenames or imply the work was iterative. The client should see a finished product, not a process.

---

## Verified facts (confirmed by the client)

**Hours** — the same at all three locations:
- Mon–Thu, Sun: 11:00am – 8:30pm
- Fri–Sat: 11:00am – 9:30pm

| Location | Address | Phone | Notes |
|---|---|---|---|
| Crestview | 2505 S Ferdon Blvd, Crestview, FL 32536 | (850) 689-1391 | Original, est. 2007. No drive-thru. |
| Fort Walton Beach | 9 Eglin Pkwy NE, Fort Walton Beach, FL 32548 | (850) 200-4250 | Drive-thru |
| Niceville | 117 W John Sims Pkwy, Niceville, FL 32578 | (850) 678-0771 | Drive-thru |

- Founded October 2007 by Joe Rice and Danny Ledford. Started with a 45-seat room in Crestview. Fort Walton Beach followed, Niceville in 2015.
- Instagram: `@bamboo_crestview`, `@bamboo_fwb`, `@bambooniceville`
- Awards: Community's Choice "Finest on the Emerald Coast — Best Sushi", 2023 and 2024.

---

## The core brand idea

**Two houses, one roof.**

- **The Bar** — out front, in the open. Guests watch every roll get cut. Visible craft. Language: *rolled, cut, by hand.*
- **The Line** — Hibachi Express, a closed kitchen in back. No tableside show. Speed and consistency. Language: *fired, griddled, out fast.*

Everything in the design hangs off this split. Two absolute rules follow from it:

- **Never** imply hibachi is cooked in front of guests. There is no teppanyaki performance.
- **Never** describe sushi as hot, sizzling, or grilled.

---

## Design system, short version

Single dark theme. Do not add a light mode or a theme toggle.

- Background `#1A1817` (warm charcoal) · Cards `#232020` · Deep bands `#100E0E`
- Text `#F2EDE4` · Secondary `#B9AFA4` · Borders `#332E2C`
- Brand red `#D8262A` for buttons, fills, large headlines
- Light red `#F25A53` for links and small text — **never** full-strength red on small type
- Gold `#C9962F` sparingly

Fonts: **Fraunces** (headlines) · **Inter** (body) · **IBM Plex Mono** (small caps labels).

Signature element: the **Order No. 01 / 02 / 03** eyebrow labels. Spaced monospace capitals, red bullet, dashed underline. Protect this in any redesign.

Full detail is in `design.md`.

---

## Still open — needs the client

1. **Ordering URL.** All three concepts read from a single `CONFIG.ORDER_URL` value at the top of the script block. Set it once and every order button updates.
2. **Catering lead time.** Copy still says "as much advance notice as you can." Needs a real number.
3. **Review scores.** 4.5 Google / 4.3 Tripadvisor / 4.2 Yelp were carried over — confirm before launch.

---

## Things already fixed — do not reintroduce

- Hours were published as a 9:00am open in both the visible copy and the structured data Google reads. Corrected to 11:00am.
- The old site described sushi as "served sizzling hot" and led with "Fun on the grill," pointing guests at the closed kitchen instead of the sushi bar.
- Handheld phone photos of the printed menu boards were removed. They were snapshots of a laminated page, not scans, and read as low quality next to the food photography. **Note: these are still live on the production site.**

---

## Working notes

- Rob's primary machine is an Ubuntu PC. He also works from Android/Termux.
- Repo lives on GitHub; site deploys to Netlify.
- Build is plain static HTML/CSS/vanilla JS. No framework, no build step. Keep it that way unless the client needs a CMS or real backend ordering.
- Image paths are relative (`images/food/...`), so HTML files must sit at the project root beside `index.html`.
- New photography was expected but hadn't arrived as of the last session.
