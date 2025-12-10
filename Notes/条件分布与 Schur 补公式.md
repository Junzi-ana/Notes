---
{}
---
#SmallEssays/多元统计分析 

假设 $X$ 是 $p$ 维正态随机变量
$$
X=\begin{bmatrix}
X_{1}\\X_{2}
\end{bmatrix},\quad \Sigma=\begin{bmatrix}
\Sigma_{11}&\Sigma_{12}\\ \Sigma_{21}&\Sigma_{22}
\end{bmatrix}
$$
在笔记[[多元正态分布的条件分布]]中计算了条件分布
$$
X_{2}|X_{1}\sim N(\mu_{2|1},~ \Sigma_{2|1})
$$
本篇笔记并不关心均值，着重关心协方差矩阵。那么，第一个问题就是，长得那么怪异的 $\Sigma_{2|1}$ 应该如何理解？

我们首先计算**精度矩阵**
$$
\Lambda=\Sigma ^{-1}=\begin{bmatrix}
\Lambda_{11}&\Lambda_{12}\\ \Lambda_{21}&\Lambda_{22}
\end{bmatrix}
$$
需要用到**打洞原理**，即对 $\Sigma$ 作分块初等行变换，使得 $\Sigma$ 的左下角出现一个零矩阵。
$$
\begin{bmatrix}
I&O\\ -\Sigma_{21}\Sigma_{11}^{-1}&I
\end{bmatrix}
\begin{bmatrix}
\Sigma_{11}&\Sigma_{12}\\ \Sigma_{21}&\Sigma_{22}
\end{bmatrix}=
\begin{bmatrix}
\Sigma_{11}&\Sigma_{12}\\ O&\Sigma_{2|1}
\end{bmatrix}
$$
此时，对应的右下角就出现了 $\Sigma_{2|1}$，满足
$$
 \Sigma_{2|1}=\Sigma_{22}-\Sigma_{21}\Sigma_{11}^{-1}\Sigma_{12}
$$
称为 $\Sigma_{11}$ 的 **Schur 补**。通过对调下标 $1$ 和 $2$ ，我们也可以得到
$$
 \Sigma_{1|2}=\Sigma_{11}-\Sigma_{12}\Sigma_{22}^{-1}\Sigma_{21}
$$

借助这个记号，我们可以计算 ^a39c43
$$
\begin{align}

\begin{bmatrix}
\Sigma_{11}&\Sigma_{12}\\ \Sigma_{21}&\Sigma_{22}
\end{bmatrix}^{-1}&=\left( \begin{bmatrix}
I&O\\ -\Sigma_{21}\Sigma_{11}^{-1}&I
\end{bmatrix}^{-1}
\begin{bmatrix}
\Sigma_{11}&\Sigma_{12}\\ O&\Sigma_{2|1}
\end{bmatrix} \right) ^{-1}\\
&=
\begin{bmatrix}
\Sigma_{11}^{-1}&-\Sigma_{11}^{-1}\Sigma_{12}\Sigma_{2|1}^{-1}\\ O&\Sigma_{2|1}^{-1}
\end{bmatrix} 
\begin{bmatrix}
I&O\\ -\Sigma_{21}\Sigma_{11}^{-1}&I
\end{bmatrix}\\
&=\begin{bmatrix}
\Sigma_{11}^{-1}+\Sigma_{11}^{-1}\Sigma_{12}\Sigma_{2|1}^{-1}\Sigma_{21}\Sigma_{11}^{-1}&-\Sigma_{11}^{-1}\Sigma_{12}\Sigma_{2|1}^{-1}\\ 
-\Sigma_{2|1}^{-1}\Sigma_{21}\Sigma_{11}^{-1}&\Sigma_{2|1}^{-1}
\end{bmatrix}
\end{align}
$$

只不过，左上角的元素似乎有些过于复杂了，我们可以通过在右上角打洞得到这个位置的元素实际上是 $\Sigma_{1|2}^{-1}$，于是我们就得到了如下 **Schur 补公式**，又称为**分块矩阵求逆公式**
$$
\begin{bmatrix}
\Lambda_{11}&\Lambda_{12}\\ \Lambda_{21}&\Lambda_{22}
\end{bmatrix}=\begin{bmatrix}
\Sigma_{1|2}^{-1}&-\Sigma_{11}^{-1}\Sigma_{12}\Sigma_{2|1}^{-1}\\ 
-\Sigma_{2|1}^{-1}\Sigma_{21}\Sigma_{11}^{-1}&\Sigma_{2|1}^{-1}
\end{bmatrix}
$$
其中，我们特别关心的是对角元，即 $\Lambda_{11}=\Sigma_{1|2}^{-1},~\Lambda_{22}=\Sigma_{2|1}^{-1}$ 。

有了 Schur 补公式，我们可以着手研究更加复杂的命题了。考虑将 $X$ 剖分为三部分
$$
X=\begin{bmatrix}
X_{1}\\ X_{2}\\ X_{3}
\end{bmatrix},\quad \Sigma=\begin{bmatrix}
\Sigma_{11}&\Sigma_{12} & \Sigma_{13} \\
\Sigma_{21}&\Sigma_{22} & \Sigma_{23}
\\ \Sigma_{31}&\Sigma_{32} & \Sigma_{33}
\end{bmatrix}
$$
我们希望研究在 $X_{3}$ 的条件下 $X_{1},X_{2}|X_{3}$ 的联合分布。此时，我们不妨将 $X_{1},~X_{2}$ 看作一个随机向量 $X_{12}$，对应地可以重新写为
$$
X=\begin{bmatrix}
X_{12}\\X_{3}
\end{bmatrix},\quad \Sigma=\begin{bmatrix}
\Sigma_{1221}&*\\ *&\Sigma_{33}
\end{bmatrix}
$$
那么，$X_{12}|X_{3}$ 的条件协方差阵 $\Sigma_{1221|3}$ 就是 $\Sigma_{3}$ 的 Schur 补，于是计算
$$
\begin{align}
\Sigma_{1221|3}&=\begin{bmatrix}
\Sigma_{11}&\Sigma_{12}\\ \Sigma_{21}&\Sigma_{22}
\end{bmatrix}-
\begin{bmatrix}
\Sigma_{13}\\\Sigma_{23}
\end{bmatrix}\Sigma_{33}^{-1}\begin{bmatrix}
\Sigma_{31}&\Sigma_{32}
\end{bmatrix}\\
&=\begin{bmatrix}
\Sigma_{1|3}&\Sigma_{12}-\Sigma_{13}\Sigma_{33}^{-1}\Sigma_{32} \\
\Sigma_{21}-\Sigma_{23}\Sigma_{33}^{-1}\Sigma_{31} & \Sigma_{2|3}
\end{bmatrix}
\end{align}

$$
倘若再引入记号
$$
\Sigma_{12|3}=\Sigma_{12}-\Sigma_{13}\Sigma_{33}^{-1}\Sigma_{32},\quad \Sigma_{21|3}=\Sigma_{21}-\Sigma_{23}\Sigma_{33}^{-1}\Sigma_{31}
$$
那么 $\Sigma_{12|3}$ 是 $X_{1},~X_{2}$ 在 $X_{3}$ 下的条件协方差矩阵，而 $\Sigma_{1|3}$ 是 $X_{1}$ 在 $X_{3}$ 下的条件协方差矩阵。进一步就有如下一个较为简单直觉的形式
$$
\Sigma_{1221|3}=
\begin{bmatrix}
\Sigma_{1|3}&\Sigma_{12|3} \\
\Sigma_{21|3} & \Sigma_{2|3}
\end{bmatrix}
$$
假如给 $\Lambda$ 作同样的剖分，由于
$$\Lambda_{1221}=
\begin{bmatrix}
\Lambda_{11}&\Lambda_{12}\\ \Lambda_{21}&\Lambda_{22}
\end{bmatrix}=
\begin{bmatrix}
\Sigma_{1|3}&\Sigma_{12|3} \\
\Sigma_{21|3} & \Sigma_{2|3}
\end{bmatrix}^{-1}=\Sigma_{1221|3}^{-1}
$$
$\Sigma_{1221}$ 是分块对角矩阵当且仅当 $\Lambda_{1221}$ 也是分块对角矩阵，于是我们证明了

**定理** $X_{1}$ 与 $X_{2}$ 在 $X_{3}$ 的条件下独立当且仅当 $\Lambda_{12}$ 和 $\Lambda_{21}$ 是零矩阵

---
*2025-11-12*