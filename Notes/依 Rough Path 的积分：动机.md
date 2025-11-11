#SmallEssays/RoughPath 

在最早时，笔记 [[Rough Path 的动机、Lévy's Area]] 中就指出了，由于 Brown 运动的轨道过于粗糙没有办法像 L-S 积分那样按路径定义随机积分，而 Itô 积分也回避了这个问题。而现如今，我们定义了 [[Rough Path 的 Chen's Relation|Rough Path]] ，也说明了 [[Brown 轨道作为 Rough Path：Kolmogorov准则|Brown 运动的轨道是 Rough Path]]，现在我们可以开始尝试解决这个问题了。

在此之前，我们仍然有必要简单回忆一下传统的积分定义。我们希望定义 $\displaystyle\int^{T}_{0} Y_{t}  \; \mathrm{d}X_{t}$ ，在此我们首先假定 $Y_{t}=F(X_{t})$ ，其中 $V,~W$ 是两个 Banach 空间，$X$ 是 $V$ 上的轨道，即有 $X:[0, T]\to V$，另外希望 $\displaystyle\int^{\cdot}_{0} Y_{t}  \; \mathrm{d}X_{t}$ 是 $W$ 上的轨道，此时应有 $Y:[0,T]\to \mathcal{L}(V,W)$ ，那么 $F:V\to \mathcal{L}(V,W)$ 。例如在金融数学中，$X_{t}$ 是 Brown 运动而 $Y_{t}$ 是波动率矩阵 $\sigma_{t}$ 。

倘若 $X_{t}$ 有足够的光滑性，假设有分划 $P$ ，沿用笔记 [[Rough Path 的 Chen's Relation]] 中的记号，我们可以写出 Riemann 和
$$
\int^{T}_{0}F(X_{t})  \; \mathrm{d}X_{t} =\lim_{ \| P \|  \to 0}  \sum_{u,v\in P} F(X_{u})X_{u,v}
$$
其中 $u,v$ 取遍 $P$ 的所有相邻分点。

然而，当 $X_{t}$ 缺少必要的光滑性时，我们却不能这么做，有可能是因为用 $F(X_{u})$ 来代替 $X_{t}$ 在 $[u,v]$ 上的值有些过于草率了，倘若用更精细的估计会怎么样呢？于是尝试用 $F$ 在 $X_{u}$ 处的一阶 Taylor 展开来替换上面的 $F(X_{u})$ （相当于展开到 $0$ 阶），即有
$$
F(X_{t})\approx F(X_{u}) +DF(X_{u})X_{u,t}
$$
此处假设 $F$ 具有所需的光滑性，那么 $DF$ 应当理解为 $F$ 在 $X_{u}$ 处的 Fréchet 导数，$DF(X_{s})\in \mathcal{L}(V,\mathcal{L}(V,W))\cong\mathcal{L}(V^{\otimes2},W)$ 。在两端形式地在 $[u,v]$ 上积分，得到
$$
\int^{v}_{u} F(X_{t}) \; \mathrm{d}X_{t} \approx \int^{v}_{u} F(X_{u}) \; \mathrm{d}X_{t} +\int^{v}_{u} DF(X_{u})X_{u,t}\otimes \mathrm{d}X_{t}  
$$
注意到 $\displaystyle X_{u,v}=\int^{v}_{u}   \mathrm{d}X_{t}$ 且回顾定义 $\mathbb{X}_{u,v}=\displaystyle\int^{v}_{u} X_{u,t}\otimes \mathrm{d}X_{t}$，我们可以尝试定义
$$
\int^{T}_{0} F(X_{t}) \; \mathrm{d}\boldsymbol{X}_{t}=\lim_{ \| P \|  \to 0}\sum_{u,v\in P}\big( F(X_{u})X_{u,v}+DF(X_{u})\mathbb{X}_{u,v} \big)
$$
作为 **$F(X_{t})$ 对 Rough Path $\boldsymbol{X}_{t}$ 的积分**。

当然，以上的所有的推导都是非严格的，我们还须证明这个极限存在且与分划无关，这里面涉及更细致的研究，将在之后的笔记中探讨。

---
*Reference: A Course on Rough Paths, Peter K. Friz*

---
*2025-11-11*


















