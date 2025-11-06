---
{}
---
#SmallEssays/泛函分析 

在笔记 [[交换 Banach 代数的 Gelfand 理论]] 中已经介绍了用乘性泛函和极大理想研究 Banach 代数中元素可逆性的主要结论。本文在此基础上揭示一些更加深刻的结构，它们虽看上去没有直接地解决什么问题，却能给我们带来一些的启发。

仍然假设 $\mathcal{L}$ 是交换 Banach 代数，在前文的讨论中我们构造了一个极大理想 $\mathcal{M}$ 并据此构造了一个同态 $p_{\mathcal{M}}:\mathcal{L}\to\mathcal{L}/\mathcal{M}\to \mathbb{C}$ 。我们可以把这样的一个同态看成是 $\mathcal{M}$ 和 $N$ 的函数 $p(\mathcal{M},N)$，即固定 $\mathcal{M}$，$p$ 是 $\mathcal{L}$ 到 $\mathbb{C}$ 的同态；固定 $N$ 时，$p$ 成为**极大理想空间** $\mathscr{J}$ 上的函数。

从这个角度，$p$ 将每个 $N\in \mathcal{L}$ 对应到一个 $\mathscr{J}$ 上的函数 $p(\cdot,N)$，称为 $\mathcal{L}$ 在 $\mathscr{J}$ 上的 **Gelfand 表示** 。它有如下性质：

**性质** 设 $p$ 是 $\mathcal{L}$ 在 $\mathscr{J}$ 上的 Gelfand 表示
1. $p$ 是 $\mathcal{L}$ 到 $\mathbb{C}^{\mathscr{J}}$ 的代数同态，其中 $\mathbb{C}^{\mathscr{J}}$ 是 $\mathscr{J}$ 上的复值函数全体
2. $p$ 是一个收缩，即 $\left| p (\mathcal{M},N) \right|\leq \left\| N \right\|,\quad \forall\; N\in \mathcal{L}$
3. $p(\cdot,N)$ 的值域就是 $\sigma(N)$
4. $p(\cdot,I)=1$ 
5. $p$ **分离 $\mathscr{J}$ 中两点**，即对两个不同的极大理想 $\mathcal{M},~\mathcal{M'}$，存在 $N$ 使得 $p(N,\mathcal{M})\neq p(N,\mathcal{M}')$

$\mathscr{J}$ 上的自然拓扑是使得对所有函数 $\{ p(\cdot,\mathcal{M}) \}_{N\in \mathcal{L} }$ 连续的最弱的拓扑，称为 **Gelfand 拓扑**。利用 Tychonov 定理可以证明 $\mathscr{J}$ 在 Gelfand 拓扑下是紧的。

---
*Reference: 泛函分析, Peter D. Lax*

---
*2025-9-11*
