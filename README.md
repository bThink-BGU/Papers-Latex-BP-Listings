# BP listings

[![GitHub license](https://img.shields.io/badge/license-LLPL--1.3c-blue)](https://github.com/bThink-BGU/Papers-Latex-BP-Listings/blob/master/LICENSE)
![GitHub release](https://img.shields.io/github/release/bThink-BGU/Papers-Latex-BP-Listings)

This is a LaTeX package for adding BP languages and styles to the listings package.

Current release includes BPjs and BPPy.

This project is licensed under the LaTeX Project Public License v1.3c or later, see http://www.latex-project.org/lppl.txt

## 1. Behaviroal Programming (BP)
Behavioral Programming (BP) is a novel, language-independent paradigm for programming reactive systems, centered on natural and incremental specification of behavior.

For more information visit [here](https://m-cacm.acm.org/magazines/2012/7/151241-behavioral-programming/fulltext).

[BPjs](https://github.com/bThink-BGU/BPjs) is an environment for running behavioral programs written in Javascript.

## 2. Installation
Add the [bp-listings.sty](bp-listings.sty) file to your Latex project.

In [Overleaf](https://www.overleaf.com/) this can be done by:
1. Adding a new file to the repository.
1. Selecting "From External URL".
1. In the first textbox write https://raw.githubusercontent.com/bThink-BGU/Papers-Latex-BP-Listings/master/bp-listings.sty
1. Press "Create".

## 3. Usage
### 3.1. Loading the package
Load the package with 
```latex
\usepackage{bp-listings}
```
Do not load the listings package, bp-listings will do that for you.

### 3.2. Package options
#### 3.2.1. nobpjs
If you do not wish to load the BPjs language, you can use the *nobpjs* flag:
```latex
\usepackage[nobpjs]{bp-listings}
```

#### 3.2.2. nobppy
If you do not wish to load the BPPy language, you can use the *nobppy* flag:
```latex
\usepackage[nobppy]{bp-listings}
```

#### 3.2.3. babel
The *listings* package is incompatibile with the *babel* package when writing right-to-left languages.
If you get some strange behaviors and you use babel - try loading the bp-listings package with the *babel* option:
```latex
\usepackage[babel]{bp-listings}
```
If you still have problems - double check that you do not load the *listings* package in your code.

For more information regarding the bug and the solution, see [here](https://tex.stackexchange.com/questions/454720/babel-with-hebrew-and-listings-conflicts-makes-the-listings-look-weird).

## 4. Usage Examples
The hot-cold example.
### 4.1. BPjs
```latex
\documentclass{standalone}
\usepackage{bp-listings}

\begin{document}
	
\begin{lstlisting}[
  style=BPjs
]
bp.registerBThread("Add Hot Three Times", function() {
  bp.sync({request: bp.Event("hot")});
  bp.sync({request: bp.Event("hot")});
  bp.sync({request: bp.Event("hot")});
});


bp.registerBThread("Add Cold Three Times", function() {
  bp.sync({ request: bp.Event("cold") });
  bp.sync({ request: bp.Event("cold") });
  bp.sync({ request: bp.Event("cold") });
});

bp.registerBThread("Interleave", function() {
  while(true) {
    bp.sync({ waitFor: bp.Event("cold"), block: bp.Event("hot") });
    bp.sync({ waitFor: bp.Event("hot"), block: bp.Event("cold") });
  }
});
\end{lstlisting}
	
\end{document}
```

### 4.2. BPPy
```latex
\documentclass{standalone}
\usepackage{bp-listings}

\begin{document}
	
\begin{lstlisting}[
  style=BPPy
]
def add_cold_three_times():
  yield { request: cold }
  yield { request: cold }
  yield { request: cold }
  
def add_hot_three_times():
  yield { request: hot }
  yield { request: hot }
  yield { request: hot }
  
def interleave():
  while True:
    yield { waitFor: cold, block: hot }
    yield { waitFor: hot, block: cold }
\end{lstlisting}
	
\end{document}
```
