---
{}
---
#SmallEssays/RoughPath 

在笔记 [[Rough Path 的 Chen's Relation]] 中给出了 Rough Path 的定义，现在考虑其所处的空间。对 $\displaystyle\alpha \in(\frac{1}{2},\frac{1}{3}]$，记所有 Rough Path 作成的空间为 $\mathcal{C}^{\alpha}$，称为 **Rough Path 空间**。

依照定义，$X$ 是 $\alpha$ 阶 Hölder 连续，而 $\mathbb{X}$ 是 $2\alpha$ 阶 Hölder 连续的，其中 $\alpha \in(\dfrac{1}{3},\dfrac{1}{2}]$ 。为此，可以把 $\mathbf{X}$ 视为空间 $H^{\alpha}([0,T],V)\oplus H^{2\alpha}([0,T]^{2},V\otimes V)$ 中的元素，而 $\mathcal{C}^{\alpha}$ 视为它的一个子空间。总取初值为 $0$，在 $\alpha$ 阶 Hölder 空间 $H^{\alpha}$ 上可以定义范数 $\|\cdot\|_{\alpha}$
$$
\left\| f \right\|_{\alpha}=\sup_{s\neq t} \frac{\left| f(s)-f(t) \right| }{\left| s-t \right| ^{\alpha}}<\infty,\quad f\in H^{\alpha} 
$$
于是在 $\mathcal{C}^{\alpha}$ 上定义 $\rho$
$$
\rho(\mathbf{X})=\left\| X \right\| _{\alpha}+\left\| \mathbb{X} \right\| _{2\alpha}
$$
使得 $\mathcal{C}^{\alpha}$ 成为一个赋范线性空间。

满足 Chen's Relation 的提升 $X\mapsto(X,\mathbb{X})$ 可能有多种，比如 $X$ 是 Brown 运动，可以分别通过 Itô 积分和 Stratonovich 积分来定义 $\mathbb{X}$ 。二者最大的区别就是，Stratonovich 积分**满足分部积分公式**。如果使用分部积分公式，Chen's Relation 可以进一步简化为 ^ct6fo7
$$
\frac{1}{2}(\mathbb{X}_{s,t}+\mathbb{X}_{s,t}^{T})=\frac{1}{2}X_{s,t}\otimes X_{s,t}
$$
于是，将满足这一层关系的 Rough Path 称为**弱几何 Rough Path**，作成的空间记为 $\mathcal{C}^{\alpha}_{g}$ 。

光滑的路径也可以自然地提升，作成的空间依 $\rho$ 取闭包之后记为 $\mathcal{C}^{\alpha}_{0,g}$ ，并且有如下关系
$$
\mathcal{C}^{\alpha}_{0,g}\subsetneqq \mathcal{C}^{\alpha}_{g} \subsetneqq \mathcal{C}^{\alpha}
$$
很容易找到例子验证真包含是成立的。

---
*Reference: A Course on Rough Paths, Peter K. Friz*

---
*2025-8-27*