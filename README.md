# Jambro Beamer theme
Ambrogio Cesa-Bianchi's theme for Beamer.

Jambro is a simple Beamer theme. It allows to comment on text and figures using handwritten-like text, using Tikz, e.g.:

<img width="764" alt="screenshot" src="https://user-images.githubusercontent.com/45069084/201373761-2ae948e3-750d-4ba8-9326-b179e1d0fb0f.png">

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
