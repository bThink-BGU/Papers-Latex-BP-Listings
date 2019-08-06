# BP listings

This is a LaTeX package for adding BP languages and styles to the listings package.

Current release includes BPjs and BPPy.

This project is licensed under the LaTeX Project Public License v1.3c or later, see http://www.latex-project.org/lppl.txt

## BP
Behavioral Programming (BP) is a novel, language-independent paradigm for programming reactive systems, centered on natural and incremental specification of behavior.

For more information visit [here](https://m-cacm.acm.org/magazines/2012/7/151241-behavioral-programming/fulltext).

[BPjs](https://github.com/bThink-BGU/BPjs) is an environment for running behavioral programs written in Javascript.

## Usage

A short example to demonstrate the use of the TikZducks:
```latex
\documentclass{standalone}
\usepackage{bp-listings}

\begin{document}
	
\begin{lstlisting}[
  style=BPjs
]
\end{lstlisting}
	
\end{document}
```

```latex
\documentclass{standalone}
\usepackage{bp-listings}

\begin{document}
	
\begin{lstlisting}[
  style=BPPy
]
\end{lstlisting}
	
\end{document}
```
