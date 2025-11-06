#SmallEssays/BSDE

考虑如下形式的 BSDE：
$$
y(t)+\int^{T}_{t} f(s,y(s),z(s)) \; \mathrm{d}s+ \int^{T}_{t} \big[ g(s,y(s)) +z(s)\big]\; \mathrm{d}W_{s}=\xi
$$
其中 $\xi$ 是终端条件，$y(T)=\xi \in L^{2}(\Omega,\mathcal{F}_{T},\mathbb{P})$，$f,~g$ 有所需的正则性（循序可测与平方可积）。直观地理解，**$y(t)$ 是状态过程而 $z(t)$ 是控制过程，都可能带有随机性**（即是 $\omega$ 的函数），使得上述方程成立的一对适应过程 $(y,z)$ 称为上述 **BSDE 的解**。
 
为简便起见，所有变量均为 $1$ 维，在 Peng 的原文中，$y(t),~\xi$ 和 $W_{t}$ 为 $d$ 维向量，$z(t)$ 维 $d\times k$ 维矩阵。并且，为了行文紧凑，在无需强调时省略 $y$ 和 $z$ 对 $t$ 的依赖。

为了建立上述 BSDE 解的存在唯一性，我们将分三步走。

<b><font style="font-size: 120%;"><font color="#de7802">第一步</font></font></b> 考虑如下简化的 BSDE：
$$
y(t)+\int^{T}_{t} f(s) \; \mathrm{d}s+ \int^{T}_{t} \big[ g(s) +z(s)\big]\; \mathrm{d}W_{s}=\xi
$$
直接移项，取条件期望得
$$
y(t)=\mathbb{E}_{t}\left[ \xi-\int^{T}_{t} f(s) \; \mathrm{d}s \right]
$$
借助**鞅表示定理**，存在 $\bar{z}$ 满足 $\displaystyle y(t)=y(0)+\int^{t}_{0} \bar{z}(s) \; \mathrm{d}W_s$，进而 $z=\bar{z}-g$ 即为所求，且鞅表示定理保证了唯一性。`[!!alarm-clock-check|Checked|79, 255, 66]` 

<b><font style="font-size: 120%;"><font color="#de7802">第二步</font></font></b> 考虑如下依赖 $z$ 的 BSDE：
$$
y+\int^{T}_{t} f(s,z) \; \mathrm{d}s+ \int^{T}_{t} \big[ g(s) +z\big]\; \mathrm{d}W_{s}=\xi
$$
毫不意外地，需要假定 $f$ 关于 $z$ 满足 Lipschitz 条件。

**唯一性** 设 $(y_{1},z_{1}),~(y_{2},z_{2})$ 是两个解，通过对 $(y_{1}-y_{2})^{2}$ 用 Itô 公式，得
$$
\begin{align}
&( y_{1}-y_{2} )^{2}+\int^{T}_{t} (z_{1}-z_{2})^{2} \; \mathrm{d}s\\
=&-2\int^{T}_{t} \big(f(s,z_{1})-f(s,z_{2})\big) (y_{1}-y_{2})\; \mathrm{d}s 
-2\int^{T}_{t} (y_{1}-y_{2})(z_{1}-z_{2})\; \mathrm{d}W_{s}
\end{align}
$$

> [!note]-
>  在 BSDE 的框架下，将微分式 $\mathrm{d}x = \mu \;\mathrm{d}t+\sigma \;\mathrm{d}W_{t}$ 还原为积分式时，应从 $T$ 积分到 $t$，从而**相差负号**，即
> $$x(t)+\int^{T}_{t} \mu \; \mathrm{d}t + \int^{T}_{t} \sigma \; \mathrm{d}t =x(T)$$
> 二者如此对应，切记。

两边同时取期望（需要验证可积性），得到
$$
\begin{align}
&\mathbb{E}( y_{1}-y_{2} )^{2}+\mathbb{E}\int^{T}_{t} (z_{1}-z_{2})^{2} \; \mathrm{d}s\\
=&-2\mathbb{E}\int^{T}_{t} \big(f(s,z_{1})-f(s,z_{2})\big) (y_{1}-y_{2})\; \mathrm{d}s \\
\leq& 2c^{2}\mathbb{E}\int^{T}_{t} (y_{1}-y_{2})^{2} \; \mathrm{d}s +\frac{1}{2} \mathbb{E}\int^{T}_{t} (z_{1}-z_{2})^{2} \; \mathrm{d}s

\end{align}
$$
于是唯一性由 **Gronwall 不等式**得出。

> [!method]-
> 这是做存在唯一性有关证明的常用技巧，即**调系数**。本质上是利用了均值不等式 $2ab\leq a^{2}+b^{2}$，进一步，增加一个调节的系数 $\lambda>0$，得到不等式 $2ab\leq\lambda ^{-1} a ^{2} +\lambda b^{2}$ 。此处通过适当的调节，使第一项前面的系数小于 $1$，第二项前面的系数任意，因为会用 Gronwall 不等式处理。

> [!note]-
>  **Gronwall 不等式** 若 $g(t)$ 连续，且满足
> $$0\leq g(t)\leq \alpha(t)+\beta \int^{t}_{0} g(s) \; \mathrm{d}s,~\beta \geq0$$
> 则成立 
> $$g(t) \leq \alpha(t) + \beta \int^{t}_{0} \alpha(s) e^{\beta (t-s)} \; \mathrm{d} s$$
> 特别地，$\alpha(t) \equiv0$ 时有 $g(t)\equiv0$，这**是证明唯一性的重要技巧**。Gronwall 不等式的证明过程也有学习价值，即将原条件写成微分的形式，并凑出如下形式再积分
> $$\dfrac{\mathrm{d}}{\mathrm{d}t}   \left( e^{-\beta t}g(t) \right) \leq \alpha(t)e^{-\beta t}$$

**存在性** 正如几乎所有的解的存在唯一性证明一样，证明过程基于 **Picard 迭代** 。为此构造迭代序列
$$
y_{n}+\int^{T}_{t} f(s,z_{n-1}) \; \mathrm{d}s+ \int^{T}_{t} \big[ g(s) +z_{n}\big]\; \mathrm{d}W_{s}=\xi
$$
其在 $z_{n-1}$ 既定的情况下，退化成第一步中的方程，由上一步的结果，这个迭代序列是良定义的。

与唯一性证明类似（需要留意下标），再次利用 Itô 公式和调系数的技巧，得到估计
$$
\begin{align}
&\mathbb{E}( y_{n+1}-y_{n} )^{2}+\mathbb{E}\int^{T}_{t} (z_{n+1}-z_{n})^{2} \; \mathrm{d}s\\
\leq& 2c^{2}\mathbb{E}\int^{T}_{t} (y_{n}-y_{n-1})^{2}  \; \mathrm{d}s +\frac{1}{2} \mathbb{E}\int^{T}_{t} (z_{n+1}-z_{n})^{2} \; \mathrm{d}s

\end{align}
$$
记 $\displaystyle u_{n} = \mathbb{E}\int^{T}_{t} (y_{n}-y_{n-1})^{2} \; \mathrm{d}s,~v_{n}=\mathbb{E}\int^{T}_{t} (z_{n}-z_{n-1})^{2} \; \mathrm{d}s$，**要证明迭代序列收敛，只需证明 $u_{n}^{\frac{1}{2}}(0),~v_{n}^{\frac{1}{2}}(0)$ 是可和的**。 

简记 $K=2c^{2}$ 。为了给出 $u_{n},~v_{n}$ 的估计，面对上面的形式，我们仍然希望使用 Gronwall 不等式。然而直接应用是不现实的，必须做一定的修改。我们可以**从 Gronwall 不等式的证明过程中得到灵感**。
$$
-\frac{\mathrm{d}}{\mathrm{d}t} \left( e^{Kt}u_{n+1}(t) \right) +e^{Kt}v_{n+1}(t)\leq \frac{1}{2} e^{Kt}v_{n}(t)
$$
积分后亦有
$$
u_{n+1}(0)+\int^{T}_{0} e^{Kt}v_{n+1}(t) \; \mathrm{d}t\leq \frac{1}{2} \int^{T}_{0} e^{Kt}v_{n}(t) \; \mathrm{d}t
$$
通过迭代不等式并注意到 $\dfrac{\mathrm{d}}{\mathrm{d}t}u_{n}\leq0$，简单得到
$$u_{n+1}(0)\leq2^{-n}Ce^{K},\quad v_{n+1}(0)\leq Ku_{n+1}(0)+\dfrac{1}{2}v_{n}(0)$$
这足以证明我们所需的可和性。这说明了 $\{ y_{n} \}_{1}^{\infty},~\{ z_{n} \}_{1}^{\infty}$ 在我们给定的范数下是 Cauchy 列，依 $L^{2}$ 范数的完备性，取极限即为所求。

<b><font style="font-size: 120%;"><font color="#de7802">第三步</font></font></b> 考虑如下一般形式 BSDE：
$$
y+\int^{T}_{t} f(s,y,z) \; \mathrm{d}s+ \int^{T}_{t} \big[ g(s,y) +z\big]\; \mathrm{d}W_{s}=\xi
$$
此时 $f$ 需要对 $y,~z$ 同时满足 Lipschitz 条件，而 $g$ 也需要对 $y$ 满足 Lipschitz 条件。

**唯一性** 其余步骤与第二步基本类似，在使用 Itô 公式时，会多出关于 $g$ 的两项，即有
$$
\begin{align}
&\mathbb{E}( y_{1}-y_{2} )^{2}+\mathbb{E}\int^{T}_{t} (z_{1}-z_{2})^{2} \; \mathrm{d}s\\
=&-2\mathbb{E}\int^{T}_{t} \big(f(s,y_{1},z_{1})-f(s,y_{2},z_{2})\big)(y_{1}-y_{2}) \; \mathrm{d}s \\
&-\mathbb{E}\int^{T}_{t} (g(s,y_{1})-g(s,y_{2}))^{2} \; \mathrm{d}s -2\mathbb{E}\int^{T}_{t} \big(g(s,y_{1})-g(s,y_{2})\big)(z_{1}-z_{2}) \; \mathrm{d}s\\
\leq &C\mathbb{E}\int^{T}_{t} ( y_{1}-y_{2} )^{2} \; \mathrm{d}s+\frac{1}{2}\mathbb{E}\int^{T}_{t} ( z_{1}-z_{2} )^{2} \; \mathrm{d}s 
\end{align}
$$
需要通过 Lipschitz 条件和**调系数**，使得第二项前面的系数为 $\dfrac{1}{2}$，利于不等式的迭代。

**存在性** 到此时，迭代序列应为
$$
y_{n}+\int^{T}_{t} f(s,y_{n-1},z_{n}) \; \mathrm{d}s+ \int^{T}_{t} \big[ g(s,y_{n-1}) +z_{n}\big]\; \mathrm{d}W_{s}=\xi
$$
其在 $y_{n-1}$ 既定的情况下，退化成第二步中的方程。

像第二步一样，基本上重复唯一性的步骤，仍然通过 Itô 公式和调系数（注意下标的变化），得到
$$
\begin{align}
&\mathbb{E}( y_{n+1}-y_{n} )^{2}+\frac{1}{2}\mathbb{E}\int^{T}_{t} (z_{n+1}-z_{n})^{2} \; \mathrm{d}s\\
\leq &C\left(   \mathbb{E}\int^{T}_{t} (  y_{n+1}-y_{n} )^{2} \; \mathrm{d}s+\mathbb{E}\int^{T}_{t} (  y_{n}-y_{n-1} )^{2} \; \mathrm{d}s\right) 
\end{align}
$$
在估计 $\displaystyle u_{n} = \mathbb{E}\int^{T}_{t} (y_{n}-y_{n-1})^{2} \; \mathrm{d}s$ 时（对 $v_{n}$ 的估计同样由上一个不等式给出），我们得到的不等式是
$$
u_{n+1}(0)\leq C\int^{T}_{0} e^{Ct}u_{n}(t) \; \mathrm{d}t
$$
迭代此不等式足以说明 $u_{n},~v_{n}$ 是可和的，进而完成证明。<span style="float: right">Q.E.D</span>

更进一步，解的存在唯一性可以推广到如下更一般的 BSDE：
$$
y(t)+\int^{T}_{t} f(s,y(s),z(s)) \; \mathrm{d}s+ \int^{T}_{t}  g(s,y(s),z(s)) \; \mathrm{d}W_{s}=\xi
$$
其证明仍然要分成三步走，其最大的变化在于要求 $g(s,y,z)$ 满足
$$
\left| g(t,y,z_{1})-g(t,y,z_{2}) \right|\geq \alpha \left| z_{1}-z_{2} \right|,\quad \alpha>0  
$$
这保证在给定 $\bar{z}=g(t,y,z)$ 后，可以用**隐函数定理**确定 $z$ （还需额外克服一些可测性问题）。

---
*Reference: [[papeng1.pdf]]*

---
*2025-8-17*