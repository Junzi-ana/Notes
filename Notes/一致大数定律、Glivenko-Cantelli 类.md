---
{}
---
#SmallEssays/数理统计 

正如中心极限定理可以推出弱大数定律一般，[[非参数估计：数理统计基本定理|数理统计基本定理]]也可以简单地推出
$$
D_{n}(\omega)=\sup_{x\in \mathbb{R}}\left| \widehat{F}(x;\omega)-F(x) \right| \xrightarrow{\mathbb{P}}0 
$$
但是是否有几乎必然收敛呢？亦如强大数定律一样，几乎必然收敛虽然不能直接得到，但它确实是成立的，可以说它是另一个基本定理。

**Glivenko-Cantelli 定理** 
$$
D_{n}(\omega)\to0\quad \text{a.s.} 
$$

定理的证明可以参考*施利亚耶夫《概率 I》第 412 页*，我们不在其证明上多费口舌，因为我们急于更进一步。

经验分布 $\widehat{F}(x;\omega)$ 是对 $\mathbb{P}(X(\omega)\leq x)$ 的估计，从而实际上是对期望 $\mathbb{E}(\mathbb{1}_{\{ X\leq x \}})$ 的估计。对于这样一个期望，我们采用的估计方式是简单的加和取平均值，记为 $\widehat{\mathbb{E}}(\mathbb{1}_{\{ X\leq x \}})$ 。现在，将示性函数换为一般的 $f$，我们发现 Glivenko-Cantelli 定理实际上证明了对于某一族函数 $\mathcal{F}=\{ \mathbb{1}_{\{ \;\cdot\;\leq x \}} \}_{x\in \mathbb{R} }$，一致成立这样的强大数定律
$$
\sup_{f\in \mathcal{F}} |\widehat{\mathbb{E}}f(X)-\mathbb{E}f(X)|\to0\quad \text{a.s.} 
$$
以下我们改用经验过程理论中惯用的记号，因为此后我们的研究重点在于函数类 $\mathcal{F}$，故总是省略总体 $X$，记 $\mathbb{P}f$ 为 $\mathbb{E}f(X)$ ，记 $\mathbb{P}_{n}f$ 为经验测度的期望 $\mathbb{P}_{n}f=\frac{1}{n}\sum^{n}_{i=1}f(X_{i})$ 。借用这个记号，上式改写成
$$
\sup_{f\in \mathcal{F}}| \mathbb{P}_{n}f-\mathbb{P}f |\to0\quad \text{a.s.} 
$$

既然写成了这个形式，那么方向也明确了：对于怎样的 $\mathcal{F}$，上面的**一致强大数律**成立呢？这样似乎有点难以下手，因此我们改换一下问题的表述

**定义** $X$ 是总体，设 $\mathcal{F}$ 由一些满足 $\mathbb{P}|f|<\infty$ 的可测函数 $f$ 作成，若其满足
$$
\sup_{f\in \mathcal{F}}| \mathbb{P}_{n}f-\mathbb{P}f| \xrightarrow{\text{a.s.} \;(\mathbb{P})} 0
$$
则称 $\mathcal{F}$ 为**强（弱）Glivenko-Cantelli 类**，简称 **GC 类（弱 GC 类）**。

记 $\mathcal{S}=\{ X_{1}, \cdots,~ X_{n} \}$ 为数据集，$D_{n}(\mathcal{F})=\sup_{f\in \mathcal{F}}| \mathbb{P}_{n}f-\mathbb{P}f|$，我们接下去的推导过程主要分两部分：
1. 证明 $D_{n}$ 集中在 $\mathbb{E}_{\mathcal{S}}(D_{n})$ 附近
2. 估计 $\mathbb{E}_{\mathcal{S}}(D_{n})$

对于第一部分，我们需要用到如下**集中不等式**

**定理（McDiarmid 不等式）** 假设函数 $g(x_{1}, \cdots,~ x_{n})$ 满足有界差条件
$$
|g(\cdots,x_{i},\cdots)-g(\cdots,x_{i}',\cdots)|\leq c_{i}
$$
即当 $g$ 只有第 $i$ 个变元不同时，其差有界。若 $X_{1}, \cdots,~ X_{n}$ 相互独立，则成立不等式
$$
\mathbb{P}\left( g(X_{1}, \cdots,~ X_{n}) -\mathbb{E}g(X_{1}, \cdots,~ X_{n})\geq t\right)\leq  \exp \left( -\frac{2t^{2}}{\sum^{n}_{i=1}c_{i}^{2} } \right) 
$$
可以验证，当 $f\in \mathcal{F}$ 一致有界时，$D_{n}$ 是满足有界差条件的，于是完成了第一部分。

至于第二部分，在给定数据集 $\mathcal{S}$ 时，$\mathbb{P}_{n}f$ 可能被数据驱动地解决，但 $\mathbb{P}f$ 是依赖于总体的分布的，而总体的分布又是未知的，此时需要用到一个非常重要的**对称化技巧**。

引入 $\mathcal{S}$ 的独立拷贝 $\mathcal{S}'$，则
$$
\begin{align}
\mathbb{E}_{\mathcal{S}}\left[ \sup_{f\in \mathcal{F}}(\mathbb{P}_{n}f-\mathbb{P}f) \right]&= \mathbb{E}_{\mathcal{S}}\left[ \sup_{f\in \mathcal{F}}(\mathbb{P}_{n}f-\mathbb{E}_{\mathcal{S'}}[\mathbb{P}_{n}'f]) \right]\\
{\scriptsize(\text{sup is convex, Jensen})}&\leq \mathbb{E}_{\mathcal{S},\mathcal{S}'}\left[\sup_{f\in \mathcal{F}}(\mathbb{P}_{n}f-\mathbb{P}_{n}'f)  \right] \\
&=\mathbb{E}_{\mathcal{S},\mathcal{S}'}\left[ \sup_{f\in \mathcal{F}} \frac{1}{n}\sum^{n}_{i=1}(f(X_{i})-f(X_{i}'))  \right] 
\end{align}
$$
注意到由于 $X_{i},~X_{i}'$ 独立同分布，我们可以随机地决定每一项 $f(X_{i})-f(X_{i}')$ 的符号，且又由于每对 $(X_{i},X_{i}')$ 相互独立，这一行为是可以跨过上确界运算的。因此引入随机符号 $\varepsilon _{i}$ ，独立同分布且等概率取 $\pm1$ ，于是得到
$$
\mathbb{E}_{\mathcal{S},\mathcal{S}'}\left[\sup_{f\in \mathcal{F}}(\mathbb{P}_{n}f-\mathbb{P}_{n}'f)  \right]=\mathbb{E}_{\mathcal{S},\mathcal{S}',\varepsilon}\left[ \sup_{f\in \mathcal{F}} \frac{1}{n}\sum^{n}_{i=1}\varepsilon _{i}(f(X_{i})-f(X_{i}'))  \right] 
$$
再引入记号
$$
\mathfrak{R}_{n}(\mathcal{F})=\mathbb{E}_{\mathcal{S},\varepsilon} \left| \sup_{f\in \mathcal{F}} \frac{1}{n}\sum^{n}_{i=1}\varepsilon _{i}f(X_{i})  \right|   
$$
为函数类 $\mathcal{F}$ 的 **Rademacher 复杂度**，则利用三角不等式，得到最终的估计
$$
\mathbb{E}_{\mathcal{S}}D_{n}\leq 2\mathfrak{R}_{n}(\mathcal{F})
$$
最后当 $\mathfrak{R_{n}}(\mathcal{F})\to0$ 时，借助 Borel-Cantelli 定理可得到
$$
D_{n}(\mathcal{F})\to0\quad \text{a.s.}
$$
于是我们非常简略地证明了如下定理

**定理** 设 $\mathcal{F}$ 是一致有界的函数类，若 $\mathfrak{R}_{n}(\mathcal{F})\to0$，则 $\mathcal{F}$ 是 GC 类。

现在，我们将估计 $D_{n}(\mathcal{F})$ 的问题转化为估计不依赖分布的 $\mathfrak{R}_{n}(\mathcal{F})$ 。当给定 $\mathcal{S}$ 时，$\mathfrak{R}_{n}(\mathcal{F})$ 不再依赖样本的分布，而只依赖于数据点和函数族 $\mathcal{F}$ 的内在结构，对此，我们有度量熵、组合维数等方法能够分析，碍于篇幅所限，本篇笔记在此处停笔。

---
*Reference:*
1. *概率（第一卷）, A. H. 施利亚耶夫*
2. [[lecture3.pdf]]

---
*2025-11-18*