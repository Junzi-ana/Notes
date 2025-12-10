---
{}
---
#SmallEssays/数理统计  

本篇笔记解决经验似然比的极限分布问题。我们此前在[[似然比检验的 Wilks 定理]]中讨论了参数估计中似然比的渐近分布问题，在非参数情形下，我们则考虑[[非参数回归：经验似然方法|经验似然比]]。尽管在表达式上略显复杂，但仍然有类似的 Wilks 定理。

**定理** 设 $x_{1}, ~ x_{2}, \cdots,~ x_{n}\in \mathbb{R}^{d}$ 是来自总体 $F_{0}$ 的简单随机样本，得分函数为 $Z(X;\theta)$，信息阵 $H=\mathbb{E}ZZ^{T}$ 的秩为 $d$，记经验似然比为
$$
R(\theta)=\max\{ \prod^{n}_{i=1}np_{i} : \sum^{n}_{i=1} p_{i}=1,~ \sum^{n}_{i=1} p_{i}Z_{i}=0,~ p_{i}\geq 0\}
$$
则当 $n\to \infty$ 时，$-2\ln R(\theta_{0})$ 有渐近分布 $\chi^{2}_{d}$ 。

仍然，我们只简单介绍其证明思路，这已经够长了。

**证明** 为了计算 $R(\theta)$，使用 Lagrange 乘子法。令
$$
f(\lambda_{1}, \lambda_{2})=\sum^{n}_{i=1} \ln(np_{i})-\lambda_{1}(\sum^{n}_{i=1} p_{i}-1)-\lambda_{2}^{T}(\sum^{n}_{i=1} p_{i}Z_{i})
$$
并求解方程组
$$
\frac{\partial f}{\partial p_{i}} =\frac{1}{np_{i}}-\lambda_{1}-\lambda ^{T}_{2}Z_{i}=0,\quad i=1,\cdots,n
$$
不是一般性令 $\lambda_{1}=1$ 。代入并改记 $\lambda_{2}$ 为 $\lambda$，解得最优权重为 $p_{i}=\frac{1}{n}\frac{1}{1+\lambda ^{T}Z_{i}}$，进而得到
$$
-2\ln R(\theta)=2\sum^{n}_{i=1} \ln(1+\lambda ^{T}Z_{i})
$$
为了 Taylor 展开，需要先对 $\lambda$ 进行估阶。由[[似然比检验的 Wilks 定理#^05167c|中心极限定理]]，记标准化得分 $S_{Z}=\frac{1}{\sqrt{ n }}\sum^{n}_{i=1}Z_{i}=O_{p}(1)$；样本信息阵 $H_{Z}=\frac{1}{n}\sum^{n}_{i=1}Z_{i}Z_{i}^{T}=O_{p}(1)$ ，并利用 Borel-Cantelli 定理，得 $\max_{i}\|Z_{i}\|=o_{p}(n^{\frac{1}{2}})$，事实上，这是因为二阶矩存在，有 $\sum^{\infty}_{n=0}\mathbb{P}(Z^{T}Z>n)<\infty$，从而 $\|Z_{i}\|>\sqrt{ n }$ 只可能发生有限次。

将 $p_{i}$ 代入估计方程，并整理得到
$$
\sum^{n}_{i=1} Z_{i}=\sum^{n}_{i=1} Z_{i} \frac{\lambda ^{T}Z_{i}}{1+\lambda ^{T}Z_{i}}
$$
等式两边同乘 $\frac{\lambda ^{T}}{n}$ ，并记 $\lambda=\left\| \lambda \right\|\xi$，$\xi$ 是单位向量，得
$$
\begin{align}
\frac{1}{\sqrt{ n }}\xi ^{T}S_{Z}&=\left\| \lambda \right\| \cdot \frac{1}{n}\sum^{n}_{i=1}\xi ^{T} \frac{Z_{i}Z_{i}^{T} }{1+\left\| \lambda \right\|\xi ^{T}Z_{i} }\xi\\
&\geq   \frac{\left\| \lambda \right\|}{1+\left\| \lambda \right\|\max_{i}\left\| Z_{i} \right\|  }  \cdot( \xi ^{T}H_{Z}\xi)
\end{align}

$$
忽略单位向量带来的影响，进一步化简得到
$$
 O_{p}(n^{-\frac{1}{2}})    \gtrsim \frac{1}{\left\| \lambda \right\|^{-1}+o_{p}(n^{\frac{1}{2}})}
$$
即求得 $\lambda =O_{p}(n^{-\frac{1}{2}})$，进而 $\lambda ^{T}Z_{i}=o_{p}(1)$ 。

现对估计方程进行 Taylor 展开得
$$
\frac{1}{n}\sum^{n}_{i=1}Z_{i}\big( 1-\lambda ^{T}Z_{i} +o_{p}(\lambda ^{T}Z_{i})\big)  =0
$$
化简得
$$
\frac{1}{\sqrt{ n }}S_{Z}-H_{Z}\lambda+o_{p}(n^{-\frac{1}{2}})=0
$$
进而得到
$$
\lambda=\frac{1}{\sqrt{ n }}H_{Z}^{-1}S_{Z}+o_{p}(n^{-\frac{1}{2}})
$$

同时对 $-2\ln R(\theta)$ 作 Taylor 展开得
$$
-2\ln R(\theta)=2\sqrt{ n }\lambda ^{T}S_{Z}-n\lambda ^{T}H_{Z}\lambda+O_{p}\big( \sum^{n}_{i=1}( \lambda ^{T}Z_{i})^{3} \big) 
$$
由 $\sum^{n}_{i=1}( \lambda ^{T}Z_{i})^{3}\leq \left\| \lambda \right\|\max_{i}\left\| Z_{i}\right\|\cdot n\lambda ^{T} H_{Z}\lambda$ 得
$$
\begin{align}
-2\ln R(\theta)&=2\sqrt{ n }\lambda ^{T}S_{Z}-n\lambda ^{T}H_{Z}\lambda+o_{p}(1)\\
&=S_{Z}^{T}H^{-1}_{Z}S_{Z}+o_{p}(1)
\end{align}

$$
最后由知 $S_{Z}\xrightarrow{d}N(0,H)$ ，得到 $-2\ln R(\mu)\xrightarrow{d}\chi^{2}_{d}$ 。

---
*Reference:*
	[[回归分析与线性模型第二章.pdf]]
	[[回归分析与线性模型第二章supp.pdf]]

---
*2025-10-28*






