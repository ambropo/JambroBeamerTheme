# Jambro Beamer theme
Ambrogio Cesa-Bianchi's theme for Beamer.

Jambro is a simple Beamer theme. It allows to comment on text and figures using handwritten-like text, using Tikz, e.g.:

![alt text](https://github.com/ambropo/JambroBeamerTheme/graphics/scrteenshot.jpg?raw=true)

To use the theme, simply download the .sty file to the folder containing your presentation. Then load the theme using \usetheme{jambro} in the preamble of your Beamer document.

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
