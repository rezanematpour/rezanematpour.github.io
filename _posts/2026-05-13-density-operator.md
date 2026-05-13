---
title: "Density operator"
date: 2026-05-13 12:00:00 +0000
categories: [Quantum Computing, Density Operators]
tags: [quantum, measurement, density]
math: true
---

# 1. Defining an ensemble and the density operator

- **Ensemble of pure states** $\{(p_{1},\psi_{1}),\cdots ,(p_{n},\psi_{n})\}$ 
    - Suppose a quantum system is prepared in one of the (normalized) pure states $\{\ket{{\psi_{i}}}\}$, each occurring with classical probability $p_{i}$​. We call the collection $\{p_{i},\ket{{\psi_{i}}}\}$ an **ensemble**.
- **Density operator** $\rho$
	- We package the ensemble into the single operator $$\rho=\sum_{i}p_{i}\ket{\psi_{i}}\bra{\psi_{i}}.$$
- **Properties** 
	$\rho$ is 
	1. **Positive:** $\braket{ \phi|\rho |\phi  }\geq{0}\ \text{for all}\ \ket{\phi}.$
	2. **Unit trace:** $\mathrm{Tr}(p)=\sum_{i}p_{i}=1$ 
	These match exactly the requirements for a probability **density** over quantum states.

# 2. Unitary evolution in the density‐matrix picture
Suppose that we have a closed quantum system and it's evolution is described by the unitary operator $U$. 
If our initial state is $\ket{{\psi_{i}}}$ with the probability $p_{i}$, then after the evolution the system will be in the state $U\ket{{\psi_{i}}}$ with the probability $p_{i}$. So the evolution of the density matrix $\rho$ is described by $$U\rho=\sum_{i} p_{i}(U\ket{{\psi_{i}}})(\bra{{{\psi_{i}}}}U^{\dagger})=U\bigg(\sum_{i}p_{i}\ket{{\psi_{i}}}\bra{\psi_{i}}\bigg)U^{\dagger}=U\rho U^{\dagger} .$$
Why $U\rho=\sum pU\ket{\psi}\bra{\psi}U^{\dagger}$?{: .prompt-tip }
>$$\boxed{\begin{aligned}\ket{{\psi}}'&=U\ket{{\psi}}\\\bra{\psi}'&=(\ket{\psi}')^{\dagger}=\bra{\psi}U^{\dagger}\end{aligned}}$$
>By definition, a closed‐system unitary acts on any operator $P$ as
$P  ⟼  U P U^{\dagger}$. Applied to the projector $P=\ket{{\psi}}\bra{\psi}$ gives $U\ket{{\psi}}\bra{\psi}U^{\dagger}=\ket{\psi}'\bra{\psi}'$.

# 3. Measurement described by $\rho$ language
Suppose we perform a measurement described by measurement operators $M_{m}$. If the initial state was $\ket{{\psi_{i}}}$, then the probability of getting result $m$ is $$p(m|i)=\braket{ \psi_{i}|M_{m}^{\dagger}M_{m} |\psi_{i}}=\mathrm{Tr}(M^{\dagger}_{m}M_{m}\ket{\psi_{i}}\bra{{\psi_{i}}}). $$
By the law of total probability the probability of obtaining result $m$ is $$\begin{aligned}p(m)&=\sum_{i}p(m|i)\cdot p_{i}\\&=\sum_{i}\bigg(\mathrm{Tr}(M_{m}^{\dagger}M_{m}\ket{\psi_{i}}\bra{\psi_{i}})\bigg)\cdot p_{i}\\
&=\mathrm{Tr}\left( M^{\dagger}_{m}M_{m}\sum_{i}p_{i}\cdot \ket{\psi_{i}}\bra{\psi_{i}}   \right)
\\
&=\mathrm{Tr}(M^{\dagger}_{m}M_{m}\rho).\end{aligned}$$
If the initial state was $\ket{{\psi_{i}}}$ then the state after obtaining the result $m$ is $$\ket{{\psi^m_{i}}}=\frac{M_{m}\ket{{\psi_{i}}}}{\sqrt{\braket{ \psi_{i}|M^{\dagger}_{m}M_{m}|\psi_{i}}}}.$$
Thus, after a measurement which yields the result $m$ we have an ensemble of states $\ket{\psi^{m}_{i}}$ with respective probabilities $p(i|m)$. The corresponding density operator $\rho_{m}$ is therefore $$\begin{aligned}\rho_{m}&=\sum_{i}p({i|m})\ket{\psi_{i}^m}\bra{\psi_{i}^m}\\&=\sum_{i}p(i|m)\cdot\frac{M_{m}\ket{{\psi_{i}}}\bra{\psi_{i}}M_{m}^{\dagger} }{\sqrt{\braket{ \psi_{i}|M^{\dagger}_{m}M_{m}|\psi_{i}}}}\\ \underrightarrow{p(i|m)=\frac{p(m,i)}{p(m)}=\frac{{p(m|i)\cdot p_{i}}}{p(m)}} \\&=\sum_{i}p_{i}\cdot\frac{M_{m}\ket{{\psi_{i}}}\bra{\psi_{i}}M^{\dagger}_{m}}{\mathrm{Tr}(M^{\dagger}_{m}M_{m}\rho)}\\&=\frac{M_{m}\rho M_{m}^{\dagger}}{\mathrm{Tr}(M^{\dagger}_{m}M_{m}\rho)}.\end{aligned}$$

>The post-measurement STATE should be:
>- For **kets**: divided with $\sqrt{ p(m) }$ for normalization: $\ket{\psi^m}=\frac{M_{m}\ket{{\psi}}}{\sqrt{ p(m) }}$
>- For **density** matrices: no need, we have density operator normalization: $\rho_{m}=\ket{\psi_{i}^m}\bra{\psi^m}=\frac{M_m\ket{{\psi}}}{\sqrt{ p(m) }}\cdot\frac{\bra{{\psi}}M^{\dagger}_m}{\sqrt{ p(m) }}=\frac{M_{m}\ket{{\psi}}\bra{\psi}M^{\dagger}_{m}}{p(m)}=\frac{M_{m}\rho M^{\dagger}_{m}}{p(m)}$
>{: .prompt-tip }



> Pure vs Mixed state
> If we know the exact state $\ket{{\psi}}$ of a quantum system; we say it is in a *pure state* and its density operator is $\rho=\ket{{\psi}}\bra{\psi}$. 
> Otherwise, $\rho$ is in a *mixed state*; it is said to be a mixture of the different pure states in the ensemble for $ρ$. 
> - pure state satisfies $tr(ρ^2 ) = 1$. 
> - mixed state satisfies $tr(ρ^2 ) < 1$. {: .prompt-tip }

> Imagine a quantum system is prepared in the state $\rho_{i}$ with probability $p_{i}$.
> The system may be described by the density matrix $\sum_{i}p_{i}\rho_{i}$. 
> A proof of this is to suppose that $\rho_{i}$ arises from some ensemble $\{p_{ij}, \ket{\psi_{ij}}\}$ of pure states($i$ is fixed), so the probability for being in the state $\ket{{\psi_{ij}}}$ is $p_{i}\cdot p_{ij}$ . The density matrix for the system is thus $$\begin{aligned}\rho&=\sum_{ij}p_{i}\cdot p_{ij}\ket{{\psi_{ij}}}\bra{\psi_{ij}}\\&=\sum_{i}p_{i}\rho_{i},\end{aligned}$$ where we have used the definition $\rho_{i}=\sum_{j}p_{ij}\ket{\psi_{ij}}\bra{\psi_{ij}}$. 
> We say that $\rho$ is a *mixture* of states $\rho_{i}$ with probabilities $p_{i}$.  



# My own word
Suppose that we have a quantum biased coin.
It lands head $(\ket{{\psi_{1}}}=\ket{{0}})$ with probability $0.4$ and lands tail $\left( \ket{{\psi_{2}}}=\frac{{\ket{{0}}+\ket{1}}}{\sqrt{ 2 }} \right)$ with probability $0.6$. 
We can describe this quantum system with ensemble(a group of items viewed as a whole rather than individually) $\{p_{i},\ket{\psi_{i}}\}$: $$\big\{(0.4,\ket{0} ),(0.6,\frac{\ket{0}+\ket{1}}{\sqrt{ 2 }} )\big\}.$$
We can write the ensemble as a single mathematical object called *density matrix* or *density operator* $\rho$ $$\begin{aligned}\rho&=\sum_{i}p_{i}\cdot\ket{\psi_{i}}\bra{\psi_{i}}\\&=\bigg[0.4\ket{0}\bra{0}\bigg]+\bigg[0.6\frac{\ket{0}+\ket{1}}{\sqrt{ 2 }}\frac{\bra{0}+\bra{1}}{\sqrt{ 2 }}  \bigg].
\end{aligned}$$
---
## Density matrix is positive and trace=1
### Positive
$\braket{ \phi|\rho |\phi  }$ is the probability of the system described by density matrix $\rho$ is found in state $\ket{\phi}$. 
- For a pure state $\ket{{\psi}}$, density matrix is defined $\rho=\ket{{\psi}}\bra{\psi}$. $$\begin{aligned}\braket{ \phi| \rho|\phi}&=\braket{ \phi |\psi  }\braket{ \psi | \phi }\\&=(\braket{ \phi |\psi  })(\braket{ \phi |\psi  })^{\dagger}\\&=|(\braket{ \phi |\psi  })^2|\\\text{since }|(\braket{ \phi |\psi  })^2|\geq 0 \Longrightarrow \braket{ \phi| \rho|\phi}&\geq 0. \end{aligned}$$
- For a mixed sate $\rho=\sum_{i}p_{i}\ket{\psi_{i}}\bra{\psi_{i}}$ and we know that $p_{i}\geq 0$; so $$\braket{ \phi |\rho|\phi}=\sum_{i}p_{i}|\braket{ \phi |\psi_{i}  } |^2\geq 0.$$
Since $\braket{ \phi|\rho |\phi  }$ is non-negative, <font color="#00b050">density matrix is positive operator. </font>

### Trace = 1
- For a pure state $\ket{{\psi}}$: $$\mathrm{Tr}(\rho=\ket{\psi}\bra{\psi})=\braket{ \psi | \psi }=1. $$
- For a mixed sate $\rho=\sum_{i}p_{i}\ket{\psi_{i}}\bra{\psi_{i}}$: $$\mathrm{Tr}(\rho)=\sum_{i}p_{i}\mathrm{Tr}(\ket{\psi_{i}}\bra{\psi_{i}})=\sum_{i}p_{i}\cdot 1=\sum_ip_{i}=1$$

>The eigenvalues of $\rho$ are probabilities (they lie in $[0,1]$ and sum to $1$).
>The probability of measuring an outcome associated with projector $M$ is:$$
{0\leq\mathrm{Tr}(Mρ)\leq 1}.$$
>Pure states: $ρ^2=ρ$ (idempotent, trace=1).
>Mixed states: $ρ^2≠ρ$ (trace still 1).

---
## Evolution
If the evolution of a quantum system is described by the unitary $U$, we define the evolution of the density matrix as $$U\rho=U\sum_{i}p_{i}\ket{\psi_{i}}\bra{\psi_{i}}=\sum_{i}p_{i}U\ket{{\psi_{i}}}\bra{\psi_{i}}U^{\dagger}=U\rho U^{\dagger}.$$

---
## Measurement

>Some basic stuff
>- $\ket{{\psi_{i}}}\equiv \rho_{i}=\ket{{\psi_{i}}}\bra{\psi_{i}}$
>- $\mathrm{Tr}(A)=\sum_{j}\braket{ j|A |j  }$ where $\{\ket{{j}}\}$ is some orthonormal basis.
>	- Example: $\mathrm{Tr}(A_{2\times2})=\braket{ 0|A |0  }+\braket{ 1|A |1  }$
>- $\sum_{j}\ket{j}\bra{j}=I$
>- $\mathrm{Tr}(ABC)=\mathrm{Tr}(BCA)$
>- {: .prompt-tip }

Suppose that we perform a measurement by operator $M_{m}$. If the initial state is a pure state $\ket{{\psi_{}}}$, then the probability of getting $m$ is $$\begin{aligned}p(m|i)&=\braket{ \psi_{} |M_{m}^{\dagger}M_{m}|\psi_{}}\\&=\sum_{j}\braket{\psi_{}|M_{m}^{\dagger}|j}\braket{j|M_{m}|\psi_{}}\\&=\sum_{j}\braket{j|M_{m}|\psi_{}}\braket{\psi_{}|M_{m}^{\dagger}|j}\\&={\mathrm{Tr}(M_{m}\ket{{\psi_{}}}\bra{\psi_{}}M_{m}^{\dagger})}\\&=\boxed{\mathrm{Tr}(M_{m}^{\dagger}M_{m}\ket{\psi_{}}\bra{\psi_{}}  )}.\end{aligned}$$and density matrix after the measurement that obtained result $m$ and the initial state was pure state $\ket{{\psi_{}}}$ can be described as $$\ket{{\psi_{}^m}}=\frac{M_{m}\ket{{\psi_{}}}}{\sqrt{ \braket{\psi_{}|M_{m}^{\dagger}M_{m}|\psi_{}} }}.$$

No if we have a mixed state, the probability of obtaining result $m$ is $$\begin{aligned}p(m)&=\sum_{i}p(m|i)\cdot p_{i}\\&=\sum_{i}\mathrm{Tr}(M_{m}^{\dagger}M_{m}\ket{\psi_{}}\bra{\psi_{}})\cdot p_{i}\\&=\boxed{\mathrm{Tr}(M_{m}^{\dagger}M_{m}\rho)}.\end{aligned}$$and density matrix after the measurement is $$\rho_{m}=\sum_{i}p_{i}\ket{\psi_{i}^m}\bra{\psi_{i}^m}=\sum_{i}p(i|m)\frac{M_{m}\ket{{\psi_{i}}}\bra{\psi_{i}}M_{m}^{\dagger}}{\braket{\psi_{i}|M_{m}^{\dagger}M_{m}|\psi_{i}}}.$$
We know that $p(i∣m)=\frac{p(m,i)}{p(m)}​=\frac{p(m∣i)\cdot pi}{p(m)}$ where:
- $p_{i}$​: Probability the initial state was $\ket{{\psi_{i}}}$.
- $p(m|i)$: Probability of outcome $m$ given $\ket{{\psi_{i}}}$ (from Born rule).
- $p(m)$: Total probability of outcome $m$ (averaged over all $i$).
So $$\begin{aligned}\rho_{m}&=\sum_{i}p(i|m)\frac{M_{m}\ket{{\psi_{i}}}\bra{\psi_{i}}M_{m}^{\dagger}}{\braket{\psi_{i}|M_{m}^{\dagger}M_{m}|\psi_{i}}}\\&=\sum_{i}\frac{p(m|i)\cdot p(i)}{p(m)}\cdot\frac{M_{m}\ket{{\psi_{i}}}\bra{\psi_{i}}M_{m}^{\dagger}}{\braket{\psi_{i}|M_{m}^{\dagger}M_{m}|\psi_{i}}}\\&=\sum_{i}\frac{{\braket{\psi_{i}|M_{m}^{\dagger}M_{m}|\psi_{i}}}\cdot p(i)}{p(m)}\cdot\frac{M_{m}\ket{{\psi_{i}}}\bra{\psi_{i}}M_{m}^{\dagger}}{\braket{\psi_{i}|M_{m}^{\dagger}M_{m}|\psi_{i}}}\\&=\sum_{i}\frac{p(i)\cdot M_{m}\ket{{\psi_{i}}}\bra{\psi_{i}}M_{m}^{\dagger}}{p(m)}\enspace \bigg(\text{since}\ {M_{m}\ket{{\psi_{i}}}\bra{\psi_{i}}M_{m}^{\dagger}}=p(m|i)\bigg)\\ &=\boxed{\frac{M_{m}\rho M_{m}^{\dagger}}{\mathrm{Tr}(M_{m}^{\dagger}M_{m}\rho)}}\enspace \bigg( \text{since}\ \sum_{i}p_{i}\ket{{\psi_{i}}}\bra{\psi_{i}}=\rho\ \text{and}\ p(m)=\mathrm{Tr}(M_{m}^{\dagger}M_{m}\rho) \bigg).\end{aligned}$$





# Learnt by myself
We have a pure and mixed states. 
Pure state is like $\ket{{\psi}}=\ket{0}$ or $\ket{{\psi}}=\alpha \ket{0}+\beta \ket{1}$. We know that it is a single state or a superposition. It is definitive.
Mixed state is a state that we do not know which state it is. It is random. 
Why  $\ket{{\psi}}=\frac{1}{\sqrt{ 2 }} (\ket{0}+\beta \ket{1})$ is a pure state? although if we measure it in $\{\ket{0}, \ket{1}\}$ basis we get $\ket{0}$ with $\frac{1}{2}$ probability and $\ket{1}$ with $\frac{1}{2}$ probability, but if we measure it in $\{\ket{+},\ket{-}\}$ basis, we get $\ket{+}$ with  $1$ probability.
A pure state always has a "home basis" where it feels certain. A mixed state is homeless, uncertain in all bases. If you measure a mixed state in any basis, it will not be in a definitive basis like $\ket{0},\ket{+},\ket{i}$ with probability 1. 

We can represent any state in the matrix form: 
$$\begin{align}
\ket{\psi}&=\ket{{\psi}}\bra{\psi}   \\
\ket{0}&=\ket{0}\bra{0}=\begin{bmatrix}1&0\\0&0\end{bmatrix}   
\end{align}$$
We can't show a mixed state with a vector we show it by a matrix we call density matrix: $$\rho=\sum_{i}p_{i}\ket{\psi_{i}} \bra{\psi_{i}}$$
Suppose we have a pure state $\ket{{\psi}}=\alpha \ket{0}+\beta \ket{1}$ and we want to write it's density matrix:
$$\rho_{\psi}=1\times \ket{{\psi}}\bra{\psi}=\begin{pmatrix}\alpha\\ \beta\end{pmatrix} \begin{pmatrix}\alpha ^{*}&\beta ^{*}\end{pmatrix}=\begin{pmatrix}|\alpha|^2&\alpha \beta ^{*}\\ \beta \alpha ^{*} & |\beta|^2\end{pmatrix}$$
$p_{i}=1$ because it is a pure state and we do not have classical probability. 
We see that the diagonal elements of the density matrix are probabilities. The first element tells us the probability of outcome $\ket{0}$ and the top-right is the probability of $\ket{1}$. 

Another example of pure state:
$$\begin{align}
\ket{{\psi}}&=\frac{1}{\sqrt{ 2 }}\ket{0}+\frac{1}{\sqrt{ 2 }}\ket{1} \\
  \rho_{\psi}&=\ket{{\psi}}\bra{\psi}=\begin{pmatrix}\frac{1}{ \sqrt{ 2 }}\\ \frac{1}{\sqrt{ 2 }}\end{pmatrix} \begin{pmatrix}\frac{1}{\sqrt{ 2 }}&\frac{1}{\sqrt{ 2 }}\end{pmatrix}= \begin{pmatrix}\frac{1}{\sqrt{ 2 }}&\frac{1}{\sqrt{ 2 }}\\ \frac{1}{\sqrt{ 2 }}& \frac{1}{\sqrt{ 2 }} \end{pmatrix}
\end{align}$$

Example of a mixed state:
	Suppose we have a machine that randomly spits electrons, half of the time it spits $\ket{0}$ and half of the time $\ket{1}$. So we do not know the next electron's spin. The probability of $\ket{0}$ is 0.5 and the probability of $\ket{1}$ is also $0.5$. 
	$$\begin{align}
\rho&=\sum_{i}p_{i}\ket{{\psi}}\bra{\psi}  \\
\rho&=0.5\times \ket{0}\bra{0}+0.5\ket{1}\bra{1} \\
&=0.5\times \begin{pmatrix}1&0 \\0&0\end{pmatrix}   +0.5\times \begin{pmatrix}0&0 \\0&1\end{pmatrix} \\
&=   \begin{pmatrix}0.5&0 \\0&0.5\end{pmatrix}
\end{align}$$


>The off-diagonal elements of the mixed state density matrix are **zero**.{: .prompt-tip }

Suppose we have a pure state :$$\rho_{\psi}=\begin{pmatrix}a&b\\ c & d\end{pmatrix}$$
- Diagonal elements are the probabilities; $a$ tells us the probability of outcome $\ket{0}$ and $d$ is the probability of $\ket{1}$.
- Off-diagonal elements are the coherence: ($c=b^{*}$, c is the mirror of b)
	- If $b=0$ it means that two state $\{\ket{0},\ket{1}\}$ are not connected, they do not know each other, they are separate.
	- If $b \neq 0$, it means there is a connection between two states, this is one thing not two separate two things or states. 

Because of this the off-diagonal elements of the mixed state are zero. 
For example we have a coin that is spinning on the table, it is neither  head nor tail state in real, it is in spinning state. When we measure it becomes head or tail. On the other hand suppose we have a bag of coins that half of them are heads in real and definite and half of them are tail. When we pick one of them, with %50 it is head or tail. It is mixed and spinning coin is pure.


