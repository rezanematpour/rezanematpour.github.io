---
title: Evolution
date: 2026-06-23 12:00:00 +0000
categories: [Quantum Computing]
tags: [quantum computing, hermitian, evolution]
math: true
---
> The evolution of a *closed* quantum system is described by a *unitary transformation*. That is, the state $\ket{\psi}$ of the system at time $t_1$ is related to the state $\ket{\psi'}$ of the system at time $t_2$ by a unitary operator $U$ which depends only on the times $t_1$ and $t_2$:
>
> $$
\ket{\psi'} = U \ket{\psi}
$$
{: .prompt-info }

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


>  The time evolution of the state of a closed quantum system is described by the Schrodinger equation,
> $$
> H\ket{\psi}=i\hbar \frac{d \ket{\psi}}{d t}
> $$ 
>  
>   - $\hbar$: Planck’s constant whose value must be experimentally determined. The exact value is not important to us. In practice, it is common to absorb the factor into $H$, effectively setting $= 1$. 
>   - $\mathcal{i}$: Imaginary number = $\sqrt{-1}$
>  - $H$ is a fixed Hermitian operator known as the *Hamiltonian* of the closed system.
{: .prompt-info }

If we know the *Hamiltonian* of a system, then (together with a knowledge of $\hbar$) we understand the system's dynamics completely. 

Quantum mechanics doesn't tell us the *Hamiltonian* of a system, it just tells: "Once you have $H$, here’s how the system evolves!"

A *Hamiltonian* is a [Hermitian]({% post_url 2026-06-23-hermitian %}) operator: 
-  It has **real eigenvalues** (these are the **possible energies** of the system).
- The corresponding **eigenvectors** (states $\ket{E}$) form an **orthonormal basis**.
-  So it has spectral decomposition: $H=\sum_EE\ket{E}\bra{E}$
	- where:
		- $E$: the **energy** of each state.
		- $\ket{E}$: corresponding **quantum state**.
- The **eigenstates** $\ket{E}$ of the Hamiltonian are called **stationary states** because when they evolve in time, they **only** change by a **phase factor**: $\ket{E}\longmapsto e^{-iEt/\hbar}\ket{E}$
	- This phase factor **does not** change the **probabilities** of measurement outcomes, so these states **don’t change their observable properties** over time—they’re "stationary."
- **Ground State**
	- The **lowest energy eigenvalue** is called the **ground state energy**.
	- The corresponding state is called the **ground state**.
	- All other states are **excited states** (higher energy).

 ## Connection between the Hamiltonian picture of dynamics, and the unitary operator picture
Schrodinger’s equation:
$$
\ket{\psi_{t_2}}=exp[\frac{-iH(t_2-t_1)}{\hbar}]\ket{\psi_{t_1}}=U(t_1,t_2)\ket{\psi_{t_1}}
$$
$$
U(t_1,t_2)\equiv e[\frac{-iH(t_2-t_1)}{\hbar}]
$$
$$
U=e^{-iH(t_2-t_1)}
$$

> Any unitary operator $U$ can be written as: $U=e^{(iK)}$ for some Hermitian operator $K$.
It means unitary evolution (like quantum gates in quantum computing) is equivalent to **continuous-time evolution** under some **Hamiltonian-like** operator $K$.
- In **discrete-time** (like in quantum circuits), we usually use **unitary gates**.
- In **continuous-time** (like natural evolution of atoms), we describe evolution via **Hamiltonians**.

> This bridge—between unitary gates (quantum computing) and time-dependent Hamiltonians (quantum physics)—is what makes quantum control possible!
{: .prompt-tip }

