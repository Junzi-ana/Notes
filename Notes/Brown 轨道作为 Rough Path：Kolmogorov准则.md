#SmallEssays/RoughPath 

回想定义 Rough Path 的一大目的就是解决 SDE 不能逐轨道地求解的局限性，见笔记 [[Rough Path 的动机、Lévy's Area]] 。在 [[Rough Path 的 Chen's Relation]] 中给出了 Rough Path 的定义，自然会考虑，如何将这套理论应用到 Brown 运动的轨道中呢？

不论是从直观还是从动机的角度，对于一个具体的样本点 $\omega \in\Omega$，样本轨道 $B(\omega)$ 应该是一条“粗糙的”轨道。于是考虑 $\displaystyle \mathbb{B}_{s,t}=\displaystyle \int_{s}^{t} B_{s,r}\otimes\mathrm{d}B_{r}$，积分由 Itô 积分定义，并作提升 $\mathbf{B}(\omega)=(B,~\mathbb{B})(\omega): [0,T]\mapsto \mathbb{R}^{n}\oplus \mathbb{R}^{n\otimes2}$ 。此处的 $\mathbf{B}(\omega)$ 是逐点定义的，我们希望它对于 $\text{a.e.} ~\omega \in \Omega$ 都是 Rough Path。

> [!remark]-
> 依照定义，$\mathbf{B}(\omega)$ 应该定义在 $[0,T]^{2}$ 上，但根据 [[Rough Path 的张量代数结构#^d570ff]]，$\mathbf{B}$ 可视为一条 $T_{1}^{(2)}$ 中的路径，故可以写成定义在 $[0,T]$ 上。

很容易验证 $\mathbf{B}(\omega)$ 满足 Chen's Relation，然而要说明其轨道的 Hölder 连续性，却并不直接，要依赖如下定理。这个定理的形式与证明过程基本类似于 Kolmogorov-Čentsov 定理，因此得名为 **Kolmogorov Criterion** 。

> [!note]-
> **Kolmogorov-Čentsov 定理** 设 $X$ 是 $(\Omega,\mathcal{F},\mathbb{P})$ 上的过程，满足条件：存在 $\alpha,~\beta,~C>0$，成立
> $$\mathbb{E}\left| X_{t}-X_{s} \right|^{\alpha}\leq C\left| t-s \right|^{1-\beta},\quad 0\leq s,t\leq T  $$
> 则 $X$ 有连续修正，且可以是 $\gamma$ 阶局部 Hölder 连续的，$\forall\;\gamma \in(0,\dfrac{\beta}{\alpha})$。这个定理被用来证明 Brown 运动的存在性。

**定理** 设 $q\geq2,~\beta>\dfrac{1}{q}$，且 $\forall\;s,~t\in[0,T]$，$\exists\;C>0$：
$$
\mathbb{E}\|X_{s,t}\|^{q}\leq C\left| t-s \right| ^{\beta q},\quad \mathbb{E}\|\mathbb{X}_{s,t}\|^{\frac{q}{2}}\leq C\left| t-s \right| ^{\beta q}
$$
则对任意 $\alpha \in[0,\dfrac{\beta}{q})$，存在 $(X,~\mathbb{X})(\omega)$ 的修正，仍记为 $(X,~\mathbb{X})(\omega)$，和依赖于 $\omega$ 的常数 $K_{\alpha},~\mathbb{K}_{\alpha}$，满足 $X$ 和 $\mathbb{X}$ 分别是 $\alpha$ 和 $2\alpha$ 阶连续的，即
$$
\|X_{s,t}\|\leq K_{\alpha}\left| t-s \right| ^{\alpha},\quad \|\mathbb{X}_{s,t}\|\leq \mathbb{K}_{\alpha}\left| t-s \right| ^{2\alpha},\quad  \forall\; s,~t\in[0, T]
$$
此外，$K_{\alpha}(\omega),~\mathbb{K}_{\alpha}(\omega)$ 视为随机变量是 $L^{q},~L^{\frac{q}{2}}$ 中的元素。特别地，若 $\beta-\dfrac{1}{q}>\dfrac{1}{3}$，则 $\mathbf{X}=(X,~\mathbb{X})\in \mathcal{C}^{\alpha},~~\text{a.s.}$

$B$ 的 Hölder 连续性早有说明，剩余的任务是说明 $\mathbb{B}$ 的 Hölder 连续性，利用 BDG 不等式可以完成估计，因估计过程冗长复杂，在此不再赘述。总之，**Brown 运动的轨道可以视为 Rough Path** 。

---
*Reference: 
	A Course on Rough Paths, Peter K. Friz
	Brownian Motion and Stochastic Calculus, Ioannis Karatzas, Steven E. Shreve*

---
*2025-9-5*