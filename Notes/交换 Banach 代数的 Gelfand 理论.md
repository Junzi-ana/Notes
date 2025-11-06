---
{}
---
#SmallEssays/泛函分析 

我们通常使用**乘性泛函**和**极大理想**来研究交换 Banach 代数中元素的可逆性。

在 [[Gelfand 理论的动机：可除性研究]] 中给出了乘性泛函 $p$ 的定义，它有如下基本性质。

**性质** $\mathcal{L}$ 是交换 Banach 代数，则 $p$ 是压缩，即
$$
\left| p(M) \right|\leq \left\| M \right\|,\quad \forall\;M\in \mathcal{L} 
$$
借助这条性质，我们很容易说明，若 $M$ 可逆，则 $p(M)\neq0$，然而其逆命题是否成立？这是本文的核心。

沿着前文的思路，如果 $M\in \mathcal{L}$ 不可逆，则它应该属于某个理想。哪个理想呢？不管怎么样，$M$ 肯定属于由它生成的主理想 $(M)$ ，进而属于某个包含 $(M)$ 的极大理想 $\mathcal{M}$，进而再由前文的讨论，$\mathcal{L}/\mathcal{M}$ 是一个可除的 Banach 代数。

> [!remark]
> 从抽象代数的角度来看，$\mathcal{M}$ 是极大理想只能保证 $\mathcal{L}/\mathcal{M}$ 作为环是可除的。还须说明 $\mathcal{M}$ 本身是 $\mathcal{L}$ 的闭子空间，才能保证 $\mathcal{L}/\mathcal{M}$ 在**商范数**下它成为一个 Banach 代数。

于是由 Mazur 定理，若 $M$ 不可逆，则复合 $p_{\mathcal{M}}:\mathcal{L}\to\mathcal{L}/\mathcal{M}\to \mathbb{C}$ 就是一个乘性泛函，满足 $p_{\mathcal{M}}(M)=0$ 。于是我们证明了如下定理

**定理** $\mathcal{L}$ 是交换 Banach 代数，$M\in \mathcal{L}$ 可逆 $\iff$ 对任意 $p:\mathcal{L}\to \mathbb{C}$ 是非 $0$ 同态，$p(M)\neq0$

特别地，$\zeta I-M$ 不可逆 $\iff$ 存在非 $0$ 同态 $p:\mathcal{L}\to \mathbb{C}$ 使得 $p(\zeta I-M)=0$，即 $\zeta=p(M)$ 。于是我们证明了如下推论

**推论** $\mathcal{L}$ 是交换 Banach 代数，$M\in \mathcal{L}$ 是任何元素，成立谱刻画
$$
\sigma(M)=\{ p(M) \}
$$
$p$ 取遍 $\mathcal{L}$ 到 $\mathbb{C}$ 所有非 $0$ 同态

---
*Reference: 泛函分析, Peter D. Lax*

---
*2025-9-11*