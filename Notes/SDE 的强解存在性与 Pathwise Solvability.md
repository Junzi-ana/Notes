#SmallEssays/随机分析 

在 [[SDE 的弱解与唯一性]] 一文中，我们作了一些关于弱解的讨论。既然强解能推出弱解，弱解什么时候能推出强解呢？以下命题是 **Yamada-Watanabe 定理** 的一个推论。

**推论** 设 $(X,W),~(\Omega,\mathcal{F},\mathbb{P}),~\{ \mathcal{F}_{t} \}_{t \geq0}$ 是如下 SDE
$$
\mathrm{d} X_{t}=b(t,X_{t})\;\mathrm{d} t+\sigma(t,X_{t})\;\mathrm{d} W_{t}
$$
的弱解，初始分布为 $\mu$，且满足依路径唯一性，则存在 Borel 可测函数 $h:\mathbb{R}^{d}\times C[0,\infty)^{r}\to C[0,\infty)^{d}$，满足 $\forall\;0\leq t<\infty$：
$$
X_{\cdot}=h(X_{0},W),\quad \text{a.s.} ~\mathbb{P}
$$
此外，对任何足够大的概率空间，仍记作 $(\Omega,\mathcal{F},\mathbb{P})$，
$$
X_{\cdot}=h(\xi,W_{\cdot})
$$
是初值为 $\xi$ 的强解，此处的 $h$ 更是循序可测的。

这个推论包含两层含义，其一是 **弱解存在 $+$ 依路径唯一 $\implies$ 强解存在**；其二是，这个推论给出了强解的表示，接下来着重解释这一点。

在 [[SDE 的 Pathwise Solvability]] 中介绍了，对于一部分特殊的 SDE，我们可以直接通过 Itô 公式和 Girsanov 定理验证，给出解映射的显示依赖。但除此之外，我们会发现，就连这个解映射是否是良定义的都很难说，更别提可测性和循序可测性之类的性质了。

而这个推论就表明了，强解总是能被表成一个系统在给定初值和驱动过程下的输出，从而我们可以对一个 SDE 进行如下建模
```tikz
\usepackage{tikz}

\begin{document}
\begin{tikzpicture}[ box/.style={draw, rectangle, minimum width=4cm, minimum height=2cm, align=center, font=\Large},
font=\large, ]
\node[box] (module) at (0,0) {$b, \sigma$};
\draw[->, line width=1pt] (-4,0)  -- (module.west) node[midway, above] {input $W$};
\draw[->, line width=0.7pt] (0,2) -- (module.north) node[pos=0, above] {$\xi$};
\draw[->, line width=1pt] (module.east) -- (4,0) node[midway, above] {$X$ output};
\end{tikzpicture}
\end{document}
```
称之为动力系统的 **principle of causality** 。此前我们直觉上习惯默认它的存在，直到现在我们给出了相对严格的数学保障。

---
*Reference: Brownian Motion and Stochastic Calculus, Ioannis Karatzas, Steven E. Shreve*

---
*2025-9-8*