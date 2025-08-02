---
title: 準ニュートン法 (Quasi-Newton method)
date: 2025-04-02 12:00 +0900
categories: [Math, Nonlinear Programming]
tags: [Optimization, Quasi-Newton, BFGS, DFP, Numerical, Algorithm]
author: Youkoutaku
math: true
mermaid: true
---

### 2.4.3 準ニュートン法 (Quasi-Newton method)

ニュートン法における勾配のヤコビ行列（評価関数 $f$ のヘッセ行列 $H=\partial^2f/\partial x^2$）は計算が複雑なので，近似行列で置き換えられば計算量が減らせる．

ある点 $x_k$ から次の点 $x_{k+1}$ への修正量 $\Delta x_k = x_{k+1}-x_k$を求める際に，勾配のヤコビ行列$\partial \nabla f(x_k)/\partial x$の近似行列 $B_k$として

$$\Delta x_k=-B_k^{-1}\nabla f(x_k)$$

とすることが考える．これを準ニュートン法(quasi-Newton method)という．

$H_k$の更新式を決めるために，$x_{k+1}$における勾配のテイラー展開する(1次まで)と，

$$\nabla f(x_{k+1})\approx \nabla f(x_{k+1})+H(x_{k})(x_{k+1}-x_k)$$
- $s_k:=x_{k-1}-x_k$
- $y_k:=\nabla f(x_{k+1}) - \nabla f(x_k)$

整理すると，

$$y_k=H(x_k)s_k$$

準ニュートン法においてヘッセ行列$H(x_k)$を直接計算せずに，ヘッセ行列の近似$B_k$を作るため，

$$B_{k+1}s_k=y_k$$

という条件で近似行列を更新する．これは**セカント条件(secant equation)** という．この条件を満たす$B_{k+1}$は無数にある．

#### BFGS（最も一般的な準ニュートン法）
BFGS（Broyden-Fletcher-Goldfarb-Shanno）アルゴリズムは、準ニュートン法の中でも最も広く使われる手法の一つで、次の更新則を用いる。
$$ B_{k+1} = B_k - \frac{B_k s_k s_k^T B_k}{s_k^T B_k s_k} + \frac{y_k y_k^T}{y_k^T s_k} $$
また、$B_k^{-1}$ を直接更新する方法（Inverse BFGS: L-BFGS）もよく用いられる。
$$ B_{k+1}^{-1} = (I - \rho_k s_k y_k^T) B_k^{-1} (I - \rho_k y_k s_k^T) + \rho_k s_k s_k^T $$
ここで、$\rho_k = \frac{1}{y_k^T s_k}$ である。

#### DFP（Davidon-Fletcher-Powell法）
BFGSとは異なるアプローチで、次の更新式を用いるDFP（Davidon-Fletcher-Powell）法もある：

$$B_{k+1}^{-1} = B_k^{-1} + \frac{s_k s_k^T}{s_k^T y_k} - \frac{B_k^{-1} y_k y_k^T B_k^{-1}}{y_k^T B_k^{-1} y_k}$$

---
#### Algorithm : Quasi-Newton method
1. $k \gets 0$ 
2. Initial point $\gets x_0\in\mathbb{R}^n$ 
3. Initial matrix $\gets B_0 \in \mathbb{R}^{n\times n}$
4. Loop:
	1. If  $\|\nabla f(x_k) \| = \|d_k\| \approx 0$ 
		a. break
	2. $\Delta x_{k} \gets -B_k^{-1}\nabla f(x_k)$
	3. $\min{f(x_k+\alpha_k\Delta_x)}\to \alpha_k$
	4. $x_{k+1}\gets x_k+\alpha_k\Delta _k$
	5. $s_k\gets x_{k-1}-x_k$
	6. $y_k\gets \nabla f(x_{k+1}) - \nabla f(x_k)$
	7. $B_{k+1}\gets BFGS\;or\;DFP$
	8. $k \gets k+1$
5. Next setup
---
最初の$B_0$は単位行列を用いることで，最初の探索方向$\Delta x_0$は最急降下方向になる．

---
## 参考資料
- [大塚 敏之](https://www.ids.sys.i.kyoto-u.ac.jp/index.html), 非線形最適制御入門(Introduction to Nonlinear Optimal Control)，コロナ社, 2011. 