# Jambro Beamer theme
Ambrogio Cesa-Bianchi's theme for Beamer. This version: 1.1

## Features

Jambro is a custom Beamer theme designed with a strong focus on clarity and readability. It features a clean, minimalist layout, a subtle and professional color palette, modern typography, and a spacious design that makes it especially well suited for academic and policy-oriented presentations.

Its main features include annotation tools for text, figures, and tables using TikZ-based arrows and handwritten-style fonts (e.g., Augie), as well as highlighting, underlining, and boxing elements with pencil-like effects. The theme supports different colors (blue is default, red can be specified), a night mode, different fonts, and a handout mode with notes.

<img width="370" alt="arrow" src="https://user-images.githubusercontent.com/45069084/201375060-75b98059-c461-4ab8-81b8-f39472bb8578.png"> <img width="370" alt="arrow" src="https://user-images.githubusercontent.com/45069084/201373761-2ae948e3-750d-4ba8-9326-b179e1d0fb0f.png"> 
<img width="370" alt="red" src="https://user-images.githubusercontent.com/45069084/201955212-cbb5db2e-974f-449e-bb3a-572a63ec7755.png"> <img width="370" alt="night" src="https://user-images.githubusercontent.com/45069084/201954770-dbd3600a-cd50-4142-9fd3-34d1d059ad38.png">

## Getting Started

To use the theme, simply download the `beamerthemejambro.sty` to the folder containing your presentation (or install it in your local TeX tree). Then load the theme using `\usetheme{jambro}` in the preamble of your Beamer document.

## Manual and examples

A [slide deck](https://github.com/ambropo/JambroBeamerTheme/blob/main/Demo.pdf "Demo") (`Demo.pdf` and corresponding `Demo.tex` file) provides more information on the features of the theme and a series of examples.

The following code shows a minimal example of a Beamer presentation using jambro.

```
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

## License
The theme is licensed under a GNU General Public License v3.0
