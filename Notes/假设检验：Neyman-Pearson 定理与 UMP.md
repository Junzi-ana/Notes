---
{}
---
#SmallEssays/数理统计 

对于假设检验问题
$$
H_{0}:\theta =\Theta_{0}\leftrightarrow H_{1}:\theta =\Theta_{1}
$$
什么时候该拒绝原假设 $H_{0}$，如何评价这个检验是好是坏，怎么样得到最好的检验，这些都是值得研究的问题。

Fischer 采用的方法是，控制犯第一类错误（弃真）的概率，在此基础上使犯第二类错误的概率尽可能小。记 $\phi(x)$ 为检验统计量，$\beta(\theta)=\mathbb{E}_{\theta} (\phi(X))$ 为 $\phi$ 的**效函数**，那么犯第一类错误的概率可以表示为 $\beta(\theta)\mathbb{1}_{\Theta_{0}}$，犯第二类错误的概率可以表示为 $(1-\beta(\theta))\mathbb{1}_{\Theta_{1}}$ 。于是，上述思想可以表达为：选定一个水平 $\alpha$，使得 $\beta(\theta)\leq\alpha$ 对一切 $\theta \in \Theta_{0}$ 成立，在此约束下，使 $\beta(\theta)$ 在 $\Theta_{1}$ 上尽可能大。为此，引出如下定义：

**定义** 记 $\Phi_{\alpha}$ 为一切水平为 $\alpha$ 的检验 $\phi$ 作成的集合，若 $\phi \in \Phi_{\alpha}$ 满足对任何 $\phi_{1}\in \Phi_{\alpha}$，都有
$$
\beta_{\phi}(\theta)\geq \beta_{\phi_{1}}(\theta),\quad \theta \in\Theta_{1}
$$
则称 $\phi$ 是**水平 $\alpha$ 的一致最优检验（UMP）**。

遗憾的是，这个条件比较苛刻，一般来说 UMP 是不存在的，尤其是当 $\Theta_{1}$ 不止包含一个点时，使得 $\beta(\theta_{1})$ 大的检验不一定同时使得 $\beta(\theta_{2})$ 大。在 $\Theta_{1}$ 为单点时，UMP 一般存在，但仍然难以确定。只在一种特殊情况下，即 $\Theta_{0}$ 和 $\Theta_{1}$ 都是单点时，UMP 容易确定，即如下定理：

**Neyman-Pearson 基本引理** 设样本 $X\sim f(x;\theta)$，对于简单假设检验问题
$$
H_{0}:\theta =\theta_{0}\leftrightarrow H_{1}:\theta =\theta_{1}
$$
对任给的水平 $\alpha$，其 UMP 存在且为[[数理统计基本思想：似然函数、似然比 |似然比检验]]。

---
*Reference: 数理统计学教程, 陈希孺, 倪国熙*

---
*2025-10-1*