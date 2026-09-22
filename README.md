# Network Effect — landing page

A single-file static landing page for **Network Effect**, a business
networking group in Sacramento.

> Connect. Contribute. Grow.

Everything lives in [`index.html`](index.html): markup, styles, and script. No
build step, no dependencies. Open it in a browser, or drop it on any static
host.

## Run it locally

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

Opening the file directly with `file://` works too, though a local server is
closer to how it will behave in production.

## Deploy

Any static host will do — Netlify, Vercel, Cloudflare Pages, GitHub Pages, or
plain S3. Publish the repository root; `index.html` is the entry point.

## Before you go live

These are the placeholders left in the page. Each is marked with a `TODO`
comment in `index.html` at the spot it applies to.

| What | Where | Notes |
| --- | --- | --- |
| Application form endpoint | `CONFIG.formEndpoint` in the `<script>` | Point it at Formspree, Basin, Getform, Netlify Forms, or a Google Apps Script web app. |
| Fallback contact email | `CONFIG.contactEmail` in the `<script>` | Used only when `formEndpoint` is blank — the form then opens the visitor's mail client instead. If both are blank the form tells people to use Discord. |
| Social share URL and image | `<meta property="og:*">` in `<head>` | Needs your real domain and a 1200×630 image. |
| Professions list | "Who it's for" section | Swap the placeholder tags for the trades actually represented in the room. |
| Membership cost | FAQ | Currently answered as "get in touch" — replace with your real dues. |
| One-per-profession policy | FAQ | Replace with your actual rule. |
| Discord access for guests | FAQ | Confirm whether the invite is open to non-members. |

Nothing on the page invents a member count, a testimonial, or a price. If you
want social proof on there, add it once you have real quotes to use.

## Content that came from the brand assets

Taken verbatim from the Network Effect flyer, so it should match your other
material:

- Tagline: *Connect. Contribute. Grow.*
- Positioning line: *A business networking group done differently.*
- Mission paragraph (the "We exist to build a trusted circle…" copy)
- **When:** Wednesdays, 12 – 1:30pm; people arrive 15 minutes early to socialise
- **Where:** Sparkle Professional Cleaning, 5580 Power Inn Rd, Sacramento
- Discord: `discord.gg/FxANYmJ5nq`

Everything else — the pillars, the four steps, the FAQ — is new copy written to
fit that positioning. Read it as a draft and change anything that misrepresents
how the group actually runs.

## Brand colors

The CSS custom properties on `:root` are named after the "Primary Colors"
board. Change them in one place and the whole page follows.

| Token | Value | Used for |
| --- | --- | --- |
| `--navy-900` | `#0E1324` | Page background, dark cards |
| `--navy-700` / `--navy-500` | `#1B2338` / `#3B4759` | Hero gradient |
| `--orange-300` / `--orange-600` | `#EFBE62` / `#DD6A13` | Primary buttons, mission card, accents |
| `--teal-500` / `--teal-900` | `#178C8C` / `#0A3A54` | Meeting details card |
| `--tan-300` / `--tan-800` | `#C09C64` / `#4C3F1C` | Icon accents |
| `--peri-200` / `--peri-600` | `#BFCDE1` / `#6B709C` | Closing CTA card, muted text |
| `--cream-200` / `--peach-400` | `#EFE8DC` / `#E9AF87` | Warm neutrals |
| `--green-400` / `--green-700` | `#9BE617` / `#17980E` | Growth accents, success states |
| `--white-50` / `--white-200` | `#FCFCF9` / `#EDEBDE` | Body text, light sections |

Values were sampled from the color board image, so nudge any that do not match
your source file exactly.

## Typography

- **Jost** for display and the wordmark — a geometric sans close to the flyer's
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
