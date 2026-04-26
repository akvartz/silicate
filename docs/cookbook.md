# Cookbook

silicate ships no layout primitives, no utility classes, and no
components. When you need a real-world pattern, use raw HTML and a
handful of CSS lines scoped to your project. These recipes show how —
and stay honest to the philosophy.

Each recipe is the smallest amount of code that does the job.

## Wider page for one-off pages

Don't fight the measure globally. Override per-page:

```css
:root { --silicate-measure: 56rem; }
```

## Two-column reading layout

For sidebars, asides, or two-up cards:

```css
main {
  display: grid;
  grid-template-columns: minmax(0, 1fr) 14rem;
  gap: var(--silicate-space-6);
  max-width: 56rem;
}

@media (max-width: 40rem) {
  main { grid-template-columns: 1fr; }
}
```

```html
<main>
  <article>...</article>
  <aside>...</aside>
</main>
```

## Top navigation

```css
body > header nav ul {
  display: flex;
  gap: var(--silicate-space-4);
  padding: 0;
  list-style: none;
}
```

```html
<header>
  <h1>Title</h1>
  <nav>
    <ul>
      <li><a href="/">Home</a></li>
      <li><a href="/docs">Docs</a></li>
      <li><a href="/about">About</a></li>
    </ul>
  </nav>
</header>
```

## Card-like grouping

Use `<article>`. Add a thin border and padding only when the visual
grouping carries meaning the content alone wouldn't.

```css
article.surface {
  padding: var(--silicate-space-4);
  border: 1px solid var(--silicate-rule);
  border-radius: 4px;
  background: var(--silicate-surface);
}
```

```html
<article class="surface">
  <h3>Quartz</h3>
  <p>SiO₂. Hardness 7.</p>
</article>
```

A class is acceptable here because "this article is visually grouped"
isn't something HTML expresses on its own.

## Inline notice / callout

Use `<aside>` with a role:

```css
aside[role="note"] {
  padding: var(--silicate-space-3) var(--silicate-space-4);
  border-left: 3px solid var(--silicate-accent);
  background: var(--silicate-surface);
  margin-bottom: var(--silicate-space-4);
}
```

```html
<aside role="note">
  <strong>Note.</strong> The measure caps at 38rem by default.
</aside>
```

## Buttons that aren't primary

silicate's default `<button>` is filled. For a secondary action, drop
the fill:

```css
button.ghost {
  background: transparent;
  color: var(--silicate-fg);
}
```

Reserve a class for intent that markup can't carry. Don't add
`.btn-large`, `.btn-rounded`, etc. — they're decoration without
meaning.

## Print stylesheet additions

silicate already ships a basic print block. Extend it for your project:

```css
@media print {
  nav, footer, .no-print { display: none; }
  article { break-inside: avoid; }
}
```

## Brand retheme

Change identity in five lines:

```css
:root {
  --silicate-font-sans: "Inter", system-ui, sans-serif;
  --silicate-accent: #c2410c;
  --silicate-measure: 42rem;
}

@media (prefers-color-scheme: dark) {
  :root { --silicate-accent: #fb923c; }
}
```

That's the whole theming story.

## When to add a new class

Ask, in order:

1. Is there an HTML element that already says this? Use it.
2. Can a token override at `:root` solve it? Do that.
3. Does the class name describe **intent**, not appearance? (`role="note"`,
   `.surface`, `.ghost` — yes. `.text-blue-500`, `.mt-4` — no.)

If you reach step 3 and the answer is yes, the class earns its keep.
