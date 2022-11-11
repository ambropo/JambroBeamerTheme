# Jambro Beamer theme
Ambrogio Cesa-Bianchi's theme for Beamer. Its main feature is to allow to comment on text, figures and tables using Tikz and handwritten-like text, e.g.:

<img width="420" alt="Screenshot2" src="https://user-images.githubusercontent.com/45069084/201375060-75b98059-c461-4ab8-81b8-f39472bb8578.png"> <img width="420" alt="screenshot1" src="https://user-images.githubusercontent.com/45069084/201373761-2ae948e3-750d-4ba8-9326-b179e1d0fb0f.png"> 

## Installation

To use the theme, simply download the `beamerthemejambro.sty' to the folder containing your presentation. Then load the theme using `\usetheme{jambro}` in the preamble of your Beamer document.

## Manual and examples

The file `Manual.pdf' (and corresponding .tex file) provides more information on the features of the theme and a series of examples.

The following code shows a minimal example of a Beamer presentation using Metropolis.

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

License
The theme is licensed under a GNU General Public License v3.0
