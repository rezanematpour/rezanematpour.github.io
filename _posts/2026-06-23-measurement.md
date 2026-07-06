---
title: Quantum Measurement
date: 2026-06-07 12:00:00 +0000
categories: [Quantum Computing]
tags: [quantum computing]
math: true
toc: true
comments: true
---

> Quantum measurements are described by a collection $\{M_m\}$ of *measurement operators*. These are operators acting on the state space of the system being measured. The index $m$ refers to the measurement outcomes that may occur in the experiment. If the state of the quantum system is $\ket{\psi}$ immediately before the measurement then the probability that result $m$ occurs is given by $p(m)=\bra{\psi}M^\dagger_mM_m\ket{\psi}$, and the state of the system after measurement is $\frac{M_m\ket{\psi}}{\sqrt{\bra{\psi}M^\dagger_mM_m\ket{\psi}}}$. 
> The measurement operators satisfy the *completeness equation*, $\sum_mM^\dagger_mM_m=I$.
> The completeness equation expresses the fact that probabilities sum to one: $1=\sum_mp(m)=\sum_m\bra{\psi}M^\dagger_mM_m\ket{\psi}$
{: .prompt-info }

**Explanation**
1. We have a quantum system in a pure state $\ket{\psi}$, and we perform a measurement that can have several possible outcomes, which we label by $m$. 
	1. We model this process like this: Associate to each outcome $m$ an operator $M_m$ acting on the quantum system's state space. The set $\{M_m\}$ is called *measurement operators*. 
	2. After the measurement, we will see one of the labels $m$. The chance of seeing $m$ is $p(m)=\bra{\psi}M^\dagger_mM_m\ket{\psi}$ 
		1. $M_m^\dagger M_m$ act as a projector $P$ that we had. Since $M$ is [[11 Hermitian]]; then we have $M^\dagger_m=M_m$ and $M_m^2=M_m$ so we get $M_m^\dagger M_m=M_m$ and at last $p(m)=\bra{\psi}M_m\ket{\psi}$. 
	3. If we see outcome $m$, the system collapses to $\frac{\text{Measurement Operator}\ *\ \text{state}}{\text{Probability of the outcome}}=\frac{M_m\ket{\psi}}{\sqrt{\bra{\psi}M^\dagger_mM_m\ket{\psi}}}$. We just normalized the new state so it has a unit length.
	4. Completeness (sum of probabilities = 1): $\sum_mp(m)=1\ \Longrightarrow\sum_m\bra{\psi}M^\dagger_mM_m\ket{\psi}=1$ for every $\ket{\psi}$. 
		1. The simplest way to check this issue is with the *completeness equation* that uses the Identity operator: $\boxed{\sum_mM^\dagger_mM_m=I}$.


**Example**
We want to measure a qubit in the $\{\ket{0},\ket{1}\}$ basis. 
We choose our measurement operators: $$M_0=\ket{0}\bra{0} \,\ ,\ M_1=\ket{1}\bra{1}$$
First we should check the completeness of our measurement operators:
$$
M_0^\dagger M_0+M_1^\dagger M_1=I
$$
$$
M^\dagger_0=M_0=\begin{bmatrix} 1 & 0 \\ 0 & 0\end{bmatrix}
$$
$$
M^\dagger_1=M_1=\begin{bmatrix} 0 & 0 \\ 0 & 1\end{bmatrix}
$$
$$
M^\dagger_0=M_0=\begin{bmatrix} 1 & 0 \\ 0 & 0\end{bmatrix}
$$
$$
M_0^\dagger M_0+M_1^\dagger M_1=\begin{bmatrix} 1 & 0 \\ 0 & 1\end{bmatrix}=I
$$

Now we want to calculate the probabilities. If $\ket{\psi}=\alpha\ket{0}+\beta\ket{1}$, then 
$$p(0)=\bra{\psi}M_0\ket{\psi}=|\alpha|^2, \ \ p(1)=|\beta|^2
$$
The post-measurement states:
	If outcome is $0$: $\frac{M_0\ket{\psi}}{\sqrt{|\alpha^2|}}=\frac{\alpha\ket{\psi}}{|\alpha|} \cong \ket{0}$
	If outcome is $1$: $\frac{M_1\ket{\psi}}{\sqrt{|\beta^2|}}=\frac{\beta\ket{\psi}}{|\beta|} \cong \ket{1}$


## Cascade measurements 
> Cascaded measurements are single measurements Suppose ${L_l}$ and ${M_m}$ are two sets of measurement operators. Show that a measurement defined by the measurement operators ${L_l}$ followed by a measurement defined by the measurement operators ${M_m}$ is physically equivalent to a single measurement defined by measurement operators ${N_{lm}}$ with the representation $N_{lm}≡ M_mL_l$.
>
> ### 1. Joint Probability Matches
1. **First measurement** $\{L_l\}$ on $\ket{\psi}$:  
   - $p(l) = \bra{\psi}\,L_l^\dagger L_l\,\ket{\psi}$.  
   - (Unnormalized) post-measurement state: $L_l\ket{\psi}$.
1. **Second measurement** $\{M_m\}$ on $L_l\ket{\psi}$:  
   - Conditional probability  
     $$
       p(m\mid l)
       = \frac{\bra{\psi}\,L_l^\dagger M_m^\dagger M_m L_l\,\ket{\psi}}
              {\bra{\psi}\,L_l^\dagger L_l\,\ket{\psi}}.
     $$

3. **Joint probability**
   $$
     p(l,m)
     = p(l)\,p(m\mid l)
     = \bra{\psi}\,L_l^\dagger M_m^\dagger M_m L_l\,\ket{\psi}
     = \bra{\psi}\,N_{lm}^\dagger N_{lm}\,\ket{\psi}.
   $$

### 2. Post-Measurement State Agrees

- Cascaded collapse (outcome $(l,m)$):  
  $$
    \frac{M_m\bigl(L_l\ket{\psi}\bigr)}
         {\sqrt{\bra{\psi}\,L_l^\dagger L_l\,\ket{\psi}}\;\sqrt{\bra{\psi}\,L_l^\dagger M_m^\dagger M_m L_l\,\ket{\psi}}}
    \;=\;
    \frac{N_{lm}\ket{\psi}}{\sqrt{\bra{\psi}\,N_{lm}^\dagger N_{lm}\,\ket{\psi}}}.
  $$

- Single-step POVM $\{N_{lm}\}$ prescribes exactly this same normalized state.


### 3. Completeness (Total Probability = 1)

To be valid, $\{N_{lm}\}$ must satisfy  
$$
  \sum_{l,m} N_{lm}^\dagger N_{lm} \;=\; I.
$$

Compute:
$$
\begin{aligned}
\sum_{l,m} N_{lm}^\dagger N_{lm}
&= \sum_{l,m} L_l^\dagger M_m^\dagger M_m L_l\\
&= \sum_l L_l^\dagger\Bigl(\sum_m M_m^\dagger M_m\Bigr)L_l\\
&= \sum_l L_l^\dagger\,I\,L_l\\
&= \sum_l L_l^\dagger L_l\\
&= I.
\end{aligned}
$$

Here, we used the completeness of each set:  
- $\sum_m M_m^\dagger M_m = I$,  
- $\sum_l L_l^\dagger L_l = I$.

- 
### Conclusion

1. **Probabilities**: $p(l,m)=\bra{\psi} N_{lm}^\dagger N_{lm}\ket{\psi}$.  
2. **States**: post-measurement state $=N_{lm}\ket{\psi}/\sqrt{\bra{\psi} N_{lm}^\dagger N_{lm}\ket{\psi}}$.  
3. **Completeness**: $\sum_{l,m}N_{lm}^\dagger N_{lm}=I$.

Hence, cascaded measurements $\{L_l\}$ then $\{M_m\}$ form a single POVM $\{N_{lm}=M_mL_l\}$.


# Why $\braket{\psi|M_{m}^{\dagger}M_{m}|\psi}$?
$\braket{\psi|M_{m}^{\dagger}M_{m}|\psi}$ is a real and positive(non-negative) scaler.
Since $M_m$ is a hermitian operator, $M_{m}^{\dagger}M_{m}$ is also a hermitian operator: 
$$
\begin{align}
(M_{m}^{\dagger}M_{m})^{\dagger}&=M_{m}^{\dagger}M_{m} \\ \braket{\psi|M_{m}^{\dagger}M_{m}|\psi}&=\braket{\psi|M^{\dagger}(M|\psi})=(M\ket{{\psi}})^{\dagger}(M\ket{{\psi}})=|\lvert M\ket{{\psi}} \rvert|^2 
\end{align}
$$
and since the norm squared of any matrix is always non-negative, $\braket{\psi|M_{m}^{\dagger}M_{m}|\psi}$ is always non-negative, and since $M$ is hermitian, it is real. 

