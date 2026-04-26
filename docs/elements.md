# Elements

silicate styles HTML elements, not classes. This is the working reference:
what each element does, what it looks like, and what tag to reach for when
you'd otherwise type `<div>`.

For the visual version, open `index.html`.

## Sectioning

Use real landmarks. Browsers, screen readers, and reader modes all rely
on them.

| Tag         | Use it for                                                  |
| ----------- | ----------------------------------------------------------- |
| `<header>`  | Page or section header. Holds the title block.              |
| `<main>`    | The single primary content region of the document.          |
| `<footer>`  | Page or section footer. Meta, links, copyright.             |
| `<article>` | A self-contained piece (post, comment, card-like unit).     |
| `<section>` | A thematic grouping with its own heading.                   |
| `<nav>`     | A primary set of navigation links.                          |
| `<aside>`   | Tangential content (sidenote, callout).                     |

silicate doesn't decorate these. They flow as block elements with the
default body measure. Reach for them anyway — meaning matters more than
paint.

## Headings

`<h1>`–`<h6>` are sized on a flat, readable scale (2rem → 1rem) with
tighter leading (1.25) than body. `<h5>` and `<h6>` go muted because
they're for shoulder text, not display.

Rules of thumb:

- One `<h1>` per page or per `<article>`.
- Don't skip levels for visual reasons. If you want a smaller display
  heading, override `font-size` inline; don't reach for `<h3>` to fake it.

## Text and inline

| Tag           | Behavior                                                  |
| ------------- | --------------------------------------------------------- |
| `<p>`         | Body block, default measure, default leading.             |
| `<a>`         | Underlined, accent color, visited color, focus ring.      |
| `<strong>`    | Semantic emphasis. Weight 600.                            |
| `<em>`        | Stress emphasis. Italic.                                  |
| `<small>`     | 0.875em, muted color. For fine print.                     |
| `<mark>`      | Highlight using the selection token.                      |
| `<abbr>`      | Dotted underline; needs a `title`.                        |
| `<kbd>`       | Mono, surface background, slight bottom-edge weight.      |
| `<code>`      | Inline mono with surface background.                      |
| `<samp>`      | Same treatment as `<code>`.                               |

Don't use `<b>` or `<i>` for emphasis — pick `<strong>` or `<em>` so the
meaning carries.

## Lists

`<ul>` and `<ol>` indent by `--silicate-space-5`. Nested lists indent
again, and adjacent items get `--silicate-space-2` of breathing room.
`<dl>` is the right tag for term/definition pairs (glossaries,
metadata) — silicate makes `<dt>` bold and gives `<dd>` block flow.

## Block

| Tag            | Behavior                                                       |
| -------------- | -------------------------------------------------------------- |
| `<pre>`        | Mono block, surface background, horizontal scroll on overflow. |
| `<blockquote>` | Left rule, muted text, internal padding. No quotation marks.   |
| `<figure>`     | A bundled image + caption block. Stays within the measure.     |
| `<figcaption>` | Muted, smaller, sits beneath the figure content.               |
| `<hr>`         | Hairline using `--silicate-rule`. No fancy shapes.             |
| `<details>`    | Bordered disclosure block. `<summary>` is the trigger.         |

## Tables

`<table>` claims full container width with bottom-border rows. Use
`<caption>` (it sits above the table, italic, muted) and proper
`<thead>` / `<tbody>` so screen readers and printers do the right thing.

silicate intentionally does not zebra-stripe. If you need it, add it
yourself in your project's CSS — it's a content decision, not a system
default.

## Forms

silicate styles every common form control:

- `<fieldset>` + `<legend>` group related inputs. Use them — they're
  free structure for assistive tech.
- `<label>` is block-level and bold; pair every input with one.
- `<input>`, `<select>`, `<textarea>` fill their container, take inherited
  font, and share a focus ring.
- `<button>` is filled (foreground on background). It's the only element
  in the system with a strong color block — use it sparingly.

For checkboxes and radios, wrap the label around the input so the click
target stays generous.

## Media

Images, video, and inline SVG are capped at 100% of their container with
auto height. Wrap meaningful images in `<figure>` so captions ride along.
Decorative images should set `alt=""` (silicate doesn't enforce it; you
should).

## What we don't ship

- No `.btn`, `.card`, `.alert`, `.badge`. Use the right tag.
- No grid system. Use `display: grid` where you need it.
- No icons. Bring your own.
- No JavaScript components. Behavior is yours to write.
