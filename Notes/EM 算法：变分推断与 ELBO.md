---
{}
---
#SmallEssays/统计学习 

在笔记 [[EM 算法：一般形式]]中指出了，我们可以用似然量的期望代替似然量，这需要我们知道隐变量的后验分布 $p(z|x)$ 。然而，尽管有 Bayes 公式，在 $Z$ 的维度较高时估计 $p(z|x)$ 也是极其困难的，因此我们尝试使用一个分布 $q(z)$ 代替 $p(z|x)$ ，这便是**变分推断**的思想。

为了让 $q(z)$ 与 $p(z|x)$ 尽可能接近，我们采用 **KL 散度** 来度量两个分布的接近程度
$$
D_{KL}(q\|p)=\int \log \frac{q(z)}{p(z|x)} \cdot q(z) \; \mathrm{d}z 
$$
表示[[非参数回归：经验似然方法#^a086b4|平均信息量的损失]]。

在开始优化之前，有这样一个问题：既然 KL 散度没有对称性，那**为什么要优化 $D_{KL}(q\|p)$ 而不是 $D_{KL}(p\|q)$ 呢？**

除了计算的简便性之外，由于 $q(z)$ 是变化的，为了让 $D_{KL}(q\|p)$ 尽可能小，在 $q(z)$ 与 $p(z|x)$ 不接近的地方 $q(z)$ 应当尽可能小；反之，如果要让 $D_{KL}(p\|q)$ 尽可能小，则即使是那些 $p(z|x)$ 接近 $0$ 的地方，$q(z)$ 也不能相去太远。

```tikz
\usepackage{pgfplots}
\usepackage{pgf}
\begin{document}
\begin{tikzpicture}[font=\large ]
\draw[->, thick] (1,0) -- (12,0) ;
\foreach \t in {1,2,...,11}
	\draw (\t,0) -- (\t,0.2);

\draw[line width=1pt, domain=1:10, samples=40] plot (\x, {1*exp(-(\x-5)^2/2)+2.25*exp(-(\x-8)^2/0.88)});

\draw[line width=1.25pt, domain=1:10, samples=40, dashed] plot (\x, {0.3*exp(-(\x-5)^2/3)+2.5*exp(-(\x-8)^2/0.72)});
\draw[line width=1.5pt, domain=1:10, samples=40, dotted] plot (\x, {0.003*(\x-1)^2.5*(10-\x)^1.5});

\draw[line width=1.25pt, dashed, font=\normalsize ] (10,3.12) -- (10.75,3.12) node[right]{$~~q_1$};
\draw[line width=1.5pt, dotted, font=\normalsize ] (10,2.74) -- (10.75,2.74) node[right]{$~~q_2$};
\draw[line width=1pt, font=\normalsize] (10,3.5) -- (10.75,3.5) node[right]{$~~p$};
\draw (9.7,2.48) rectangle (11.7,3.77);

\end{tikzpicture}
\end{document}
```

上图显示的就是分别优化 $D_{KL}(q_{1}\|p)$ 和 $D_{KL}(p\|q_{2})$ 得到的 $q_{1}$ 和 $q_{2}$ 得到的大致图像。可以看出，优化 $D_{KL}(q\|p)$ 更适合捕捉 $p$ 的局部特性，而优化 $D_{KL}(p\|q)$ 的结果往往比较保守，导致各处的逼近效果都不佳。

于是计算
$$
\begin{align}
D_{KL}(q\|p)&=\int \log \frac{q(z)}{p(z|x)} \cdot q(z) \; \mathrm{d}z \\
&=\int \big(\log q(z)+\log p(x)-\log p(x,z) \big)q(z) \; \mathrm{d}z \\
&=\log p(x)-H(q(z)) -\int q(z)\log p(x,z)\;\mathrm{d} z\geq 0
\end{align}
$$
得到不等式
$$
\log p(x)\geq H(q)+\int q(z)\log p(x,z)\;\mathrm{d} z
$$
不等号的左端是数据的对数似然（证据），而右端称为**证据下界（ELBO）**。

借助这个恒等关系式
$$
\log p(x)=ELBO+D_{KL}(q\|p)
$$
我们得出到如下观察
1. 当近似分布 $q(z)$ 给定，要通过抬高 ELBO 来抬高似然量 
2. 当似然量被给定时，要最小化 $D_{KL}$，就是要尽可能地抬高 ELBO。

从第一个角度理解 EM 算法，选取 $q(z)=p(z|x,\theta^{(n)})$，那么
$$
\begin{align}
ELBO_{\theta^{(n)}}(\theta)&=H(p(z|x,\theta^{(n)}))+\int \log p(x,z|\theta)\cdot p(z|x,\theta^{(n)})\;\mathrm{d} z\\
&=Q(\theta;\theta^{(n)})+\text{const.} 
\end{align}

$$
从而优化 $Q$ 函数的过程就是抬高 ELBO 的过程。并且借用这个恒等式，我们可以非常简单地得到在笔记 [[EM 算法：a toy model]] 末尾提到的收敛性问题
$$
\begin{align}
\ell(\theta^{(n+1)})&=ELBO_{\theta^{(n)}}(\theta^{(n+1)}) +D_{KL}(\theta^{(n+1)}||\theta^{(n)})\\
&\geq ELBO_{\theta^{(n)}}(\theta^{(n)})+0=\ell(\theta^{(n)})
\end{align}



$$
从而每次迭代都可以抬高似然量，直至收敛。

从第二个角度出发，我们希望采用具有简单形式的 $q(z)$ 来逼近 $p(z|x)$，假设 $q(z)$ 各分量独立，即 $q(z)=\prod^{n}_{i=1}q_{i}(z_{i})$ 。似然量给定时，我们希望通过抬高 ELBO 来优化 KL 散度
$$
\begin{align}
ELBO&=\sum^{n}_{i=1}  H(q_{i})+\mathbb{E}_z\log p(x,z)\\
\end{align}
$$
只看与 $z_{j}$ 有关项，可以写成
$$
\begin{align}
ELBO&=H(q_{j})+\mathbb{E}_{z_{j}}\mathbb{E}_{z_{-j}}\log p(x,z) +\text{const.} \\
&=H(q_{j})+\mathbb{E}_{z_{j}}\log \tilde{p}_{-j}(z_{j}) +\text{const.} \\
&=-D_{KL}\big( q(z_{j})\|\tilde{p}_{-j}(z_{j}) \big) +\text{const.}
\end{align}
$$
其中 $\tilde{p}_{-j}(z_{j})\propto \exp \big( \mathbb{E}_{z_{-j}}\log p(x,z) \big)$，在相差一个常数的意义下，$\tilde{p}_{-j}$ 成为一个概率分布。

于是我们得到了**变分 EM 算法**
1. 确定迭代初值 $\theta^{(0)},~q^{(0)}(z)$
2. **(Expectation)** 对每个 $j$，计算 $q^{(n)}_{j}(z_{j})\propto\tilde{p}_{-j}(z_{j})$
3. **(Maxmization)** 优化 $\theta^{(n+1)}=\underset{\theta}{\text{argmax}}\;ELBO(q^{(n)};\theta^{(n)})$
4. 重复直至收敛

相比于标准 EM 算法，变分 EM 算法在后验概率 $p(z|x)$ 难以计算时，用 $q(z)$ 来逼近，并在每个分量上逐步优化。当后验本身可以分解成 $p(z|x)=\prod^{n}_{i=1}p(z_{i}|x)$ 时，变分 EM 算法退化为标准 EM 算法。

---
*2025-11-26*