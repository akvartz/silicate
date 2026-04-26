# silicate

A minimalist design system. One stylesheet. No classes. No build step.
Style raw HTML and let the content do the work.

> The browser already knows how to render text. We give it just enough help —
> readable measure, comfortable leading, honest contrast — and step out of the
> way.

## Lineage

silicate is the direct descendant of three short manifestos:

- [motherfuckingwebsite.com](https://motherfuckingwebsite.com/) — _the
  browser's defaults are already good._
- [bettermotherfuckingwebsite.com](http://bettermotherfuckingwebsite.com/) —
  _seven lines of CSS make them better._
- [thebestmotherfucking.website](https://thebestmotherfucking.website/) —
  _a little more, but not much._

silicate keeps the spirit and adds the bare minimum a real product needs:
a token system, dark mode, focus styles, and styled coverage of every
HTML element you'll actually use.

## Principles

1. **Content first.** Markup carries meaning; CSS only refines it.
2. **Style elements, not classes.** If a tag exists for the job, use it.
   No `.btn`, no `.card` — `<button>`, `<article>`.
3. **One file, no dependencies.** The whole system is `silicate.css`.
   Drop it in. Done.
4. **Tokens, not magic numbers.** Every value is a `--silicate-*` custom
   property. Override at `:root` to retheme.
5. **Light + dark, by default.** Honors `prefers-color-scheme`. The user
   wins, not us.
6. **Accessible by default.** Visible focus rings, real contrast, generous
   tap targets, semantic landmarks.
7. **Print is a first-class medium.** Pages reflow and ink stays cheap.
8. **No JavaScript.** The system is presentation; behavior is your
   business.

## Use it

```html
<link rel="stylesheet" href="silicate.css">
```

That's the whole API. Now write HTML.

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Hello</title>
  <link rel="stylesheet" href="silicate.css">
</head>
<body>
  <h1>Hello</h1>
  <p>This is already styled.</p>
</body>
</html>
```

Open `index.html` in this repo for the full living showcase.

## Tokens

All design decisions are exposed as CSS custom properties under the
`--silicate-*` namespace.

### Type

| Token                       | Default                          | Purpose                          |
| --------------------------- | -------------------------------- | -------------------------------- |
| `--silicate-font-sans`      | system UI sans stack             | Body and headings                |
| `--silicate-font-mono`      | system UI mono stack             | Code, kbd, samp                  |
| `--silicate-font-size`      | `1.125rem` (18px)                | Body size                        |
| `--silicate-line-height`    | `1.6`                            | Body leading                     |
| `--silicate-measure`        | `38rem` (~70 chars)              | Max line length                  |

### Space

A geometric scale (~1.5×) from `--silicate-space-1` (0.25rem) to
`--silicate-space-7` (3.5rem). Use `4` for default block flow, `5`/`6`
for section breathing room.

### Color

| Token                            | Light       | Dark       | Purpose                       |
| -------------------------------- | ----------- | ---------- | ----------------------------- |
| `--silicate-fg`                  | `#1a1a1a`   | `#e8e8e6`  | Body text                     |
| `--silicate-bg`                  | `#fafaf7`   | `#111`     | Page background               |
| `--silicate-muted`               | `#666`      | `#999`     | De-emphasized text            |
| `--silicate-rule`                | `#ddd`      | `#333`     | Borders, hairlines            |
| `--silicate-accent`              | `#0a66c2`   | `#6cb6ff`  | Links, focus rings            |
| `--silicate-accent-visited`      | `#6b3fa0`   | `#c9a3ff`  | Visited links                 |
| `--silicate-surface`             | `#f0f0eb`   | `#1c1c1c`  | Code blocks, kbd backgrounds  |
| `--silicate-selection`           | `#ffec99`   | `#5a4d1f`  | Text selection, marks         |

## Retheming

Override tokens at `:root` (or any scope). No build, no plugin.

```css
:root {
  --silicate-measure: 42rem;
  --silicate-accent: #c2410c;
  --silicate-font-sans: "Inter", system-ui, sans-serif;
}
```

Want a brand palette? Set `--silicate-fg`, `--silicate-bg`, and
`--silicate-accent` in both light and dark blocks. That's it.

## Element coverage

silicate styles the elements you actually ship:

- Sectioning: `body`, `header`, `main`, `footer`, `article`, `section`
- Headings: `h1`–`h6`
- Text: `p`, `a`, `strong`, `em`, `small`, `mark`, `abbr`, `kbd`, `code`
- Lists: `ul`, `ol`, `dl`, `dt`, `dd`
- Block: `pre`, `blockquote`, `figure`, `figcaption`, `hr`
- Tables: `table`, `caption`, `thead`, `tbody`, `tr`, `th`, `td`
- Forms: `form`, `fieldset`, `legend`, `label`, `input`, `select`,
  `textarea`, `button`
- Disclosure: `details`, `summary`
- Media: `img`, `video`, `svg`, `picture`

If you reach for a `<div class="…">`, ask first: is there a tag for this?

## What silicate does *not* include

By design:

- No grid system. Use CSS grid or flexbox where you need them.
- No utility classes. Add your own if your project warrants them.
- No icons, no JS components, no themes-as-a-package.
- No opinions about your build pipeline.

silicate is a foundation. Build on top of it; don't fight it.

## Project layout

```
silicate/
├── README.md       — you are here
├── silicate.css    — the design system, one file
└── index.html      — living showcase + style guide
```

## Status

Foundation. Tokens, base elements, light/dark, print. Enough to build a
real page today. More will land as we use it in anger.
