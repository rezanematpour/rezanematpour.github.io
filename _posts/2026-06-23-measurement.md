---
title: Quantum Measurement
date: 2026-06-07 12:00:00 +0000
categories: [Quantum Computing]
tags: [quantum, quantum-computing, measurement, povm]
math: true
toc: true
comments: true
---

## Quantum Measurement: The Operator Formalism

> Quantum measurements are described by a collection of measurement operators $\{M_m\}$. Each operator corresponds to a possible outcome $m$ of the measurement.
>
> If the system is in state $\ket{\psi}$ before measurement, then:
>
> - Probability of outcome $m$:
> $$
> p(m) = \bra{\psi} M_m^\dagger M_m \ket{\psi}
> $$
>
> - Post-measurement state:
> $$
> \ket{\psi_m} = \frac{M_m \ket{\psi}}{\sqrt{\bra{\psi} M_m^\dagger M_m \ket{\psi}}}
> $$
>
> The operators satisfy the completeness relation:
> $$
> \sum_m M_m^\dagger M_m = I
> $$
{: .prompt-info }

---

## Key Idea

A quantum measurement is not just a “readout” — it is a transformation of the state.

Each outcome:
- occurs probabilistically
- updates the state of the system
- is represented by a linear operator

---

## Probability Rule

Given a quantum state $\ket{\psi}$:

$$
p(m) = \bra{\psi} M_m^\dagger M_m \ket{\psi}
$$

Define:

$$
E_m = M_m^\dagger M_m
$$

Then:
- $E_m \ge 0$ (positive semidefinite)
- $\sum_m E_m = I$

So probabilities are:

$$
p(m) = \bra{\psi} E_m \ket{\psi}
$$

This is the POVM formulation of measurement.

---

## State Update Rule

If outcome $m$ occurs, the state collapses to:

$$
\ket{\psi} \rightarrow \ket{\psi_m}
= \frac{M_m \ket{\psi}}{\sqrt{p(m)}}
$$

This ensures normalization:

$$
\lVert \ket{\psi_m} \rVert = 1
$$

---

## Projective Measurement (Special Case)

If measurement operators are projectors:

$$
M_m = P_m, \quad P_m^2 = P_m, \quad P_m^\dagger = P_m
$$

Then:

$$
p(m) = \bra{\psi} P_m \ket{\psi}
$$

and

$$
\ket{\psi_m} = \frac{P_m \ket{\psi}}{\sqrt{p(m)}}
$$

---

## Example: Measuring a Qubit

Consider measurement in the computational basis:

$$
M_0 = \ket{0}\bra{0}, \quad M_1 = \ket{1}\bra{1}
$$

### Completeness check:

$$
M_0 + M_1 =
\ket{0}\bra{0} + \ket{1}\bra{1} = I
$$

### State:

$$
\ket{\psi} = \alpha \ket{0} + \beta \ket{1}
$$

### Probabilities:

$$
p(0) = |\alpha|^2, \quad p(1) = |\beta|^2
$$

### Post-measurement states:

- If outcome 0:
$$
\ket{\psi_0} = \ket{0}
$$

- If outcome 1:
$$
\ket{\psi_1} = \ket{1}
$$

---

## Cascade Measurements

Suppose we perform two measurements in sequence:

- First: $\{L_l\}$
- Then: $\{M_m\}$

We define a single combined measurement:

$$
N_{lm} = M_m L_l
$$

---

### Joint Probability

First measurement:

$$
p(l) = \bra{\psi} L_l^\dagger L_l \ket{\psi}
$$

Second measurement:

$$
p(m|l) =
\frac{\bra{\psi} L_l^\dagger M_m^\dagger M_m L_l \ket{\psi}}
{\bra{\psi} L_l^\dagger L_l \ket{\psi}}
$$

Joint probability:

$$
p(l,m)
= \bra{\psi} L_l^\dagger M_m^\dagger M_m L_l \ket{\psi}
= \bra{\psi} N_{lm}^\dagger N_{lm} \ket{\psi}
$$

---

### Post-Measurement State

The final state after outcomes $(l,m)$ is:

$$
\ket{\psi_{lm}} =
\frac{M_m L_l \ket{\psi}}{\sqrt{\bra{\psi} N_{lm}^\dagger N_{lm} \ket{\psi}}}
$$

---

### Completeness

We verify:

$$
\sum_{l,m} N_{lm}^\dagger N_{lm} = I
$$

Proof:

$$
\begin{aligned}
\sum_{l,m} N_{lm}^\dagger N_{lm}
&= \sum_{l,m} L_l^\dagger M_m^\dagger M_m L_l \\
&= \sum_l L_l^\dagger \left(\sum_m M_m^\dagger M_m\right) L_l \\
&= \sum_l L_l^\dagger I L_l \\
&= \sum_l L_l^\dagger L_l \\
&= I
\end{aligned}
$$

---

## Why $M_m^\dagger M_m$ is Always Valid

For any measurement operator $M_m$:

$$
M_m^\dagger M_m \ge 0
$$

And:

$$
\langle \psi | M_m^\dagger M_m | \psi \rangle
= \| M_m \ket{\psi} \|^2 \ge 0
$$

Thus:
- probabilities are always non-negative
- expectation values are real
- normalization is guaranteed

---

## Summary

- Measurement operators define both outcomes and state updates
- Probabilities are given by:
  $$
  p(m) = \bra{\psi} M_m^\dagger M_m \ket{\psi}
  $$
- State collapse is:
  $$
  \ket{\psi} \rightarrow \frac{M_m \ket{\psi}}{\sqrt{p(m)}}
  $$
- Sequential measurements are composed via:
  $$
  N_{lm} = M_m L_l
  $$

Quantum measurement is therefore a **linear, probabilistic state transformation described fully by operator algebra.**
