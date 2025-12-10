---
{}
---
#SmallEssays/数理统计 

[[数理统计基本思想：似然函数、似然比|似然比检验]]在数理统计学中占据着重要地位，是一个泛用的假设检验手段，并且可以用于构造[[假设检验：Neyman-Pearson 定理与 UMP|一致最优检验]]。然而，除了某些简单情况外，似然比 $\lambda$ 的表达式非常复杂，精确分布难以求得。因此，我们讨论大样本时 $\lambda$ 的极限分布。

由于 Wilks 定理的具体叙述和证明极其复杂和繁琐，就连关于总体概率的假定也需要两页纸才能写完，在此着重于阐述其证明思路，关于各种细节点到为止，详见*陈希孺《数理统计引论》第 326~330 面*。但它可以简略地表述如下：

**Wilks 定理** 记 $\mathrm{dim}\Theta=r,~\mathrm{dim}\Theta_{0}=k$，则在原假设 $H_{0}:\theta \in\Theta_{0}$ 的条件下，当 $n\to \infty$ 时，$2\ln\lambda$ 有极限分布 $\chi^{2}_{r-k}$  `[!!air-vent|Proved by DeepSeek|117, 188, 255]`

**证明** 在开始证明之前，我们先思考一个问题：这个 $\chi^{2}$ 分布究竟是如何导出来的？$\chi^{2}$ 分布来自于正态变量的平方和，更进一步说，应该是正态变量的二次型。因此，推导到最后，$2\ln\lambda$ 应该有类似于 $S^{T}H^{-1}S$ 的形式，其中 $S$ 是多元正态随机变量，$H$ 为其协方差矩阵。

现在我们可以开始推导 $2\ln\lambda$ 的极限分布的形式了。似然比原先的定义如下
$$
\lambda=\frac{\sup_{\theta \in\Theta}L(\theta;x)}{\sup_{\theta \in\Theta_{0}}L(\theta ;x)}
$$
然而这个形式较为复杂。在一定的正则条件下，可以简单将分子和分母写成 $L(\hat{\theta})$ 和 $L(\theta_{0})$，分别是在参数空间 $\Theta$ 和 $\Theta_{0}$ 上的极大似然估计。在取对数之后写成
$$
2\ln\lambda =2(\ell(\hat{\theta})-\ell(\theta_{0}))
$$
其中 $\ell(\theta)=\sum^{n}_{i=1}\ell(\theta;x_{i})$ 表示[[数理统计基本思想：似然函数、似然比#^80c880|对数似然函数]]。

对 $\ell(\theta)$ 在 $\theta_{0}$ 处 Taylor 展开，得
$$
\begin{align}
\ell(\hat{\theta})=\ell(\theta_{0})+\nabla \ell(\theta_{0})\cdot(\hat{\theta}-\theta_{0}) +\frac{1}{2}(\hat{\theta}-\theta_{0})^{T}\nabla^{2}\ell(\theta_{*})(\hat{\theta}-\theta_{0})

\end{align}
$$
记 $S(\theta)=\frac{1}{\sqrt{ n }}\sum^{n}_{i=1}\ell(\theta;x_{i})=\frac{1}{\sqrt{ n }}\nabla\ell(\theta)$ 是标准化得分向量，$H(\theta)=-\frac{1}{n}\sum^{n}_{i=1}\nabla^{2}\ell(\theta;x_{i})=-\frac{1}{n}\nabla^{2} \ell(\theta)$ 是样本信息阵，上式化为
$$
\begin{align}
2\ln\lambda=2\sqrt{ n }S(\theta_{0})\cdot(\hat{\theta}-\theta_{0})-n(\hat{\theta}-\theta_{0})^{T}H(\theta_{*})(\hat{\theta}-\theta_{0})
\end{align}

$$
由大数定律，$H(\theta_{*})=I(\theta_{0})+o_{p}(1)$，$I(\theta_{0})$ 为期望 Fischer 信息矩阵，有 $I(\theta_{0})=\text{Cov}\,(\nabla \ell(\theta ;X))=-\mathbb{E}\nabla^{2}\ell(\theta;X)$ 。

与此同时，对 $S(\theta)$ 在 $\theta_{0}$ 处 Taylor 展开
$$
S(\hat{\theta})=S(\theta_{0})+\sqrt{ n }H(\theta_{**})(\hat{\theta}-\theta_{0})
$$
且因为 $\hat{\theta}$ 是 MLE，有 $S(\hat{\theta})=0$，于是得到
$$
\sqrt{ n }(\hat{\theta}-\theta_{0})=H^{-1}(\theta_{**})S(\theta_{0})=I^{-1}(\theta_{0})S(\theta_{0})+o_{p}(1)
$$
代入 $2\ln\lambda$ 的表达式得到
$$
2\ln\lambda =S^{T}(\theta_{0}) I(\theta_{0})^{-1}S(\theta_{0})+o_{p}(1)
$$
其中因为 $\ell(\theta;x_{i})$ 独立同分布且二阶矩存在，根据中心极限定理，$S(\theta)\xrightarrow{d}N(0,I(\theta_{0}))$ 得到 $S^{T}(\theta_{0}) I(\theta_{0})^{-1}S(\theta_{0})\xrightarrow{d} \chi^{2}_{r-k}$ 。 ^05167c

此外，由公式
$$
\sqrt{ n }(\hat{\theta}-\theta_{0})=I^{-1}(\theta_{0})S(\theta_{0})+o_{p}(1)
$$
和 $S(\theta)\xrightarrow{d}N(0,I(\theta_{0}))$ 还可以得到
$$
\sqrt{ n }(\hat{\theta}-\theta_{0})\xrightarrow{d}N(0,I^{-1}(\theta_{0})) 
$$
于是证明了 **MLE 的渐近正态性**。

---
*Reference:*
	*数理统计学教程, 陈希孺, 倪国熙*
	[[数理统计引论 (陈希孺) (Z-Library).pdf]]

---
*2025-10-20*