#SmallEssays/数理统计 

在笔记[[统计判决：minimax 准则、Bayes 准则]]中，证明了在正态总体中抽取单个样本 $x$，则在方差已知的情形下，$x$ 本身就是其均值的 minimax 估计。尽管我们只对 $1$ 维情形做了证明，但结论可以简单推广到高维情形。这个结论本身非常符合直觉，毕竟总共只有一个样本，不用 $x$ 还能用什么呢？这也是反直觉所在，当维数 $d\geq3$ 时，还真有在某种意义上比 $x$ 更好的估计量，被称为 **Stein 悖论**。

在介绍这个估计之前，我们需要介绍一下估计的比较。在此之前，我们建立的多种多样的准则来评判一个估计的好坏，例如常见的无偏性、相合性、有效性，甚至于此前介绍的 minimax 准则和 Bayes 准则等。一般来说，不会有一个估计能具有一切理想的性质，我们只能根据实际的需要来选取对应的估计。尽管两个不同的估计很难比出绝对的好坏，不过偶尔这种情况也会出现。

**定义** 如果对于一个决策 $a$（估计 $\hat{\theta}$），若存在另一个决策 $a'$ 满足 $R(a;\theta)\geq R(a';\theta),~\forall\;\theta \in\Theta$，且至少在一点 $\theta_{0}$ 处不等号严格成立，则称 $a$ 是不可容许的。

> [!remark]-
> 若 $R(a;\theta)\geq R(a';\theta),~\forall\;\theta \in\Theta$，则记 $a\succeq a'$，若还至少在一点 $\theta_{0}$ 处不等号严格成立，则记 $a\succ a'$

这个定义是符合直觉的，因为如果真的有一个选择 $a'$，在所有可能下风险都比 $a$ 更小，那为什么不选 $a'$ 呢？在容许性的意义下，$a$ 和 $a'$ 就是可以比较的。

接下去证明 $x$ 作为 $\mu$ 的估计量，在 $d\geq3$ 时是不可容许的，即能构造 $\hat{\mu}(x)\succ x$ 。我们认为，$\hat{\mu}$ 应当具有球对称性，即 $\hat{\mu}(x)=g(\| x \|)x$ ，$g$ 称为 Stein's shrinker 。于是只需要构造 $g$ 使得
$$
R(\hat{\mu};\mu)-R(x;\mu)=R(\hat{\mu};\mu)-d\sigma^{2}<0
$$
为此计算风险
$$
\begin{align}
R(\hat{\mu};\mu)&=\mathbb{E}_{\mu}\| \hat{\mu}-\mu \|^{2}\\&
=R(x;\mu)+\mathbb{E}_{\mu}\| \hat{\mu}-x \|^{2}+2\mathbb{E}_{\mu}(\hat{\mu}-x)^{T}(x-\mu)
\end{align}
$$
其中可进一步计算
$$
\begin{align}
\mathbb{E}_{\mu}(\hat{\mu}-x)(x-\mu)&=\mathbb{E}_{\mu}\hat{\mu}^{T}(x-\mu)-\mathbb{E}x^{T}(x-\mu)\\
&=\mathbb{E}_{\mu}\hat{\mu}^{T}(x-\mu)-\mathbb{E}(x-\mu)^{T}(x-\mu)
\\&=\sum^{d}_{i=1}\mathbb{E}_{\mu}\hat{\mu}_{i}(x_{i}-\mu _{i})-d\sigma^{2} 
\end{align}
$$
由于 $x$ 的每个分量服从正态分布，利用 [[正态分布的 Stein 引理、中心极限定理的收敛速度|Stein 引理]]得
$$
\mathbb{E}_{\mu}\hat{\mu}_{i}(x_{i}-\mu _{i})=\sigma^{2}\mathbb{E}_{\mu}\left[ \frac{\partial \hat{\mu}_{i}}{\partial x_{i}}  \right] =\sigma^{2}\mathbb{E}_{\mu}\left[ \frac{\partial g}{\partial x_{i}}x_{i}+g  \right] 
$$
Stein 猜测 $g$ 有形式 $1-\frac{c}{\| x \|^{2}}$，于是 $\frac{\partial g}{\partial x_{i}}=\frac{2c}{\| x \|^{4}}x_{i}$，代入以上全部得
$$
R(\hat{\mu};\mu)-R(x;\mu)=\mathbb{E}_{\mu}\left[ \frac{1}{\| x \|^{2} }(c^{2}+4c\sigma^{2}-2d\sigma^{2}c) \right] 
$$
括号内对 $c$ 取最小值为 $-\sigma^{4}(d-2)^{2}$。巧就巧在，只有当 $d\geq3$ 时，$\mathbb{E}_{\mu}\left[ \frac{1}{\| x \|^{2}} \right]$ 才存在（直接计算重积分），此时就有 $R(\hat{\mu};\mu)-R(x;\mu)<0$ 对一切 $\mu$ 成立，于是 $x$ 是一个不可容许的估计量，我们构造的 $\hat{\mu}=x-\frac{\sigma^{2}(d-2)}{\| x \|^{2}}x$ 是一个更好的估计量，称为 James-Stein 估计。

---
*Reference: [[lecture2 (1).pdf]]*

---
*2025-12-1*










