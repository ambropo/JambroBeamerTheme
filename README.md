# Jambro Beamer Theme

Ambrogio Cesa-Bianchi's theme for **academic and policy-oriented Beamer presentations**: a clean, minimalist layout with a subtle color palette, modern typography, and a spacious design. It adds TikZ-based annotation tools — sketched arrows and handwritten-style fonts — plus pencil-style highlighting, underlining, and boxing.

A fully worked feature showcase is in **[`Demo.tex`](Demo.tex)** — see the rendered **[`Demo.pdf`](Demo.pdf)**.

> Status: `v1.3-dev`. Backwards-compatible within the 1.x line; changes are recorded in [`ChangeLog.md`](ChangeLog.md).

<img width="370" alt="arrow" src="https://user-images.githubusercontent.com/45069084/201375060-75b98059-c461-4ab8-81b8-f39472bb8578.png"> <img width="370" alt="arrow" src="https://user-images.githubusercontent.com/45069084/201373761-2ae948e3-750d-4ba8-9326-b179e1d0fb0f.png"> 
<img width="370" alt="red" src="https://user-images.githubusercontent.com/45069084/201955212-cbb5db2e-974f-449e-bb3a-572a63ec7755.png"> <img width="370" alt="night" src="https://user-images.githubusercontent.com/45069084/201954770-dbd3600a-cd50-4142-9fd3-34d1d059ad38.png">

---

## Features

Jambro is a custom Beamer theme designed with a strong focus on clarity and readability. It features a clean, minimalist layout, a subtle and professional color palette, modern typography, and a spacious design that makes it especially well suited for academic and policy-oriented presentations.

Its main features include annotation tools for text, figures, and tables using TikZ-based arrows and handwritten-style fonts (e.g., Augie), as well as highlighting, underlining, and boxing elements with pencil-like effects. The theme supports different colors (blue is default, red can be specified), a night mode, different fonts, and a handout mode with notes.

---

## Getting Started

To use the theme, simply download `beamerthemejambro.sty` to the folder containing your presentation (or install it in your local TeX tree). Then load the theme using `\usetheme{jambro}` in the preamble of your Beamer document.

The theme loads its own dependencies (fonts, TikZ, tcolorbox, tabularx, and the Augie handwriting font); a recent TeX Live (2022 or newer) is recommended. Features that draw arrows to named nodes need **two compiler passes** to resolve. Compile with `latexmk -pdf Demo.tex`.

---

## Package options

Theme options are passed as class options to `\documentclass[…]{beamer}`:

| Option | Effect |
| --- | --- |
| `red` | Red color scheme (default is blue). |
| `night` | Dark-mode color scheme (overrides `red`). |
| `light` | Fira Sans Light body font (default is Fira Sans Book). |
| `cabin` | Switch to the Cabin font family. |
| `roboto` | Switch to the Roboto font family. |
| `3to2` | 3:2 aspect ratio (default is 16:9). |
| `itemsep` | Generous itemize spacing (default is standard Beamer spacing). |
| `onesec` | Show only the current section in the footline. |
| `centertitle` | Center frame titles. |
| `shownotes` | Display speaker notes alongside slides. |
| `handout2x1` | 2×1 handout layout for printing. |
| `wiggle=<n>` | Amplitude (pt) of the pencil/sketch effect (default `0.4`; larger = more expressive). |
| `hidememo` | Suppress every `\memo{…}` for a clean final build. |

```latex
\documentclass[red,light,itemsep]{beamer}
\usetheme{jambro}
```

---

## Public API

### Typography & fonts
| Command | Usage |
| --- | --- |
| `\hand` | Switch to the Augie handwriting font; use inside a group: `{\hand …}`. |
| `\handbold[<stroke>]{text}` | Bold handwriting; optional stroke width (default `0.6`). |

### Pencil marks & arrows
| Command | Usage |
| --- | --- |
| `\lapis[<color>]{text}` | Hand-drawn underline (default color `carandache` gold). |
| `\lapisbox[color=<c>,label=<id>]{text}` | Inline pencil box; `label=` names a TikZ node for arrow targeting. |
| `\lapisboxeq[color=<c>,label=<id>]{a=b}` | Pencil box around an equation. |
| `\jarrowu` `\jarrowd` `\jarrowl` `\jarrowr` | Inline sketched arrows (up/down/left/right). Options: `color=`, `len=`, `lw=`, `pad=`. |
| `\marker{name}{text}` | Wrap visible text in a named node; a later `tikzpicture[tpstyle]` draws an arrow to it. |
| `\lapisnote[<options>]{node}{text}` | One-step shortcut to attach a handwritten note to a named `node` via an arrow (options: `color=`, `xshift=`, `yshift=`, `from=`, `to=`, `bend=`, `width=`). |
| `\stabilo[<color>]{text}` | Highlighter-style marking (default yellow). |

### Notes & annotations
| Command | Usage |
| --- | --- |
| `\NB[<width>]{text}` | Note call-out; optional width (default full width). |
| `\memo[user=<u>,color=<c>]{text}` | Draft annotation; defaults via `\memouser` / `\memocolor`; hidden by the `hidememo` option. |
| `\shownotesblock{text}`, `\shownotesblockzero{text}` | Speaker-notes blocks (shown in `shownotes` mode; `…zero` targets the title slide). |

### Math, tables & code
| Command | Usage |
| --- | --- |
| `\EE[…]` | Expectation operator. |
| `Y` / `S` columns + `\tablesize` | Auto-width `tabularx` columns; `\tablesize` for compact table text. |
| `\sym{***}` | Significance stars (rendered, but kept machine-readable). |
| `\jverb{…}`, `jVerb` (env) | Inline / block verbatim. |
| `\jcode{…}`, `\jCode{…}` | Inline / multi-line code (non-verbatim). |
| `\citej{ref}` | Citation typeset in the theme's main color. |
| `\vs{<n>}` | `\vspace` shortcut in tenths of a cm. |
| `changemargin` (env) | Temporarily change the left/right margins. |
| `\cmark` / `\xmark` | Check / cross marks. |

---

## Colors

Defined centrally and reusable anywhere a color is accepted:

- **Base palette:** `main`, `title`, `text`, `note`, `light`, `tomato`, `cobalt`, `carandache` / `gold`, `green`, `purple`, `maroon`, `brick`, `mint`, `bubble`.
- **Highlights:** `hlight`, `hlightYellow`, `hlightPurple` (used by `\stabilo`).
- **BoE palette:** `BoEblue`, `BoEacqua`, `BoEorange`, `BoEpurple`, `BoEgold`, `BoEgray`, `BoEred`.

The `red` and `night` options remap the base palette.

---

## Manual and examples

A [slide deck](https://github.com/ambropo/JambroBeamerTheme/blob/main/Demo.pdf "Demo") (`Demo.pdf` and the corresponding `Demo.tex`) provides more information on the features of the theme and a series of examples.

The following code shows a minimal example of a Beamer presentation using jambro.

```latex
\documentclass{beamer}
\usetheme{jambro}
\title{A minimal example}
\date{\today}
\author{Ambrogio Cesa-Bianchi}
\begin{document}
  \maketitle
  \begin{frame}{Example}
    This is a frame using Jambro
  \end{frame}
\end{document}
```

---

## License

The theme is licensed under a GNU General Public License v3.0.

---

## Changelog

See [`ChangeLog.md`](ChangeLog.md).
