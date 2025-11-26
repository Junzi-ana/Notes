---
{}
---
#SmallEssays/数理统计 

延续上篇笔记[[一致大数定律、Glivenko-Cantelli 类]]的内容，要说明 $\mathcal{F}$ 是 GC 类，只需要去计算 $\mathfrak{R}_{n}(\mathcal{F})\to0$，在实践中由于不知道样本分布，我们只能计算经验 Rademacher 复杂度
$$
\widehat{\mathfrak{R}}_{\mathcal{S}}(\mathcal{F})=\mathbb{E}_{\varepsilon} \sup_{f\in \mathcal{F}} \left| \frac{1}{n}\sum^{n}_{i=1}\varepsilon _{i}f(X_{i})   \right|  
$$
不过由于 $\widehat{\mathfrak{R}}_{\mathcal{S}}(\mathcal{F})$ 作为 $\mathcal{S}$ 的函数满足有界差条件，利用前文提及的 McDiarmid 不等式和 Borel-Cantelli 定理，就可以得到，$|\widehat{\mathfrak{R}}_{\mathcal{S}}(\mathcal{F})-\mathfrak{R}_{n}(\mathcal{F})|\to0\quad\text{a.s.}$

接下来我们尝试估计经验 Rademacher 复杂度。为此我们从一个较为简单的情形考虑，即 $\mathcal{F}=\{ f_{i} \}_{1}^{m}$ 只包含有限个元素。记 $Z_{f}=\frac{1}{n}\sum^{n}_{i=1}\varepsilon _{i}f(X_{i})$ ，其均值为 $0$，且一致有界，因而是次高斯变量，方差参数 $\sigma_{f}^{2}\leq \frac{M^{2}}{n}$ 。于是利用如下引理可得到其上界。

**次高斯变量的极大不等式** 设 $\mathcal{F}=\{ f_{i} \}_{1}^{m}$ ，且参数 $\sigma _{i}\leq\sigma$，即对 $i=1, \cdots, m$ 和任意 $\lambda>0$，成立 $\mathbb{E}e^{\lambda Z_{i}}\leq e^{\frac{\lambda^{2}\sigma^{2}}{2}}$，则有
$$
\begin{align}
\mathbb{E}\max_{\mathcal{F}}Z_{f}&\leq \sigma \sqrt{ 2\log(m) }\\
\mathbb{E}\max_{\mathcal{F}}|Z_{f}|&\leq C\sigma \sqrt{ 2\log(m) }
\end{align}
$$
$C$ 是一个不太大的常数，一般可以取作 $\sqrt{ 2 }$ 。

当 $\mathcal{F}$ 不是有限集时，我们希望能用有限个元素来代表 $\mathcal{F}$ 。设 $\delta>0$，$\mathcal{G}_{\delta}$ 是 $\mathcal{F}$ 的一个有限 $\delta$ 覆盖，其覆盖数依赖于范数的选取，记为 $N(\delta,\mathcal{F},\| \cdot \|)$ 。当选用 $L^{\infty}$ 范数时，有
$$
\begin{align}
\sup_{f\in \mathcal{F}}\left| \frac{1}{n}\sum^{n}_{i=1}\varepsilon _{i}f(X_{i}) \right|   &\leq \sup_{g\in \mathcal{G}_{\delta}}\left| \frac{1}{n}\sum^{n}_{i=1}\varepsilon _{i}g(X_{i}) \right|   +\delta\\
&\lesssim \sqrt{ \frac{\log N(\delta,\mathcal{F},\| \cdot \| )}{n} }+\delta
\end{align}

$$
因此，当 $\delta_{n}\to0,~ \frac{\log N(\delta_{n},\mathcal{F},\| \cdot \|)}{n}\to0$ 时，$\mathcal{F}$ 是 GC 类。

此外，利用 **Dudley 熵积分**，可以得到更加精细的界
$$
\widehat{\mathfrak{R}}_{\mathcal{S}}(\mathcal{F})\lesssim \frac{1}{\sqrt{ n }}\int^{R}_{0} \sqrt{ \log N(\varepsilon,\mathcal{F},\| \cdot \| ) } \; \mathrm{d}\varepsilon 
$$
通常选用 $L^{\infty}$ 范数或者离散 $L^{2}$ 范数 $\| f \|_{2}=\sqrt{\frac{1}{n} \sum^{n}_{i=1}f^{2}(x_{i}) }$ ,其中 $R$ 是 $\mathcal{F}$ 的直径。

**例 1** 指示函数类 $\mathcal{F}=\{\mathbb{1}_{\{ x\leq c \}}\}_{c\in \mathbb{R}}$

**分析** 取定样本 $\mathcal{S}=\{ x_{1}, \cdots,~ x_{n} \}$ ，对于两个不同的指示函数 $\mathbb{1}_{x\leq c}$ 和 $\mathbb{1}_{x\leq c'}$ ，计算其在 $\mathcal{S}$ 上的 $L^{2}$ 距离
$$
\|\mathbb{1}_{x\leq c}-\mathbb{1}_{x\leq c'}  \|_{2}\leq  \sqrt{ \frac{k}{n} }
$$
其中 $k$ 为落在 $c$ 和 $c'$ 之间的样本数。因此选取不同的 $c$ 落在每两个样本之间，即可得到
$$
N(\varepsilon,\mathcal{F},L^{2})\leq n+1
$$
从而 $\frac{\log N(\varepsilon,\mathcal{F},L^{2})}{n}\to0$ ，即 $\mathcal{F}$ 是 GC 类，于是我们得到了 [[一致大数定律、Glivenko-Cantelli 类|Glivenko-Cantelli 定理]] 。

**例 2** $[0,1]\to[0,1]$ 的 Lipschitz 函数类 $\mathcal{F}$，且系数 $L\leq1$

**分析** 将 $[0,1]$ 按步长 $\varepsilon$ 均匀剖分，对于 $f\in \mathcal{F}$，用网格上的分段常值 $\tilde{f}$ 逼近 $f$，如图所示，显然有 $\| \tilde{f}-f \|_{\infty}\leq \varepsilon$ 。

```tikz
\usepackage{pgfplots}
\usepackage{pgf}
\begin{document}
\begin{tikzpicture}[font=\large ]
\draw[->, thick] (0,0) -- (6.5,0) ;
\draw[->, thick] (0,0) -- (0,6.5) ;
\foreach \t in {1,2,...,6}{
	\draw[dashed, gray] (\t,0) -- (\t,6);
	\draw[dashed, gray] (0,\t) -- (6,\t);}

\draw[thick, domain=0:6, samples=20] plot (\x, {3+(\x-1)*(\x-3)*(\x-5)/15});

\draw[line width=1.25pt, dotted] (0,2)--(1,2) (1,3)--(3,3)  (3,2)--(5,2) (5,3)--(6,3);

\draw (4,3) node[above right]{$f$};
\draw (5,2) node[right]{$\tilde{f}$};
\draw (0,0) rectangle (6,6);

\end{tikzpicture}
\end{document}
```

那么所有可能的分段常值函数有多少个呢？考虑到 Lipschitz 条件，除了第一个节点可以任意取值，后一个节点的值都只能在前一个节点的上下 $\varepsilon$ 范围内选取。忽略上下边界，有
$$
N(\varepsilon,\mathcal{F},L^{\infty}) =\frac{1}{\varepsilon} \cdot3^{\frac{1}{\varepsilon}-1}
$$
对于固定的 $\varepsilon>0$，有
$$
\frac{\log N(\varepsilon,\mathcal{F},L^{\infty})}{\sqrt{ n }}\lesssim \frac{1}{\varepsilon \sqrt{ n }}\to0
$$
从而 $\mathcal{F}$ 是 GC 类。

---
*Reference:* [[lecture3.pdf]]

---
*2025-11-26*