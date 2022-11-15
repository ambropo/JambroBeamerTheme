# Jambro Beamer theme
Ambrogio Cesa-Bianchi's theme for Beamer. 

## Features

Jambro a relatively minimal theme with only an outline of presentation's sections in the footline. Its main feature is to allow annotation of text, figures, and tables using arrows (Tikz) and handwritten-like text (Augie):

<img width="370" alt="arrow" src="https://user-images.githubusercontent.com/45069084/201375060-75b98059-c461-4ab8-81b8-f39472bb8578.png"> <img width="370" alt="arrow" src="https://user-images.githubusercontent.com/45069084/201373761-2ae948e3-750d-4ba8-9326-b179e1d0fb0f.png"> 

The theme supports different colors (blue is default, red can be specified) and a night mode:

<img width="370" alt="red" src="https://user-images.githubusercontent.com/45069084/201955212-cbb5db2e-974f-449e-bb3a-572a63ec7755.png"> <img width="370" alt="night" src="https://user-images.githubusercontent.com/45069084/201954770-dbd3600a-cd50-4142-9fd3-34d1d059ad38.png">

## Installation

To use the theme, simply download the `beamerthemejambro.sty` to the folder containing your presentation. Then load the theme using `\usetheme{jambro}` in the preamble of your Beamer document.

## Manual and examples

A [slide deck](https://github.com/ambropo/JambroBeamerTheme/blob/main/Manual.pdf "Manual") (`Manual.pdf` and corresponding `Manual.tex` file) provides more information on the features of the theme and a series of examples.

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
    Hello, world!
  \end{frame}
\end{document}
```

## License
The theme is licensed under a GNU General Public License v3.0
