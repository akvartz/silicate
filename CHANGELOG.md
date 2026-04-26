# Changelog

## Unreleased

### Changed — design system handoff from Claude Design

Replaced the early foundation with the canonical Silicate Design System
bundle (claude.ai/design). The system is now driven by a written brief
plus iteration captured in the design tool, not by my initial sketch.

**Visual identity**

- **Palette: gruvbox.** Light is gruvbox cream (`#fbf1c7` bg / `#3c3836`
  fg); dark is gruvbox dark (`#282828` bg / `#ebdbb2` fg). One accent —
  faded gruvbox orange (`#af3a03` light, `#fe8019` dark) — for links,
  focus rings, and the filled `submit` button.
- **Body type: system serif.** Iowan Old Style → Palatino → Book Antiqua
  → Georgia → Times. No webfont round-trip. 18px / 1.55 leading.
- **Measure: 34rem** (~70 characters at 18px serif).
- **Spacing: 7-step scale** — `4 / 8 / 16 / 24 / 32 / 48 / 80 px`.
- Hairlines instead of boxes. No shadows. No rounded corners. No
  gradients. No emoji.

**Files added**

- `silicate.css` — replaced. The whole system, ~360 lines.
- `colors_and_type.css` — token layer alone, for use inside other apps.
- `SKILL.md` — Agent Skills manifest for Claude Code.
- `assets/wordmark.svg` — wordmark, uses `currentColor`.
- `preview/` — 21 specimen cards (color, type, spacing, components).
- `preview/index.html` — gallery index linking each card.
- `ui_kits/article/` — the canonical surface: long-form article,
  components page, contact form.
- `index.html` — replaced. Top-level landing page that links to the
  article surface, the preview gallery, and the docs.
- `README.md` — replaced with the bundle's project README (principles,
  content fundamentals, visual foundations, iconography, ground rules).

**Files removed**

- `docs/elements.md` — superseded by the new README's *Visual
  foundations* section.
- `docs/cookbook.md` — earlier recipes (two-column, card-with-radius,
  ghost button) contradicted the new system's ground rules. The article
  surfaces and the README replace them.

**Open iteration items from the design transcript**

The design session ended mid-edit. Two items were not fully reconciled
between the previews and the canonical `silicate.css`:

1. **Form input borders.** The `preview/forms.html` card uses 1px
   borders on all four sides (per the user's explicit ask in the
   transcript). The canonical `silicate.css` still uses bottom-rule-only
   inputs. Confirm whether the four-side treatment should land in the
   system stylesheet too.
2. **Submit button hover swap.** The transcript ends mid-edit on
   "swap hover color with default" for `<button type="submit">`. The
   bundled `silicate.css` already lands in the correct end state
   (default = filled `fg`, hover = filled `accent`); no further change
   needed unless the user reads it differently.

## 0.0.1 — initial sketch (superseded)

- Token-driven single-file stylesheet sketched against the brief.
- Light + dark via `prefers-color-scheme`. Sans-serif body. Off-white +
  ink palette. Element coverage and showcase.
- Companion `docs/elements.md` and `docs/cookbook.md` (both removed in
  the handoff above).
