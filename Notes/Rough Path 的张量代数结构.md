---
{}
---
#SmallEssays/RoughPath 

在笔记 [[Rough Path 的 Chen's Relation]] 中，引入了 Chen's Relation 并据此定义了 Rough Path $\mathbf{X}=(X,~\mathbb{X})$ 。不过，Chen's Relation 在形式上较为复杂和反直觉，通过对空间结构的研究，可以将其化为一种简单且符合直觉的形式。

简单在 $\mathbf{X}$ 前面加个 $1$，即 $\mathbf{X}_{s,t}=(1,X_{s,t},\mathbb{X}_{s,t})\in \mathbb{R}\oplus V\oplus V^{\otimes2}$，这一空间记为 $T^{(2)}(V)$ ，赋乘积空间的范数。再定义 $T^{(2)}$ 上的运算 $\otimes$
$$
(a,b,c)\otimes (a',b',c')=(aa',ab'+a' b,ac'+a' c+b\otimes b)
$$
这个运算看似复杂，其实很好理解：**每一项之间分别 $\otimes$ 运算，丢弃高阶项后按空间分类**。并且很容易验证，$(1,0,0)$ 是 $\otimes$ 运算的单位元，$(1,b,c)$ 有逆元 $(1,-b,-c-b\otimes b)$ 。

于是，记 $T_{1}^{(2)}=\{ (1,b,c)\in T^{(2)} \}$ ，$T_{1}^{(2)}$ 称为一个代数，称为**到 $2$ 截断的张量代数**。在这一框架下，原先的 Chen's Relation 就可以简单写成
$$
\mathbf{X}_{s,t}=\mathbf{X}_{s,u}\otimes \mathbf{X}_{u,t}
$$
因为有了群结构，$\mathbf{X}_{s,t}$ 的双下标可以固定一个 $s=0$，记 $\mathbf{X}_{t}=\mathbf{X}_{0,t}$，$\mathbf{X}:t\mapsto \mathbf{X}_{t}$ 可视作一条 $T^{(2)}_{1}(V)$ 中的路径。 ^d570ff

注意，$\mathbf{X}$ 理解为 $(X,\mathbb{X})$ 还是 $(1,X,\mathbb{X})$ 可以通过上下文语境确定，但无论哪种，一般不存在什么本质的影响。

---
*Reference: A Course on Rough Paths, Peter K. Friz*

---
*2025-8-26*