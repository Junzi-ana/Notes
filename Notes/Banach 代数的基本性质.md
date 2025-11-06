#SmallEssays/泛函分析 

假设 $V$ 是一个 $\mathbb{C}$ 上的 Banach 空间，它上面还可以附加代数的结构(若不声明，总假定是**含幺的**)，从而成为一个 Banach 代数 $\mathcal{L}$，其元素之间的乘法应该满足 (广义的) Cauchy-Schwartz 不等式：
$$
\left\| MN \right\| \leq \left\| M \right\|\left\| N \right\|,\quad M,~ N \in  \mathcal{L}
$$
最直接的例子是 $V$ 上的**算子代数** $\mathcal{L}(X,X)$，范数取作算子范数，乘法为映射的复合。

**性质** Banach 代数 $\mathcal{L}$ 有如下分析性质
1. $M\in \mathcal{L}$ 可逆 $\implies$ $\forall\;A\in \mathcal{L}:\left\| A \right\|<\left\| M^{-1} \right\|^{-1}$，有 $M-A$ 可逆
2. $\sigma(M)$ 是非空有界闭集，$\rho(M)$ 是开集
3. 预解式 $(\zeta I-M)^{-1}$ 作为 $\zeta$ 的函数在 $\rho(M)$ 上解析
4. **(Gelfand 公式)** $|\sigma(M)|=\lim_{ k \to \infty } \left\| M^{k} \right\|^{\frac{1}{k}}$

作为对上述性质的应用，则有如下重要结论

**Mazur 定理** 可除 Banach 代数同构于 $\mathbb{C}$

**证明** 设 $M\in\mathcal{L}$ ，$\sigma(M)$ 非空表明存在 $\lambda \in \mathbb{C}$ ，使得 $\lambda I-M$ 不可逆。又由于 $\mathcal{L}$ 可除，知 $\lambda I-M$ 只能等于零元，即 $M=\lambda I$ 。于是 $M\mapsto \lambda$ 就是 $\mathcal{L}$ 到 $\mathbb{C}$ 的同构。

---
*Reference: 泛函分析, Peter D. Lax*

---
*2025-9-9*