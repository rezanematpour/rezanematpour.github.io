---
title: Evolution
date: 2026-06-23 12:00:00 +0000
categories: [Quantum Computing]
tags: [quantum computing, qubit, superposition]
math: true
---


Closed System
: A system that doesn't interact with any other systems.

Quantum mechanics doesn't tell us which unitary operators $U$ describe real-world quantum dynamics. It just assures us that the evolution of a closed system can be described in that way.

Some examples of $U$:

- $X$: bit-flip  
- $Z$: phase-flip  
- $Y$: i-flip  
- Hadamard gate:

$$
H = \frac{1}{\sqrt{2}}
\begin{bmatrix}
1 & 1 \\
1 & -1
\end{bmatrix}
$$

and its action:

$$
H\ket{0} = \frac{\ket{0} + \ket{1}}{\sqrt{2}}, \quad
H\ket{1} = \frac{\ket{0} - \ket{1}}{\sqrt{2}}
$$
