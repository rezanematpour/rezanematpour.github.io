---
title: Quantum Measurement
date: 2026-05-10 12:00:00 +0000
categories: [Quantum Computing, Measurement]
tags: [quantum, measurement, qubit]
math: true
---
Quantum mechanics is a mathematical framework for the development of physical theories.
Quantum mechanics doesn't give us the *state space* or *state vector* of the physical system. It just tells us how states evolve and how measurements happen **if** we have the *initial state* and *state space* of the system. 

# Simplest Quantum Mechanical System: Qubit
A Qubit has two dimensional state space $$ \mathbb{C}^2 $$ with orthonormal basis $$ \ket{0}, \ket{1} $$. 
An arbitrary state vector in state space can be created by the linear combination of$$ \ket{0},\ket{1} $$with complex$$ \alpha,\beta $$: 

$$
\ket{\psi}=\alpha\ket{0}+\beta\ket{1}
$$

**Normalization Condition:** $$ \ket{\psi} $$should be a unit vector ($$ \braket{\psi|\psi}=1 $$), so that 

$$
(\| \ket{\psi}\|=1)=(\sqrt{|\alpha|^2+|\beta|^2}=1)=(\sqrt{|\alpha|^2+|\beta|^2}^2=1^2)=|\alpha|^2+|\beta|^2=1
$$.


# Superposition 
Any linear combination$$ \sum_i\alpha_i\ket{\psi_i} $$is a superposition of the states$$ \ket{\psi_i} $$with *amplitude*$$ \alpha_i $$for the state$$ \ket{\psi_i} $$.
	Example: 
  
  $$
  \frac{\ket{0}-\ket{1}}{\sqrt{2}}$ is a superposition of the states $\ket{0}$ and $\ket{1}$ with amplitudes $\alpha=\frac{1}{\sqrt{2}}$ and $\beta=-\frac{1}{\sqrt{2}}
  $$. 
