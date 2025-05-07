---
title: 从有限温度场论导出量子力学微扰论能级修正公式
date: 2025-05-07 21:31:00 +0800
description: 通过有限温度场论的方法推导出量子力学微扰论中的能级修正公式
categories: [量子场论]
tags: [量子场论, 凝聚态场论, 量子力学, 微扰论]     # TAG names should always be lowercase
math: true
fig_path: /assets/gh_pages_assets/img/post/2025-05-07-perturbation
image:
  path: /assets/gh_pages_assets/img/post/2025-05-07-perturbation/G_definition_preview.png
  alt: 格林函数的费曼图定义
---

新开通了主页，贴一篇以前写的文章充实一下网站内容&#129325;。

在这篇笔记中，我们将通过有限温度场论的方法推导出量子力学微扰论中的能量公式。（娱乐向，用大炮打蚊子。）

## 1. 微扰哈密顿量
微扰哈密顿量有如下形式

$$
\begin{align}
    H=H_0+V 
\end{align}
$$

假设 $H_0$ 是我们可以严格求解的部分，$V$ 是扰动项。

把 $H_0$ 的第 $n$ 能级本征态记作 $\{\|n\rangle\}$， 满足
$H_0\|n\rangle=E_n \|n\rangle$.

## 2. 有限温度路径积分
考虑一个无相互作用的费米子系统，每个费米子都由哈密顿量 $H$ 描述.
可以写出相干态路径积分

$$
\begin{align}
    \mathcal{Z}=\int \mathcal{D}\left[c^\dagger, c\right]e^{-S}
\end{align}
$$

其中作用量是

$$
\begin{align}
    S=\int_0^{\beta} d\tau\left[\sum_n c^\dagger_n\left(\partial_\tau+E_n-\mu\right)c_n+\sum_{mn}c^\dagger_m V_{mn}c_n\right] \label{action}
\end{align}
$$

这里 $c_n^\dagger\left(\tau\right)$，$c_n\left(\tau\right)$ 是相干态费米场， $V_{mn}\equiv\langle m\|V\|n\rangle$，$\mu$ 是化学势，$\beta=1/T$ 是温度的倒数。

<div> 
<b>注: </b> <span class="remark_context">&nbsp;&nbsp;为什么用费米子系统而不用玻色子系统？因为费米子具有Pauli不相容的特性，在零温极限下，会各自占据一个能级，这样我们可以通过改变化学势来改变系统基态时的能级占据情况，方便从基态系统能量期望值求出各能级的能量特征值。
</span>
</div>
<br/>
傅立叶变换到频域表象
$c_n(\tau)=\frac{1}{\beta}\sum_{m\in\mathbb{Z}} e^{-i\omega_m\tau}c_{n\omega_m}$,
频率 $\omega_m=\left(2m+1\right)\pi/\beta$, $m\in\mathbb{Z}$。 无势场 $V$ 时，松原格林函数是

$$
\begin{align}
\mathcal{G}_m\left(\omega\right)=\frac{1}{-i\omega+E_n-\mu}
\end{align}
$$

## 3. 微扰论能级修正公式的推导
现在我们开始计算加上扰动 $V$ 后的能量期望值 $E=\left<\hat{H}\right>$，这里的期望值 $$\left\langle\cdot\right\rangle$$ 指的是对应温度为$\frac{1}{\beta}$的平衡态系综平均值 $$\left\langle\cdot\right\rangle=\text{Tr}\left[e^{-\beta\hat{H}}(\cdot)\right]$$。


$$ 
\begin{align}
    \left<\hat{H}\right> = \sum_{mn}\left(E_{m}\delta_{mn}+V_{mn}\right)\left<c^\dagger_mc_n\right> \label{Hamiltonian_expect}
\end{align}
$$

$\left<c^\dagger_mc_n\right>$ 可以由虚时序的松原格林函数得到

$$
\begin{align}
    \left<c^\dagger_mc_n\right>=\lim_{\tau\to0^+}\left<c^\dagger_m\left(\tau\right)c_n\left(0\right)\right>
\end{align}
$$

做傅立叶变换得到

$$
\begin{align}
    \left<c^\dagger_m c_n\right>=\frac{1}{\beta}\sum_{\omega\omega'}e^{i\omega 0^+}\left<c^\dagger_{m\omega}c_{n\omega'}\right>
\end{align}
$$

从这里开始使用简化符号 $$\sum_{\omega} f (\omega)$$ 代替 $\sum_{m\in\mathbb{Z}}f(\omega_m)$，$\omega_m=(2m+1)\pi/\beta$

定义包含微扰后的格林函数为

![Green's function]({{ page.fig_path }}/G_definition.png){: .center  w="300"}

则有

$$
\begin{align}
    \left<c^\dagger_{m\omega}c_{n\omega'}\right>=
    -\delta_{\omega\omega'}G_{mn}\left(\omega\right)
\end{align}
$$

根据Dyson方程
![Dyson Equation]({{ page.fig_path }}//DysonEquation.png)

$$
\begin{align}
    G\left(\omega\right)=\mathcal{G}\left(\omega\right)-\mathcal{G}\left(\omega\right)VG\left(\omega\right)
\end{align}
$$

有

$$
    \begin{aligned}
    G\left(\omega\right)&=\left(1+\mathcal{G}V\right)^{-1}\mathcal{G} \\
    &=\sum_{k=0}^{+\infty}(-1)^k(\mathcal{G}V)^k\mathcal{G}
    \end{aligned}
$$

（也可由直接把式 \eqref{action} 中费米场二次型的矩阵取逆得出该关系。）

代入式 \eqref{Hamiltonian_expect},

$$
\begin{align}
    \left<\hat{H}\right> &=
    \sum_{mn}\left(E_m\delta_{mn}+V_{mn}\right)\frac{1}{\beta}\sum_\omega
        e^{i\omega 0^+}\sum_{k=0}^{+\infty}(-1)^{k+1}\left[(\mathcal{G}V)^k\mathcal{G}\right]_{nm} \notag \\
    &=\frac{1}{\beta}\sum_\omega
    e^{i\omega 0^+}\sum_{k=0}^{+\infty}
    \left\{
    (-1)^{k+1}\text{Tr}\left[\left(E+V\right)(\mathcal{G}V)^k\mathcal{G}\right]
    \right\} \label{E_n_result}
\end{align}
$$

这里我们用了矩阵记号 $$\left[ E \right]_{mn} = E_m \delta_{mn}$$.

那么$n$ 阶微扰的能量有限温期望值 $$\left<\hat{H}\right>$$ 可由

$$
\begin{align}
    \left<\hat{H}^{\left(n\right)}\right> &=
    \left(-1\right)^{n+1}\frac{1}{\beta}\sum_{\omega}e^{i\omega 0^+}
    \text{Tr}\left[E\left(\mathcal{G}V\right)^n\mathcal{G}-\left(V\mathcal{G}\right)^n\right]
    \text{, for }n=1,2,\dots
\end{align}
$$

给出。

零温极限 $\beta\to\infty$下，能量期望值就是基态的能量特征值。而由于费米子具有Pauli不相容的性质，基态下费米子从最低能级开始向上填充，系统的基态能量等于各被填充能级能量特征值的加和。通过改变化学式 $\mu$ 可以改变系统费米子的个数，从而改变能级占据情况，根据系统基态能量的变化即可求出各能级的能量特征值。



## 4. 例：二阶微扰能级修正公式

接下来我们来计算到二阶项的具体表达式。
第 $0$ 阶也就是式 \eqref{E_n_result} 中 $k=0$ 包含 $E$ 的那一项，我们得到

$$
    \begin{align}
    \left<\hat{H}^{\left(0\right)}\right>
    &= -\frac{1}{\beta}\sum_{\omega}e^{i\omega 0^+}
    \text{Tr}\left[E\mathcal{G}\right] \notag\\
    &= -\frac{1}{\beta}\sum_{n}E_n\sum_{\omega}e^{i\omega 0^+}
    \frac{1}{-i\omega+E_n-\mu} \notag \\ 
    &=\sum_n E_n n_F\left(E_n\right)
    \end{align}
$$

取零温极限 $T\to0$ 可得

$$
\begin{align}
    \left<\hat{H}^{\left(0\right)}\right>\xrightarrow{\beta\to+\infty}\sum_{E_n<\mu}E_n
\end{align}
$$

计算 $1$ 阶项, 可得

$$
\begin{align}
    \left<\hat{H}^{\left(1\right)}\right>
    &=\frac{1}{\beta}\sum_\omega
    e^{i\omega 0^+}\text{Tr}\left[E\mathcal{G}V\mathcal{G}-V\mathcal{G}\right] \notag\\
    &=\frac{1}{\beta}\sum_{\omega}e^{i\omega 0^+}\left(
        \sum_m E_m\frac{1}{-i\omega+E_m-\mu}V_{mm}\frac{1}{-i\omega+E_m-\mu}
        -\sum_m V_{mm}\frac{1}{-i\omega+E_m-\mu}
    \right)\notag\\
    &=\sum_m E_m V_{mm}\left[-\frac{\beta}{4}\text{ sech}\left(\frac{(E_m-\mu)\beta}{2}\right)^2\right]
    +\sum_m V_{mm}n_F\left(E_m-\mu\right) \notag\\
    &\xrightarrow{\beta\to+\infty} \sum_{E_n<\mu}V_{nn}
\end{align}
$$

计算 $2$ 阶项，有

$$
\begin{align}
    \left<\hat{H}^{\left(2\right)}\right>
    =&-\frac{1}{\beta}\sum_{\omega}e^{i\omega 0^+}\text{Tr}
    \left[E\mathcal{G}V\mathcal{G}V\mathcal{G}-V\mathcal{G}V\mathcal{G}\right] \notag \\
    =&-\frac{1}{\beta}\sum_{\omega}e^{i\omega 0^+} 
    \left[\sum_{mn}E_mV_{mn}V_{nm}\mathcal{G}_m^2\mathcal{G}_n-\sum_{mn}V_{mn}V_{nm}\mathcal{G}_m\mathcal{G}_n\right]
    \notag\\
    =& \sum_{mn}E_{m}V_{mn}V_{nm}\left[\frac{\beta\text{ sech}\left(\frac{(E_m-\mu)\beta}{2}\right)^2}{4\left(E_n-E_m\right)}
        + \frac{\tanh\left(\frac{(E_m-\mu)\beta}{2}\right)-\tanh\left(\frac{(E_n-\mu)\beta}{2}\right)}{2\left(E_m-E_n\right)^2}\right] \notag \\
    &-\sum_{mn}V_{mn}V_{nm}\frac{\tanh\left(\frac{(E_m-\mu)\beta}{2}\right)
    -\tanh\left(\frac{(E_n-\mu)\beta}{2}\right)}{2\left(E_m-E_n\right)} \notag \\
    \xrightarrow{\beta\to+\infty}&
    -\sum_{\substack{E_m>\mu\\E_n<\mu}}\frac{V_{mn}V_{nm}}{E_n-E_m} +2\sum_{\substack{E_m>\mu\\E_n<\mu}}\frac{V_{mn}V_{nm}}{E_n-E_m} \notag \\
    =&\sum_{\substack{E_m>\mu\\E_n<\mu}}\frac{V_{mn}V_{nm}}{E_n-E_m} 
\end{align}
$$

通过调整化学势 $\mu$ 的值，即可得到微扰下各能级的能量。