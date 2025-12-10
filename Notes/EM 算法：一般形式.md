---
{}
---
#SmallEssays/统计学习 

在笔记 [[EM 算法：a toy model]] 中，我们通过一个例子引入了 EM 算法，本文给出其一般形式。

回忆混合 Gauss 模型，归属向量 $\gamma_{ik}$ 相当于 $p(z_{ik}=1|x_{i})$，需要在每一次迭代中更新，而每一步的优化目标
$$
\begin{align}
\ell(x|\pi,\mu,\Sigma)&=\sum^{n}_{i=1} \sum^{K}_{k=1}\gamma_{ik}(\ln \pi_{k}+\ln p(x_{i}|\mu_{k},\Sigma_{k})) \\
&=\mathbb{E}_{z}\ell(x,z|\pi,\mu,\Sigma)
\end{align}

$$
实际上可以看做是所有样本的对数似然量关于隐变量取期望。这其实是合理的，因为没办法真正观测到隐变量。接着**用似然量的期望来代替真正的似然量作优化**，得到一组新的参数，如是反复。

现假设观测值为 $X$，隐变量为 $Z$，条件分布 $p(x,z|\theta),~p(z|x,\theta)$ 已知，那么毫无疑问 $p(z|x,\theta)$ 的地位等同于归属向量 $\gamma_{ik}$，于是优化目标可以写为
$$
\ell(X|\theta)=\mathbb{E}_{Z}\big[ \ell(X,Z|\theta)\,\big|X,\theta ] 
$$

于是 EM 算法可以被总结如下：
1. 确定迭代初值 $\theta^{(0)}$
2. **(Expectation)** 计算 $Q(\theta;\theta^{(n)})=\mathbb{E}_{Z}\big[ \ell(X, Z|\theta)\,\big|X,\theta^{(n)} ]$
3. **(Maxmization)** 优化 $\theta^{(n+1)}=\underset{\theta}{\text{argmax}}\;Q(\theta;\theta^{(n)})$
4. 重复直至收敛

---
*2025-11-25*