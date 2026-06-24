---
title: Evolution
date: 2026-06-24 12:00:00 +0000
categories: [Quantum Computing]
tags: [quantum computing, qubit, superposition]
math: true
---

> The evolution of a *closed* quantum system is described by a *unitary transformation*. That is, the state $\ket{\psi}$ of the system at time $t_1$ is related to the state $\ket{\psi'}$ of the system at time $t_2$ by a unitary operator $U$ which depends only on the times $t_1$ and $t_2$,
$$
 \ket{\psi'} = U\ket{\psi}
$$
{: .prompt-info }

> **Closed System**:  A system that doesn't interact with any other systems.

Quantum mechanics doesn't tell us which unitary operators $U$ describe real-world quantum dynamics. It just assures us that the evolution of a closed system may be described in that way.  
Some $U$ examples:
$X$: bit-flip
	$Z$: phase-flip
	$Y$: i-flip
	Hadamard:  $$
  \begin{split} H=\frac{1}{\sqrt{2}}\begin{bmatrix} 1 & 1 \\ 1 & -1 \end{bmatrix}\\ \\ H\ket{0}=\frac{\ket{0}+\ket{1}}{\sqrt{2}}
	 \\ H\ket{1}=\frac{\ket{0}-\ket{1}}{\sqrt{2}}\\
	 \end{split}
   $$
