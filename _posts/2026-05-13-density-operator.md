---
title: "Quantum Measurement and Density Operators"
date: 2026-05-13 12:00:00 +0000
categories: [Quantum Computing, Measurement]
tags: [quantum, measurement, density-operator, mixed-states]
math: true
---

This note covers the density operator formalism, unitary evolution, and measurement in quantum mechanics - essential concepts for understanding quantum computing and measurement theory.

 1. Defining an Ensemble and the Density Operator{: .mt-4 .mb-0 }

- **Ensemble of pure states** $\{(p_{1},\psi_{1}),\cdots ,(p_{n},\psi_{n})\}$ 
    - Suppose a quantum system is prepared in one of the (normalized) pure states $\{\ket{{\psi_{i}}}\}$, each occurring with classical probability $p_{i}$​. We call the collection $\{p_{i},\ket{{\psi_{i}}}\}$ an **ensemble**.
- **Density operator** $\rho$
    - We package the ensemble into the single operator:

$$
\rho=\sum_{i}p_{i}\ket{\psi_{i}}\bra{\psi_{i}}.
$$

- **Properties** 
    $\rho$ is:
    1. **Positive:** $\braket{ \phi|\rho |\phi  }\geq{0}\ \text{for all}\ \ket{\phi}.$
    2. **Unit trace:** $\mathrm{Tr}(\rho)=\sum_{i}p_{i}=1$ 

These match exactly the requirements for a probability **density** over quantum states.

