---
{}
---
#SmallEssays/数理统计 

在统计里，推断和决策是一体两面的。假定总体 $X\sim F_{\theta}$，我们往往需要根据试验的结果作出某种决策 $d(X)$，最典型的例子就是[[假设检验的基本原理、测度之间的距离|假设检验]]了，$d$ 可以是拒绝或者接受原假设。决策的后果使用损失函数 $L(d;\theta)$ 来衡量，我们作出的决策应当最小化损失函数。另一方面，我们可以将对 $\theta$ 的估计行为本身也可以看作是一种决策，进而 $\hat{\theta}$ 应当使 $L(\hat{\theta};\theta)$ 尽可能小。

针对于某种决策风格 $d$ 或估计量 $\hat{\theta}$，定义
$$
R(d;\theta)=\mathbb{E}_{X} L(d(X);\theta)
$$
为**风险函数**，表示在平均意义上这种决策风格会带来的损失。但毕竟 $\theta$ 未知，很多时候我们关心最坏情况下的风险，即定义
$$
M(d)=\sup_{\theta \in\Theta}R(d;\theta)
$$
并希望能作出使得最大风险最小的决策，这一准则称为 **minimax 准则**，$R^{*}=\inf_{d} M(d)$ 称为**极小极大风险**。

统计推断中经常取用平方损失函数 $L(\hat{\theta};\theta)=(\hat{\theta}-\theta)^{2}$，此时 $R(\hat{\theta})$ 实际上就是均方误差 $MSE$。局限于无偏估计，$MSE$ 就是方差 $\text{Var}\,\hat{\theta}$，此时 minimax 估计就是 UMVUE。

不过以上的讨论仅仅是给出了一种准则，我们显然不可能通过优化 $M(d)$ 来作估计或者决策。甚至于，证明一个估计或决策满足 minimax 准则都是极其困难的，事实上，很多情况下满足 minimax 准则的决策根本就不存在。为此，我们需要一个更加可行的办法。

首先 $R(d;\theta)$ 的定义大概是不好修改了，我没没法对样本提出什么要求，而且也没有比期望更容易计算的量了。关键还是在于我们可以对 $R(d;\theta)$ 里的 $\theta$ 做些什么。我们当然可以取下确界来除掉 $\theta$ ，但这样得到的结果未免也太过荒谬了，如果可以对 $\theta$ 积分就好了。

可以吗？按频率学派的观点，那必然是不可以的，因为 $\theta$ 是一个固定的数。但按 [[Bayes 统计：基本原理与例子|Bayes 学派]]的观点，也不是不行。假设有分布 $\theta \sim \pi(\theta)$ ，我们可以计算后验平均风险
$$
R(d;\pi)=\mathbb{E}_{\theta}R(d;\theta)=\mathbb{E}_{\theta}\mathbb{E}_{X|\theta}L(d(X);\theta)
$$
我们希望能作出后验平均风险最小的决策 $d^{\pi}$，称为 **Bayes 准则**，并记 $R^{*}_{\pi}=\inf_{d}R(d;\pi)$ 为 **Bayes 风险**。当然，可进一步定义 $R^{*}_{B}=\sup_{\pi}R^{*}_{\pi}$ 为最坏 Bayes 风险，显然成立如下关系
$$
R^{*}\geq R^{*}_{B}=\sup_{\pi }R^{*}_{\pi}
$$

有趣的是，使用 Fubini 定理得到
$$
\begin{align}
R(d;\pi)=\mathbb{E}_{\theta}\mathbb{E}_{X|\theta}L(d(X);\theta)=\mathbb{E}_{X}\mathbb{E}_{\theta|X}L(d(X);\theta)=\mathbb{E}_{X}\rho_{\pi}(d|X)
\end{align}

$$
其中，$\rho_{\pi}(d|X)$ 是后验损失。要最小化 $R(d;\pi)$，我们只需要对每个样本 $X$，作出使得 $\rho_{\pi}(d|X)$ 最小的决策 $d^{\pi}(X)$ 即可，这并非难事，因为 $\rho_{\pi}(d|X)$ 可以写为对损失函数对后验概率 $\pi(\theta|X)$ 取期望
$$
\rho_{\pi}(d|X)=\int L(d;\theta) \; \mathrm{d}\pi(\theta|X) 
$$
而 $\pi(\theta|X)$ 可以由 Bayes 公式直接计算，于是得到 **Bayes 决策（Bayes 估计）** $d^{\pi}(X)=\underset{d}{\text{argmin}}\;\rho_{\pi}(d|X)$ 。

利用 Bayes 估计和上述关系，我们可以证明一个估计是 minimax 估计。下面举一个非常简单的例子

**例** $X\sim N(\mu,~1)$，对于单个样本 $x$，$x$ 是 $\mu$ 在平方损失下的 minimax 估计。

**证明** 计算风险函数
$$
R(x;\mu)=\mathbb{E}(x-\mu)^{2}=\text{Var}\,x=1,\quad \forall\;\mu
$$
根据 minimax 估计的定义
$$
R^{*}=\inf_{\hat{\mu}}R(\hat{\mu};\mu)\leq R(x;\mu)=1
$$
接下去只需证明 $R^{*}\geq1$ 。根据 minimax 风险和 Bayes 风险的关系，只需找到一个分布 $\pi(\mu)$ 使得 $R^{*}_{\pi}=1$，当然更有可能的是找到一列 $\pi (\mu)$ 使得 $R^{*}_{\pi}\to1$ 。直接选取 $\pi$ 为共轭先验分布 $N(0,\sigma^{2})$，根据笔记 [[Bayes 统计：基本原理与例子#^1a3092]] 其后验分布
$$
\mu|x\sim N\left( \frac{\sigma^{2}}{1+\sigma^{2}}x,~ \frac{\sigma^{2}}{1+\sigma^{2}} \right) 
$$
于是后验损失
$$
\rho_{\pi}(\hat{\mu}|x)=\mathbb{E}_{\mu}(\mu-\hat{\mu})^{2}
$$
当 $\hat{\mu}_{\sigma}=\mathbb{E}(\mu|x)=\frac{\sigma^{2}}{1+\sigma^{2}}x$ 时后验损失达到最小，为后验方差 $\frac{\sigma^{2}}{1+\sigma^{2}}$，此时的 Bayes 风险就等于 $\frac{\sigma^{2}}{1+\sigma^{2}}$ 。令 $\sigma \to \infty$ 得 $R^{*}_{\pi}\to1$ ，从而 $R^{*}\geq \sup_{\pi }R^{*}_{\pi}=1$，$x$ 是 $\mu$ 的 minimax 估计。

---
*Reference: [[lecture2 (1).pdf]]*

---
*2025-11-28*














