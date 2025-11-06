#SmallEssays/RoughPath 

考虑这样一个带控制的微分方程
$$\mathrm{d}Y_{t}=f_{0}(Y_{t})+f(Y_{t})\;\mathrm{d}X_{t}$$
其中 $X_{t}$ 作为控制过程输入，是**驱动过程**。按理，对于任意确定的驱动过程 $X_{t}$，$Y_{t}$ 应有确定的演化，由上述微分方程描述。然而，这个方程常常**不是良定义**的，比如一个完全由白噪声驱动 $X_{t}=W_{t}$ 的系统，上述方程变成一个 SDE。由于 Brown 运动的轨道不是有界变差的，即对每个给定的样本轨道 $W_{t}(\omega)$，不能用 L-S 积分来求解出对应的 $Y_{t}(\omega)$，而 Itô 积分在定义时，利用 **Itô 等距回避了对这个问题的正面回答**。

与此同时，想用光滑过程逼近的方法也是行不通的，因为解映射 **$S:X\mapsto Y$ 往往是不连续的**。例如，对于如下简单的系统
$$
\left\{\begin{aligned}
\;\mathrm{d} Y^{1}&=X^{1}\;\mathrm{d} X^{2}\\
\;\mathrm{d} Y^{2}&=\mathrm{d} X^{1}
\end{aligned}\right.
$$
选取一列驱动过程
$$
X_{n}^{1}=\frac{\cos(n^{2}\pi t)}{n},\quad X_{n}^{2}=\frac{\sin (n^{2}\pi t)}{n} 
$$
于是有 $\mathrm{d}Y^{1}_{n}=X_{n}^{1}\;\mathrm{d}X_{n}^{2}$，进而计算 $Y_{n}^{1}(2\pi)=\displaystyle \int_{0}^{2\pi}X_{n}^{1}\;\mathrm{d}X_{n}^{2}=2\pi$ 。
然而，当 $n\to \infty$ 时，$X_{n}^{1},~X_{n}^{2}\to0$，而 $Y_{n}^{1}(2\pi)\not\to Y^{1}(2\pi)=0$，即 $S:X\to Y$ 不是连续的。更进一步，有如下定理。

**定理** 不存在一个可分 Banach 空间 $\mathcal{B}\subseteq C[0,1]$，满足
1. Brown 运动的轨道几乎必然属于 $\mathcal{B}$
2. 定义在光滑函数类上的映射 $(f,g)\mapsto \displaystyle \int_{0}^{\cdot}f\;\mathrm{d}g$ 可以连续延拓到连续函数类 $\mathcal{B}\times \mathcal{B}$ 上

问题出在了哪呢？回看刚才的例子，形如 $\displaystyle \int_{s}^{t} X^{i}\;\mathrm{d}X^{j}$ 的积分一定蕴含了某种被忽略的信息。事实上，利用 Green 公式可以看出，这个积分实际上表示由 $(X^{i},X^{j})$ 的一段轨迹所围成区域的面积，这一区域称为 **Lévy's Area** 。

---
*Reference: A Course on Rough Paths, Peter K. Friz*

---
*2025-8-20*