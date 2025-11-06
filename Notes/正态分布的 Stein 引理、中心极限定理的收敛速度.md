#SmallEssays/概率论

Stein 引理是正态分布的一个重要性质，尽管它直到近些年来才被提出，但它却出人意料地简单，并且一经问世，就得到了广泛的应用。本文以**中心极限定理的收敛速度估计**为例，介绍 Stein 方法的应用。

**Stein 引理** 设 $f:\mathbb{R}\to \mathbb{R}$ 可微，$Z\sim N(0,1)$，则有
$$
\mathbb{E}\left[ f'(Z)-Zf(Z) \right]=0 
$$

这个引理的证明是简单直接的，只需要用一个分部积分公式，甚至可以说是弱智的，但它真正的威力还需要结合下面这个引理才能体现。

**Stein 方程** 设 $h:\mathbb{R}\to \mathbb{R}$ Lipschitz 连续，$X$ 是某个随机变量，$Z\sim N(0,1)$，则存在 $f_{h}$ 满足方程
$$
\mathbb{E}\left[ h(X)-h(Z) \right]=\mathbb{E}\left[ f_{h}'(X)-Xf_{h}(X) \right]  
$$
其中，$f_{h}$ 有显式表示
$$
f_{h}(x)=\int^{x}_{-\infty} g(t)e^{-\frac{t^{2}}{2}} \; \mathrm{d}t,\quad g(x)=h(x)-\mathbb{E}\left[ h(Z) \right]  
$$

这个定理看似复杂，但实际上思想简单。Stein 引理给出了一个对正态分布的刻画，那么一个很自然的想法是：**当 $X$ 接近正态分布时，Stein 引理也应当近似地成立**。为了描述这种近似成立，需要度量 $X$ 和 $Z$ 的距离，我们很自然地选择了 $BL^{*}$ 距离
$$
d(X,Z):=\sup_{h}\mathbb{E}\left|h(X)-h(Z)  \right| 
$$
其中 $h$ 取遍 Lipschitz 连续的函数，这个度量它与弱收敛等价。接下来，我们用这两个引理来估计中心极限定理的收敛速度。

**定理** $X_{1}, ~ X _{2}, \cdots,~ X_n\overset{\text{i.i.d}}{\sim} P_{X}$，$\mathbb{E}X=0,~EX^{2}=1,~\mathbb{E}\left| X \right|^{3}<\infty$，记 $\widetilde{X}=\frac{1}{\sqrt{ n }}\sum^{n}_{i=1}X_{i}$ ，则有
$$
\sup_{h}\mathbb{E}\left|h(\widetilde{X})-h(Z)  \right| \lesssim \frac{E\left| X \right| ^{3}}{\sqrt{ n }}
$$

**证明** 由 Stein 方程，存在 $f_{h}$ 满足
$$
\sup_{h}\mathbb{E}\left[ h(X)-h(Z) \right]=\sup_{h}\mathbb{E}\left[ f_{h}'(X)-Xf_{h}(X) \right]  
$$
记 $X'=\widetilde{X}-\frac{1}{\sqrt{ n }}X_{1}=\frac{1}{\sqrt{ n }}\sum^{n}_{i=2}X_{i}$ ，显然 $X'$ 与 $X_{1}$ 独立。以下改记 $f_{h}$ 为 $f$ 。

对称性可知 $\mathbb{E}[\widetilde{X}f(\widetilde{X})]=\mathbb{E}[\sqrt{ n }X_{1}f(\widetilde{X})]$，由 $\widetilde{X}=X'+\frac{1}{\sqrt{ n }}X_{1}$ ，将 $f$ 在 $\widetilde{X}$ 处展开得
$$
\mathbb{E}[\widetilde{X}f(\widetilde{X})]=\mathbb{E}[\sqrt{ n }X_{1}\big(f(X')+\frac{X_{1}}{\sqrt{ n }}f'(X')\big)]+R_{1}
$$
由独立性和 $\mathbb{E}X=0,~\mathbb{E}X^{2}=1$，上式即为 $\mathbb{E}\left[ f' (X') \right]+R_{1}$，又写成 $\mathbb{E}[f' (\widetilde{X}) ]+R_{1}+R_{2}$。下面分别估计两项。
$$
\left| R_{1} \right|\leq \mathbb{E}\frac{\left| X_{1} \right|^{3}}{\sqrt{ n }}\left| f''(\xi) \right|\lesssim \frac{\mathbb{E}\left| X_{1} \right| ^{3}}{\sqrt{ n }}  
$$
$$
|R_{2}|=|\mathbb{E}[f'(X')-f'(\widetilde{X})]|\leq \mathbb{E}\frac{\left| X_{1} \right|^{3}}{\sqrt{ n }}\left| f''(\zeta) \right|\lesssim \frac{\mathbb{E}\left| X_{1} \right| ^{3}}{\sqrt{ n }}  
$$
其中 $f''$ 的有界性可以直接验证，于是完成了证明。

---
*Reference: [[lecture1.pdf]]

---
*2025-9-22*
