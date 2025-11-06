---
{}
---
#SmallEssays/随机控制 #FromDeepSeek 

考虑如下最优控制问题
$$
\begin{align}
\min~~J(u)&=g(x(T))+\int^{T}_{0} L(t,x,u) \; \mathrm{d}t \\
~~\text{s.t.}~~ \mathrm{d} x &= f(t,x,u)\;\mathrm{d} t\\
\end{align}

$$
$x_{t}$ 为状态过程，$u$ 为控制过程，$J(u)$ 为成本函数。

Potryagin 方法从力学系统的角度考虑这个控制问题，将 $L$ 认为是 Lagrange 量，于是引入协变量 $p$，定义 **Hamilton 量**
$$
H^{u}(t,x,p)=p\cdot f(t,x,u)-L(t,x,u)
$$
显然有 $\displaystyle \dot{x} =\frac{\partial H^{u}}{\partial p}$，但什么时候成为一个 Hamilton 系统呢？假如把它看作一个力学系统，那么它应该满足**最小势能原理**，在控制的语境下，即 $u^{*}$ 是最优控制，此时系统成为一个 Hamilton 系统
$$
\dot{x} =\frac{\partial H^{u^{*}}}{\partial p},\quad \dot{p} =-\frac{\partial H^{u^{*}}}{\partial x}  
$$

**虚功原理**暗示我们，可以将对 $J$ 的最优化转化成对 $H$ 的最优化，事实上也确实如此，经过复杂的变分运算，可以推出
$$
\delta J=\int^{T}_{0} \frac{\partial H}{\partial u} \delta u  \; \mathrm{d}t
$$
由于 $J$ 的极值性，对于所有允许的 $\delta u$，$\delta J\geq0$，从而要求 $H$ 在 $u^{*}$ 处取极小值，即对几乎所有 $t$, 满足 
$$
H^{u^{*}}(t,x^{*},p^{*})\leq H^{u}(t,x^{*},p^{*})
$$
`[!!alarm-clock-check|Checked|79, 255, 66]` 

此外，要确定这个系统，自然需要边界条件，初值自然选取 $x^{*}(0)=x_{0}$，对于**自由边界**，终端选取 $p^{*}(T)=g'(x(T))$ 。

于是我们得到了最优控制的三个必要条件，合称 **Potryagin 极大值原理**。

Potryagin 极大值原理可以比较自然地推广到随机控制系统的情形（这里改成了最大化问题，为了和书上一致，并非本质）
$$
\begin{align}
\max~~J(u)&=\mathbb{E}\left[  g(X_{T})+\int^{T}_{0} f(t,X_{t},u) \; \mathrm{d}t\right]  \\
~~\text{s.t.}~~ \mathrm{d} X_{t} &= b(t,X_{t},u)\;\mathrm{d} t+\sigma(t,X_{t},u)\;\mathrm{d} W_{t}\\
\end{align}

$$
由于有随机项，引入两个协变量 $(y,z)$，定义
$$
H^{u}(t,x,y,z)=y\cdot b(t,x,u)+z\cdot\sigma(t,x,u)-f(t,x,u)
$$
在最优控制 $u^{*}$ 下得到协态方程
$$
\;\mathrm{d} Y^{*}_{t}=-\frac{\partial H^{u^{*}}}{\partial x}(t,X^{*}_{t},Y^{*}_{t},Z^{*}_{t})\;\mathrm{d} t+Z_{t} ^{*}\;\mathrm{d} W_{t}~,\quad Y^{*}_{T}=g'(X^{*}_{T})
$$
这是一个 **BSDE**。进一步，有如下定理成立。

**定理** 记 $h(t,x,y,z)=\sup_{u\in \mathcal{U}_{0}} H^{u}(t,x,y,z)$，设 $u^{*}\in \mathcal{U}_{0}$，满足
1. 上述 BSDE 有解 $(Y^{*},Z^{*})$
2. $u^{*}$ 满足极大性 $H^{u^{*}}(t,X^{*}_{t},Y^{*}_{t},Z^{*}_{t})=h(t,X^{*}_{t},Y^{*}_{t},Z^{*}_{t})$
3. 满足**包络定理**，即 $\displaystyle \frac{\partial H^{u^{*}}}{\partial x}(t,X^{*}_{t},Y^{*}_{t},Z^{*}_{t})=\frac{\partial h}{\partial x}(t,X^{*}_{t},Y^{*}_{t},Z^{*}_{t})$ 且 $g$ 和 $h$ 对于固定的 $x$ 是凹 *(concave)* 的
则 $u^{*}$ 是上述随机控制问题的最优控制。

---
*Reference: Optimal Stochastic Control, Stochastic Target Problems and Backward SDE, Nizar TOUZI*

---
*2025-8-23*
