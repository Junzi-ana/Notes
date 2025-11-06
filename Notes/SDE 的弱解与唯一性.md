#SmallEssays/随机分析 

考虑如下 SDE
$$
\mathrm{d} X_{t}=b(t,X_{t})\;\mathrm{d} t+\sigma(t,X_{t})\;\mathrm{d} W_{t}
$$
相比于强解，已然给定了概率空间 $(\Omega,\mathcal{F},\mathbb{P})$ 和其上的 Brown 运动 $W_{t}$ 与初值 $\xi$；弱解以三元组 $(X,W),~(\Omega,\mathcal{F},\mathbb{P}),~\{ \mathcal{F}_{t} \}_{t \geq0}$ 作为它的定义，即只需要**在适当的空间上定义适当的 Brown 运动**，满足上述形式的 SDE 即可。于是弱解的**初始条件以初始分布 $\mu$ 给出**，而不是初值随机变量 $\xi$ 。显然，强解存在，弱解一定存在。

弱解有两种唯一性的定义，一种是**依路径唯一**，一种是**依分布唯一**。

依路径唯一是对强解唯一性的直接推广，要求两组弱解定义所依赖的空间和 Brown 运动完全相同，在此基础上若 $X$ 与 $\widetilde{X}$ **初值相同且不可区分**，则这个 SDE 的弱解依路径唯一。由于强解的唯一性不依赖滤子的具体形式，所以上述定义中的**滤子可能有所不同**，且**关于强解唯一性的论断都直接适用于弱解的依路径唯一**。

依分布唯一则可对于任意两组弱解 $(X,W),~(\Omega,\mathcal{F},\mathbb{P}),~\{ \mathcal{F}_{t} \}_{t \geq0}$ 和 $(\widetilde{X},\widetilde{W}),~(\widetilde{\Omega},\widetilde{\mathcal{F}},\widetilde{\mathbb{P}}),~\{ \widetilde{\mathcal{F}}_{t} \}_{t \geq0}$ 讨论，只要 $X$ 和 $\widetilde{X}$ **有相同的初始分布和有限维分布**，则这个 SDE 的弱解依分布唯一。

依路径唯一蕴含依分布唯一（反之不然），这很符合直觉，但想要解释清楚，还需做一点额外工作。这是因为在讨论依分布唯一性时，两个弱解位于不同的空间，需要构造一个典范空间，从而将它们放在同一个空间上讨论。为了简化记号和区分，以下用角标 $j=1,2$ 来区分两个弱解，用 $\nu_{j}$ 表示各自的概率测度。

我们的目的是构造一个足够大的概率空间 $(\Omega,\mathcal{F},\mathbb{P})$ 。首先，回想 Brown 运动的典范空间是 $C[0,\infty)^{r}$，在它的 Borel 代数上定义了 Wiener 测度。我们希望，$W^{(1)}$ 和 $W^{(2)}$ 可以共用这个典范空间，但作为讨论对象的 $X^{(1)}$ 和 $X^{(2)}$ 可能得分开讨论，因此 $\Omega$ 还得包含 $C[0,\infty)^{d}\times C[0,\infty)^{d}$ 一项才行。最后，初始分布 $\mu$ 定义在 $\mathbb{R}^{d}$ 上，综合而言，应该定义 $\Omega=\mathbb{R}^{d}\times C[0,\infty)^{r}\times C[0,\infty)^{d}\times C[0,\infty)^{d}$，取乘积 Borel 代数。虽然这个定义冗长得吓人，但如此定义是为了在使用时，其**边缘分布是我们希望的样子**，往往不会同时考虑全部的分量。

现在希望构造 $\Omega$ 上的一个概率 $\mathbb{P}$，使得其边缘分布包含了初始分布和有限维分布的信息。首先将初始分布的信息分离出来，即令 $Y_{t}^{(j)}=X_{t}^{(j)}-X_{0}^{(j)}$，样本点形如 $\omega=(x,w,y_{1},y_{2})$ 。那么 $\mathbb{P}$ 在 $x$ 分量上的边缘分布就是 $\mu$，由独立性，在 $w$ 分量上的边缘分布是 Wiener 测度。考虑整个弱解的联合分布，应当有
$$
\mathbb{P}(\omega:(x,w,y_{j})\in A)=\nu_{j}\left( (X_{0}^{(j)},W^{(j)},Y^{(j)})\in A \right)
$$
其中 $A$ 的定义只包含 $\Omega$ 的乘积中的三项。

> [!note]
> 因为 $(X_{0}^{(j)},W^{(j)},Y^{(j)})$ 实际上相互依赖，只对应一条样本轨道，所以上述等式右侧可以视为 $\mathcal{F}_{j}$ 中的一个事件。

$\mathbb{P}$ 的存在性及具体构造依赖于**正则条件概率**相关结论，在此略去。但总之在这种框架下，$(X^{(j)},W^{(j)})$ 在 $\nu_{j}$ 下的分布等同于 $(x+y_{j},w)$ 在 $\mathbb{P}$ 下的分布。于是，依路径唯一性可以写成
$$
\mathbb{P}\left( \omega:y_{1}=y_{2} \right)=1 
$$
而依分布唯一可以写成
$$
\mathbb{P}\left( \omega:(x,w,y_{1})\in A \right) =\mathbb{P}\left( \omega:(x,w,y_{2})\in A \right) 
$$
这样一来，蕴含关系就变得显然了，即成立如下定理。

**定理（Yamada & Watanabe (1971)）** 弱解的依路径唯一性 $\implies$ 依分布唯一。 ^1ce516

---
*Reference: Brownian Motion and Stochastic Calculus, Ioannis Karatzas, Steven E. Shreve*

---
*2025-9-7*