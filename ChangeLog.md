# Changelog

All notable changes to this project will be documented in this file.

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
