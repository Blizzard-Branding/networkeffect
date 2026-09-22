# Network Effect landing page

A single-file static landing page for **Network Effect**, a business
networking group in Sacramento. Registration runs through Eventbrite.

> Connect. Contribute. Grow.

Everything lives in [`index.html`](index.html): markup, styles, and script. No
build step, no dependencies. Open it in a browser, or drop it on any static
host.

## House style

No em dashes anywhere in the copy. Use a comma, a colon, or a full stop
instead. En dashes stay in numeric ranges (`11:45am – 1:30pm`).

## Run it locally

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

Opening the file directly with `file://` works too, though a local server is
closer to how it will behave in production.

## Deploy

Any static host will do: Netlify, Vercel, Cloudflare Pages, GitHub Pages, or
plain S3. Publish the repository root; `index.html` is the entry point.

## Registration

There is no form on this site. Both the nav button and every call to action
point at the Eventbrite listing:

```
https://www.eventbrite.com/e/network-effect-tickets-2002092173586
```

That means no endpoint to configure, no spam filtering to worry about, and no
attendee data held here. Eventbrite handles confirmations and reminders. If
you ever move to a different event, search `index.html` for `eventbrite.com`;
the URL appears in four places (hero, registration card, closing CTA, footer).

Prefer an in-page checkout? Eventbrite's embedded widget is a drop-in
replacement for the registration card.

## Before you go live

These are the placeholders left in the page. Each is marked with a `TODO`
comment in `index.html` at the spot it applies to.

| What | Where | Notes |
| --- | --- | --- |
| Meeting time | Throughout | Set to **Wednesdays, 11:45am – 1:30pm** per the charter. The flyer said 12 – 1:30pm with people arriving 15 minutes early; confirm the Eventbrite listing agrees. |
| Social share URL and image | `<meta property="og:*">` in `<head>` | Needs your real domain and a 1200×630 image. |
| Professions list | "Who it's for" section | Swap the placeholder tags for the trades actually represented in the room. |
| Cost | FAQ | Points at the Eventbrite listing. Add membership dues if they differ from the meeting ticket. |
| One-per-profession policy | FAQ | Replace with your actual rule. |
| Discord access for guests | FAQ | Confirm whether the invite is open to non-members. |

Nothing on the page invents a member count, a testimonial, or a price. If you
want social proof on there, add it once you have real quotes to use.

## Where the copy came from

**From the charter** (authoritative: edit the charter first, then here):

- Mission statement, in full
- The four "What we'll do together" commitments
- Meeting time: Wednesdays, 11:45am – 1:30pm, as a standing weekly commitment
- The attendance philosophy, including the deliberate departure from BNI's
  rules: no substitute-representative requirement, no annual cap on misses
- The Convener's standing menu of activities, in place of a fixed weekly format
- The DEIB+ "bridge, not a mirror" statement, in full

**From the flyer:**

- Tagline: *Connect. Contribute. Grow.*
- Positioning line: *A business networking group done differently.*
- **Where:** Sparkle Professional Cleaning, 5580 Power Inn Rd, Sacramento
- Discord: `discord.gg/FxANYmJ5nq`

**Draft copy written to fit the above.** Read it as a starting point and change
anything that misrepresents the group:

- The "Referrals are a by-product of trust, not a quota" heading and lede
- The one-line descriptions under each of the four commitments
- The four "How it works" steps
- The "Who it's for" section
- The FAQ answers

## Brand colors

The CSS custom properties on `:root` are named after the "Primary Colors"
board. Change them in one place and the whole page follows.

| Token | Value | Used for |
| --- | --- | --- |
| `--navy-900` | `#0E1324` | Page background, dark cards |
| `--navy-700` / `--navy-500` | `#1B2338` / `#3B4759` | Hero gradient |
| `--orange-300` / `--orange-600` | `#EFBE62` / `#DD6A13` | Primary buttons, mission card, accents |
| `--teal-500` / `--teal-600` / `--teal-900` | `#178C8C` / `#11787A` / `#0A3A54` | Accents, meeting details card |
| `--tan-300` / `--tan-600` / `--tan-800` | `#C09C64` / `#6B5828` / `#4C3F1C` | Icon accents, "On showing up" panel |
| `--peri-200` / `--peri-500` / `--peri-600` | `#BFCDE1` / `#9AA2C4` / `#6B709C` | Closing CTA, "On the meeting itself" panel, muted text |
| `--cream-200` / `--peach-400` | `#EFE8DC` / `#E9AF87` | Warm neutrals |
| `--green-400` / `--green-700` | `#9BE617` / `#17980E` | Growth accents, success states |
| `--white-50` / `--white-200` | `#FCFCF9` / `#EDEBDE` | Body text, light sections |

Values were sampled from the color board image, so nudge any that do not match
your source file exactly.

## Typography

- **Jost** for display and the wordmark, a geometric sans close to the flyer's
  lettering.
- **Inter** for body copy.

Both load from Google Fonts with `display=swap` and a system fallback. To
self-host, drop the font files in `assets/fonts/` and replace the `<link>` with
`@font-face` rules.

## Accessibility and performance

- Single HTML file, no third-party scripts beyond the font stylesheet.
- Skip link, visible focus rings, labelled form fields, and inline validation
  messages announced with `aria-live`.
- The animated hero network and all scroll reveals are disabled under
  `prefers-reduced-motion: reduce`.
- The hero canvas stops animating when the tab is hidden.
- Layout is fluid from 320px up; no horizontal scrolling.
- Every text-bearing gradient panel was checked against WCAG AA (4.5:1) at
  **both** ends of its gradient. Four failed on the first pass and the stops
  were adjusted, which is why `--tan-600`, `--peri-500`, and `--teal-600` exist
  alongside the board colors. If you retheme, re-check both ends of a gradient,
  not just the top.
