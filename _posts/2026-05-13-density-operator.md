---
title: "Quantum Measurement and Density Operators"
date: 2026-05-13 12:00:00 +0000
categories: [Quantum Computing, Measurement]
tags: [quantum, measurement, density-operator, mixed-states]
math: true
---

This note covers the density operator formalism, unitary evolution, and measurement in quantum mechanics - essential concepts for understanding quantum computing and measurement theory.

## 1. Defining an Ensemble and the Density Operator

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

## 2. Unitary Evolution in the Density-Matrix Picture

Suppose we have a closed quantum system and its evolution is described by the unitary operator $U$. 

If our initial state is $\ket{{\psi_{i}}}$ with probability $p_{i}$, then after evolution the system will be in state $U\ket{{\psi_{i}}}$ with probability $p_{i}$. The evolution of the density matrix $\rho$ is:

$$
U\rho = \sum_{i} p_{i}(U\ket{{\psi_{i}}})(\bra{{{\psi_{i}}}}U^{\dagger}) = U\bigg(\sum_{i}p_{i}\ket{{\psi_{i}}}\bra{\psi_{i}}\bigg)U^{\dagger} = U\rho U^{\dagger}.
$$

> Why $U\rho = \sum p U\ket{\psi}\bra{\psi}U^{\dagger}$?
> 
> $$
> \boxed{\begin{aligned}\ket{{\psi}}'&=U\ket{{\psi}}\\\bra{\psi}'&=(\ket{\psi}')^{\dagger}=\bra{\psi}U^{\dagger}\end{aligned}}
> $$
> 
> By definition, a closed-system unitary acts on any operator $P$ as $P \longmapsto U P U^{\dagger}$. Applied to the projector $P=\ket{{\psi}}\bra{\psi}$ gives $U\ket{{\psi}}\bra{\psi}U^{\dagger}=\ket{\psi}'\bra{\psi}'$.


## 3. Measurement in the Density Operator Language

Suppose we perform a measurement described by measurement operators $M_{m}$. If the initial state was $\ket{{\psi_{i}}}$, the probability of getting result $m$ is:

$$
p(m|i) = \braket{ \psi_{i}|M_{m}^{\dagger}M_{m} |\psi_{i}} = \mathrm{Tr}(M^{\dagger}_{m}M_{m}\ket{\psi_{i}}\bra{{\psi_{i}}}).
$$

By the law of total probability, the probability of obtaining result $m$ is:

$$
\begin{aligned}
p(m) &= \sum_{i} p(m|i)\cdot p_{i} \\
&= \sum_{i} \bigg(\mathrm{Tr}(M_{m}^{\dagger}M_{m}\ket{\psi_{i}}\bra{\psi_{i}})\bigg)\cdot p_{i} \\
&= \mathrm{Tr}\left( M^{\dagger}_{m}M_{m}\sum_{i}p_{i}\ket{\psi_{i}}\bra{\psi_{i}} \right) \\
&= \mathrm{Tr}(M^{\dagger}_{m}M_{m}\rho).
\end{aligned}
$$

If the initial state was $\ket{{\psi_{i}}}$, the state after obtaining result $m$ is:

$$
\ket{{\psi^m_{i}}} = \frac{M_{m}\ket{{\psi_{i}}}}{\sqrt{\braket{ \psi_{i}|M^{\dagger}_{m}M_{m}|\psi_{i}}}}.
$$

Thus, after a measurement yielding result $m$, we have an ensemble of states $\ket{\psi^{m}_{i}}$ with respective probabilities $p(i|m)$. The corresponding density operator $\rho_{m}$ is:

$$
\begin{aligned}
\rho_{m} &= \sum_{i} p({i|m})\ket{\psi_{i}^m}\bra{\psi_{i}^m} \\
&= \sum_{i} p(i|m)\cdot\frac{M_{m}\ket{{\psi_{i}}}\bra{\psi_{i}}M_{m}^{\dagger}}{\braket{ \psi_{i}|M^{\dagger}_{m}M_{m}|\psi_{i}}} \\
&\underrightarrow{p(i|m)=\frac{p(m,i)}{p(m)}=\frac{p(m|i)\cdot p_{i}}{p(m)}} \\
&= \sum_{i} p_{i}\cdot\frac{M_{m}\ket{{\psi_{i}}}\bra{\psi_{i}}M^{\dagger}_{m}}{\mathrm{Tr}(M^{\dagger}_{m}M_{m}\rho)} \\
&= \frac{M_{m}\rho M_{m}^{\dagger}}{\mathrm{Tr}(M^{\dagger}_{m}M_{m}\rho)}.
\end{aligned}
$$

> **Critical Distinction**
> 
> The post-measurement state for:
> - **Kets**: divide by $\sqrt{p(m)}$ for normalization: $\ket{\psi^m} = \frac{M_{m}\ket{{\psi}}}{\sqrt{p(m)}}$
> - **Density matrices**: no square root needed because the density operator normalization gives: 
> 
> $$
> \rho_{m} = \frac{M_{m}\rho M_{m}^{\dagger}}{p(m)}
> $$


## 4. Pure vs Mixed States

> If we know the exact state $\ket{{\psi}}$ of a quantum system, we say it is in a **pure state** and its density operator is $\rho = \ket{{\psi}}\bra{\psi}$. 
> 
> Otherwise, $\rho$ is in a **mixed state**; it is a mixture of the different pure states in the ensemble.
> 
> - Pure state satisfies $\mathrm{Tr}(\rho^2) = 1$
> - Mixed state satisfies $\mathrm{Tr}(\rho^2) < 1$
{: .prompt-info }

**Mixture of mixtures:** If a quantum system is prepared in state $\rho_{i}$ with probability $p_{i}$, the system may be described by the density matrix $\sum_{i}p_{i}\rho_{i}$.

Proof: Suppose $\rho_{i}$ arises from ensemble $\{p_{ij}, \ket{\psi_{ij}}\}$ of pure states ($i$ fixed). The probability of being in state $\ket{{\psi_{ij}}}$ is $p_{i}\cdot p_{ij}$. The density matrix is:

$$
\begin{aligned}
\rho &= \sum_{ij} p_{i}\cdot p_{ij}\ket{{\psi_{ij}}}\bra{\psi_{ij}} \\
&= \sum_{i} p_{i}\rho_{i},
\end{aligned}
$$

where $\rho_{i} = \sum_{j} p_{ij}\ket{\psi_{ij}}\bra{\psi_{ij}}$. We say $\rho$ is a **mixture** of states $\rho_{i}$ with probabilities $p_{i}$.

## 5. Intuitive Example: The Quantum Biased Coin

Suppose we have a quantum biased coin:
- Heads $(\ket{{\psi_{1}}} = \ket{{0}})$ with probability $0.4$
- Tails $\left( \ket{{\psi_{2}}} = \frac{{\ket{{0}}+\ket{1}}}{\sqrt{2}} \right)$ with probability $0.6$

We can describe this quantum system with ensemble $\{p_{i},\ket{\psi_{i}}\}$:

$$
\{(0.4,\ket{0}), (0.6,\frac{\ket{0}+\ket{1}}{\sqrt{2}})\}.
$$

We write the ensemble as the **density operator** $\rho$:

$$
\begin{aligned}
\rho &= \sum_{i} p_{i} \ket{\psi_{i}}\bra{\psi_{i}} \\
&= \left[0.4\ket{0}\bra{0}\right] + \left[0.6\frac{\ket{0}+\ket{1}}{\sqrt{2}}\frac{\bra{0}+\bra{1}}{\sqrt{2}}\right].
\end{aligned}
$$

### Density Matrix Properties: Positive and Trace = 1

#### Positivity
$\braket{ \phi|\rho |\phi  }$ is the probability the system described by $\rho$ is found in state $\ket{\phi}$.

- **For pure state** $\ket{{\psi}}$ with $\rho = \ket{{\psi}}\bra{\psi}$:

$$
\begin{aligned}
\braket{ \phi| \rho|\phi} &= \braket{ \phi |\psi  }\braket{ \psi | \phi } \\
&= (\braket{ \phi |\psi  })(\braket{ \phi |\psi  })^{\dagger} \\
&= |\braket{ \phi |\psi  }|^2 \geq 0.
\end{aligned}
$$

- **For mixed state** $\rho = \sum_{i}p_{i}\ket{\psi_{i}}\bra{\psi_{i}}$ with $p_{i} \geq 0$:

$$
\braket{ \phi |\rho|\phi} = \sum_{i} p_{i} |\braket{ \phi |\psi_{i} }|^2 \geq 0.
$$

Thus, **density matrices are positive operators**.

#### Trace = 1

- **Pure state**: $\mathrm{Tr}(\rho = \ket{\psi}\bra{\psi}) = \braket{ \psi | \psi } = 1$
- **Mixed state**: $\mathrm{Tr}(\rho) = \sum_{i} p_{i} \mathrm{Tr}(\ket{\psi_{i}}\bra{\psi_{i}}) = \sum_{i} p_{i} \cdot 1 = \sum_i p_i = 1$

> **Important:** The eigenvalues of $\rho$ are probabilities (they lie in $[0,1]$ and sum to $1$). The probability of measuring an outcome associated with projector $M$ is:
> 
> $$
> \boxed{0 \leq \mathrm{Tr}(M\rho) \leq 1}
> $$
> 
> - Pure states: $\rho^2 = \rho$ (idempotent, trace = 1)
> - Mixed states: $\rho^2 \neq \rho$ (trace still 1)
{: .prompt-warning }

## 6. Matrix Representation of States

We can represent any state in matrix form:

$$
\begin{aligned}
\ket{\psi} &= \ket{\psi}\bra{\psi} \\
\ket{0} &= \ket{0}\bra{0} = \begin{bmatrix}1 & 0 \\ 0 & 0\end{bmatrix}
\end{aligned}
$$

We can't show a mixed state with a single vector; we represent it with the density matrix:

$$
\rho = \sum_{i} p_{i} \ket{\psi_{i}}\bra{\psi_{i}}
$$

### Pure State Example

For $\ket{\psi} = \alpha\ket{0} + \beta\ket{1}$:

$$
\rho_{\psi} = 1 \times \ket{\psi}\bra{\psi} = \begin{pmatrix}\alpha \\ \beta\end{pmatrix} \begin{pmatrix}\alpha^{*} & \beta^{*}\end{pmatrix} = \begin{pmatrix}|\alpha|^2 & \alpha\beta^{*} \\ \beta\alpha^{*} & |\beta|^2\end{pmatrix}
$$

Note: $p_i = 1$ because it's a pure state with no classical probability.

The diagonal elements are probabilities: the first element gives $P(\ket{0})$, the second gives $P(\ket{1})$.

### Pure State: Equal Superposition

$$
\ket{\psi} = \frac{1}{\sqrt{2}}\ket{0} + \frac{1}{\sqrt{2}}\ket{1}, \quad
\rho_{\psi} = \begin{pmatrix}\frac{1}{\sqrt{2}} \\ \frac{1}{\sqrt{2}}\end{pmatrix} \begin{pmatrix}\frac{1}{\sqrt{2}} & \frac{1}{\sqrt{2}}\end{pmatrix} = \begin{pmatrix}\frac{1}{2} & \frac{1}{2} \\ \frac{1}{2} & \frac{1}{2}\end{pmatrix}
$$

### Mixed State Example: Random Electron Source

Suppose a machine randomly spits electrons: half the time it spits $\ket{0}$ and half the time $\ket{1}$.

$$
\begin{aligned}
\rho &= 0.5 \times \ket{0}\bra{0} + 0.5\ket{1}\bra{1} \\
&= 0.5 \times \begin{pmatrix}1 & 0 \\ 0 & 0\end{pmatrix} + 0.5 \times \begin{pmatrix}0 & 0 \\ 0 & 1\end{pmatrix} \\
&= \begin{pmatrix}0.5 & 0 \\ 0 & 0.5\end{pmatrix}
\end{aligned}
$$

> The off-diagonal elements of a mixed state density matrix are **zero**.
{: .prompt-tip }

## 7. Understanding Diagonal and Off-Diagonal Elements

For a pure state density matrix:

$$
\rho_{\psi} = \begin{pmatrix}a & b \\ c & d\end{pmatrix}
$$

- **Diagonal elements** ($a$, $d$): Probabilities of outcomes $\ket{0}$ and $\ket{1}$ respectively
- **Off-diagonal elements** ($b$, $c = b^{*}$): Represent **coherence**
    - If $b = 0$: The two states $\{\ket{0},\ket{1}\}$ are not connected; they exist independently
    - If $b \neq 0$: There is a connection/interference between states; this represents a single coherent quantum system, not separate classical probabilities

This is why mixed states have zero off-diagonal elements—there is no quantum coherence between the possibilities.

## 8. Pure vs Mixed: The "Homeless" Intuition

> A pure state always has a "home basis" where it feels certain. A mixed state is homeless—uncertain in all bases.
{: .prompt-info }

**Example:** $\ket{\psi} = \frac{1}{\sqrt{2}}(\ket{0} + \ket{1})$ is a pure state because:
- In $\{\ket{0}, \ket{1}\}$ basis: 50% $\ket{0}$, 50% $\ket{1}$ (looks mixed!)
- But in $\{\ket{+}, \ket{-}\}$ basis: 100% $\ket{+}$ (reveals its pure nature!)

A mixed state, however, will never show certainty in **any** basis. If you measure a mixed state in any basis, you will never get a definite outcome with probability 1.

## Summary: Evolution Operators

### Unitary Evolution

$$
\rho \longrightarrow U\rho U^{\dagger}
$$

### Measurement Postulate

**Probability of outcome $m$:**

$$
p(m) = \mathrm{Tr}(M_{m}^{\dagger}M_{m}\rho)
$$

**Post-measurement state:**

$$
\rho_{m} = \frac{M_{m}\rho M_{m}^{\dagger}}{\mathrm{Tr}(M_{m}^{\dagger}M_{m}\rho)}
$$

---

*This note covers the essential formalism of density operators, which is crucial for understanding quantum information, open quantum systems, and quantum measurement theory.*
