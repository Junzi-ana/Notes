---
{}
---
#SmallEssays/随机分析 

对于一般的 SDE
$$
\mathrm{d} X_{t}=b(t,X_{t})\;\mathrm{d} t+\sigma(t,X_{t})\;\mathrm{d} W_{t}
$$
由于 Itô 积分不是对每条样本轨道 $\omega$ 单独定义的，解映射 $S:W\to X$ 几乎无法被显式表出，而且一般也不是连续的，部分细节见此笔记：[[Rough Path 的动机、Lévy's Area]] 。

然而，对于一些特殊的 SDE，建立**显式的解映射**并不困难，例如
$$
\;\mathrm{d} X_{t} = b(t,X_{t})\;\mathrm{d} t+\mathrm{d} W_{t}
$$
直接积分可得到
$$
X_{t}=\xi+\int^{t}_{0} b(s,X_{s}) \; \mathrm{d}t+W_{t} 
$$
从而得到了显式的解映射 $S:W\to X$，它显然是连续线性的。

事实上，对于一大类的 SDE，我们都可以用一个巧妙的变换来建立显式的解映射。具体而言，有如下定理

**定理** 设 $u:[0,\infty)\times \mathbb{R}^{d}\to \mathbb{R}^{d}$ ，是 $C^{1,2}$ 类函数，满足方程
$$
\frac{\partial u_{i}}{\partial t} =b(t,u(t,y)),\quad \frac{\partial u_{i}}{\partial y_{j}}  = \sigma_{ij}(t,u(x,y))
$$
其中 $b_{i}(t,x)$ 和 $\sigma_{ij}(t,x)$ 也是 $C^{1,2}$ 类函数。则 $X_{t}=u(t,W_{t})$ 是如下 **Stratonovich 型 SDE** 的解
$$
\mathrm{d} X_{t}=b(t,X_{t})\;\mathrm{d} t+\sigma(t,X_{t})\circ\mathrm{d} W_{s}
$$

---
*Reference: Brownian Motion and Stochastic Calculus, Ioannis Karatzas, Steven E. Shreve*

---
*2025-8-24*