---
{}
---
#SmallEssays/数理统计

在笔记 [[M 估计：基本问题与相合性]] 中，我们介绍了 M 估计的一般理论和主要研究问题，并给出了其相合性的条件，即要函数类 $\{ m(\cdot,\theta) \}_{\theta \in\Theta }$ 是 [[一致大数定律、Glivenko-Cantelli 类|GC 类]]。本文研究关于收敛速度的问题，事实上，很容易猜出，在适当的条件下收敛速度就是 $\sqrt{ n }$ 阶的且由渐近正态性，只不过与之对应地，我们需要函数类 $\{ m(\cdot,\theta) \}_{\theta \in\Theta }$ 是 [[一致 CLT、Donsker 定理|Donsker 类]]。沿用之前的记号和上下文，我们直接给出如下定理

**定理** 若前述 M 估计问题满足
1. 真值 $\theta _{0}$ 是 $M(\theta)$ 的唯一最大值点
2. 函数类 $\{ m(\cdot,\theta) \}_{\theta \in\Theta }$ 是 Donsker 类
3. $M(\theta)$ 满足一定的正则性条件
则有渐近正态性 
$$
\sqrt{ n }(\hat{\theta}_{n}-\theta_{0})\xrightarrow{d}N(0,H^{-1}\Sigma H^{-1})
$$
其中 $\Sigma=\mathbb{E}\psi(X;\theta_{0}) \psi(X;\theta_{0}) ^{T}$，$\psi(x;\theta)=\nabla_{\theta}m(x;\theta)$ 是得分向量，$H=\nabla^{2}_{\theta}m(x;\theta_{0})$ 。 `[!!air-vent|Proved by DeepSeek|117, 188, 255]`

> [!note]
> 当 $m(\cdot,\theta)$ 满足一定的可微性和关于 $\theta$ 的 Lipschitz 条件时，其导数类 $\{ \psi(\cdot,\theta) \}_{\theta \in\Theta }$ 也是 Donsker 类，下述证明中用到的 Hesse 矩阵属于 GC 类也由此而来。

这个定理需要额外对正则性作一些要求，与 [[似然比检验的 Wilks 定理#^e5b801|MLE 的渐近正态性]]的证明有许多相似之处，本文只简要介绍一下证明思路。

**证明** 定义 $\mathbb{P}_{n}\psi(\cdot,\theta)=\varPsi_{n}(\theta),~\mathbb{P}\psi(\cdot,\theta)=\varPsi(\theta)$，记经验过程 
$$
\mathbb{G}_{n}\psi(\cdot,\theta)=\sqrt{ n }(\mathbb{P}_{n}-\mathbb{P})\psi(\cdot,\theta)=\sqrt{ n }(\varPsi_{n}(\theta)-\varPsi(\theta))
$$
由于 $\hat{\theta}_{n}$ 是 M 估计，于是 $\varPsi_{n}(\hat{\theta}_{n})=0$ 。在 $\theta_{0}$ 处对 $\varPsi_{n}$ 展开得
$$
0=\varPsi_{n}(\hat{\theta}_{n})=\varPsi_{n}(\theta_{0})+\nabla \varPsi_{n}(\theta_{*})(\hat{\theta}_{n}-\theta_{0})
$$
一方面，因为 $\varPsi(\theta_{0})=0$ ，也有
$$
\sqrt{ n }\varPsi_{n}(\theta_{0})=\mathbb{G}_{n}\psi(\cdot,\theta_{0})\xrightarrow{d}\mathbb{G}_{\mathbb{P}}\psi(\cdot,\theta_{0}) \sim N(0,~ \Sigma)
$$
且若 $\{\nabla \varPsi_{n}(\theta)\}_{\theta \in\Theta}$ 是 GC 类，则有一致收敛
$$
\sup_{\theta ^{*}}|\nabla \varPsi_{n}(\theta_{*})-H|\xrightarrow{\mathbb{P}}0 
$$
结合得到
$$
\sqrt{ n }(\hat{\theta}_{n}-\theta)=-H^{-1}\mathbb{G}_{\mathbb{P}}\psi(\cdot,\theta_{0})+o_{p}(1)
$$
即为所求。

---
*2025-12-10*