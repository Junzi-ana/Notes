---
{}
---
#SmallEssays/BSDE 

对于*参考文献 (2.4)* 给出的效用最大化问题，其对应一个 $BSDE(F,f)$
$$
Y_{t}=F+\int^{T}_{t} f(s,Y_{s},Z_{s}) \; \mathrm{d}s-\int^{T}_{t} Z_{s}^{T} \; \mathrm{d}B_{s}  
$$
其中生成子取作
$$
f(t,z)=\frac{\alpha}{2}\text{dist}^{2}_{\sigma_{t}^{T}\mathcal{C}}(z+\frac{1}{\alpha}\theta_{t})-z^{T}\theta_{t}-\frac{1}{2\alpha}\left| \theta_{t} \right| ^{2}
$$
是局部 Lipschitz 的。

当回报 $F$ 有界时，BSDE 的解是存在唯一的，参见*参考文献 Lemma 3.3*，更进一步在 *Remark 3.4* 中指出了 $\displaystyle \int^{s}_{0} Z^{T}_{t} \; \mathrm{d}B_{t},~s \in[0,T]$ 是 $BMO$ 鞅，详见笔记 [[BMO 空间、BMO 鞅]]。

当**回报 $F$ 无界**时，对于一个无界变量，最常见的做法是对它**局部化**，或者说**截断**，然后再取极限。那么我们不禁要问，在 BSDE 的语境下，这个极限应该怎么取？我们有如下定理（完整的记号表述参见原文）。

**定理** *(Lemma 3.5)* 考虑一列 $BSDE(F^{n},f ^{n})$ 满足如下条件
1. $F^{n}$ 是一致有界的 $\mathcal{F}_{T}$ 随机变量，且 $F^{n}\to F~~\text{a.s.}$
2. $f^{n}$ 连续且关于 $y$ 单调，关于 $z$ 满足线性增长条件，对 $t\in[0,T]$，当 $z_{n}\to z$ 时有 $f ^{n}(t,z_{n})\to f(t,z)~~\text{a.s.}$
若 $BSDE(F^{n},f^{n})$ 的解 $(Y^{n},Z^{n})$ 满足 $Y^{n}$ 关于 $n$ 单调增且 $\sup_{n}{\left\| Y^{n} \right\|_{\mathcal{S}^{\infty}}}\leq C$，则 $(Y,Z)$ 是 $BSDE(F,f)$ 的解，其中 $Y^{n} \overset{[0,T]}{\rightrightarrows} Y$ 依概率，$Z^{n}\xrightarrow{M^{2}}Z$ 。

现在，令 $F^{n,k}=F^{+}\wedge n-F^{-}\wedge k$，于是 $BSDE(F^{n,k},f)$ 有唯一解 $(Y^{n,k},Z^{n,k})$ 。由**比较原理**，$Y^{n,k}$ 对 $n$ 单调增而对 $k$ 单调减，且有**先验估计** `[!!archive-restore|To be Linked|255, 234, 0]`  
$$
\underline{Y}_{t}\leq Y^{n,k}_{t}\leq \overline{Y}_{t}
$$
其中 $\underline{Y}$ 是 $BSDE(F^{n,k},-z^{T}\theta-\frac{1}{2\alpha}\left| \theta \right|^{2})$ 的解， $\overline{Y}$ 是 $BSDE(F^{n,k},\frac{\alpha}{2}\left| z \right|^{2})$ 的解，它们都依赖 $n,~k$ 。此时，$\underline{Y}$ 和 $\overline{Y}$ 都有显示表达式，这将利用最小局部鞅测度（MLMM）给出。在此可以通过将 $F^{n,k}$ 分别放缩为 $F^{-}$ 和 $F^{+}$ 得到不依赖于 $n,~k$ 的估计，仍记作 $\underline{Y},~\overline{Y}$ 。`[!!archive-restore|To be Linked|255, 234, 0]` 

然而，这个估计只能说明 $Y^{n,k}$ 是局部有界，为此还需要使用局部化方法使它一致有界。对 $j\geq1$ 引入停时列
$$
\tau_{j}=T\wedge \inf\{t\in[0,T]:\overline{Y}_{t} \wedge(-\underline{Y}_{t})>j\}
$$
并记 $(Y^{n,k}_{j}(t),Z^{n,k}_{j}(t))=(Y^{n,k}_{t\wedge \tau_{j}},Z^{n,k}_{t}\mathbb{1}_{\{t\leq \tau_{j}\}})$ 是 $BSDE(F^{n,k}_{j},\mathbb{1}_{\{t\leq \tau_{j}\}}f)$ 的解，其中 $F^{n,k}_{j}=Y^{n,k}_{j}(T)$ 。

此时，对于固定的 $j$，$Y^{n,k}_{j}$ 一致有界。现在我们需要的各种有界性都被满足，从而可以对 $n,~k$ 取极限，由 *Lemma 3.5* 知 $(Y_{j},Z_{j})$ 是 $BSDE(F_{j},\mathbb{1}_{\{t\leq \tau_{j}\}}f)$ 的解，其中 $F_{j}=Y_{j}(T)$ 。

最后再对 $j$ 取极限，这个极限需要人工定义为
$$
Y_{t}=Y_{1}(0)+\sum^{\infty}_{j=1}Y_{j}(t)\mathbb{1}_{(\tau_{j-1},\tau_{j}]}(t),\quad  Z_{t}=\sum^{\infty}_{j=1}Z_{j}(t)\mathbb{1}_{(\tau_{j-1},\tau_{j}]}(t)
$$
可以验证，$Y_{j}(t)\overset{[0,T]}{\rightrightarrows}Y_{t}$ 和 $\displaystyle\int^{T}_{0} \left| Z_{j}(t)-Z_{t} \right|^{2} \; \mathrm{d}t \to0~~\text{a.s.}$ 进而有 $(Y,Z)$ 满足 $BSDE(F,f)$ 。

最后，还需要说明 $(Y,Z)$ 定义在适当的空间上，即满足一些可积性条件，这些条件的叙述和验证都异常繁琐，在此不多赘述。

---
*Reference: Utility maximization in constrained and unbounded financial markets: Applications to indifference valuation, regime switching, consumption and Epstein-Zin recursive utility, Ying Hu, Gechun Liang, Shanjian Tang*

---
*2025-9-28*


