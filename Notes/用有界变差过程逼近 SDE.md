---
{}
---
#SmallEssays/随机分析 

对于一般的 SDE
$$
\mathrm{d} X_{t}=b(t,X_{t})\;\mathrm{d} t+\sigma(t,X_{t})\;\mathrm{d} W_{t}
$$
由于 Brown 运动的轨道不是有界变差的，因此无法简单地对于每一条轨道 $\omega$，把上述方程视作一个 ODE 求解。一个自然的想法是，**用一列有界变差函数 $\{ V^{(n)} \}_{1}^{\infty}$ 逼近 Brown 运动**，分别对每个 $n$ 求解如下 ODE
$$
\mathrm{d} X^{(n)}_{t}=b(t,X^{(n)}_{t})\;\mathrm{d} t+\sigma(t,X^{(n)}_{t})\;\mathrm{d} V^{(n)}_{t}
$$
并期待令 $n\to \infty$ 使得解 $X^{(n)}_{t}\to X_{t}$ 。

然而，在笔记 [[Rough Path 的动机、Lévy's Area]] 中给出了例子，表明解映射 $S:V\mapsto X$ 往往是不连续的，为了能对 $n$ 取极限，不得不做一些额外的限制。即要求**系数函数 $b$ 和 $\sigma$ 与 $t$ 无关**，从而 $X_{t}$ 是一个 Markov 过程。

**定理** 设 $\sigma$ 有有界的前两阶导数，$b$ 满足 Lipschitz 条件，$\{ V_{t}^{(n)} \}_{1}^{\infty}$ 是一列有界变差过程。若 $\{ V_{t}^{(n)} \}_{1}^{\infty}$ 几乎必然、内闭一致收敛到 Brown 运动 $W_{t}$，即对一切 $0\leq t<\infty$，有
$$
\lim_{ n \to \infty } \sup_{0\leq s\leq t}\left| V_{s}^{(n)}-W_{s} \right|=0\quad \text{a.s.}  
$$
则方程
$$
\mathrm{d} X^{(n)}_{t}=b(X^{(n)}_{t})\;\mathrm{d} t+\sigma(X^{(n)}_{t})\;\mathrm{d} V^{(n)}_{t}
$$
的唯一解 $X_{t}^{(n)}$ 几乎必然、内闭一致收敛到如下方程
$$
\mathrm{d} X_{t}=b(X_{t})\;\mathrm{d} t+\sigma(X_{t})\circ\mathrm{d} W_{t}
$$
的唯一解 $X_{t}$ 。

此外还须注意，**$1$ 维与多维情形有本质区别**，上述的结果只针对 $1$ 维情形给出，对于多维的情形一般不成立。如果 $V^{(n)}$ 通过对 Brown 运动插值给出，那能得到类似的结果。

---
*Reference: Brownian Motion and Stochastic Calculus, Ioannis Karatzas, Steven E. Shreve*

---
*2025-8-26*