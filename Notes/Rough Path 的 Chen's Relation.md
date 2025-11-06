---
{}
---
#SmallEssays/RoughPath 

对于这样的带控制的微分方程
$$\mathrm{d}Y_{t}=f_{0}(Y_{t})+f(Y_{t})\;\mathrm{d}X_{t}$$
传统的路径积分忽略了一些信息，比如关于 [[Rough Path 的动机、Lévy's Area|Lévy's Area]] 的信息，导致解映射 $S:X\mapsto Y$ 在常规的空间 $C[0,1]$ 上不连续。为此，最简单直接的想法是把 Lévy's Area 的信息 $\mathbb{X}_{t}$ 直接添加到路径 $X_{t}$ 中，**将原有的路径信息 $X_{t}$ 强化为 $\mathbf{X}_{t}=(X_{t},~\mathbb{X}_{t})$**。

如何描述 Lévy's Area 的信息呢？依照定义，对于一个 $d$ 维的过程 $X_{t}$，它应当由所有形如 $\displaystyle \int_{s}^{t} X^{i}\;\mathrm{d}X^{j}$ 的积分描述，可将其排成一个 $d\times d$ 的矩阵，即
$$
\mathbb{X}_{s,t}=\begin{bmatrix}
\displaystyle\int_{s}^{t} X^{1}_{s,r}\;\mathrm{d}X^{1}_{r}  & \displaystyle\int_{s}^{t} X^{1}_{s,r}\;\mathrm{d}X^{2}_{r} &\cdots  & \displaystyle\int_{s}^{t} X^{1}_{s,r}\;\mathrm{d}X^{d}_{r}\\
\displaystyle\int_{s}^{t} X^{2}_{s,r}\;\mathrm{d}X^{1}_{r}  & \displaystyle\int_{s}^{t} X^{2}_{s,r}\;\mathrm{d}X^{2}_{r} &\cdots  & \displaystyle\int_{s}^{t} X^{2}_{s,r}\;\mathrm{d}X^{d}_{r}\\
 \vdots & \vdots & \ddots & \vdots\\
\displaystyle\int_{s}^{t} X^{d}_{s,r}\;\mathrm{d}X^{1}_{r}  & \displaystyle\int_{s}^{t} X^{d}_{s,r}\;\mathrm{d}X^{2}_{r} &\cdots  & \displaystyle\int_{s}^{t} X^{d}_{s,r}\;\mathrm{d}X^{d}_{r}

\end{bmatrix}
$$
其中，$X_{s,r}=X_{r}-X_{s}$ 。

还可以用一种更紧凑的形式，即 $\displaystyle \mathbb{X}_{s,t}=\displaystyle \int_{s}^{t} X_{s,r}\otimes\mathrm{d}X_{r}$，对于无穷维的情形，应理解为 **Banach 空间中的张量积**，参见 [[Banach 空间的张量积]]。

可以验证，$X$ 与 $\mathbb{X}$ 之间满足如下的代数关系
$$
\mathbb{X}_{s,t}-\mathbb{X}_{s,u}-\mathbb{X}_{u,t}=X_{s,u}\otimes X_{u,t}
$$
这称为 **Chen's Relation** 。其导出过程并是**没有涉及分部积分公式**的，是**重积分基本性质**。对于 $d$ 维光滑曲线或者 Brown 运动，$\mathbb{X}$ 中的积分可以理解为常规的 L-S 积分或是 Itô 积分，然而对于一般的路径粗糙的驱动过程，$\mathbb{X}$ 中的积分实际上并没有被良好定义，因此考虑直接将 Chen's Relation 作为公理来定义 $\mathbb{X}$ 。于是我们引出如下定义。

**定义** 设 $V$ 是 Banach 空间，$X_{t}:[0,T] \to V,~\mathbb{X}_{s,t}:[0,T]^{2}\to V\otimes V$，
$\alpha \in(\dfrac{1}{3},\dfrac{1}{2}]$，若满足
1. $X$ 是 $\alpha$ 阶 Hölder 连续，$\mathbb{X}$ 是 $2\alpha$ 阶 Hölder 连续
2. $\mathbb{X}$ 满足 Chen's Relation
则称 $\mathbf{X}=(X,~\mathbb{X})$ 为 Rough Path。

---
*Reference: A Course on Rough Paths, Peter K. Friz*

---
*2025-8-21*