---
title: Dynamic Programming for Discrete-time System
date: 2024-05-24 11:05:21 +0900 #Tokyo
categories: [Control Theory, Optimal Control]
tags: [Optimal Control, Dynamic Programming, Discrete-Time Systems]
author: Youkoutaku
math: true #Mathematical
mermaid: true
#pin: 
#img_path: 
#image:
#  path: 
#  alt: 
---

## Discrete-time system

$$x_{[k+1]}=f(x_{[k]},u_{[k]})$$

- $x_{[k]}:$ system states
- $u_{[k]}:$ input
- $f():$ linear or nonlinear function


## Performance function

$$J=h(x_{[N]})+\sum_{k=0}^{N-1}g(x_{[k]},u_{[k]})$$

- $x_{[0]}:$ Initial states
- $x_{[N]}:$ Terminal states

## Control task
The task of optimal control is find optimal control inputs

$$u^\ast_{[0]},u^\ast_{[1]},\dots,u^\ast_{[N-1]}$$ 
which hold the minimum $J$.

---
## Backward multi stages
### $k=N\to k=N$

$$J_{N\to N}(x_{[N]})=h(x_{[N]})$$

- $J_{N\to N}=J^\ast_{N\to N}:$ The optimal cost to go for $N\to N$ (Terminal cost function)

### $k=N-1\to k=N$

$$\begin{aligned}
J_{N-1\to N}(x_{[N]},x_{[N-1]},u_{[N-1]})&=h(x_{[N]})+\sum_{k=N-1}^{N-1}g(x_{[k]},u_{[k]})\\&=J_{N\to N}(x_{[N]})+g(x_{[N-1]},u_{[N-1]})
\end{aligned}$$
According to $x_{[k]}=f(x_{[k-1]},u_{[k-1]})$, We have the following equation relying on $x_{[N-1]},u_{[N-1]}$

$$
J_{N-1\to N}(x_{[N-1]},u_{[N-1]})=J^\ast_{N\to N}(f(x_{[N-1]},u_{[N-1]}))+g(x_{[N-1]},u_{[N-1]})
$$

- $x_{[N-1]}:$ the states for $k=N-1$ (known)

Then, We can obtain the optimal cost and optimal Control for $k=N-1$ 

$$
J_{N-1\to N}^\ast(x_{[N-1]})=\min_{u_{[N-1]}}\left(J^\ast_{N\to N}(f(x_{[N-1]},u_{[N-1]}))+g(x_{[N-1]},u_{[N-1]})\right)
$$

$$
\frac{\partial J_{N-1\to N}(x_{[N-1]},u_{[N-1]})}{\partial u_{[N-1]}}=0\implies u^\ast_{[N-1]}$$

### $k=N-2\to k=N-1$

$$\begin{aligned}
&J_{N-2\to N-1}(x_{[N]},x_{[N-1]},x_{[N-2]},u_{[N-1]},u_{[N-2]})\\&=h(x_{[N]})+g(x_{[N-1]},u_{[N-1]})+g(x_{[N-2]},u_{[N-2]})
\end{aligned}$$
$$\begin{aligned}
&J_{N-2\to N-1}(x_{[N-2]},u_{[N-1]},u_{[N-2]})\\&=J_{N-1\to N}+g(x_{[N-2]},u_{[N-2]})
\end{aligned}$$

$$
\begin{aligned}
&J_{N-2\to N-1}^\ast(x_{[N-2]})\\&=\min_{u_{[N-1]},u_{[N-2]}}\left(J_{N-1\to N}(x_{[N-1]},u_{[N-1]})+g(x_{[N-2]},u_{[N-2]})\right)
\end{aligned}
$$

According to Bellman optimal theory, for $k=N-2\to k=N$, whatever the initial states $x_{[0]},\cdots,x_{[N-3]}$ and initial inputs $u_{[0]},\cdots, u_{[N-3]}$  , The remaining control must be optimal. Therefor, $$J^\ast_{N-1\to N}$$ must be obtained by $$u^\ast_{[N-1]}$$. The $u^\ast_{[N-1]}$ is known.

$$
\begin{aligned}
&J_{N-2\to N-1}^\ast(x_{[N-2]})\\&=\min_{u_{[N-2]}}\left(J^\ast_{N-1\to N}(x_{[N-1]})+g(x_{[N-2]},u_{[N-2]})\right)
\end{aligned}
$$

According to $x_{[N-1]}=f(x_{[N-2]},u_{[N-2]})$, We have the following equation relying on $x_{[N-2]},u_{[N-2]}$

$$
\begin{aligned}
&J_{N-2\to N-1}^\ast(x_{[N-2]})\\&=\min_{u_{[N-2]}}\left(J^\ast_{N-1\to N}(f(x_{[N-2]},u_{[N-2]}))+g(x_{[N-2]},u_{[N-2]})\right)
\end{aligned}
$$

$$
\frac{\partial J_{N-2\to N}(x_{[N-2]},u^\ast_{[N-1]},u_{[N-2]})}{\partial u_{[N-2]}}=0\implies u^\ast_{[N-2]}$$

## Summary
- $N-k\to k$

$$\begin{aligned}
	&J_{N-k\to N}^{*}(x_{[N-k]})\\&=\min_{u_{[N-k]}}(J_{N-(k-1)\to N}^{*}(f(x_{[N-k]},u_{[N-k]}))+g(x_{[N-k]},u_{[N-k]}))
\end{aligned}$$

$$
\frac{\partial J_{N-k\to N}(x_{[N-k]},u^\ast_{[N-(k-1)]},u_{[N-k]})}{\partial u_{[N-k]}}=0\implies u^\ast_{[N-k]}$$

---
## Reference
1. [Optimal Control by DR_CAN ](https://space.bilibili.com/230105574/channel/collectiondetail?sid=1814750)
2. 王天威. 控制之美(卷2). 清华大学出版社. 2023.
3. Rakovic, S. V., & Levine, W. S. Handbook of model predictive control. 2018. 
3. Dingyu Xue. Solving Optimization Problems with MATLAB. Tsinghua University Press. 2020.