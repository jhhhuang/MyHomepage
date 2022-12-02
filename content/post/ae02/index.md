---
title: "[Lecture notes] Advanced Electrodynamics 02"
subtitle: Green's function, dydadic Green's function
date: 2022-03-22T00:00:00Z
summary: Green's function, dydadic Green's function.
draft: false
featured: false
authors:
  - admin
lastmod: 2022-03-22T00:00:00Z
tags:
  - Academic
categories:
  - Lecture notes
projects: []
image:
  caption: "Image credit: [**Unsplash**](https://unsplash.com/photos/CpkOjOcXdUY)"
  focal_point: ""
  placement: 2
  preview_only: false
---
# 【高等电动力学笔记02】格林函数，并矢格林函数

## 频域下的Maxwell方程

傅立叶变换（注意这边与我们常用的定义是相反的）
{{< math >}}
$$
F( t) =\int *{-\infty }^{+\infty }\mathcal{F}( \omega ) e^{-i\omega t} d\omega ,\ \mathcal{F}( \omega ) =\frac{1}{2\pi }\int* {-\infty }^{+\infty } F( t) e^{i\omega t} dt
$$
{{< math >}}

宏观Maxwell方程：

{{< math >}}
$$
\nabla \cdotp \mathbf{B}(\mathbf{r} ,t)  =0\

\nabla \cdotp \mathbf{D}(\mathbf{r} ,t)  =\rho (\mathbf{r} ,t)\
\nabla \times \mathbf{E}(\mathbf{r} ,t)  =-\frac{\partial }{\partial t}\mathbf{B}(\mathbf{r} ,t)\
\nabla \times \mathbf{H}(\mathbf{r} ,t)  =\mathbf{j}(\mathbf{r} ,t) +\frac{\partial }{\partial t}\mathbf{D}(\mathbf{r} ,t)
$$
{{< math >}}

对上述四条方程做傅立叶变换（根据我们定义的傅立叶变换，在使用求导定理时要注意符号）

{{< math >}}
$$
\nabla \cdotp \mathcal{B}(\mathbf{r} ,\omega )  =0\
\nabla \cdotp \mathcal{D}(\mathbf{r} ,\omega )  =\rho (\mathbf{r} ,\omega )\
\nabla \times \mathcal{E}(\mathbf{r} ,\omega )  =i\omega \mathcal{B}(\mathbf{r} ,\omega )\
\nabla \times \mathcal{H}(\mathbf{r} ,\omega )  =\mathcal{J}(\mathbf{r} ,\omega ) -i\omega \mathcal{D}(\mathbf{r} ,\omega )
$$
{{< math >}}

## 本构关系

线性材料频域下的本构关系可以写为

{{< math >}}
$$
\mathcal{D}( \omega ) =\stackrel {\leftrightarrow}{\epsilon }( \omega )\mathcal{E}( \omega ) +\stackrel {\leftrightarrow}{\xi }( \omega )\mathcal{H}( \omega )\
\mathcal{B}( \omega ) =\stackrel {\leftrightarrow}{\eta }( \omega )\mathcal{E}( \omega ) +\stackrel {\leftrightarrow}{\mu }( \omega )\mathcal{H}( \omega )
$$
{{< math >}}

可以定义下面的张量

{{< math >}}
$$
\stackrel {\leftrightarrow}{K}( \omega ) \equiv \begin{bmatrix}
\stackrel {\leftrightarrow}{\epsilon }( \omega ) & \stackrel {\leftrightarrow}{\xi }( \omega )\
\stackrel {\leftrightarrow}{\eta }( \omega ) & \stackrel {\leftrightarrow}{\mu }( \omega )
\end{bmatrix}
$$
{{< math >}}

引入本构关系后，可以将宏观Maxwell方程写成如下形式（当然，还有两条散度方程）

{{< math >}}
$$
(\stackrel {\leftrightarrow}{D} -i\omega \stackrel {\leftrightarrow}{K})\mathbf{e} =-\mathbf{J}
$$
{{< math >}}

其中

{{< math >}}
$$
\stackrel {\leftrightarrow}{D} =\begin{bmatrix}
0 & -\nabla \times \
\nabla \times  & 0
\end{bmatrix} ,\ \mathbf{e} =\begin{bmatrix}
\mathcal{D}( \omega )\
\mathcal{B}( \omega )
\end{bmatrix} ,\ \mathbf{J} =\begin{bmatrix}
\mathcal{J}(\mathbf{r} ,\omega )\
0
\end{bmatrix}
$$
{{< math >}}

## 格林函数

如果只考虑体系的 {{< math >}}$\displaystyle \epsilon${{< math >}} ，（ {{< math >}}$\displaystyle \mu =\mu _{0}${{< math >}} ），宏观Maxwell方程可以写为

{{< math >}}
$$
\left( \nabla \times ( \nabla \times ) -\frac{\omega ^{2}}{c^{2}} \epsilon *{r}(\mathbf{r} ,\omega )\right)\mathcal{E}(\mathbf{r} ,\omega ) =i\omega \mu* {0}\mathcal{J}_{f}(\mathbf{r} ,\omega )
$$
{{< math >}}

更普遍地，我们考虑如下形式的方程

{{< math >}}
$$
(\mathcal{L} -\lambda \rho (\mathbf{r})) u(\mathbf{r}) =f(\mathbf{r})
$$
{{< math >}}

其中 {{< math >}}$\displaystyle \mathcal{L}${{< math >}} 是某个线性微分算子， {{< math >}}$\displaystyle u(\mathbf{r})${{< math >}} 是待求解的场。对应于这条方程的格林函数定义为

{{< math >}}
$$
(\mathcal{L} -\lambda \rho (\mathbf{r})) g(\mathbf{r} ,\mathbf{r} ') =\delta (\mathbf{r} -\mathbf{r} ')
$$
{{< math >}}

这是标量形式的方程和格林函数。我们研究的电磁波是矢量，因此矢量形式的微分方程为

{{< math >}}
$$
(\mathcal{L} -\lambda \stackrel {\leftrightarrow}{\rho }(\mathbf{r}))\mathbf{u}(\mathbf{r}) =\mathbf{f}(\mathbf{r})
$$
{{< math >}}

相应的格林函数则应该写成并矢形式

{{< math >}}
$$
(\mathcal{L} -\lambda \stackrel {\leftrightarrow}{\rho }(\mathbf{r}))\stackrel {\leftrightarrow}{G}(\mathbf{r} ,\mathbf{r} ') =\stackrel {\leftrightarrow}{I} \delta (\mathbf{r} -\mathbf{r} ')
$$
{{< math >}}

因为格林函数表示的是对“源”的某种响应形式，因此在矢量情况下把格林函数写成并矢是自然的。对式(19)两边同乘 {{< math >}}$\displaystyle f(\mathbf{r} ')${{< math >}} 并对全空间积分

{{< math >}}
$$
\int (\mathcal{L} -\lambda \stackrel {\leftrightarrow}{\rho }(\mathbf{r}))\stackrel {\leftrightarrow}{G}(\mathbf{r} ,\mathbf{r} ') f(\mathbf{r} ') d^{3}\mathbf{r} '\=(\mathcal{L} -\lambda \stackrel {\leftrightarrow}{\rho }(\mathbf{r}))\int \stackrel {\leftrightarrow}{G}(\mathbf{r} ,\mathbf{r} ') f(\mathbf{r} ') d^{3}\mathbf{r} '=\int \stackrel {\leftrightarrow}{I} \delta (\mathbf{r} -\mathbf{r} ') f(\mathbf{r} ') d^{3}\mathbf{r} '=f(\mathbf{r})
$$
{{< math >}}

不难看出

{{< math >}}
$$
\mathbf{u}(\mathbf{r}) =\int \stackrel {\leftrightarrow}{G}(\mathbf{r} ,\mathbf{r} ') f(\mathbf{r} ') d^{3}\mathbf{r} '
$$
{{< math >}}

于是所有的问题都转化为了对（并矢）格林函数的求解。同时我们可以看到，格林函数是不依赖于源的具体形式的，只跟方程的形式，即体系有关（ {{< math >}}$\displaystyle \mathcal{L}${{< math >}} ， {{< math >}}$\displaystyle \stackrel {\leftrightarrow}{\rho }${{< math >}} ）。格林函数可以理解为按照某种规则对空间源的分布进行求和，所有的响应叠加起来就是我们要求解的场。

## 并矢格林函数的形式

出于简单，我们考虑三维空间中的各向同性介质。Maxwell方程为

{{< math >}}
$$
\left( \nabla \times \nabla \times -k^{2}\right)\mathcal{E}(\mathbf{r} ,\omega ) =i\mu \omega \mathcal{J}(\mathbf{r} ,\omega )
$$
{{< math >}}

其中{{< math >}}$\displaystyle k=\frac{\omega }{c/n}${{< math >}}。并矢格林函数定义为

{{< math >}}
$$
\left( \nabla \times \nabla \times -k^{2}\right)\stackrel {\leftrightarrow}{G}(\mathbf{r} ,\mathbf{r} ') =\stackrel {\leftrightarrow}{I} \delta (\mathbf{r-r} ')\
\mathcal{E}(\mathbf{r} ,\omega ) =i\mu \omega \int \stackrel {\leftrightarrow}{G}(\mathbf{r} ,\mathbf{r} ')\mathcal{J}(\mathbf{r} ',\omega ) d^{3}\mathbf{r} '
$$
{{< math >}}

 {{< math >}}$\displaystyle \nabla \times \nabla \times${{< math >}} 这个算符是不好处理的，因此我们一般从洛伦兹规范下的标量波动方程出发。将标势和矢势根据定义带入Maxwell方程组后，可以得到

{{< math >}}
$$
\nabla ^{2} \Phi +\frac{\partial }{\partial t}( \nabla \cdotp \mathbf{A}) =-\frac{\rho }{\epsilon *{0}}\
\nabla ^{2}\mathbf{A} -\frac{1}{c^{2}}\frac{\partial ^{2}}{\partial t^{2}}\mathbf{A} -\nabla \left( \nabla \cdotp \mathbf{A} +\frac{1}{c^{2}}\frac{\partial \Phi }{\partial t}\right) =-\mu* {0}\mathbf{j}
$$
{{< math >}}

洛伦兹规范为

{{< math >}}
$$
\nabla \cdotp \mathbf{A} +\frac{1}{c^{2}}\frac{\partial \Phi }{\partial t} =0
$$
{{< math >}}

在洛伦兹规范下，标势和矢势都满足波动方程（为了包括介质中的情况，此处已经将 {{< math >}}$\displaystyle \epsilon *{0} ,\mu* {0}${{< math >}} 换成了 {{< math >}}$\displaystyle \epsilon ,\mu${{< math >}} ）

{{< math >}}
$$
\left( \nabla ^{2} -\frac{1}{c^{2}}\frac{\partial ^{2}}{\partial t^{2}}\right)\mathbf{A}(\mathbf{r} ,t) =-\mu \mathbf{j}(\mathbf{r} ,t)\
\left( \nabla ^{2} -\frac{1}{c^{2}}\frac{\partial ^{2}}{\partial t^{2}}\right) \Phi (\mathbf{r} ,t) =-\frac{\rho (\mathbf{r} ,t)}{\epsilon }
$$
{{< math >}}

傅立叶变换后

{{< math >}}
$$
\left( \nabla ^{2} +k^{2}\right)\mathcal{A}(\mathbf{r} ,\omega ) =-\mu \mathcal{J}(\mathbf{r} ,\omega )\
\left( \nabla ^{2} +k^{2}\right) \Phi (\mathbf{r} ,t) =-\frac{\rho (\mathbf{r} ,\omega )}{\epsilon }
$$
{{< math >}}

定义格林函数如下

{{< math >}}
$$
\left( \nabla ^{2} +k^{2}\right) G_{0}(\mathbf{r} ,\mathbf{r} ') =-\delta (\mathbf{r-r} ')
$$
{{< math >}}

注意，之前我们见到的格林函数，自变量都直接写成 {{< math >}}$\displaystyle \mathbf{r-r} '${{< math >}} ，即 {{< math >}}$\displaystyle G(\mathbf{r} ,\mathbf{r} ') =G(\mathbf{r-r} ')${{< math >}} 。但实际上这只在线性微分算符与空间无关的情况下成立。考虑简单的情况， {{< math >}}$\displaystyle \mathcal{A}$和$\displaystyle \Phi${{< math >}} 为

{{< math >}}
$$
\mathcal{A}(\mathbf{r} ,\omega ) =\mu \int G*{0}(\mathbf{r-r} ')\mathcal{J}(\mathbf{r} ',\omega ) d^{3}\mathbf{r} ',\ \Phi (\mathbf{r} ,\omega ) =\frac{1}{\epsilon }\int G*{0}(\mathbf{r-r} ') \rho (\mathbf{r} ',\omega ) d^{3}\mathbf{r} '
$$
{{< math >}}

然后进一步得到电场和磁场

{{< math >}}
$$
\mathcal{E}(\mathbf{r} ,\omega ) =i\omega \mathcal{A} -\nabla \Phi ,\ \mathcal{H}(\mathbf{r} ,\omega ) =\frac{1}{\mu } \nabla \times \mathcal{A}
$$
{{< math >}}

电场可以写为

{{< math >}}
$$
\mathcal{E}(\mathbf{r} ,\omega ) =i\omega \mu \int G*{0}(\mathbf{r-r} ')\mathcal{J}(\mathbf{r} ',\omega ) d^{3}\mathbf{r} '-\frac{1}{\epsilon } \nabla \int G*{0}(\mathbf{r-r} ') \rho (\mathbf{r} ',\omega ) d^{3}\mathbf{r} '
$$
{{< math >}}

由频域下的电荷守恒

{{< math >}}
$$
\nabla \cdotp \mathcal{J}(\mathbf{r} ,\omega ) -i\omega \rho (\mathbf{r} ,\omega ) =0
$$
{{< math >}}
{{< math >}}
$$
\mathcal{E}(\mathbf{r} ,\omega ) =i\omega \mu \int G*{0}(\mathbf{r-r} ')\mathcal{J}(\mathbf{r} ',\omega ) d^{3}\mathbf{r} '-\frac{1}{\epsilon } \nabla \int G*{0}(\mathbf{r-r} ')\frac{1}{i\omega } \nabla '\cdotp \mathcal{J}(\mathbf{r} ',\omega ) d^{3}\mathbf{r} '
$$
{{< math >}}
利用公式 {{< math >}}$\displaystyle \nabla \cdotp ( f\mathbf{a}) =\nabla f\cdotp \mathbf{a} +f\nabla \cdotp \mathbf{a}${{< math >}} ，

{{< math >}}
$$
\int G*{0}(\mathbf{r-r} ')\frac{1}{i\omega } \nabla '\cdotp \mathcal{J}(\mathbf{r} ',\omega ) d^{3}\mathbf{r} '\=\int \frac{1}{i\omega }{\nabla '\cdotp ( G*{0}(\mathbf{r-r} ')\mathcal{J}(\mathbf{r} ',\omega )) -\mathcal{J}(\mathbf{r} ',\omega ) \cdotp \nabla 'G_{0}(\mathbf{r-r} ')} d^{3}\mathbf{r} '
$$
{{< math >}}

前面一项可以用高斯定理 {{< math >}}$\displaystyle \int *{V} d\tau \nabla \cdotp \mathbf{A} =\oint* {S} d\mathbf{S} \cdotp \mathbf{A}${{< math >}} 化为面积分，并且运用边界条件（格林函数在无穷远处趋于0）消去，因此电场化为

{{< math >}}
$$
\mathcal{E}(\mathbf{r} ,\omega ) =i\omega \mu \int G*{0}(\mathbf{r-r} ')\mathcal{J}(\mathbf{r} ',\omega ) d^{3}\mathbf{r} '+\frac{1}{i\omega \epsilon } \nabla \int \mathcal{J}(\mathbf{r} ',\omega ) \cdotp \nabla 'G*{0}(\mathbf{r-r} ') d^{3}\mathbf{r} '
$$
{{< math >}}

注意到 {{< math >}}$\displaystyle \nabla 'G*{0}(\mathbf{r-r} ') =-\nabla G*{0}(\mathbf{r-r} ')${{< math >}}，{{< math >}}$\displaystyle k=w\sqrt{\epsilon \mu }${{< math >}} ，于是得到

{{< math >}}
$$
\mathcal{E}(\mathbf{r} ,\omega ) =i\omega \mu \int \left{G*{0}(\mathbf{r-r} ')\stackrel {\leftrightarrow}{I} +\frac{1}{k^{2}} \nabla \nabla G*{0}(\mathbf{r-r} ')\right}\mathcal{J}(\mathbf{r} ',\omega ) d^{3}\mathbf{r} '
$$
{{< math >}}

从而得到并矢格林函数

{{< math >}}
$$
\stackrel {\leftrightarrow}{G}(\mathbf{r} ,\mathbf{r} ') =\left(\stackrel {\leftrightarrow}{I} +\frac{1}{k^{2}} \nabla \nabla \right) G_{0}(\mathbf{r-r} ')\
\mathcal{E}(\mathbf{r} ,\omega ) =i\omega \mu \int \stackrel {\leftrightarrow}{G}\mathcal{( r , r ') J}(\mathbf{r} ',\omega ) d^{3}\mathbf{r} '\
\mathcal{H}(\mathbf{r} ,\omega ) =\int \nabla \times \stackrel {\leftrightarrow}{G}\mathcal{( r , r ') J}(\mathbf{r} ',\omega ) d^{3}\mathbf{r} '
$$
{{< math >}}

我们已经知道，标量格林函数为

{{< math >}}
$$
G_{0}(\mathbf{r-r} ') =\frac{e^{ik|\mathbf{r} -\mathbf{r} '|}}{4\pi |\mathbf{r} -\mathbf{r} '|}
$$
{{< math >}}

就可以求解并矢格林函数了。

## 并矢格林函数的具体求解

并矢格林函数的具体形式
{{< math >}}
$$
\stackrel {\leftrightarrow}{G}(\mathbf{r} ,\mathbf{r} ',\omega ) \\

\=\left(\stackrel {\leftrightarrow}{I} +\frac{1}{k^{2}} \nabla \nabla \right)\frac{e^{ikR}}{4\pi R}\\

\=\frac{k}{4\pi }\left(\frac{e^{ikR}}{kR}\stackrel {\leftrightarrow}{I} +\frac{1}{k^{2}} \nabla \left( e^{ikR} \nabla \frac{1}{kR} +\frac{\mathbf{R}}{R} ike^{ikR}\frac{1}{kR}\right)\right)\\

\=\frac{k}{4\pi }\left{\frac{e^{ikR}}{kR}\stackrel {\leftrightarrow}{I} +\frac{1}{k^{2}}\left\[ e^{ikR} \nabla \nabla \left(\frac{1}{kR}\right) +\frac{ik\mathbf{R}}{R} e^{ikR} \nabla \left(\frac{1}{kR}\right) +\nabla \left(\frac{ie^{ikR}}{R^{2}}\mathbf{R}\right)\right]\right}
$$
{{< math >}}
{{< math >}}
$$
\nabla \left(\frac{ie^{ikR}}{R^{2}}\mathbf{R}\right) =\\

\nabla \left(\frac{ie^{ikR}}{R^{2}}\right)\mathbf{R} +\frac{ie^{ikR}}{R^{2}} \nabla \mathbf{R}\\

\=-ke^{ikR}\frac{\mathbf{RR}}{R^{3}} +ie^{ikR}\left( -\frac{2\mathbf{R}}{R^{4}}\right)\mathbf{R} +\frac{ie^{ikR}}{R^{2}}\stackrel {\leftrightarrow}{I}
$$
{{< math >}}
{{< math >}}
$$
\frac{ik\mathbf{R}}{R^{2}} e^{ikR} \nabla \left(\frac{1}{kR}\right) \\

\=\frac{i\mathbf{R}}{R^{2}} e^{ikR}\left( -\frac{\mathbf{R}}{R^{2}}\right)
$$
{{< math >}}
故
{{< math >}}
$$
\stackrel {\leftrightarrow}{G}(\mathbf{r} ,\mathbf{r} ',\omega ) \\

\=\frac{k}{4\pi }\left{\frac{e^{ikR}}{kR}\stackrel {\leftrightarrow}{I} +\frac{1}{k^{2}} e^{ikR}\left\[ \nabla \nabla \left(\frac{1}{kR}\right) -k\frac{\mathbf{RR}}{R^{3}} -\frac{3i\mathbf{RR}}{R^{4}} +\frac{i}{R^{2}}\stackrel {\leftrightarrow}{I}\right]\right}
$$
{{< math >}}
我们有
{{< math >}}
$$
\nabla \nabla \frac{1}{r} \\

\=-\frac{4\pi }{3} \delta (\mathbf{r})\stackrel {\leftrightarrow}{I} +\frac{1}{r^{3}}\left(\frac{3\mathbf{rr}}{r^{2}} -\stackrel {\leftrightarrow}{I}\right)
$$
{{< math >}}
因此
{{< math >}}
$$
\stackrel {\leftrightarrow}{G}(\mathbf{r} ,\mathbf{r} ',\omega ) \\

\=\frac{k}{4\pi }\frac{e^{ikR}}{kR}\left\[\stackrel {\leftrightarrow}{I}\left( 1-\frac{4\pi }{3k^{2}} \delta (\mathbf{R}) -\frac{1}{k^{2} R^{2}} +\frac{i}{kR}\right) +\frac{\mathbf{RR}}{R^{2}}\left(\frac{3}{k^{2} R^{2}} -1-\frac{3i}{kR}\right)\right]
$$
{{< math >}}
定义下列函数
{{< math >}}
$$
A( x) =e^{ix}\left( x^{-1} +ix^{-2} -x^{-3}\right) ,\\ 

B( x) =e^{ix}\left( -x^{-1} -3ix^{-2} +3x^{-3}\right)
$$
{{< math >}}
于是

{{< math >}}
$$
\stackrel {\leftrightarrow}{G}(\mathbf{r} ,\mathbf{r} ',\omega ) \\

=-\frac{1}{3k^{2}} \delta (\mathbf{R})\stackrel {\leftrightarrow}{I} +\frac{k}{4\pi }\left\[\stackrel {\leftrightarrow}{I} A( kR) +\frac{\mathbf{RR}}{R^{2}} B( kR)\right]
$$
{{< math >}}
根据 $\displaystyle 1/R$ 衰减的速度，我们可以将格林函数分为近场，中场，远场区域
{{< math >}}
$$
\stackrel {\leftrightarrow}{G}(\mathbf{r} ,\mathbf{r} ',\omega ) =\stackrel {\leftrightarrow}{G}_{\text{NF}} +\stackrel {\leftrightarrow}{G}_{\text{IF}} +\stackrel {\leftrightarrow}{G}_{\text{FF}} \\\\
\stackrel {\leftrightarrow}{G}_{\text{NF}} =\frac{e^{ikR}}{4\pi R}\frac{1}{k^{2} R^{2}}\left( -\stackrel {\leftrightarrow}{I} +\frac{3\mathbf{RR}}{R^{2}}\right) \\\\
\stackrel {\leftrightarrow}{G}_{\text{IF}} =\frac{e^{ikR}}{4\pi R}\frac{i}{kR}\left(\stackrel {\leftrightarrow}{I} -\frac{3\mathbf{RR}}{R^{2}}\right) \\\\
\stackrel {\leftrightarrow}{G}_{\text{FF}} =\frac{e^{ikR}}{4\pi R}\left(\stackrel {\leftrightarrow}{I} -\frac{\mathbf{RR}}{R^{2}}\right)
$$
{{< math >}}
