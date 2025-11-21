---
{}
---
#SmallEssays/统计学习 

对于线性回归模型
$$
y_{i}=\beta ^{T} X_{i}+\varepsilon _{i},\quad i=1, \cdots, n
$$
使用最小二乘法求解，根据笔记[[非参数回归：回归的原理与最优化]]所说，实质上是最小化如下的损失函数
$$
L(\beta)=\sum^{n}_{i=1}(y_{i}-\beta ^{T}X_{i})^{2} 
$$

在建立回归模型时，我们总是预设好了协变量 $y$ 对哪些因变量作回归。假如一次性添加了太多的特征，$X$ 的维数太高，$\hat{\beta}$ 的方差会很大，或者模型的可解释性会非常差。因此，在 $X$ 的维度高时，我们希望一些不重要的特征对应的斜率 $\beta _{j}$ 绝对值很小，由此实现**特征选择**。

特征选择的手段很多，本文介绍的方法是给 $L(\beta)$ 加一个**惩罚项**。通过对一些对一些不希望 $\beta$ 具有的性质施加惩罚，在最小化损失的过程中，$\beta$ 会自发地像我们希望的样子靠近。例如为了挑选特征，避免过拟合，我们希望 $\beta$ 是稀疏的，其分量应该尽可能小，于是可以对模长施加惩罚。常见的惩罚项有 $\mathscr{l}^{1}$ 惩罚和 $\mathscr{l}^{2}$ 惩罚，分别对应 **Lasso 回归**和**岭回归**，接下去将逐一介绍。

Lasso 回归使用的损失函数为
$$
L(\beta) = \sum^{n}_{i=1}(y_{i}-\beta ^{T}X_{i})^{2}+\lambda\| \beta \| _{1} 
$$
通过施加 $\mathscr{l}^{1}$ 惩罚，一些 $\beta_{j}$ 自动会被压缩成 $0$ ，具体推导在[[Lasso：进一步研究、MCP]] 中给出，从而实现了特征选择。

正如笔记 [[Bayes 统计：基本原理与例子]] 中讨论的，频率统计有时也可以看作是隐含了某种先验假设的 Bayes 统计。而对 $\beta$ 施加 $\mathscr{l}^{1}$ 惩罚就相当于 $\beta$ 具有 Laplace 先验分布。

为了说明这一点，我们假设 $\beta$ 有先验分布
$$
p(\beta)\propto \prod^{p}_{j=1}e^{-\alpha|\beta_{j}| }
$$
假设噪声强度为 $\sigma^{2}$，协变量 $y_{i}\sim N(\beta ^{T}X,~\sigma^{2})$ ，由 Bayes 公式
$$
\begin{align}
p(\beta|y,X)&\propto \prod^{n}_{i=1} p(y_{i}|X,\beta) \cdot p(\beta)\\
&\propto \exp\left(- \frac{1}{2\sigma^{2}} \sum^{n}_{i=1} (y_{i}-\beta ^{T}X_{i})^{2}-\alpha \sum^{p}_{j=1}|\beta_{j}|   \right) 
\end{align}
$$
可以看出，要最大化后验概率，实际上就是最小化带 $\mathscr{l}^{1}$ 惩罚的最小二乘损失，即
$$
\hat{\beta}_{\text{Lasso}}= \underset{\beta}{\text{argmin}}\; \sum^{n}_{i=1}(y_{i}-\beta ^{T}X_{i})^{2}+\lambda\| \beta \| _{1} ,\quad \lambda=2\alpha\sigma^{2}
$$

将 $\mathscr{l}^{1}$ 惩罚换成 $\mathscr{l}^{2}$ 惩罚，我们得到了岭回归。岭回归假设 $\beta$ 具有正态先验分布
$$
p(\beta)\propto \prod^{n}_{j=1}\exp\left( -\frac{\beta^{2}_{j}}{2\tau^{2}} \right)  
$$
则类似地，有后验分布
$$
p(\beta|y,X) \propto \exp\left( -\frac{1}{2\sigma^{2}}  \sum^{n}_{i=1} (y_{i}-\beta ^{T}X_{i})^{2}-\frac{1}{2\tau^{2}} \sum^{p}_{j=1}\beta_{j}^{2}\right) 
$$
进而
$$
\hat{\beta}_{\text{Ridge}}=\underset{\beta}{\text{argmin}}\;\sum^{n}_{i=1}(y_{i}-\beta ^{T}X_{i})^{2}+\lambda\| \beta \| _{2}^{2} ,\quad \lambda=\frac{\sigma^{2}}{\tau^{2}}
$$
对应于最小化带 $\mathscr{l}^{2}$ 惩罚的最小二乘损失。

岭回归的估计值相对较容易计算。假定设计矩阵 $X$ 已经标准化，则有
$$
\hat{\beta}_{\text{Ridge}}=(X^{T}X+\lambda I)^{-1}X^{T}Y
$$
相比于线性回归的表达式，仅仅是增加了一项 $\lambda I$ 。它的作用也是明显的：出现多重共线性时，$X^{T}X$ 接近奇异，导致 $\hat{\beta}$ 严重地数值不稳定，而增加这一项之后可以使得 $X^{T}X$ 的特征值远离原点，进而大大提升 $\hat{\beta}$ 的稳定性。

Lasso 和岭回归都是有偏的，而且相比于 Lasso，岭回归一般不会将 $\beta_{j}$ 的各分量压缩至 $0$，而是随着 $\lambda$ 的增大而减小。因此，为了在实现**偏差-方差均衡**，我们需要选取合适的参数 $\lambda$ 。一种比较简单的方法是**岭迹分析**。

将 $\hat{\beta}(\lambda)$ 的各分量与 $\lambda$ 画在坐标图上可以得到如下的岭迹曲线
```tikz
\usepackage{pgfplots}
\usepackage{pgf}
\begin{document}
\begin{tikzpicture}[font=\large ]
\draw[->, line width=1pt] (0,0) node[below left] {$O$} -- (6,0) node[below] {$\lambda$};
\draw[->, line width=1pt] (0,-3) -- (0,3) node[left] {$\hat{\beta}_j$};

\draw (1.8,0.1)--(1.8,0) node [below] {$\lambda_0$};

\draw[thick, domain=0.2:5, samples=20] plot (\x, {(3*\x-2)*exp(-\x+0.6)});
\draw[thick, domain=0.2:5, samples=20] plot (\x, {-0.5/(\x+0.2)^2});
\draw[thick, domain=0.2:5, samples=20] plot (\x, {-6*ln(\x+0.5)/(\x+0.7)^2});

\draw (0.35,2) node[right] {$\hat{\beta}_1$};
\draw (0.32,-2.2) node[right] {$\hat{\beta}_2$};
\draw (3.8,0.8) node[right] {$\hat{\beta}_3$};
\end{tikzpicture}
\end{document}
```
从图中可以看出，$\hat{\beta}_{2}$ 随着 $\lambda$ 的增加迅速趋于 $0$，可见自变量 $x_{2}$ 不太重要，可以剔除；$\hat{\beta}_{1}$ 在从较大的正值迅速跌为负值并趋于稳定，从传统线性回归的角度，$x_{1}$ 与 $y$ 正相关，而从岭回归的角度，它们实际上为负相关；$\hat{\beta}_{3}$ 与 $\hat{\beta}_{1}$ 类似。

当我们在选取 $\lambda$ 参数时，大体的原则是使得岭迹曲线趋于稳定，在此基础上不要选取太大的 $\lambda$ 以减小偏差，如在上图中可以选取 $\lambda=\lambda_{0}$ 。

---
*2025-11-21*