---
{}
---
#SmallEssays/RoughPath 

设 $X,~Y,Z$ 是线性空间，$A:X\times Y\to Z$ 是双线性映射，定义一种更加紧凑的写法 $\tilde{A}(x\otimes y)=A(x,y)$，使得 $\tilde{A}$ 成为一个新的空间 $W=X\otimes Y$ 上的线性映射。

为此，$x\otimes y$ 应当被定义为在某个线性空间 $X\otimes Y$ 中的元素，满足对于任意双线性映射 $A:X\times Y\to Z$，都存在另一个线性映射 $\tilde{A}:X\otimes Y\to Z$，使得 $\tilde{A}(x\otimes y)=A(x,y)$，即下图可交换
```tikz
\usepackage{tikz-cd}
\begin{document}
\begin{tikzcd}
[font=\fontsize{16pt}{12pt}\selectfont,
row sep=6em,
column sep=6em,
every arrow/.append style={line width=0.7pt},
every label/.append style={font=\fontsize{14pt}{9.6pt}\selectfont}]
  X\times Y \arrow[r, "A"] 
  \arrow[d, swap, "\otimes"] & Z \\
   X\otimes Y \arrow[ur, swap, "\tilde{A}"]  
\end{tikzcd}
\end{document}
```
并且 $X\otimes Y$ 在同构的意义下是唯一的，$\tilde{A}$ 也是唯一的。

显然，$\otimes:(x,y)\mapsto x\otimes y$ 是一个双线性运算，在这个记号下，任何一个双线性映射都可以表示成一个线性映射与这个泛用的双线性运算的复合，因此上述定理称为**张量积的泛性质**。

下面的定理与推论能最直接地体现张量积与 Descartes 积的区别。

**定理** 设 $X$ 和 $Y$ 是线性空间，$E$ 和 $F$ 分别是 $X$ 和 $Y$ 的一个线性无关集（基），则 $E\otimes F=\{ e\otimes f: e\in E,~f\in F\}$ 也是 $X\otimes Y$ 的一个线性无关集（基）。

**推论** 若 $X$ 和 $Y$ 是有限维的，则
$$
\mathrm{dim}(X\otimes Y)=\mathrm{dim}(X)\cdot\mathrm{dim}(Y)
$$

然而，上面依据泛性质对 $X\otimes Y$ 给出的定义时非构造性的，要想刻画其中的元素，可以考虑**将 $x\otimes y$ 视为双线性映射 $A$ 的函数**，满足 $\left< x\otimes y,~A \right>=A(x,y)$，于是 $X\otimes Y$ 可以视为双线性映射空间 $B(X\times Y)$ 的对偶空间的一个子空间，即
$$
X\otimes Y\subseteq B(X\times Y)^{*}
$$
而 $X\otimes Y$ 即由所有满足 $\left< x\otimes y,~A \right>=A(x,y)$ 的元素张成。因此，一个 $X\otimes Y$ 中的任意张量 $u$，都可以表成
$$
u=\sum^{n}_{i=1} x_{i}\otimes y_{i}
$$
注意，**$u$ 的表法通常是不唯一的**，但对 $A$ 的作用于表法无关。

要定义两个 Banach 空间上的张量积，事实上就是需要考虑如何定义范数 $\left\| x\otimes y \right\|$ 。一个没什么道理但比较自然的要求是 $\left\| x\otimes y \right\|\leq \| x \|\left\| y \right\|$，考虑到 $u$ 的表法不唯一，这个式子应该对所有表示都成立，即取下确界。于是，定义
$$
\pi(u)=\inf \left\{ \sum^{n}_{i=1} \|x_{i}\|\left\| y_{i} \right\|:u=\sum^{n}_{i=1} x_{i}\otimes y_{i} \right\} 
$$
可以验证，$\pi$ 是 $X\otimes Y$ 的一个范数，称为**投影范数**。$X\otimes Y$ 在 $\pi$ 下一般不完备，其完备化空间记作 $X\hat{\otimes}_{\pi}Y$，称为**投影张量积空间**。

有趣的是，$\pi$ 的定义使得上面的不等号成为等号，即
$$
\pi(x\otimes y)=\|x\|\|y\|,\quad \forall\;x\in X,~ y\in Y
$$
这一点也可以在矩阵代数中得到验证，此时 $\otimes$ 应理解为 Kronecker 积，对 Frobenius 范数或谱范数等酉不变的矩阵范数，都有这一关系成立。

---
*Reference: Introduction to Tensor Products of Banach Spaces, Raymond A. Ryan*

---
*2025-8-25*