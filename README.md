# Silicate Design System

> A well-set book page, not a landing page.

Silicate is a brutally minimal, content-first design system. It is **one
stylesheet that styles raw HTML elements** — no frameworks, no classes,
no build step. The browser's defaults are 90% right; we fix line length,
leading, and contrast and stop.

If HTML has a tag for it (`<button>`, `<article>`, `<details>`,
`<figure>`), you use the tag. You do not wrap it in a `<div class="card">`.

## Sources

- **Repo:** [`akvartz/silicate`](https://github.com/akvartz/silicate) — at
  the time of writing, the public repo contains only a placeholder README.
  This system was built from the brief; if a richer source appears later,
  reconcile against it.
- **Brief:** "Brutally minimal, content-first, content-only. Visually:
  generous whitespace, a single readable column (~70 characters wide),
  system fonts, one accent color for links and focus, hairline rules
  instead of boxes, no shadows, no gradients, no rounded-corner-everything.
  Light and dark mode swap automatically with the OS."

## What's in this folder

- `silicate.css` — the whole design system. Drop this into a page and
  silicate is on. All styling targets bare HTML elements; there are no
  utility classes.
- `colors_and_type.css` — the **token layer** alone. Use when you want
  Silicate's variables without the element styles (e.g. inside another
  app's component code).
- `assets/` — logos and brand marks.
- `preview/` — small HTML cards used to populate the Design System tab.
  Each isolates one concept (color scale, type specimen, button states).
- `ui_kits/article/` — the canonical surface: a long-form article. The
  `index.html` is what a typical Silicate page looks like in production.
- `SKILL.md` — Agent Skills manifest, so this folder works as a
  drop-in skill in Claude Code.

## Quick start

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>An essay</title>
  <link rel="stylesheet" href="silicate.css">
</head>
<body>
  <main>
    <article>
      <header>
        <time datetime="2026-04-25">April 25, 2026</time>
        <h1>An essay</h1>
      </header>
      <p>Write words. Don't reach for a class.</p>
    </article>
  </main>
</body>
</html>
```

That is the entire integration. Do not add classes; add semantics.

## Retheming

Every design value is a `--silicate-*` variable. To retheme: override at
`:root`. Five lines is enough.

```css
:root {
  --silicate-font-body: "EB Garamond", Georgia, serif;
  --silicate-accent: #458588;   /* gruvbox blue, e.g. */
  --silicate-bg: #f9f5d7;       /* gruvbox bg0_h */
  --silicate-fg: #3c3836;
  --silicate-measure: 38rem;
}
```

---

## CONTENT FUNDAMENTALS

**The vibe.** Closer to a Knuth paper than a Stripe homepage. The user's
eye should land on the words, not the chrome. Write as if you respect
your reader's time and intelligence.

**Voice.** Plain, declarative, slightly wry. Short sentences are a
feature, not a target. Avoid marketing throat-clearing ("we're excited
to announce"). Avoid hedging ("might possibly help you maybe"). State
the thing.

- Yes: "Silicate styles raw HTML. There are no classes."
- No:  "Silicate empowers teams to ship beautifully crafted, accessible
  experiences with a delightful authoring DX."

**Person.** Second-person ("you") for instructions. First-person plural
("we") only when talking about silicate-the-project's choices. Never the
royal corporate "we" pretending to be your friend.

**Casing.** Sentence case for headings. Title Case for proper nouns
only. No ALL CAPS except for `<h5>` eyebrow labels (where it's a typographic
device, not a tonal one). No "Capitalized Marketing Phrases."

**Punctuation.** Em-dashes are fine. Oxford comma. One space after
periods. Periods inside quotes when American. Numbers under ten written
out, except in technical contexts (`70 characters`, `1px`, `18px`).

**Emoji.** No. Silicate uses none. If you need a glyph, prefer a real
typographic mark — `§`, `¶`, `→`, `—`, `·`, `†`. The accent color and a
hairline rule do more work than 🎉 ever will.

**Length.** Short. Cut the introduction; start with the verb. Section
headings should be nouns or imperative verbs, not questions ("Pricing,"
"Install Silicate," not "How does pricing work?").

**Examples of in-system copy:**

> Drop one stylesheet in. There are no classes.

> If HTML has a tag for it, use the tag.

> Override `--silicate-accent` to retheme.

> Light and dark swap with the OS. You don't need a toggle.

---

## VISUAL FOUNDATIONS

### Color

The palette is **gruvbox** — Pavel Pertsev's retro-warm scheme, ported to
a reading surface. **Light** is gruvbox cream (`#fbf1c7`, bg0) against
deep brown (`#3c3836`); **dark** is the canonical gruvbox dark
(`#282828`, bg0) against fg1 cream (`#ebdbb2`). The cream + brown pair
is warmer than off-white + black and reads like an old Linux console
or a well-worn paperback.

The single accent is **gruvbox orange** — faded (`#af3a03`) in light,
bright (`#fe8019`) in dark — used for **links, focus rings, and the
filled `submit` button.** That is its whole job. Do not introduce a
second accent. Other gruvbox hues (yellow, green, red) appear only in
the rarely-used `--silicate-mark`, `--silicate-success`, and
`--silicate-danger` tokens.

Semantic colors (`success`, `warning`, `danger`) exist in the token file
but are used **rarely** — Silicate prefers prose ("This will delete the
record permanently. Type the project name to confirm.") to a red banner.

Imagery, when present, leans warm and matte. No saturated stock photography,
no neon, no duotone. B&W or sepia archival imagery is on-brand.

### Type

System serif by default — `Iowan Old Style`, falling back through
`Palatino`, `Book Antiqua`, `Georgia`, `Times`. The point is that the
reader's machine almost certainly already has a good book serif
installed; we use it. No webfont round-trip, no FOUT.

- **Body:** 18px serif at 1.55 line-height — calibrated against the
  34rem (~70ch) measure.
- **Headings:** Same family as body, 600 weight, tighter leading (1.2).
  No display face. The same letterforms throughout the page.
- **Mono:** `ui-monospace` → `SF Mono` → `Menlo` → `Consolas`.
- **Sans:** kept in the token file for UI surfaces (forms, buttons in
  app contexts) but **not** the default body. The default is serif.

### Spacing

A 7-step scale: `4px → 8px → 16px → 24px → 32px → 48px → 80px`. Use
`--silicate-space-*`. Headings get larger top margins (space-6) than
bottom margins (space-3) — the "looser above, tighter below" rule.

### Layout

**One column. ~70 characters wide.** That is the design. Everything in
`<body>` is centered with `max-width: var(--silicate-measure)`. To
escape the column for a wide image or pull-quote, use
`<figure data-bleed>` — a deliberate, semantic escape hatch. There is no
grid system. There are no sidebars. If you need sidebars, you are
building something Silicate is not for.

### Backgrounds

The page background is a flat warm tone. **No gradients, no images, no
textures, no patterns.** The only "texture" the page has is the type.
Code blocks and `<kbd>` get a subtly warmer tint (`--silicate-bg-sunken`
/ `--silicate-code-bg`) — the same hue as the page, two steps darker.

### Borders & rules

**Hairlines, not boxes.** 1px borders in `--silicate-rule`, used for:
horizontal `<hr>`, table row dividers, `<details>` separators,
`<blockquote>` left rule, form field underlines, `<fieldset>` top rule,
button outlines. No card-style 1px borders on all four sides. No
rounded corners — `border-radius: 0` everywhere, including buttons and
inputs. Form inputs are bare with a single bottom rule.

### Shadows

**None.** Anywhere. Not on cards, not on dropdowns, not on hovered
buttons. Elevation is communicated by hairlines, whitespace, and order
on the page.

### Corner radii

`0` everywhere. Sharp corners are a feature.

### Cards

There are none. If you find yourself needing a card, you are wrapping an
`<article>`, a `<figure>`, or a `<details>` — use the element.
Whitespace and a top hairline give it the structure it needs.

### Hover states

- **Links:** underline thickens from 1px to 2px. Color does not change.
- **Outlined buttons:** invert — fg becomes bg, bg becomes fg. No
  transition delay.
- **Filled (submit) buttons:** bg goes from accent to fg.

### Press / active states

Browser default. We do not animate a "shrink" or color flash. The
state change on hover does the work.

### Focus

A single 2px outline ring in `--silicate-accent`, offset 2px. Same
treatment everywhere — links, buttons, inputs. Inputs additionally
thicken their bottom rule on focus.

### Animation

**Effectively none.** No fades, no slides, no bounces, no parallax. The
only transitions are browser defaults on hover (instantaneous) and
`<details>` expanding (browser default). If you reach for a keyframe,
you are out of scope.

### Transparency & blur

None. Backgrounds are solid. There is no `backdrop-filter` anywhere.

### Iconography

Almost none. See ICONOGRAPHY below.

### Imagery

Plain `<img>` inside `<figure>`. No filters, no overlays, no rounded
corners, no fixed aspect ratio. `<figcaption>` carries the credit. Wide
images use `<figure data-bleed>`.

### Fixed elements

None. Silicate has no sticky header, no floating button, no toast
overlay, no fixed sidebar. The page is the document. If you scroll, the
chrome scrolls with you because there isn't any.

---

## ICONOGRAPHY

**Silicate's position on iconography is: don't.** Words are clearer than
icons; the system is built around prose. There is no built-in icon font,
no icon component, no SVG sprite shipped with the stylesheet.

When an icon is genuinely needed (for example, an external-link
indicator or a permalink anchor), use a **typographic mark**, not a
custom SVG:

| Need               | Use                       |
|--------------------|---------------------------|
| External link      | `↗`                        |
| Permalink anchor   | `§`                        |
| Footnote reference | `†`, `‡`                   |
| List bullet        | the browser default disc   |
| Dropdown indicator | `+` / `−` (used in `<details>`) |
| Section break      | `* * *` or `<hr>`          |
| Right arrow        | `→`                        |
| Em dash            | `—`                        |

**Emoji:** never. Silicate is a reading surface; emoji read as casual
chat decoration and break the typographic register.

**Logos / brand marks:** see `assets/`. The wordmark is set in the body
serif, weight 600, tracking tight. There is no logo lockup that depends
on a glyph beyond the wordmark.

**If you need a real icon set** (for an app surface built *on top* of
Silicate, not Silicate itself): substitute [Lucide](https://lucide.dev)
via CDN — its hairline 1.5px stroke and sharp join style match the
hairline rules in this system better than fill-style sets like
Material. **Flag the substitution in your handoff** — it is not part of
the canonical system.

---

## Index

| File                              | What's in it                                      |
|-----------------------------------|---------------------------------------------------|
| `silicate.css`                    | The whole stylesheet. The system.                 |
| `colors_and_type.css`             | Tokens only — variables, no element rules.        |
| `assets/wordmark.svg`             | Silicate wordmark (light + dark via currentColor).|
| `preview/*.html`                  | Design System tab cards.                          |
| `ui_kits/article/index.html`      | The canonical surface — a long-form article.      |
| `ui_kits/article/*.html`          | Component-level demonstrations.                   |
| `SKILL.md`                        | Agent Skills manifest.                            |

## Ground rules for designers using Silicate

1. **Use the tag.** If HTML has it, use it. No `<div class="card">`.
2. **No classes.** If you find yourself writing one, you are in the
   wrong system.
3. **No new colors.** The accent is the accent. If you need a second,
   you are designing something Silicate isn't for.
4. **No shadows, no radius, no gradients.** Ever.
5. **One column, ~70ch.** Escape with `<figure data-bleed>` only when
   the content genuinely demands it.
6. **Words over icons.** A label is clearer than a glyph.
7. **Sentence case.** No Title Case in headings.
8. **Light/dark with OS.** No toggle. The reader's machine knows.
