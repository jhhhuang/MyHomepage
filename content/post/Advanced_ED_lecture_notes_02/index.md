---
title: [Advanced Electrodynamics] lecture notes 02
subtitle: Green's function and dydadic Green's function.

# Summary for listings and search engines
summary: Green's function and dydadic Green's function.

# Link this post with a project
projects: []

# Date published
date: "2022-03-23T00:00:00Z"

# Date updated
lastmod: "2022-03-23T00:00:00Z"

# Is this an unpublished draft?
draft: false

# Show this page in the Featured widget?
featured: false

# Featured image
# Place an image named `featured.jpg/png` in this page's folder and customize its options here.
authors:
- admin

tags:
- Academic
- courses

---

# [高等电动力学笔记02] 格林函数，并矢格林函数
## 频域下的Maxwell方程
傅立叶变换（注意这边与我们常用的定义是相反的）
$$
F( t) =\int _{-\infty }^{+\infty }\mathcal{F}( \omega ) e^{-i\omega t} d\omega ,\ \mathcal{F}( \omega ) =\frac{1}{2\pi }\int _{-\infty }^{+\infty } F( t) e^{i\omega t} dt
$$
宏观Maxwell方程：
$$
\nabla \cdotp \mathbf{B}(\mathbf{r} ,t)  =0\\

\nabla \cdotp \mathbf{D}(\mathbf{r} ,t)  =\rho (\mathbf{r} ,t)\\
\nabla \times \mathbf{E}(\mathbf{r} ,t)  =-\frac{\partial }{\partial t}\mathbf{B}(\mathbf{r} ,t)\\
\nabla \times \mathbf{H}(\mathbf{r} ,t)  =\mathbf{j}(\mathbf{r} ,t) +\frac{\partial }{\partial t}\mathbf{D}(\mathbf{r} ,t)
$$
对上述四条方程做傅立叶变换（根据我们定义的傅立叶变换，在使用求导定理时要注意符号）
$$
\nabla \cdotp \mathcal{B}(\mathbf{r} ,\omega )  =0\\
\nabla \cdotp \mathcal{D}(\mathbf{r} ,\omega )  =\rho (\mathbf{r} ,\omega )\\
\nabla \times \mathcal{E}(\mathbf{r} ,\omega )  =i\omega \mathcal{B}(\mathbf{r} ,\omega )\\
\nabla \times \mathcal{H}(\mathbf{r} ,\omega )  =\mathcal{J}(\mathbf{r} ,\omega ) -i\omega \mathcal{D}(\mathbf{r} ,\omega )
$$
## 本构关系
线性材料频域下的本构关系可以写为
$$
\mathcal{D}( \omega ) =\stackrel {\leftrightarrow}{\epsilon }( \omega )\mathcal{E}( \omega ) +\stackrel {\leftrightarrow}{\xi }( \omega )\mathcal{H}( \omega )\\
\mathcal{B}( \omega ) =\stackrel {\leftrightarrow}{\eta }( \omega )\mathcal{E}( \omega ) +\stackrel {\leftrightarrow}{\mu }( \omega )\mathcal{H}( \omega )
$$
可以定义下面的张量
$$
\stackrel {\leftrightarrow}{K}( \omega ) \equiv \begin{bmatrix}
\stackrel {\leftrightarrow}{\epsilon }( \omega ) & \stackrel {\leftrightarrow}{\xi }( \omega )\\
\stackrel {\leftrightarrow}{\eta }( \omega ) & \stackrel {\leftrightarrow}{\mu }( \omega )
\end{bmatrix}
$$
引入本构关系后，可以将宏观Maxwell方程写成如下形式（当然，还有两条散度方程）
$$
(\stackrel {\leftrightarrow}{D} -i\omega \stackrel {\leftrightarrow}{K})\mathbf{e} =-\mathbf{J}
$$
其中
$$
\stackrel {\leftrightarrow}{D} =\begin{bmatrix}
0 & -\nabla \times \\
\nabla \times  & 0
\end{bmatrix} ,\ \mathbf{e} =\begin{bmatrix}
\mathcal{D}( \omega )\\
\mathcal{B}( \omega )
\end{bmatrix} ,\ \mathbf{J} =\begin{bmatrix}
\mathcal{J}(\mathbf{r} ,\omega )\\
0
\end{bmatrix}
$$
## 格林函数
如果只考虑体系的 $\displaystyle \epsilon$ ，（ $\displaystyle \mu =\mu _{0}$ ），宏观Maxwell方程可以写为
$$
\left( \nabla \times ( \nabla \times ) -\frac{\omega ^{2}}{c^{2}} \epsilon _{r}(\mathbf{r} ,\omega )\right)\mathcal{E}(\mathbf{r} ,\omega ) =i\omega \mu _{0}\mathcal{J}_{f}(\mathbf{r} ,\omega )
$$
更普遍地，我们考虑如下形式的方程
$$
(\mathcal{L} -\lambda \rho (\mathbf{r})) u(\mathbf{r}) =f(\mathbf{r})
$$
其中 $\displaystyle \mathcal{L}$ 是某个线性微分算子， $\displaystyle u(\mathbf{r})$ 是待求解的场。对应于这条方程的格林函数定义为
$$
(\mathcal{L} -\lambda \rho (\mathbf{r})) g(\mathbf{r} ,\mathbf{r} ') =\delta (\mathbf{r} -\mathbf{r} ')
$$
这是标量形式的方程和格林函数。我们研究的电磁波是矢量，因此矢量形式的微分方程为
$$
(\mathcal{L} -\lambda \stackrel {\leftrightarrow}{\rho }(\mathbf{r}))\mathbf{u}(\mathbf{r}) =\mathbf{f}(\mathbf{r})
$$
相应的格林函数则应该写成并矢形式
$$
(\mathcal{L} -\lambda \stackrel {\leftrightarrow}{\rho }(\mathbf{r}))\stackrel {\leftrightarrow}{G}(\mathbf{r} ,\mathbf{r} ') =\stackrel {\leftrightarrow}{I} \delta (\mathbf{r} -\mathbf{r} ')
$$
因为格林函数表示的是对“源”的某种响应形式，因此在矢量情况下把格林函数写成并矢是自然的。对式(19)两边同乘 $\displaystyle f(\mathbf{r} ')$ 并对全空间积分
$$
\int (\mathcal{L} -\lambda \stackrel {\leftrightarrow}{\rho }(\mathbf{r}))\stackrel {\leftrightarrow}{G}(\mathbf{r} ,\mathbf{r} ') f(\mathbf{r} ') d^{3}\mathbf{r} '\\=(\mathcal{L} -\lambda \stackrel {\leftrightarrow}{\rho }(\mathbf{r}))\int \stackrel {\leftrightarrow}{G}(\mathbf{r} ,\mathbf{r} ') f(\mathbf{r} ') d^{3}\mathbf{r} '=\int \stackrel {\leftrightarrow}{I} \delta (\mathbf{r} -\mathbf{r} ') f(\mathbf{r} ') d^{3}\mathbf{r} '=f(\mathbf{r})
$$
不难看出
$$
\mathbf{u}(\mathbf{r}) =\int \stackrel {\leftrightarrow}{G}(\mathbf{r} ,\mathbf{r} ') f(\mathbf{r} ') d^{3}\mathbf{r} '
$$
于是所有的问题都转化为了对（并矢）格林函数的求解。同时我们可以看到，格林函数是不依赖于源的具体形式的，只跟方程的形式，即体系有关（ $\displaystyle \mathcal{L}$ ， $\displaystyle \stackrel {\leftrightarrow}{\rho }$ ）。格林函数可以理解为按照某种规则对空间源的分布进行求和，所有的响应叠加起来就是我们要求解的场。

## 并矢格林函数的形式
出于简单，我们考虑三维空间中的各向同性介质。Maxwell方程为
$$
\left( \nabla \times \nabla \times -k^{2}\right)\mathcal{E}(\mathbf{r} ,\omega ) =i\mu \omega \mathcal{J}(\mathbf{r} ,\omega )
$$
其中$\displaystyle k=\frac{\omega }{c/n}$。并矢格林函数定义为
$$
\left( \nabla \times \nabla \times -k^{2}\right)\stackrel {\leftrightarrow}{G}(\mathbf{r} ,\mathbf{r} ') =\stackrel {\leftrightarrow}{I} \delta (\mathbf{r-r} ')\\
\mathcal{E}(\mathbf{r} ,\omega ) =i\mu \omega \int \stackrel {\leftrightarrow}{G}(\mathbf{r} ,\mathbf{r} ')\mathcal{J}(\mathbf{r} ',\omega ) d^{3}\mathbf{r} '
$$


 $\displaystyle \nabla \times \nabla \times$ 这个算符是不好处理的，因此我们一般从洛伦兹规范下的标量波动方程出发。将标势和矢势根据定义带入Maxwell方程组后，可以得到

$$
\nabla ^{2} \Phi +\frac{\partial }{\partial t}( \nabla \cdotp \mathbf{A}) =-\frac{\rho }{\epsilon _{0}}\\
\nabla ^{2}\mathbf{A} -\frac{1}{c^{2}}\frac{\partial ^{2}}{\partial t^{2}}\mathbf{A} -\nabla \left( \nabla \cdotp \mathbf{A} +\frac{1}{c^{2}}\frac{\partial \Phi }{\partial t}\right) =-\mu _{0}\mathbf{j}
$$
洛伦兹规范为
$$
\nabla \cdotp \mathbf{A} +\frac{1}{c^{2}}\frac{\partial \Phi }{\partial t} =0
$$
在洛伦兹规范下，标势和矢势都满足波动方程（为了包括介质中的情况，此处已经将 $\displaystyle \epsilon _{0} ,\mu _{0}$ 换成了 $\displaystyle \epsilon ,\mu$ ）
$$
\left( \nabla ^{2} -\frac{1}{c^{2}}\frac{\partial ^{2}}{\partial t^{2}}\right)\mathbf{A}(\mathbf{r} ,t) =-\mu \mathbf{j}(\mathbf{r} ,t)\\
\left( \nabla ^{2} -\frac{1}{c^{2}}\frac{\partial ^{2}}{\partial t^{2}}\right) \Phi (\mathbf{r} ,t) =-\frac{\rho (\mathbf{r} ,t)}{\epsilon }
$$
傅立叶变换后
$$
\left( \nabla ^{2} +k^{2}\right)\mathcal{A}(\mathbf{r} ,\omega ) =-\mu \mathcal{J}(\mathbf{r} ,\omega )\\
\left( \nabla ^{2} +k^{2}\right) \Phi (\mathbf{r} ,t) =-\frac{\rho (\mathbf{r} ,\omega )}{\epsilon }
$$
定义格林函数如下
$$
\left( \nabla ^{2} +k^{2}\right) G_{0}(\mathbf{r} ,\mathbf{r} ') =-\delta (\mathbf{r-r} ')
$$
注意，之前我们见到的格林函数，自变量都直接写成 $\displaystyle \mathbf{r-r} '$ ，即 $\displaystyle G(\mathbf{r} ,\mathbf{r} ') =G(\mathbf{r-r} ')$ 。但实际上这只在线性微分算符与空间无关的情况下成立。考虑简单的情况， $\displaystyle \mathcal{A}$和$\displaystyle \Phi$ 为
$$
\mathcal{A}(\mathbf{r} ,\omega ) =\mu \int G_{0}(\mathbf{r-r} ')\mathcal{J}(\mathbf{r} ',\omega ) d^{3}\mathbf{r} ',\ \Phi (\mathbf{r} ,\omega ) =\frac{1}{\epsilon }\int G_{0}(\mathbf{r-r} ') \rho (\mathbf{r} ',\omega ) d^{3}\mathbf{r} '
$$
然后进一步得到电场和磁场
$$
\mathcal{E}(\mathbf{r} ,\omega ) =i\omega \mathcal{A} -\nabla \Phi ,\ \mathcal{H}(\mathbf{r} ,\omega ) =\frac{1}{\mu } \nabla \times \mathcal{A}
$$
电场可以写为
$$
\mathcal{E}(\mathbf{r} ,\omega ) =i\omega \mu \int G_{0}(\mathbf{r-r} ')\mathcal{J}(\mathbf{r} ',\omega ) d^{3}\mathbf{r} '-\frac{1}{\epsilon } \nabla \int G_{0}(\mathbf{r-r} ') \rho (\mathbf{r} ',\omega ) d^{3}\mathbf{r} '
$$
由频域下的电荷守恒
$$
\nabla \cdotp \mathcal{J}(\mathbf{r} ,\omega ) -i\omega \rho (\mathbf{r} ,\omega ) =0
$$
$$
\mathcal{E}(\mathbf{r} ,\omega ) =i\omega \mu \int G_{0}(\mathbf{r-r} ')\mathcal{J}(\mathbf{r} ',\omega ) d^{3}\mathbf{r} '-\frac{1}{\epsilon } \nabla \int G_{0}(\mathbf{r-r} ')\frac{1}{i\omega } \nabla '\cdotp \mathcal{J}(\mathbf{r} ',\omega ) d^{3}\mathbf{r} '
$$
利用公式 $\displaystyle \nabla \cdotp ( f\mathbf{a}) =\nabla f\cdotp \mathbf{a} +f\nabla \cdotp \mathbf{a}$ ，
$$
\int G_{0}(\mathbf{r-r} ')\frac{1}{i\omega } \nabla '\cdotp \mathcal{J}(\mathbf{r} ',\omega ) d^{3}\mathbf{r} '\\=\int \frac{1}{i\omega }\{\nabla '\cdotp ( G_{0}(\mathbf{r-r} ')\mathcal{J}(\mathbf{r} ',\omega )) -\mathcal{J}(\mathbf{r} ',\omega ) \cdotp \nabla 'G_{0}(\mathbf{r-r} ')\} d^{3}\mathbf{r} '
$$
前面一项可以用高斯定理 $\displaystyle \int _{V} d\tau \nabla \cdotp \mathbf{A} =\oint _{S} d\mathbf{S} \cdotp \mathbf{A}$ 化为面积分，并且运用边界条件（格林函数在无穷远处趋于0）消去，因此电场化为
$$
\mathcal{E}(\mathbf{r} ,\omega ) =i\omega \mu \int G_{0}(\mathbf{r-r} ')\mathcal{J}(\mathbf{r} ',\omega ) d^{3}\mathbf{r} '+\frac{1}{i\omega \epsilon } \nabla \int \mathcal{J}(\mathbf{r} ',\omega ) \cdotp \nabla 'G_{0}(\mathbf{r-r} ') d^{3}\mathbf{r} '
$$
注意到 $\displaystyle \nabla 'G_{0}(\mathbf{r-r} ') =-\nabla G_{0}(\mathbf{r-r} ')$，$\displaystyle k=w\sqrt{\epsilon \mu }$ ，于是得到
$$
\mathcal{E}(\mathbf{r} ,\omega ) =i\omega \mu \int \left\{G_{0}(\mathbf{r-r} ')\stackrel {\leftrightarrow}{I} +\frac{1}{k^{2}} \nabla \nabla G_{0}(\mathbf{r-r} ')\right\}\mathcal{J}(\mathbf{r} ',\omega ) d^{3}\mathbf{r} '
$$
从而得到并矢格林函数
$$
\stackrel {\leftrightarrow}{G}(\mathbf{r} ,\mathbf{r} ') =\left(\stackrel {\leftrightarrow}{I} +\frac{1}{k^{2}} \nabla \nabla \right) G_{0}(\mathbf{r-r} ')\\
\mathcal{E}(\mathbf{r} ,\omega ) =i\omega \mu \int \stackrel {\leftrightarrow}{G}\mathcal{( r , r ') J}(\mathbf{r} ',\omega ) d^{3}\mathbf{r} '\\
\mathcal{H}(\mathbf{r} ,\omega ) =\int \nabla \times \stackrel {\leftrightarrow}{G}\mathcal{( r , r ') J}(\mathbf{r} ',\omega ) d^{3}\mathbf{r} '
$$


我们已经知道，标量格林函数为
$$
G_{0}(\mathbf{r-r} ') =\frac{e^{ik|\mathbf{r} -\mathbf{r} '|}}{4\pi |\mathbf{r} -\mathbf{r} '|}
$$
就可以求解并矢格林函数了。

## 并矢格林函数的具体求解
并矢格林函数的具体形式
$$
\stackrel {\leftrightarrow}{G}(\mathbf{r} ,\mathbf{r} ',\omega ) =\left(\stackrel {\leftrightarrow}{I} +\frac{1}{k^{2}} \nabla \nabla \right)\frac{e^{ikR}}{4\pi R}\\
=\frac{k}{4\pi }\left(\frac{e^{ikR}}{kR}\stackrel {\leftrightarrow}{I} +\frac{1}{k^{2}} \nabla \left( e^{ikR} \nabla \frac{1}{kR} +\frac{\mathbf{R}}{R} ike^{ikR}\frac{1}{kR}\right)\right)\\
=\frac{k}{4\pi }\left\{\frac{e^{ikR}}{kR}\stackrel {\leftrightarrow}{I} +\frac{1}{k^{2}}\left[ e^{ikR} \nabla \nabla \left(\frac{1}{kR}\right) +\frac{ik\mathbf{R}}{R} e^{ikR} \nabla \left(\frac{1}{kR}\right) +\nabla \left(\frac{ie^{ikR}}{R^{2}}\mathbf{R}\right)\right]\right\}
$$
$$
\nabla \left(\frac{ie^{ikR}}{R^{2}}\mathbf{R}\right) =\nabla \left(\frac{ie^{ikR}}{R^{2}}\right)\mathbf{R} +\frac{ie^{ikR}}{R^{2}} \nabla \mathbf{R}\\
=-ke^{ikR}\frac{\mathbf{RR}}{R^{3}} +ie^{ikR}\left( -\frac{2\mathbf{R}}{R^{4}}\right)\mathbf{R} +\frac{ie^{ikR}}{R^{2}}\stackrel {\leftrightarrow}{I}
$$
$$
\frac{ik\mathbf{R}}{R^{2}} e^{ikR} \nabla \left(\frac{1}{kR}\right) =\frac{i\mathbf{R}}{R^{2}} e^{ikR}\left( -\frac{\mathbf{R}}{R^{2}}\right)
$$
故
$$
\stackrel {\leftrightarrow}{G}(\mathbf{r} ,\mathbf{r} ',\omega ) =\frac{k}{4\pi }\left\{\frac{e^{ikR}}{kR}\stackrel {\leftrightarrow}{I} +\frac{1}{k^{2}} e^{ikR}\left[ \nabla \nabla \left(\frac{1}{kR}\right) -k\frac{\mathbf{RR}}{R^{3}} -\frac{3i\mathbf{RR}}{R^{4}} +\frac{i}{R^{2}}\stackrel {\leftrightarrow}{I}\right]\right\}
$$
我们有
$$
\nabla \nabla \frac{1}{r} =-\frac{4\pi }{3} \delta (\mathbf{r})\stackrel {\leftrightarrow}{I} +\frac{1}{r^{3}}\left(\frac{3\mathbf{rr}}{r^{2}} -\stackrel {\leftrightarrow}{I}\right)
$$
因此
$$
\stackrel {\leftrightarrow}{G}(\mathbf{r} ,\mathbf{r} ',\omega ) =\frac{k}{4\pi }\frac{e^{ikR}}{kR}\left[\stackrel {\leftrightarrow}{I}\left( 1-\frac{4\pi }{3k^{2}} \delta (\mathbf{R}) -\frac{1}{k^{2} R^{2}} +\frac{i}{kR}\right) +\frac{\mathbf{RR}}{R^{2}}\left(\frac{3}{k^{2} R^{2}} -1-\frac{3i}{kR}\right)\right]
$$
定义下列函数
$$
A( x) =e^{ix}\left( x^{-1} +ix^{-2} -x^{-3}\right) ,\ B( x) =e^{ix}\left( -x^{-1} -3ix^{-2} +3x^{-3}\right)
$$
于是
$$
\stackrel {\leftrightarrow}{G}(\mathbf{r} ,\mathbf{r} ',\omega ) =-\frac{1}{3k^{2}} \delta (\mathbf{R})\stackrel {\leftrightarrow}{I} +\frac{k}{4\pi }\left[\stackrel {\leftrightarrow}{I} A( kR) +\frac{\mathbf{RR}}{R^{2}} B( kR)\right]
$$
根据 $\displaystyle 1/R$ 衰减的速度，我们可以将格林函数分为近场，中场，远场区域
$$
\stackrel {\leftrightarrow}{G}(\mathbf{r} ,\mathbf{r} ',\omega ) =\stackrel {\leftrightarrow}{G}_{\text{NF}} +\stackrel {\leftrightarrow}{G}_{\text{IF}} +\stackrel {\leftrightarrow}{G}_{\text{FF}}\\
\stackrel {\leftrightarrow}{G}_{\text{NF}} =\frac{e^{ikR}}{4\pi R}\frac{1}{k^{2} R^{2}}\left( -\stackrel {\leftrightarrow}{I} +\frac{3\mathbf{RR}}{R^{2}}\right)\\
\stackrel {\leftrightarrow}{G}_{\text{IF}} =\frac{e^{ikR}}{4\pi R}\frac{i}{kR}\left(\stackrel {\leftrightarrow}{I} -\frac{3\mathbf{RR}}{R^{2}}\right)\\
\stackrel {\leftrightarrow}{G}_{\text{FF}} =\frac{e^{ikR}}{4\pi R}\left(\stackrel {\leftrightarrow}{I} -\frac{\mathbf{RR}}{R^{2}}\right)
$$