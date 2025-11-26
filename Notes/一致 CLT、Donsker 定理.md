---
{}
---
#SmallEssays/数理统计  

在此前，我们将强大数定律推广为了[[一致大数定律、Glivenko-Cantelli 类|一致大数定律]]，并且它的一个特例就是 Glivenko-Cantelli 定理，那么与之对偶的，中心极限定理也可以推广成一致版本，而此前介绍的[[非参数估计：数理统计基本定理|数理统计基本定理]]就是一个特例。采用记号 $\mathbb{G}_{n}f=\sqrt{ n }(\mathbb{P}_{n}-\mathbb{P})f$，对于固定的 $f$，$\mathbb{G}_{n}f$ 是一个离散随机过程，称为**经验过程**。我们认为 $\mathbb{G}_{n}f$ 可能收敛到一个 Gauss 元 $\mathbb{G}_{\mathbb{P}}f$ 。为此我们引入如下定义

**定义** 设 $\mathcal{F}$ 是函数类，称其为 **Donsker 类**，若 $\mathbb{G}_{n}$ 在如下意义上收敛到紧致 *(tight)* 的 Gauss 场 $\mathbb{G}_{\mathbb{P}}$
1. 有限维分布收敛：任取有限 $f_{1}, \cdots,~ f_{k}\in \mathcal{F}$，有
$$
(\mathbb{G}_{n}f_{1}, ~\cdots,\mathbb{G}_{n}f_{k})\xrightarrow{d}(\mathbb{G}_{\mathbb{P}}f_{1}, \cdots,~ \mathbb{G}_{\mathbb{P}}f_{k}) 
$$
2. 渐近等度连续性：设 $\mathcal{F}$ 上有度量 $d$，对任意 $\varepsilon>0$ 有
$$
\limsup_{ n \to \infty } \mathbb{P}\left( \sup_{d(f,g)<\delta} \left| \mathbb{G}_{n}f-\mathbb{G}_{n} g\right|>\varepsilon  \right) \to0,\quad \delta \to0
$$
这等价于 $\mathbb{G}_{n}$ 在 $\mathscr{l}^{\infty}(\mathcal{F})$ 中弱收敛到 $\mathbb{G}_{\mathbb{P}}$ 。

类似地可以通过对覆盖数的研究，来判断一个函数类是否是 Donsker 类，只不过非常复杂，在此仅做介绍。

**Donsker 定理** 设 $\mathcal{F}$ 有控制函数 $F$ 满足 $\mathbb{P}F^{2}<\infty$，若如下 **Dudley 一致熵积分**
$$
\int^{1}_{0} \sup_{\mathbb{Q}}\sqrt{ \log N\big(\varepsilon\cdot \| F \| _{L^{2}(\mathbb{Q})},\mathcal{F},L^{2}(\mathbb{Q})\big) } \; \mathrm{d}\varepsilon 
$$
有限，其中 $\mathbb{Q}$ 是任意概率测度，则 $\mathcal{F}$ 是 Donsker 类。

可以证明，指示函数类 $\mathcal{F}=\{ \mathbb{1}_{\{ \;\cdot\;\leq x \}} \}_{x\in \mathbb{R} }$ 是 Donsker 类，此时 $\mathbb{G}_{n}\mathbb{1}_{(-\infty,x]}=\sqrt{ n }(\widehat{F}_{n}(x)-F(x))$ ，简记为 $\mathbb{G}_{n}(x)$ ，其中 $F$ 是总体的分布，$\widehat{F}_{n}$ 是经验分布。$\mathbb{G}_{n}(x)$ 均值为 $0$，计算其协方差
$$
\mathbb{E}[\mathbb{G}_{n}(s)\mathbb{G}_{n}(t)]=\frac{1}{n}\mathbb{E}\left[ \sum^{n}_{i,j}\big( \mathbb{1}_{\{ X_{i}\leq s \}}-F(s) \big) \big( \mathbb{1}_{\{ X_{i}\leq t \}}-F(t) \big)   \right] 
$$
由于独立性，其交叉项为 $0$ ，即
$$
\begin{align}
\mathbb{E}[\mathbb{G}_{n}(s)\mathbb{G}_{n}(t)]&=\frac{1}{n}\mathbb{E}\left[ \sum^{n}_{i=1}\big( \mathbb{1}_{\{ X_{i}\leq s \}}-F(s) \big) \big( \mathbb{1}_{\{ X_{i}\leq t \}}-F(t) \big)   \right]\\
&=\mathbb{E}\left[ \big( \mathbb{1}_{\{ X_{1}\leq s \}}-F(s) \big) \big( \mathbb{1}_{\{ X_{1}\leq t \}}-F(t) \big) \right] \\
&=\mathbb{E}\left[ \mathbb{1}_{\{ X_{1}\leq s \}}\mathbb{1}_{\{ X_{1}\leq t \}} \right] -F(s)\mathbb{E}\mathbb{1}_{\{ X_{1}\leq t \}}\\&-F(t)\mathbb{1}_{\{ X_{1}\leq s \}}-F(s)F(t)\\
&=F(s\wedge t)-F(s)F(t)
\end{align}
 
$$
从而极限过程 $\mathbb{G}_{\mathbb{P}}(x)$ 是布朗桥。至此我们可谓是在一定程度上补足了数理统计基本定理中一带而过的收敛性部分。


---
*Reference:* [[lecture3.pdf]]

---
*2025-11-26*








