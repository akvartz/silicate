---
name: silicate-design
description: Use this skill to generate well-branded interfaces and assets for Silicate, either for production or throwaway prototypes/mocks/etc. Contains essential design guidelines, colors, type, fonts, assets, and UI kit components for prototyping.
user-invocable: true
---

Read the README.md file within this skill, and explore the other available files.

If creating visual artifacts (slides, mocks, throwaway prototypes, etc), copy assets out and create static HTML files for the user to view. If working on production code, you can copy assets and read the rules here to become an expert in designing with this brand.

If the user invokes this skill without any other guidance, ask them what they want to build or design, ask some questions, and act as an expert designer who outputs HTML artifacts _or_ production code, depending on the need.

## Quick map

- `silicate.css` — drop-in stylesheet. The whole system.
- `colors_and_type.css` — token layer only.
- `assets/wordmark.svg` — wordmark, uses `currentColor`.
- `ui_kits/article/index.html` — the canonical surface to mimic.
- `preview/*.html` — small specimens of every concept.

## Non-negotiables

- Style raw HTML. No utility classes, no `<div class="card">`.
- One readable column, ~70 characters wide (`--silicate-measure`).
- One accent color (`--silicate-accent`). Don't introduce a second.
- No shadows. No rounded corners. No gradients. No emoji.
- Light/dark via `prefers-color-scheme`. No theme toggle.
- Body type is a system serif, 18px, 1.55 line-height.
- Iconography is typographic (`↗ § † → · —`). If you need a real icon
  set, substitute Lucide via CDN and flag the substitution.

## Retheming

Override `--silicate-*` tokens at `:root`. Five lines is enough to
retheme; if you need more, you are working against the system.
