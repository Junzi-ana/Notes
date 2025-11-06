---
{}
---
#SmallEssays/数理统计  

本篇笔记解决经验似然比的极限分布问题。我们此前在[[似然比检验的 Wilks 定理]]中讨论了参数估计中似然比的渐近分布问题，在非参数情形下，我们则考虑[[非参数回归：经验似然方法|经验似然比]]。尽管在表达式上略显复杂，但仍然有类似的 Wilks 定理。

**定理** 设 $x_{1}, ~ x_{2}, \cdots,~ x_{n}\in \mathbb{R}^{d}$ 是来自总体 $F_{0}$ 的简单随机样本，$F_{0}$ 的均值向量为 $\mu$，协方差阵 $\Sigma$ 的秩为 $d$，记经验似然比为
$$
R(\mu)=\max\{ \prod^{n}_{i=1}np_{i} : \sum^{n}_{i=1} p_{i}=0,~ \sum^{n}_{i=1} p_{i}x_{i}=\mu,~ p_{i}\geq 0\}
$$
则当 $n\to \infty$ 时，$-2\ln R(\mu)$ 有渐近分布 $\chi^{2}_{d}$ 。

仍然，我们只简单介绍其证明思路，这已经够长了。

**证明** 为了计算 $R(\mu)$，使用 Lagrange 乘子法。令
$$
f(\lambda_{1}, \lambda_{2})=\sum^{n}_{i=1} \ln(np_{i})-\lambda_{1}(\sum^{n}_{i=1} p_{i}-1)-\lambda_{2}^{T}(\sum^{n}_{i=1} p_{i}x_{i}-\mu)
$$
并求解方程组
$$
\frac{\partial f}{\partial p_{i}} =\frac{1}{np_{i}}-\lambda_{1}-\lambda ^{T}_{2}x_{i}=0,\quad i=1,\cdots,n
$$
对 $i$ 求和得到 $\lambda_{1}=1-\lambda_{2}^{T}\mu$ 。代入并改记 $\lambda_{2}$ 为 $\lambda$，解得最优权重为 $p_{i}=\frac{1}{1+\lambda ^{T}(x_{i}-\mu)}$，进而得到
$$
-2\ln R(\mu)=2\sum^{n}_{i=1} \ln(1+\lambda ^{T}(x_{i}-\mu))
$$
为了进行 Taylor 展开，需要先对 $\lambda$ 进行估阶。由于中心极限定理，$\bar{x}-\mu=O_{p}(n^{-\frac{1}{2}})$；又由总体二阶矩存在， $S=\frac{1}{n}\sum^{n}_{i=1}(x_{i}-\mu)(x_{i}-\mu)^{T}=O_{p}(1)$ ；又由 Borel-Cantelli 定理，$\max_{i}\|x_{i}-\mu\|=o_{p}(n^{\frac{1}{2}})$，事实上，这是因为样本方差存在，有 $\sum^{\infty}_{n=0}\mathbb{P}(\| x_{i}-\mu \|^{2}>n)<\infty$，从而 $\|x_{i}-\mu\|>\sqrt{ n }$ 只可能发生有限次。

将 $p_{i}$ 代入估计方程，并整理得到
$$
\sum^{n}_{i=1} (x_{i}-\mu)=\sum^{n}_{i=1} (x_{i}-\mu) \frac{\lambda ^{T}(x_{i}-\mu)}{1+\lambda ^{T}(x_{i}-\mu)}
$$
等式两边同乘 $\frac{\lambda ^{T}}{n}$ ，并记 $\lambda=\left\| \lambda \right\|\theta$，$\theta$ 是单位向量，得
$$
\begin{align}
\theta ^{T}(\bar{x}-\mu)&=\left\| \lambda \right\| \cdot \frac{1}{n}\sum^{n}_{i=1}\theta ^{T} \frac{(x_{i}-\mu)(x_{i}-\mu)^{T} }{1+\left\| \lambda \right\|\theta ^{T}(x_{i}-\mu) }\theta\\
&\geq   \frac{\left\| \lambda \right\|}{1+\left\| \lambda \right\|\max_{i}\left\| x_{i}-\mu \right\|  }  \cdot( \theta ^{T}S\theta)
\end{align}

$$
忽略单位向量带来的影响，进一步化简得到
$$
 O_{p}(n^{-\frac{1}{2}})    \gtrsim \frac{1}{\left\| \lambda \right\|^{-1}+o_{p}(n^{\frac{1}{2}})}
$$
即求得 $\lambda =O_{p}(n^{-\frac{1}{2}})$，进而 $\lambda ^{T}(x_{i}-\mu)=o_{p}(1)$ 。

现对估计方程进行 Taylor 展开得
$$
\frac{1}{n}\sum^{n}_{i=1}(x_{i}-\mu)\big( 1-\lambda ^{T}(x_{i}-\mu) +o_{p}(\lambda ^{T}(x_{i}-\mu))\big)  =0
$$
化简得
$$
(\bar{x}-\mu)-S\lambda+o_{p}(n^{-\frac{1}{2}})=0
$$
进而得到
$$
\lambda=S^{-1}(\bar{x}-\mu)+o_{p}(n^{-\frac{1}{2}})
$$

同时对 $-2\ln R(\mu)$ 作 Taylor 展开得
$$
-2\ln R(\mu)=2n\lambda ^{T}(\bar{x}-\mu)-n\lambda ^{T}S\lambda+O_{p}\big( \sum^{n}_{i=1}( \lambda ^{T}(x_{i}-\mu))^{3} \big) 
$$
由 $\sum^{n}_{i=1}( \lambda ^{T}(x_{i}-\mu))^{3}\leq \left\| \lambda \right\|\max_{i}\left\| x_{i}-\mu \right\|\cdot n\lambda ^{T} S\lambda$ 得
$$
\begin{align}
-2\ln R(\mu)&=2n\lambda ^{T}(\bar{x}-\mu)-n\lambda ^{T}S\lambda+o_{p}(1)\\
&=\sqrt{ n }(\bar{x}-\mu)^{T}S^{-1}[\sqrt{ n }(\bar{x}-\mu)]+o_{p}(1)
\end{align}

$$
最后由中心极限定理知 $\sqrt{ n }(\bar{x}-\mu)\xrightarrow{d}N(0,S)$ ，从而 $-2\ln R(\mu)\xrightarrow{d}\chi^{2}_{d}$ 。

---
*Reference:*
	[[回归分析与线性模型第二章.pdf]]
	[[回归分析与线性模型第二章supp.pdf]]

---
*2025-10-28*






