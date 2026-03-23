# Changelog

All notable changes to this project will be documented in this file.

## 2026-03-23 — Drop `\ACB` in favor of `\memo`

### Changed
- `beamerthemejambro.sty`: Draft annotations now use `\memo[ user=..., color=... ]{...}` as the only public note command; the option list and inline documentation now describe `hidememo` only.
- `Demo.tex`: Replaced the old `\ACB{...}` example with `\memo{...}`, added a document-level `\renewcommand{\memouser}{ACB}` preamble example, and kept the per-note `user=` / `color=` override example on the “Handwriting and personal notes” slide.
- `beamerthemejambro.sty`: Added a proper package preamble with `\NeedsTeXFormat` / `\ProvidesPackage`, tightened comments around Beamer/soul/natbib internal patches, and rewrote several public-API comments so they explain intent and usage rather than restating the code.
- `beamerthemejambro.sty`: Synced stale inline documentation with live behavior, including the `light` option description, `\marker` behaviour, `\lapisnote` default `yshift`, and the `\memo` documentation block.
- `Demo.tex`: Synced the “Theme's options” slide with the live API by renaming `handout` to `handout2x1`, fixing the `red` / `night` relationship text, and listing `wiggle=<n>` plus `hidememo`.

### Removed
- `beamerthemejambro.sty`: Removed the deprecated `\ACB{text}` compatibility command.
- `beamerthemejambro.sty`: Removed the deprecated `hideACB` option alias.
- `beamerthemejambro.sty`: Removed unused or stale internals, including the unused `tikzmark` library, the dormant `chalky` style, the stale global `pencilboxstyle`, the global `\notesize` alias, and the `\vfuzz` / `\hfuzz` warning suppression.

### Fixed
- `beamerthemejambro.sty`: Footline boxes now use `\paperwidth` instead of slightly oversized widths, removing the repeated theme-caused overfull-box warnings that had previously been hidden by fuzz suppression.

### BREAKING
- Existing slides must rename `\ACB{...}` to `\memo{...}` and `hideACB` to `hidememo`.

## Version 1.3 — *2026-03-23*

### Added
- **`\lapisboxeq[color=...,label=...]{equation}`**: New command — pencil-style box for use directly in math mode (no `$...$` needed). Wraps content in `$\displaystyle...$` internally. Supports the same `color` and `label` options as `\lapisbox` (named nodes registered with `remember picture` for cross-frame arrow targeting).
- **`\handbold[weight]{text}`**: Bold handwriting using Augie font with PDF stroke-width literal. Optional weight argument (default `0.6`); higher values give heavier strokes.
- **`\ACB{text}`**: Inline author note in BoEred, Augie font, footnotesize with underlined prefix. Intended for draft annotations.
- **`hideACB` option**: When passed to `\documentclass` or `\usetheme`, `\ACB{}` expands to nothing, suppressing all author notes for clean output.
- **`wiggle=<n>` option**: Sets the amplitude of the pencil/sketch decoration globally (default `0.8`). Accepted in both `\documentclass[wiggle=n]{beamer}` and `\usetheme[wiggle=n]{jambro}`.
- **Demo slides**: Added "Handwriting and personal notes", "Symbols and utilities", "Pencil wiggle amplitude", and "Inline pencil arrows" slides in `Demo.tex`.

### Changed
- **`wiggle=` now controls amplitude** (was: segment length). Segment length remains fixed at `1.2pt`. Amplitude default is `0.8pt`. **BREAKING** if existing slides relied on `wiggle=` tuning segment length — recheck and rescale values.
- **Internal macro renamed**: `\jambrowiggleseg` → `\jambrowiggleamp` to reflect the new semantics. Any direct use of `\jambrowiggleseg` in user documents will break.
- **`\ProcessOptions` → `\ProcessOptions*`**: Theme now picks up global document class options (e.g. `wiggle=`, `hideACB`, `itemsep`) without needing them in `\usetheme[...]`.
- **`Demo.tex` note blocks**: All empty `\shownotesblock{\n\n}` collapsed to `\shownotesblock{}`.

### Fixed
- **`\lapisboxeq` catcode crash**: Previous implementation stored `\lapisbox@color` (contains `@`) inside a `\tikzset` style, which caused PGF math to retokenise it in document context → "Undefined control sequence `\jambro`" + memory overflow. Fixed by `\edef`-expanding the color to a plain string before `\tikz` is entered.
- **`wiggle=` option had no effect**: `\ProcessOptions` (no star) does not forward undeclared global class options to `\DeclareOption*`. Fixed by switching to `\ProcessOptions*`.
- **`\lapisboxeq` ignored `label=` option**: Node was always named `X` with no `remember picture`, so labeled nodes were never registered for cross-frame arrow targeting. Now mirrors `\lapisbox` label handling exactly.

## Version 1.2 — *2025-06*

### Added
- **New Options**:
  - `itemsep`: Enables generous vertical spacing between itemize items (14pt at level 1, 5pt at level 2). Without this option, standard Beamer itemize spacing is used.

- **New Commands**:
  - `\marker{nodename}{text}`: Creates invisible anchor points for TikZ arrow targeting.
  - `\lapisbox[color=...,label=...]{text}`: Draws a pencil-style box around text; supports color and label options for arrow targeting.
  - `\lapisnote[options]{node}{text}`: Flexible annotation command with automatic arrow direction; options include `from`, `to`, `xshift`, `yshift`, `color`, `bend`, `width`.
  - `\jverb{...}`: Inline verbatim text (detokenized).
  - `\jVerb` environment: Verbatim block with reduced font size.
  - `\jcode{...}`: Inline code with yellow highlight box (tcolorbox-based).
  - `\jCode{...}`: Code block in yellow bubble for longer snippets.
  - `\vs{n}`: Shortcut for `\vspace{0.ncm}`.

- **New TikZ Styles**:
  - `chalky`: Extra hand-drawn variation with more wobble.
  - `pencilboxstyle`: Box style with pencil effect for `\lapisbox`.

- **New Colors**:
  - `BoEblue`, `BoEred`, `mint`, `tomatobalt`, `tomatodache`, `cobalt_light`, `blue_light`.

- **New Packages**:
  - `tcolorbox` for `\jcode` boxes.
  - `etoolbox` for list manipulation.
  - `xparse` for advanced command definitions (when `itemsep` enabled).

### Changed
- **Option renamed**: `handout` → `handout2x1` for clarity.
- **Table of Contents styling**: Now uses `\lapis` underline effect instead of tabular layout.
- **Footline**: Added `\hypersetup` to force white link colors inside footline.
- **`\lapis` command**: Improved horizontal spacing (`-0.025cm` instead of `-0.05cm`).
- **`\cmark` / `\xmark`**: Now include colors (`tomato` / `cobalt`).
- **TikZ pencil style**: Adjusted parameters (`line width=0.05cm`, `segment length=1.2pt`, `amplitude=0.8pt`).
- **Natbib**: Fixed citation parenthesis colors via `\NAT@open` / `\NAT@close` redefinitions.
- **File header**: Added comprehensive documentation block with usage and options list.
- **Code organization**: Restructured into clearly labeled sections with consistent commenting style.

### Removed
- `xframe` environment (use `\begin{frame}[fragile]` directly).
- `\code` command (replaced by `\jcode`).
- `lstset` default configuration.
- `presetkeys{todonotes}{inline}{}` default.

---

## Version 1.2.2 — *2026-02-11*

### Added
- `handout2x1` now explicitly activates Beamer `handout` mode.
- Shorthand arrow aliases: `\jarrowu`, `\jarrowd`, `\jarrowr`, `\jarrowl`.
- Demo slide: “Model Details — Firms” frame in `Demo.tex`.

### Changed
- Itemize equation spacing: zero `\belowdisplayskip` / `\belowdisplayshortskip` when `itemsep` is enabled.
- Itemize line-skip behavior now uses `\lineskiplimit=-5pt` to avoid excessive glue while keeping tall math legible.
- `\lapis` underline now anchors to the text baseline (`base west/east`) for more consistent placement.

---

## Version 1.2.1 — *2026-02*

### Added
- `tcolorbox` libraries `breakable` and `skins` to support code block styling.

### Changed
- `\jCode{...}` now uses a `tcolorbox` block instead of `todonotes` to avoid list/item overlap in Beamer.

---

## Version 1.1 — *2022-04-30*

### Added
- **New Commands**:
  - `\lapis[color]{text}`: Underlines text using TikZ in the specified color. Defaults to *baseline gold* if no color is provided.
  - `\stabilo[color]{text}`: Highlights text using TikZ in the specified color. Defaults to *baseline gold* if no color is provided.

- **New Options**:
  - `shownotes`: Compiles detailed speaker notes alongside slides — useful for rehearsals or presentation printouts.
  - `handout`: Produces handouts with a 2×1 slide-per-page layout (portrait orientation). Can be combined with `shownotes` for annotated handouts.

### Changed
- The `\hlight` command for text highlighting has been replaced by `\stabilo`.

---

## Version 1.0 — *2022-11-15*

### Added
- Initial release of the Jambro Beamer Theme.
