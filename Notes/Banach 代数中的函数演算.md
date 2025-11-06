---
{}
---
#SmallEssays/泛函分析 

设 $\mathcal{L}$ 是一个 [[Banach 代数的基本性质|Banach 代数]]，我们可以定义 $\mathcal{L}$ 中元素 $M$ 的幂级数
$$
f(M)=\sum^{\infty}_{n=0} a_{n}M^{n}
$$
其中要求这个幂级数的收敛半径要大于 $M$ 的谱半径 $\left| \sigma(M) \right|$ 。利用 Cauchy 积分公式，可以给出一个 $f$ 的更加一般的延拓，即定义
$$
f(M)=\frac{1}{2\pi i} \oint_{C}(\zeta-M)^{-1}f(\zeta)\;\mathrm{d} \zeta
$$
其中，$f$ 在一个包含 $\sigma(M)$ 的区域 $G$ 上解析，$C\subseteq G\cap \rho(M)$ 是环绕 $\sigma(M)$ 每个点 $1$ 次、绕 $G$ 的补集中每个点 $0$ 次的围道，由 Cauchy 积分定理，$f(M)$ 的定义与围道的选取无关。

这样定义的 $f$ 满足一些符合直觉的性质，比如四则运算和复合性质（需要在定义域内）等等，统称为**函数演算**，但最重要的是如下性质。

**谱映射定理**
$$
\sigma(f(M))=f(\sigma(M))
$$

此外，也有算子的函数演算类似于谱分解定理的性质，在此之前先回顾一下矩阵（线性变换）的谱分解定理：

> [!note]-
> 设 $\mathcal{A}$ 是 $\mathbb{R}^{n}$ 上的半单线性算子，有 $s$ 个互异的特征值，则有分解式
> $$\mathcal{I}=\sum^{s}_{i=1} \mathcal{P}_{i}$$
> 其中 $\mathcal{P}_{i}$ 是到特征子空间上的投影算子，$\mathcal{I}$ 是恒等算子。

推广到一般的线性算子 $M\in \mathcal{L}$，应假设 $\sigma(M)$ 可以分解成 $s$ 个**不交的闭分支** $\sigma(M)=\sigma_{1}\cup\cdots\cup\sigma_{s}$，$C_{j}\subseteq \rho(M)$ 表示**环绕 $\sigma_{j}$ 中每个点 $1$ 次**而不绕其它 $\sigma_{k}$ 的围道，并且定义
$$
\mathcal{P}_{j}=\frac{1}{2\pi i} \oint_{C_{j}}(\zeta-M)^{-1}\;\mathrm{d} \zeta
$$
则成立

**谱分解定理** 
1. $\mathcal{P}_{j}$ 是不交的投影，即
$$
\mathcal{P}_{j}^{2}=\mathcal{P}_{j},\quad \mathcal{P_{i}}\mathcal{P_{k}}=0\quad (j\neq k)
$$
2. 成立分解式
$$
\mathcal{I}=\sum^{s}_{j=1}\mathcal{P}_{j} 
$$
3. 若 $\sigma_{j}$ 非空，则 $\mathcal{P}_{n}\neq0$

> [!note]-
> 注意 $C_{j}$ 环绕 $\sigma_{j}$ 中每个点 $1$ 次这个条件是本质的，正如在线性变换的情形中，要求它是半单（可对角化）的一样，这个条件表明 $\sigma(M)$ 中没有“重数”大于 $1$ 的点。

---
*Reference: 泛函分析, Peter D. Lax*

---
*2025-8-31*