---
{}
---
#SmallEssays/实分析 #SmallEssays/泛函分析 #SmallEssays/随机分析  #SmallEssays/BSDE  #FromDeepSeek 

在实变函数中，要让讨论一个可测函数 $f$ 的积分是有意义的，即 $f\in L^{1}_{\text{loc}}$，我们至少会希望 $f$ 在每个点处的行为不会太差。正如 $f$ 连续等价于 $f$ 的振幅 $\omega_{f}(x)$ 为 $0$；$f$ 局部 Lebesgue 可积，等价于 $f$ 的**平均振幅**
$$
a\omega_{f}(x)=\lim_{ \delta \to 0^{+} } \frac{1}{|B_{\delta}|}\int_{B_{\delta}} \left| f(y)-f(x) \right|  \; \mathrm{d}y 
$$
几乎处处为 $0$，即成立如下定理

**Lebesgue 微分定理** 
$$
f\in L^{1}_{\text{loc}} \iff a\omega_{f}(x)=0\quad\text{a.e.}
$$
并称满足 $a\omega_{f}(x)=0$ 的点 $x$ 为 $f$ 的 **Lebesgue 点**。

进一步，当 $f$ 各处的平均振幅**一致有界**（未必一致趋于 $0$）时，称 $f$ 是**有界平均震荡**的，记 $f\in BMO$ ，即

**定义** $f\in BMO\iff$ $a\omega_{f}(Q)$ 对任意方体 $Q$ 一致有上界 $C$ 

> [!note]-
> 定义中的方体 $Q$ 无妨可以改成球体 $B$ 。

$BMO$ 空间毫无疑问是 $L^{1}_{\text{loc}}$ 的真子空间。在 $BMO$ 空间中可以定义范数 $\|\cdot\|_{BMO}$ 为
$$
\left\| f \right\| _{BMO}=\sup_{Q} \left( \frac{1}{|Q|} \int_{Q} \left| f(x)-f_{Q} \right|^{2}   \; \mathrm{d}x  \right) ^{\frac{1}{2}}
$$
其中，$f_{Q}$ 是 $f$ 在 $Q$ 上的平均值。然而，如此定义的 $\|\cdot\|_{BMO}$ 不满足正定性，为此需要模去一个常数，或者固定一个点处的值，如 $f(0)=0$ 。

$BMO$ 空间有如下重要性质。

**John-Nirenberg 不等式** 存在只依赖于维数的常数 $C_{1},~C_{2}$，满足对任意的 $f\in BMO$ 和任意的方体 $Q$，任意 $\lambda>0$，都成立
$$
m\{x \in Q: |f-f_{Q}| \}\leq C_{1}|Q|\exp\left(-\frac{C_{2}\lambda}{\left\| f \right\| _{BMO}}  \right) 
$$
进一步，$f\in BMO\implies e^{f}\in L^{1}_{\text{loc}}$ 。

**对偶性** Hardy 空间 $H^{1}$ 的对偶空间同构于 $BMO$（相差一个常数意义下），即
$$
\left( H^{1}(\mathbb{R}^{n}) \right) ^{*} \cong BMO
$$

$BMO$ 空间可以推广到随机的情形。在 $\mathbb{R}^{n}$ 中 $BMO$ 的定义依赖的方体 $Q$，推广到随机过程中，可以用集合 $\{ \tau \leq t \}$ 来描述，其中 $\tau$ 是停时。于是引出了如下定义：

**定义** 设 $X$ 是[[鞅收敛定理|一致可积鞅]]，若满足
$$
\left\| X \right\| _{BMO}=\sup_{\tau}\left\| \mathbb{E}\left[ (X_{\infty} -X_{\tau})^{2} |\mathcal{F}_{\tau} \right]\right\| _{L^{\infty}(\Omega)}<\infty
$$
其中，$\tau$ 取遍所有停时。由 **John-Nirenberg 不等式** 可知，$X$ 的指数鞅 $\mathcal{E}(X)$ 也是一致可积的。

在*参考文献的 Lemma 3.3 和 Remark 3.4* 给出，对于一个有界回报 $F$ 的效用最大化问题，其对应的 $BSDE(F,f)$ 有唯一解 $(Y,Z)$，且过程 $\displaystyle \int^{s}_{0} Z^{T}_{t} \; \mathrm{d}W_{t},~s \in[0,T]$ 是 $BMO$ 鞅，即说明了**投资组合 $Z$ 的剩余风险总是全局可控的**。 

---
*Reference: Utility maximization in constrained and unbounded financial markets: Applications to indifference valuation, regime switching, consumption and Epstein-Zin recursive utility, Ying Hu, Gechun Liang, Shanjian Tang*

---
*2025-8-31*

