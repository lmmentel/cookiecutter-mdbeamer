---
title: {{ cookiecutter.title }}
{% if cookiecutter.subtitle %}subtitle: {{ cookiecutter.subtitle }}{% endif %}
author: {{ cookiecutter.author }}
{% if cookiecutter.affiliation %}institute: {{ cookiecutter.affiliation }}{% endif %}
fontsize: 10pt
date: {{ cookiecutter.date }}

theme: {{ cookiecutter.theme }}
{% if cookiecutter.theme == "metropolis" %}
themeoptions:
- titleformat=regular
- progressbar=foot
- block=transparent
- numbering=counter
{% endif %}
---

# Paragraphs

This is the first paragraph contents.


Second paragraph contents.


# Lists

Contains an unordered list of stuff

- normal item
- *italic item with a footnote*[^1]
- **bold item**
- \alert{alerted text}
- \textcolor{fgreen}{colored item}
- `verbatim`

. . .

Incrementally revealed numbered list:

> 1. one
> 2. two

[^1]: footnote text

# Theorem

## Theorem
Witches float on water


# Math

\begin{align}
\left(\beta mc^2 + c \left(\sum_{n=1}^{3}\alpha_{n}p_{n}\right)\right)\psi(x, t) = i\hbar\frac{\partial\psi(x, t)}{\partial t} \notag
\end{align}


# Table

| Tables   |      Are      |  Cool |
|----------|:-------------:|------:|
| col 1 is | left-aligned  | $1600 |
| col 2 is |   centered    |   $12 |
| col 3 is | right-aligned |    $1 |

# Image

![Latex logo](gfx/LaTeX.pdf)

# Code example {.fragile}

\begin{minted}{python}
import numpy as np
from scipy.optimize import minimize

def rosen(x):
    return sum(100.0 * (x[1:] - x[:-1]**2.0)**2.0 + (1 - x[:-1])**2.0)

x0 = np.array([1.3, 0.7, 0.8, 1.9, 1.2])
res = minimize(rosen, x0, method='Powell', jac=False)
print(res.x)
\end{minted}

---

\begin{center}
{\Titles\LARGE Thank you for attention!}
\end{center}
