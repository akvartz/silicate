# Article — Silicate UI kit

The canonical Silicate surface: a reading page. There is exactly one
"product" Silicate is for, and this is it.

## Files

- `index.html` — the long-form article. Open this to see what a typical
  Silicate page looks like in production.
- `components.html` — every interactive primitive on one page.
- `form.html` — a focused contact form.

## How it's built

These pages import `../../silicate.css` and use **only** raw HTML
elements: `<article>`, `<header>`, `<h1>`–`<h3>`, `<p>`, `<ul>`,
`<blockquote>`, `<details>`, `<table>`, `<pre>`, `<form>`, `<button>`,
`<input>`, `<kbd>`, `<code>`, `<mark>`, `<abbr>`. There are no
component classes; there is no JavaScript framework. Three small
inline `<style>` blocks add page-specific layout for `<nav>` and the
section dividers — they do not introduce reusable classes.

## What's deliberately missing

No card components. No icon set. No animations. No loading skeletons.
No toasts. No sticky header. No theme toggle. Each of these is a "no"
the brief explicitly asks for.

## Reusing pieces

Because Silicate styles tags directly, "reusing a component" means
using the same tag. A new article gets a new `<article>`. A new
disclosure gets a new `<details>`. There are no JSX components to
import.
