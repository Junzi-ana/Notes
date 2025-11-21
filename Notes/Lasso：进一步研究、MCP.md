---
{}
---
#SmallEssays/多元统计分析 

在笔记 [[Bayes 统计：Lasso、岭回归]]中，简要介绍了 Lasso 和岭回归两种正则化方式，其中对岭回归介绍较多，相比之下，Lasso 的计算较为繁琐，因此本文只针对自变量为 $1$ 维的情形讨论。

以一元均值估计为例，其损失函数的形式为
$$
L(x)=\frac{\kappa}{2}(x-\mu)^{2}+p(x,\lambda),\quad p(x,\lambda)=\lambda|x|
$$
下推导其最小值点 $\hat{x}$ 。由对称性，要想最小化 $L(x)$ ，则 $x$ 应当与 $\mu$ 同号。无妨假设 $\mu>0$，此时 $x\geq0$
$$
L(x)=\frac{\kappa}{2}x^{2}+(\lambda-\kappa \mu)x+\frac{\kappa}{2}\mu^{2}
$$
于是当 $\lambda-\kappa \mu \geq0$ 时，$\hat{x}=0$，否则 $x=\frac{1}{\kappa}(\kappa \mu-\lambda)$ 时取最小,因此 $\hat{x}=(\mu-\frac{\lambda}{\kappa})^{+}$ 。对于 $\mu<0$ 的情形类似，综合得到
$$
\hat{x}=\text{sgn} (\mu) \cdot \left( |\mu|-\frac{\lambda}{\kappa} \right)^{+} =S(\mu,\frac{\lambda}{\kappa})
$$
其中，$S(\mu,t)=\text{sgn}(\mu)(|\mu|-t)^{+}$ 是一个常见的记号，表示删去位于 $\pm t$ 以内的部分。

现在假设样本 $x_{1}, ~ x_{2}, \cdots,~ x_{n}\sim N(\mu,1)$ ，代入上面的计算结果得到
$$
\hat{\mu}_{\text{Lasso}}=S(\bar{x},\lambda)
$$
若真值 $\mu=0$ 时，虽有 $\bar{x}\neq0$，但当 $n$ 稍大时就有 $\hat{\mu}_{\text{Lasso}}=0$ ，但倘若 $\mu ^{*}\neq0$，则 $\mathbb{E}\hat{\mu}_{\text{Lasso}}=\mu ^{*}\pm\lambda$，是有偏的。

类似地，对于一元线性回归，其损失函数为
$$
L(\beta)=\frac{1}{2n}\sum^{n}_{i=1}(y_{i}-\beta x_{i})^{2}+\lambda|\beta| 
$$
借用[[多元线性回归：假设检验与变量选择]]中的记号，可以写成
$$
L(\beta)=\frac{1}{2n}l_{xx}\left( \beta-\frac{l_{xy}}{l_{xx}} \right)^{2}+\lambda|\beta|+\text{const.}  
$$
记 $\tilde{\beta}=l_{xy} / l_{xx}$ 为最小二乘解，那么
$$
\hat{\beta}_{\text{Lasso}}=S(\tilde{\beta},~ \tilde{\lambda}),\quad \tilde{\lambda}=\frac{n\lambda}{l_{xx}}
$$
假设 $\varepsilon _{i}\sim N(0,1)$ ，则 $\tilde{\beta}\sim N(\beta ^{*},\frac{1}{n})$ 。若真值 $\beta ^{*}=0$，则 $\hat{\beta}_{\text{Lasoo}}=0$，否则 $\mathbb{E}\hat{\beta}_{\text{Lasso}}=\tilde{\beta}\pm\tilde{\lambda}$ 。

由此可见，在 Lasso 方法中，$\lambda$ 实际上设置了一道阈值，若估计值未达阈值，则自动削减为 $0$，但对于那些比较显著的估计，却会因为惩罚的存在，变得有偏。

那么如何对惩罚项 $p(x,\lambda)$ 作出一些改进呢？我们的思想就是：**惩罚小的 $\beta_{j}$ ，让它归 $0$ ；不惩罚大的 $\beta_{j}$，让它无偏**。

MCP 方法采用的惩罚项为
$$
p(x,\lambda)=\left\{\begin{aligned}
&\lambda|x|-\frac{x^{2}}{2a},&|x|\leq a\lambda\\
&\frac{1}{2}a\lambda^{2},&|x|>a\lambda
\end{aligned}\right.
\quad \quad (a>1)
$$
如下图所示
```tikz
\usepackage{pgfplots}
\usepackage{pgf}
\begin{document}
\begin{tikzpicture}[font=\large ]
\draw[->, line width=1pt] (-3,0) -- (3,0) node[below] {$x$};
\draw[->, line width=1pt] (0,-0.3) node[left] {$O$} -- (0,3) node[left] {$p(x,\lambda)$};

\draw[thick, domain=-2:2, samples=3] plot (\x, {abs(\x)});
\draw[thick, domain=-1.4:1.4, samples=19] plot (\x, {abs(\x)-(\x*\x)/2.8});
\draw[thick, domain=1.4:2.5, samples=2] plot (\x, {0.7});
\draw[thick, domain=-2.5:-1.4, samples=2] plot (\x, {0.7});

\draw[dashed] (1.4,0.7)  -- (1.4,0) node[below] {$a\lambda$};
\draw[dashed] (-1.4,0.7)  -- (-1.4,0) node[below] {$-a\lambda$};
\draw (2,2) node[right] {Lasso} ;
\draw (2.5,0.7) node[right] {MCP} ;
\end{tikzpicture}
\end{document}
```
MCP 惩罚函数也有显式的极小值点，推导可以类似 Lasso 的做法进行，是初等的，此处省略。对于一元均值估计问题，有
$$
\hat{\mu}_{\text{MCP}}=\left\{\begin{aligned}
&\frac{S(\bar{x},\lambda)}{1-\frac{1}{a}},\quad& |\bar{x}|\leq a\lambda\\
&\bar{x},&|\bar{x}|>a\lambda
\end{aligned}\right.
$$
当真值 $\mu ^{*}=0$ 时，对稍大的 $n$ 也有 $\hat{\mu}_{\text{MCP}}=0$，当 $\mu ^{*}>0$ 时，也有 $\hat{\mu}_{\text{MCP}}=\bar{x}$ 从而 $\mathbb{E}\hat{\mu}_{\text{MCP}}=\mu ^{*}$ 是无偏的。从而 MCP 估计同时具有稀疏性和无偏性。

```tikz
\usepackage{pgfplots}
\usepackage{pgf}
\begin{document}
\begin{tikzpicture}[font=\large ]
\draw[->, line width=1pt] (-5,0) -- (5,0) node[below] {$\bar x$};
\draw[->, line width=1pt] (0,-5) -- (0,5) node[left] {$\hat{\mu}$};
\draw (0,0) node[below left] {$O$} ;
\draw (1.5,0) node[below] {$\lambda$} ;
\draw[dashed] (2.1,2.1) -- (2.1,0) node[below] {$a\lambda$} ;
\draw[dashed, domain=-4.5:4.5, samples=3] plot (\x, \x);


\draw[line width=1.75pt, domain=-1.5:1.5, samples=3] plot (\x, 0);
\draw[thick, domain=1.5:4.2, samples=3] plot (\x, {\x-1.5});
\draw[thick, domain=-4.2:-1.5, samples=3] plot (\x, {\x+1.5});
\draw[thick, domain=1.5:2.1, samples=3] plot (\x, {3.5*(\x-1.5)});
\draw[thick, domain=2.1:4.2, samples=3] plot (\x, {\x});
\draw[thick, domain=-2.1:-1.5, samples=3] plot (\x, {3.5*(\x+1.5)});
\draw[thick, domain=-4.2:-2.1, samples=3] plot (\x, {\x});

\draw[->, line width=1pt] (3,2.8) -- (3,1.7) node[midway, left]{$\lambda$};
\draw[->, line width=1pt] (-3,-2.8) -- (-3,-1.7) node[midway, left]{$\lambda$};
\draw (4,3) node[right] {Lasso} ;
\draw (3.7,4) node[left] {MCP} ;
\end{tikzpicture}
\end{document}
```
上图展示了使用 Lasso 和 MCP 两种方法，得到的估计值与最小二乘估计 $\bar{x}$ 之间的关系。

纵使 MCP 有诸多优点，但它之所以无法取代 Lasso，最大的原因在于 MCP 的惩罚函数的凹的，从而损失函数非凸。由于求解 MCP 估计不是一个凸优化，其求解会比较困难，也高度依赖于初值的选取。因此在实践中，可以先 Lasso 求得初值，再使用非凸方法作优化，一般能提升表现。

---
*2025-11-21*