---
{}
---
#SmallEssays/数理统计 

在[[数理统计基本思想：似然函数、似然比|极大似然估计]]中，我们通过最大化对数似然函数得到估计；在 [[Bayes 统计：基本原理与例子|Bayes 统计]]中，我们通过最大化后验概率得到估计；在[[非参数回归：回归的原理与最优化|回归分析]]中，我们通过最小化损失函数得到估计……这些估计方法都可以被纳入到 M 估计的框架下，即通过最大化或最小化某个函数 $\mathcal{M}(X_{1}, \cdots,X_{n};\theta)$ 来得到 $\hat{\theta}$ 。当 $\mathcal{M}$ 可微且 Hesse 矩阵半负定，则可以通过取梯度得到估计方程，从而转化为 Z 估计。

研究完全一般情形的 M 估计很难得到什么有益的结论，本文局限于形如 $M(\theta)=\mathbb{E}m(X,\theta)$ 的目标函数，$X$ 是随机变量，其分布依赖于未知参数 $\theta$，期望对真值测度取。倘若真值 $\theta_{0}$ 满足 $\theta_{0}=\underset{\theta \in\Theta}{\text{argmax}}\;M(\theta)$，则称如下经验最大化问题的解
$$
\hat{\theta}_{n}=\underset{\theta \in\Theta}{\text{argmax}}\;\mathbb{M}_{n}(\theta)
$$
为 $\theta$ 的 **M-估计量**，其中 $\mathbb{M}_{n}(\theta)=\frac{1}{n}\sum^{n}_{i=1}m(X_{i},\theta)$ 为经验目标函数。

对于这样一个 $\hat{\theta}_{n}$，我们试图从如下方面进行研究，包括
1. $\hat{\theta}_{n}$ 是 $\theta^{*}$ 的一致估计量吗
2. 如果是，$\hat{\theta}_{n}\to\theta _{0}$ 的收敛速度如何估计
3. $\hat{\theta}_{n}$ 有渐近正态性吗

这三个问题会引出非常丰富的统计理论，本篇笔记只讨论第一个问题。

首先，由于这是个最大化问题，倘若全局最大值点不唯一，我们自然无法通过这个 M 估计框架来捕获真值，因此 $\theta _{0}$ 需要满足**识别性条件**
$$
M(\theta^{*})>\sup_{\| \theta'-\theta _{0} \| >\delta} M(\theta'),\quad \forall\;\delta>0
$$
记 $A_{n}=\{ \| \hat{\theta}_{n}-\theta _{0} \|>\delta \}$，往证 $\mathbb{P}(A_{n})\to0$ 。在 $A_{n}$ 上，一方面由识别性条件，有
$$
M(\theta _{0})-M(\hat{\theta}_{n})> M(\theta^{*})-\sup_{\| \theta'-\theta _{0} \| >\delta} M(\theta')\xlongequal{\text{def}} \varepsilon_{\delta}>0
$$
另一方面，依 $\hat{\theta}_{n}$ 的定义，有 $\mathbb{M}_{n}(\hat{\theta}_{n})\geq \mathbb{M}_{n}(\theta _{0})$ ，于是
$$
\begin{align}
M(\theta _{0})-M(\hat{\theta}_{n})&\leq M(\theta _{0})-\mathbb{M}_{n}(\theta _{0})+\mathbb{M}_{n}(\hat{\theta}_{n})-M(\hat{\theta}_{n})\\&
\leq 2\sup_{\theta \in\Theta}\left| \mathbb{M}_{n}(\theta)-M(\theta) \right| 
\end{align}
$$
进而有概率的估计
$$
\mathbb{P}(A_{n})\leq \mathbb{P}\left( 2\sup_{\theta \in\Theta}\left| \mathbb{M}_{n}(\theta)-M(\theta) \right| \geq \varepsilon_{\delta} \right) 
$$

现在问题就被转化为了，何时有 $\sup_{\theta \in\Theta}\left| \mathbb{M}_{n}(\theta)-M(\theta) \right|\to0$
呢？假如再额外多写一步，即希望
$$
\sup_{\theta \in\Theta}\left| \mathbb{P}_{n}m(\cdot,\theta)-\mathbb{P}m(\cdot,\theta) \right|\xrightarrow{\text{a.s.} \;(\mathbb{P})} 0
$$
这可以用经验过程理论来解决，只需要函数类 $\{ m(\cdot,\theta) \}_{\theta \in\Theta }$ 是 [[一致大数定律、Glivenko-Cantelli 类|GC 类]]即可，至于 GC 类的验证，则可见笔记 [[Rademacher 复杂度、度量熵]] 。于是我们证明了如下定理

**定理** 对于上述 M 估计问题，若
1. 识别性条件：真值 $\theta _{0}$ 是 $M(\theta)$ 的唯一最大值点
2. 函数类 $\{ m(\cdot,\theta) \}_{\theta \in\Theta }$ 是 GC 类
则 $\hat{\theta}_{n}$ 是 $\theta _{0}$ 的强相合估计

> [!remark]-
> 弱 GC 类对应于相合估计，GC 类对应于强相合估计，十分合理，只不过单独对弱 GC 类的判定讨论较少。

---
*Reference:* [[lecture3.pdf]]

---
*2025-12-2*

