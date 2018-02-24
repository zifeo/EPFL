---
typora-copy-images-to: ./img
---

$$
\def\Y{\mathcal Y}
\def\X{\mathcal X}
\def\R{\mathbb R}
\def\N{\mathbb N}
\def\bs#1{\boldsymbol{#1}}
\def\abs#1{\left |#1\right |}
\def\indep{\perp\!\!\!\perp}
\def\norm#1{\left|\left|#1\right|\right|}
\def\iid{\overset{iid}{\sim}}
\def\p{\hat\theta}
\def\t{\theta}
\def\I{\mathcal I}
\def\L{\mathcal L}
\def\ind{\overset{ind}{\sim}}
$$

# MATH413

> [GNU General Public License v3.0](https://github.com/zifeo/EPFL/blob/master/LICENSE) licensed. Source available on [github.com/zifeo/EPFL](https://github.com/zifeo/EPFL).

Fall 2017: Statistics for data science

[TOC]

- statistics : leaning from data under uncertainty

- data : anything that we can mathematically represent

- statistics cultures
  - inference/modeling/uncertainty : focus on interpretability, reduction, statistical efficiency
  - prediction/algorithms/optimisation : focus on emulation, automation, computational efficiency

- uncertainty : measurement error, chaos, intrinsic stochasticity, sampled data, fundamental limitations to precision

- probability : use model to learn about probability of potential outcomes, given model find probability that outcome is X

- statistics : data viewed as observed outcomes from model, use outcomes to learn about the model, given outcome tell me interesting about unknown model

- general framework
  - model phenomenon by distribution $F(y_1,\ldots,y_n;\theta)$ on $\Y^n\subseteq\R^n$ for $n\ge 1$
  - distributional form known, $\theta\in\Theta\in \R^p$ unknown (nonparametric regime if $\Theta$ function of space)
  - observe realisation $(Y_1,\ldots,Y_n)^\top\in\Y^n$
  - use realisation to make assertions concerning true value of $\theta$ and quantify uncertainty

- inference tasks
  - estimation : given outcomes, give educated guess for unknown true $\theta$
  - hypothesis testing : which regions $\Theta_i$ more plausible to contain true $\theta$ that generated outcome
  - confidence intervals : given outcomes, show range of plausible $\theta$
  - prediction : given outcomes, predict future ones
  - classification : given outcomes from various distrubition, declare which generated what

- covariates
  - marginal inference : i.i.d. entries, same distribution, same parameters
  - regression : independent entries, same distribution family, different parameters​



## Background

### Probability

- elementary event : outcome $\omega$
- all possible outcome : $\Omega$ non empty
- event : $F\subset \Omega$, occurs whenever outcome belong to $F$
- union : $F_1\cup F_2$
- intersection : $F_1\cap F_2$
- complement : $F^c$
- disjoint : $F_1\cap F_2=\emptyset$
- partition : $\{F_n\}_{n\ge 1}$ s.t. pairwise disjoint $\cup_{n\ge 1}F_n=\Omega$
- difference : $F_1\setminus F_2=F_1\cap F_2^C$
- probability measure : $\mathbb P=P$ defined over $\Omega$ assign probability to event, $P(F)\ge 0$, $P(\Omega)=1$, $P(F)=\sum_{n\ge 1}P(F_n)$
  - complement : $P(F^c)=1-P(F)$
  - intersection : $P(F_1\cap F_2)\le\min(P(F_1),P(F_2))$
  - union : $P(F_1\cup F_2)=P(F_1) + P(F_2)-P(F_1\cap F_2)$
  - continuity from below : $\{F_n\}_{n\ge 1}$ nested events s.t. $F_j\subseteq F_{j+1}$, $F=\cup_{n\ge 1}F_n$ implies $P(F_n)\overset{n\to\infty}{\longrightarrow} P(F)$
  - continuity from above : $\{F_n\}_{n\ge 1}$ nested events s.t. $F_j\supseteq F_{j+1}$, $F=\cap_{n\ge 1}F_n$ implies $P(F_n)\overset{n\to\infty}{\longrightarrow} P(F)$
- conditional probability : $P(F_1\mid F_2)=\frac{P(F_1\cap F_2)}{P(F_2)}$
  - law of total probability : partition $\{F_n\}_{n\ge 1}$, $P(G)=\sum_{n=1}^\infty P(G\mid F_n)P(F_n)$
  - Bayes' theorem : parition $\{F_n\}_{n\ge 1}$, $P(F_j\mid G)=\frac{P(G\mid F_j)P(F_j)}{\sum_{n=1}^\infty P(G\mid F_n)P(F_n)}$
  - independent : $\{G_n\}_{n\ge 1}$ for any $K$ sub-collection s.t. $P(G_{i_1}\cap\cdots\cap G_{i_K})=P(G_{i_1})\times\cdots\times P(G_{i_K})$
- random variable r.v. : numerical summeries of outcome of random experiment, $X:\Omega\to\R$, $\{ X\in A\}$ denote $\{ \omega \in \Omega : X(\omega)\in A\}$
- distribution function (cumulative) : $F_X:\R\to[0,1]$, $F_X(x)=P(X\le x)$
  - increasing and continuous : $x\le y \implies F_X(x)\le F_X(y)$, $P(X > a)=1-F(a)$, $P(a<X\le b)=F_X(b)-F_X(a)$
  - bounded : $\lim_{x\to\infty}F_X(x)=1$, $\lim_{x\to-\infty}F_X(x)=0$
  - right-continous : $\lim_{y\downarrow x}F_X(y)=F_X(x)$
  - left-limited : $\lim_{y\uparrow x}F_X(y)$ exists
  - discontinuities : countable set $D_x=\{x\in\R\mid F_X(x)-\lim_{y\uparrow x}F_X(y)>0\}$
    - discrete r.v. : $P(\{X\in D_F\})=1$
    - continuous r.v. : $D_X=\emptyset$
- quantile function : $F^-_X:(0,1)\to\R$, $F^-_X(\alpha)=\inf\{t\in\R\mid F_X(t)\ge\alpha\}$, if $F_X$ strictly increasing $F^-_X=F_X^{-1}$
  - $\alpha$-quantile : $q_\alpha=F^-_X(\alpha)$
  - random number generation : $Y\sim Unif(0,1)$, distribution $F$, then distribution of $X=F^-(Y)$ is $F$
- probability mass function (frequency) : discrete r.v., $f_X:\R\to[0,1]$, $f_X(x)=P(X=x)$ s.t. $F_X(x)=\sum_{t\in (-\infty, x]\cap\mathcal X}f_x(t)$ for jumps $\mathcal X=\{x\in\R\mid f_X(x)>0\}$
- probability density function : continous r.v., $f_X:\R\to[0,+\infty)$, $F_X(b)-F_X(a)=\int_a^bf_X(t)dt$ s.t. $f_X(x)=F_X'(x)$ but $f_X(x)\not=P(X=x)=0$
- transforms
  - mass function : $Y=g(X)$ as $\Y=g(\X)$ s.t. $F_Y(y)=P(g(X)\le y)=\sum_{x\in\X} f_X(x)1\{g(x)\le y\}\;\forall y\in\Y$ and $f_Y(y)=P(g(X)= y)=\sum_{x\in\X} f_X(x)1\{g(x)= y\}\;\forall y\in\Y$
  - density function : $Y=g(X)$ as $\Y=g(\X)$, monotone, continuously differentiable, non-vashnising derivative, $f_Y(y)=\abs{\frac{\partial}{\partial y}g^{-1}(y)}f_X(g^{-1}(y))$
- random vector : $\bs X=(X_1,\ldots X_d)^\top$
  - joint distribution function : $F_\bs X (x_1,\ldots, x_d)=P(X_1\le x_1,\ldots,X_d\le x_d)$
  - joint frequency function : $f_\bs X(x_1,\ldots,x_d)=P(X_1=x_1,\ldots, X_d=x_d)$
  - joint density function : $F_\bs X(x_1,\ldots,x_d)=\int_{-\infty}^{x_1} \cdots\int_{-\infty}^{x_d}f_\bs X(u_1,\ldots,u_d)du_1 \cdots du_d$ and $f_\bs X(x_1,\ldots,x_d)=\frac{\partial^d}{\partial x_1\cdots\partial x_d}F_\bs X(x_1,\ldots,x_d)$
- marginal distribution : do not uniquely determine join distribution
  - discrete : $f_{X_i}(x_i)=P(X_i=x_i)=\sum_{x_1}\cdots\sum_{x_{i-1}}\sum_{x_{i+1}}\cdots\sum_{x^d}f_\bs X(x_1,\ldots,x_{i-1},x_i,x_{i+1},\ldots, x_d)$
  - continuous : $f_{X_i}(x_i)=\int_{-\infty}^\infty\cdots\int_{-\infty}^\infty f_\bs X(y_1,\ldots,y_{i-1},y_i,y_{i+1},\ldots, y_d)dy_1\cdots dy_{i-1} dy_{i+1}\cdots dy_d$



- conditinal distribution : $f_{X_1,\ldots,X_k\mid X_{k+1},\ldots, X_d}(x_1,\ldots,x_k\mid x_{k+1},\ldots, x_d)=\frac{f_{X_1,\ldots,X_d}(x_1,\ldots,x_k,x_{k+1},\ldots,x_d)}{f_{X_{k+1},\ldots, X_d}(x_{k+1},\ldots, x_d)}$ 

- independence : $F_{X_1,\ldots,X_d}(x_1,\ldots,x_d)=F_{X_1}(x_1)\times\cdots\times F_{X_d}(x_d)$ and $f_{X_1,\ldots,X_d}(x_1,\ldots,x_d)=f_{X_1}(x_1)\times\cdots\times f_{X_d}(x_d)$

- conditional independence : $X\indep_Z Y$ or $X\indep Y\mid Z$ s.t. $F_{X_1,\ldots,X_d\mid Y,Z}(x_1,\ldots, x_d)=F_{X_1,\ldots, X_d\mid Z}(x_1,\ldots,x_d)$ and $f_{X_1,\ldots,X_d\mid Y,Z}(x_1,\ldots,x_d)=f_{X_1,\ldots,X_d\mid Z}(x_1,\ldots,x_d)$, implies $X\indep_Z Y\iff Y\indep_Z X$

- multivariate transforms : differenciable bijection $g(x)=(g_1(x),\ldots,g_n(x))$, $\bs Y=g(\bs X)$ as $\Y^n=g(\X^n)$, $f_\bs Y(y)=f_\bs X(g^{-1}(y))\abs{\det[J_{g^{-1}}(y)]}$ with $J_{g^{-1}(y)}=\begin{bmatrix}\frac{\partial}{\partial x_1}g_1^{-1}(y) & \cdots & \frac{\partial}{\partial x_n}g_1^{-1}(y) \\ \vdots & \ddots & \vdots \\ \frac{\partial}{\partial x_1}g_n^{-1}(y) & \cdots & \frac{\partial}{\partial x_n}g_n^{-1}(y)\end{bmatrix}$


  - convolution : $f_{X+Y}(u)=\int_{-\infty}^\infty f_X(u-v)f_Y(v)dv$

- moments


  - expected value : $\mathbb E[X]$

    - continuous : $E[h(X)]=\int_{-\infty}^\infty h(x)f_X(x)dx$
    - discrete : $E[h(X)]=\sum_{x\in\X}h(x) f_X(x)$
    - linearity : $E[X_1+aX_2]=E[X_1]+a E[X_2]$
    - mean vector : $E[\bs X]=(E[X_1] \cdots E[X_d])^\top$

  - variance : $Var(X)=E[(X - E[X])^2]=E[X^2]-E[X]^2=cov(X,X)$

    - covariance : degree of linear dependency (only linear) between two r.v., $cov(X_1,X_2)=E[(X_1-E[X_1])(X_2-E[X_2])]=E[X_1X_2]-E[X_1]E[X_2]$
    - correlation : invariant to scale and fixed range version of covariance, $Corr(X_1,X_2)=\frac{cov(X_1,X_2)}{\sqrt{Var(X_1)Var(X_2)}}$
      - inequality : consequence of Cauchy-Schwarz, $\abs{Corr(X_1,X_2)}\le\sqrt{Var(X_1)Var(X_2)}$
    - properties : $Var(aX+b)=a^2Var(X)$, $Var(\sum_i X_i)=\sum_i Var(X_i)+\sum_{i\not = j}cov(X_i,X_j)$, $cov(aX_1+bX_2,Y)=acov(X_1,Y)+bcov(X_2,Y)$
    - independence : implies $E[X_1X_2]=E[X_1][X_2]$, $cov(X_1,X_2)=0$, $Var(X_1\pm X_2)=Var(X_1)\pm Var(X_2)$

  - conditional expectation : $E[X\mid Y]=q(Y)$

    - discrete : $E[X\mid Y=y]=\sum_{x\in\X} xP[X=x\mid Y=y]$
    - continuous : $E[X\mid Y=y]=\int_{-\infty}^\infty x f_{X\mid Y}(x\mid y)dx$
    - interpretation : $E[X\mid Y]=\arg\min_g\norm{X-g(Y)}^2$, among all measurable functions $E[X\mid Y]$ best approximates $X$ in mean square
    - unbiasedness : $E[E[X\mid Y]]=E[X]$
    - taking out factors : $E[g(Y)X\mid Y]=g(Y)E[X\mid Y]$
    - tower property : $E[E[X\mid Y]\mid g(Y)]=E[X\mid g(Y)]$

  - conditional variance : $var[X\mid Y]=E[(X-E[X\mid Y])^2\mid Y]=E[X^2\mid Y]-E[X\mid Y]^2$

    - law total variance : $var(X)=E[var[X\mid Y]]+var(E[X\mid Y])$

  - covariance matrix : $\bs \Omega=\{\Omega_{ij}\}$ with $\Omega_{ij}=cov(Y_i,Y_j)=E[(\bs Y-\bs\mu)(\bs Y-\bs\mu)^\top]=E[\bs Y\bs Y^\top]-\bs\mu\bs\mu^\top$

    - linear transforms : for $\bs Y$ random $d\times 1$ vector
      -  vector $\bs\beta\in\R^p$ : variance $\bs\beta^\top\bs\Omega\bs\beta\ge 0$ of $\bs\beta^\top\bs Y$
      -  $p\times d$ matrix $\bs A$ : mean $\bs A\bs\mu$ and covariance $\bs A\bs\Omega\bs A^\top$ of $\bs A\bs Y$ 
      -  vectors $\bs\beta,\bs\gamma\in\R^p$ : covariance $\bs\gamma^\top\bs\Omega\bs\beta$ of $\bs\beta^\top\bs Y$ with $\bs\gamma^\top\bs Y$

  - inequalities

    - markov : $P[X\ge \epsilon]\le\frac{E[X]}{\epsilon}$
    - chebyshev : $P[\abs{X-E[X]}\ge\epsilon]\le\frac{var[X]}{\epsilon^2}$
    - jensen : $\varphi(E[X])\le E[\varphi(X)]$ for any convex $\varphi$
    - monotonicity and covariance : $cov[X,g(X)]\ge 0$, $g$ decreasing

  - generating functions MGF : $M_X(t):\R\to\R\cup\{\infty\}$, $M_X(t)=E[e^{tX}]$

    - moments : $E[X^k]=\frac{d^kM_X}{dt^k}(0)$
    - independance : $M_{X+Y}=M_XM_Y$
    - random vector : $M_\bs X(\bs u)=E[e^{\bs u^\top\bs X}]$


### Distribution

- bernoulli : $X\sim Bern(p)$, $\X=\{0,1\}$ with $p\in(0,1)$
  - $f(x)=p1\{x=1\}+(1-p)1\{x=0\}$
  - $E[X]=p$
  - $var[X]=p(1-p)$
  - $M(t)=1-p+pe^t$
  - $\hat p=\bar Y$
- binomial : $X\sim Binom(n,p)$, $\X=\{0,1,\ldots,n\}$ with $p\in(0,1)$, $n\in\N$
  - $f(x)={n\choose x}p^x(1-p)^{n-x}$
  - $E[X]=np$
  - $var[X]=np(1-p)$
  - $M(t)=(1-p+pe^t)^n$
  - $X=\sum_{i=1}^n Y_i$ with $Y\sim Bern(p)$
- geometric : $X\sim Geom(p)$, $\X=\{0\}\cup\N$ with $p\in(0,1)$
  - $f(x)=(1-p)^x p$
  - $E[X]=\frac{1-p}{p}​$
  - $var[X]=\frac{1-p}{p^2}$
  - $M(t)=\frac{p}{1-(1-p)e^t}$ for $t<-\log(1-p)$
  - $X=\min\{k\in\N \mid Y_k=1\}-1$ with $Y\sim Bern(p)$ 
  - memoryless : $P(X>m+n\mid X \ge m)=P(X>n)$
- negative binomial : $X\sim NegBin(r,p)$, $\X=\{0\}\cup\N$ with $p\in(0,1)$, $r>0$
  - $f(x)={x+r-1\choose x}(1-p)^xp^r$
  - $E[X]=r \frac{1-p}{p}$
  - $var[X]=r\frac{1-p}{p^2}$
  - $M(t)=\frac{p^r}{[1-(1-p)e^t]^r}$ for $t<-\log(1-p)$
  - $X=\sum_{i=1}^n Y_i$ with $Y\iid Geom(p)$
- poisson : $X\sim Poisson(\lambda)$, $\X=\{0\}\cup\N$ with $\lambda >0$

  - $f(x)=e^{-\lambda}\frac{\lambda^x}{x!}$
  - $E[X]=\lambda$
  - $var[X]=\lambda$
  - $M(t)=e^{\lambda(e^t-1)}$
  - $\hat\lambda=\bar Y$
  - $\{Y_n\}_{n\ge 1}$ with $Y\sim Binom(n,p)$ follows $f_{Y_n}\overset{n\to\infty}{\to}f_X$ with $\lambda=np$
  - $X\sim Poisson(\lambda)$ and $Y\sim Poisson(\mu)$ independent, conditional of $X$ given $X+Y=k$ is $Binom(k,\lambda/(\lambda +\mu))$
- multinomial : $\bs X\sim Multi(n, p_1,\ldots, p_k)$, $\bs\X=\{0,1,\ldots,n\}^k$ with $\bs p\in(0,1)^k$ s.t. $\sum_{i=0}^k p_i=1$
  - $f(x_1,\ldots,x_k)=\frac{n!}{x_1!\cdots x_k!}p_1^{x_1}\cdots p_k^{x_k}1\{\sum_{i=1}^k x_i=n\}$
  - $E[X_i]=np_i$
  - $var[X_i]=np_i(1-p_i)$
  - $cov(X_i,X_j)=-np_ip_j$
  - $M(u_1,\ldots,u_k)=(\sum_{i=1}^kp_i e^{u_i})^n$
  - generalize binonial : $n$ independent trial, $k$ possible outcomes
  - $X=\sum_{i=1}^n Y_i$ with $Y\iid Poisson(\lambda_i)$ with $p_i=\frac{\lambda_i}{\lambda_1+\cdots +\lambda_k}$
- uniform : $X\sim Unif(\theta_1,\theta_2)$ with $\theta_1<\theta_2$
  - $f(x)=(\theta_2 - \theta_1)^{-1}$ if $x\in(\theta_1,\theta_2)$ else $0$
  - $E[X]=(\theta_1+\theta_2)/2$
  - $var[X]=(\theta_2-\theta_1)^2/12$
  - $M(t)=\frac{e^{t\theta_2}-e^{t\theta_1}}{t(\theta_2-\theta_1)}$ for $t\not=0$, $M(0)=1$
  - $\p=Y_{(n)}$ for $Unif(0,\t)$, non-differentiable
- exponential : $X\sim Exp(\lambda)​$ with $\lambda > 0​$
  - $f(x)=\lambda e^{-\lambda x}$ if $x\ge 0$ else 0
  - $E[X]=\lambda^{-1}$
  - $E[X]=\lambda^{-2}$
  - $M(t)=\frac{\lambda}{\lambda -t}$ for $t<\lambda$
  - $\hat\lambda=1/\bar Y$
  - memoryless : $P(X>t+s\mid X>t)=P(X>s)$
  - $X\sim Exp(\lambda_1)$, $Y\sim Exp(\lambda_2)$ independent, $Z=\min\{X, Y\}\sim Exp(\lambda_1+\lambda_2)$
- gamma : $X\sim Gamma(r,\lambda)$ with shape $r>0$, scale $\lambda >0$
  - $f(x)=\frac{\lambda^r}{\Gamma(r)}x^{r-1}e^{-\lambda x}$ if $x\ge 0$ else 0
  - $E[X]=r/\lambda$
  - $var[X]=r/\lambda^2$
  - $M(t)=(\frac{\lambda}{\lambda - t})^r$ for $t<\lambda$
  - $Y=\sum_{i=1}^r Y_i$ with $Y\iid Exp(\lambda)$, special case Erlang distribution
- gaussian : $X\sim N(\mu,\sigma^2)$ with mean $\mu\in\R$, variance $\sigma^2>0$
  - $f(x)=\frac{1}{\sigma\sqrt{2\pi}}e^{-\frac{1}{2}(\frac{x-\mu}{\sigma})^2}$
  - $E[X]=\mu$
  - $var[X]=\sigma^2$
  - $M(t)=e^{t\mu+t^2\sigma^2/2}$ 
  - $(\hat\mu,\hat\sigma^2)=(\bar Y,\frac{1}{n}\sum_{i=1}^n(Y_i-\bar Y)^2)$
  - standard normal : $Z\sim N(0,1)$ with density $\varphi(z)=f_Z(z)$ and CDF $\Phi(z)=F_Z(z)$
  - addition closure : $aX+b\sim N(a\mu+b,a^2\sigma^2)$, $F_X(x)=\Phi(\frac{x-\mu}{\sigma})$, $S=\sum_{i=1}^n X_i\sim N(\sum_{i=1}^n\mu_i,\sum_{i=1}^n\sigma_i^2)$ for $X\iid N(\mu_i,\sigma^2_i)$
- chi-square : $X\sim \chi_k^2$ with $k$ degree of freedom, $Gamma(k/2,1/2)$
  - $f(x)=\frac{1}{2^{k/2}\Gamma(k/2)} x^{k/2-1}e^{-x/2}$ if $x\ge 0$ else $0$
  - $E[X]=k$
  - $var[X]=2k$
  - $M(t)=(1-2t)^{-k/2}$ for $t<1/2$
- student's t : $X\sim t_k$
  - $f(x)=\frac{\Gamma(\frac{k+1}{2})}{\Gamma(\frac{k}{2})\sqrt{k\pi}}(1+\frac{x^2}{k})^{-\frac{k+1}{2}}$
  - $E[X]=0$ for $k>2$ else undefined for $k=1$
  - $var[X]=\frac{k}{k-2}$ for $k>2$ else undefined
  - $M(t)$ undefined
- Snedecor-Fisher F : $X\sim F_{d_1,d_2}$
  - $f(x)=\frac{1}{B(d_1/2,d_2/2)}(\frac{d_1}{d_2})^{d_1/2}x^{d_1/2-1}(1+\frac{d_1}{d_2}x)^{-\frac{d_1+d_2}{2}}$ if $x\ge 0$ else $0$
  - $E[X]=\frac{d_2}{d_2-2}$ for $d_2>2$
  - $var[X]=\frac{2d_2^2(d_1+d_2-2)}{d_1(d_2-4)(d_2 - 2)^2}$ for $d_2>4$
  - $M(t)$ does not exist


### Entropy and exponential families

- entropy : instrinsic disorder or unpredictability, $H(X)=-E[\log f_X(X)]$
  - discrete : $-\sum_{x\in\X} f_X(x)\log f_X(x)$, $H(X)\ge 0$, $H(g(X))\le H(X)$
  - continuous : $-\int_{-\infty}^\infty f_X(x)\log f_X(x) dx$
- Kullback-Leibler divergence : $KL(q\mid\mid p)=E[-\log(q(x)/p(x))]=\int_{-\infty}^\infty p(x)\log\frac{p(x)}{q(x)}dx\ge 0$, lack symmerty and triangle inequality
- maximum entropy : $H(f)=-\int_\X f(x)\log f(x) dx$ under $k$ linear constraints $\int_\X T_i(x)f(x)dx=\alpha_i$
  - highest entropy solution : $f(x)=Q(\lambda_1,\ldots,\lambda_k)\exp(\sum_{i=1}^k\lambda_i T_i(x))$ 
- $k$-parameter exponential family : admit representation $f(y)=\exp(\sum_{i=1}^k \phi_iT_i(y)-\gamma(\phi_1,\ldots,\phi_k)+S(y))$ with $\bs\phi=(\phi_1,\ldots,\phi_k)\in\bs\Phi\subseteq\R^k$, $T_i:\Y\to\R$, $S:\Y\to\R$, $\gamma:\R^k\to\R$ real-valued, support independ of $\phi$
  - members : binomial, negative binomial, poisson, gamma, gaussian, pareto, weibull, laplace, lognormal, inverse gaussian, inverse gamma, normal-gamma, beta, multinomial, ...
  - non-members : student's t, mixtures
  - usual parametrization : $\exp(\sum_{i=1}^k\eta_i(\theta)T_i(y)-d(\theta)+S(y))$ with $\phi=\eta(\theta)$ and $d(\theta)=\gamma(\eta(\theta))$



## Sampling theory

### Sufficient statistics

- sampling : distribution known, $\theta\in\Theta$ unknown
  - sample : realisation from that distribution
  - assertions : concerning true value of $\theta$, $T(Y_1,\ldots,Y_n)$ of sample
- statistic : any function whose domain is sample space $\Y^n$ but does not itself depend on unknown parameters, $T:\Y^n\to\R^q$
- ancillary statistic : does not depend on $\theta$, no information on it
- level sets of a statistic : $A_t=\{\bs y\in\Y^n\mid T(\bs y)=t \}$
- sufficient statistic : $F_{\bs Y\mid T(\bs Y)=t}(Y_1,\ldots,Y_n)=P[Y_1\le y_1,\ldots,Y_n\le y_n\mid T(Y_1,\ldots, Y_n)=t]$ does not depend on $\theta$
- Fisher-Neyman factorization theorem : $T=T(\bs Y)$ sufficient iff $f(\bs y;\theta)=g(T(\bs y),\theta)h(\bs y)$
  - exponential family : sufficient $\tau_j(y_1,\ldots, y_n)=\sum_{i=1}^n T_j(y_i)$ as $f_{Y_1,\ldots, Y_n}(y_1,\ldots, y_n)=\exp(\sum_{j=1}^k\phi_j\tau_j(y_1,\ldots,y_n)-n\gamma(\phi_1,\ldots,\phi_n)+\sum_{i=1}^n S(y_i))$
- minimally sufficient statistic : if for any other sufficient static $S=S(\bs Y)$, $\exists g\enspace T(\bs y)=g(G(\bs Y))$, if multiple there is bijection in between
  - suppose $f(\bs y;\theta)/f(\bs z;\theta)$ independent of $\theta$ iff $T(\bs y)=T(\bs z)$, then $T$ minimally sufficient


### Sampling distibutions

- sampling distribution : $F_T(t_1,\ldots,t_p)=P[T_1(Y_1,\ldots,Y_n)\le t_1,\ldots,T_q(Y_1,\ldots, Y_n)\le t_q]$ under $F(y_1,\ldots,y_n;\theta)$, often $q=1$, depends on unknown $\theta$, distribution of a statistic
  - gaussian sufficient statistics : $Y_1,\ldots,Y_n\iid N(\mu,\sigma^2)$
    - $\bar Y=\frac{1}{n}\sum_{i=1}^n Y_i$ with $\bar Y\sim N(\mu,\sigma^2/n)$ and $E[\bar Y]=\mu$, $var(\bar Y)=\frac{\sigma^2}{n}$
    - $S^2=\frac{1}{n-1}\sum_{i=1}^n (Y_i-\bar Y)^2$ with $\frac{n-1}{\sigma^2}S^2\sim \chi^2_{n-1}$ and $E[S^2]=\sigma^2$, $var(S^2)=\frac{2\sigma^4}{n-1}$
    - $(\bar Y, S^2)$ minimally sufficient for $(\mu,\sigma^2)$
    - $\bar Y$ independent $S^2$
  - exponential family : if $\bs\phi=(\phi_1,\ldots,\phi_k)^\top\in\bs\Phi$ open, $\gamma$ infinitely differentiable in all $k$ variable and $E[\bs \tau]=n\nabla_\bs\phi\gamma(\bs\phi) $ with $cov[\tau]=n\nabla^2_\bs\phi\gamma(\bs\phi)$
- sum of gaussian squares : $Z_i\iid N(0,1)$, $Z_1^2+\cdots+Z_k^2\sim \chi_k^2$
- gaussian empirically standardise mean : $Y_i\iid N(\mu,\sigma^2)$, $\frac{\bar Y-\mu}{S/\sqrt{n}}\sim t_{n-1}$
- ratio of gaussian sum of squares : $Y_1\sim\chi^2_{d_1}$, $Y_2\sim\chi^2_{d_2}$, $\frac{Y_1/d_1}{Y_2/d_2}\sim F_{d_1,d_2}$
- approximate sampling behaviour : sampling distribution not always obtainable in a closed/convient form, approximate it by simpler distribution

### Stochastic convergence

- in distribution (weak) : $F_n\overset{d}{\to}G$ whenever $F_n(y)\overset{n\to\infty}{\to}G(y)$ with $\lim_{\epsilon\to 0}G(y+\epsilon)=G(y)$, pointwise convergence, discontinuity points might not converge
- in probability : $Y_n\overset{p}{\to} Y$ whenever $P(\abs{Y_n-Y}>\epsilon)\overset{n\to\infty}{\to}0$ $\forall\epsilon>0$
- hierarchy
  - $Y_n\overset{p}{\to} Y$ implies $Y_n\overset{d}{\to}Y$
  - $Y_n\overset{d}{\to}c$ implies $Y_n\overset{p}{\to}c$
- continuous mapping : $g$ continous on $Y$ range
  - $Y_n\overset{p}{\to}Y$ implies $g(Y_n)\overset{p}{\to}g(Y)$
  - $Y_n\overset{d}{\to}Y$ implies $g(Y_n)\overset{d}{\to}g(Y)$
- Slutsky's theorem : $X_n\overset{d}{\to} X$, $Y_n\overset{d}{\to}c$, $g(X_n,Y_n)\overset{d}{\to}g(X,c)$
- law of large number : iid, $n^{-1}(Y_1+\cdots+Y_n)\overset{p}{\to}\mu$, for large $n$, $\bar Y\approx N(\mu,\sigma^2/n)$
- central limit theorem CLT : iid, $\sqrt{n}(\frac{1}{n}\sum_{i=1}^n Y_i-\mu)\overset{d}{\to}N(0,\sigma^2)$, for large n $Y_1+\cdots+Y_n\approx N(n\mu,n\sigma^2)$
  - vector : $\sqrt{n}(\bar{\bs X} -\bs\mu)\overset{d}{\to}N_d(0,\bs \Omega)$
- delta method : $a_n(X_n-\theta)\overset{d}{\to} Z$ with $g$ continuously differentiable, $a_n(g(X_n)-g(\theta))\overset{d}{\to}g'(\theta) Z$ as $a_n\uparrow\infty$
  - exponential family : $\bar T_n=n^{-1}\tau(X_1,\ldots,X_n)$, $\sqrt{n}(\bar T_n-\gamma'(\phi)\overset{d}{\to}N(0,\gamma''(\phi))$
  - vector : $a_n(g(\bs X_n)-g(\bs u))\overset{d}{\to}J_g(\bs u)\bs Z$
- weighted sum CLT : iid, $sup_{1\le j\le n}\frac{\gamma_j^2}{\sum_{i=1}^n \gamma_i^2}\overset{n\to\infty}{\to}0$ implies $\frac{1}{\sqrt{\sum_{i=1}^n\gamma^2_i}}\sum_{i=1}^n\gamma_i W_i\overset{d}{\to}N(0,1)$
- Cramér-Wold device : $\bs Y_n\overset{d}{\to}\bs Y$ iff $\bs u^\top\bs Y_n\overset{d}{\to}\bs u^\top\bs Y$ $\forall\bs u\in \R^n$
- Berry-Essen theorem : multivariate CLT with $\bs\mu=0​$ and $\bs\Omega=\bs I$, $sup_{u\in\R^d}\abs{F_{\sqrt{n}\bar Y}(\bs u)-F_Z(\bs u)}\le Cn^{-1/2}d^{1/4}E \norm{\bs Y_i}^3$

## Marginal inference

### Point estimation and likelihood theory

- estimator : r.v. $\hat \Theta$ where $\Theta$ deterministic parameters
- point estimator : statistic with codomain $T:Y^n\to\Theta$ 
- mean squared error : capture both notions of location and spread, $MSE(\p,\theta)=E[\norm{\p-\t}^2]$
- bias-variance decomposition : $MSE(\p,\t)=\norm{E[\p]-\t}^2+E[\norm{\p-E[\p]}^2]=bias + variance$
- consistency : if $\p_n\overset{p}{\to}\t$ as $n\to\infty$  
  - $P(\norm{\p-\t}>\epsilon)\le\frac{MSE(\p,\t)}{\epsilon^2}$, $MSE(\p_n,\t)\overset{n\to\infty}{\to}0$ vanishing MSE implies consistency but not the converse
- identifiability : probability model $\{F_\t\}_{\t\in\Theta}$ idenfiable if for any pair $\t_1$ and $\t_2$, $\t_1\not=\t_2$ implies $F_{\t_1}\not=F_{\t_2}$
- Fisher information : $\I_n(\t)=E[(\frac{\partial}{\partial\t}\log f(Y;\t))^2]=-E[\frac{\partial^2}{\partial\t^2}\log f(Y;\t)]$, $\I_n(\t)=n\I_1(\t)$ for iid, 1 over curvature
- Cramér-Rao lower bound : unbiased estimator $var(\p(Y))\ge 1/\I_n(\t)$ (by Cauchy-Schwartz)
  - tight achievable : reach lower bound iff density $Y$ is one parameter expoential family with sufficient statistic $\p$
- Rao-Blackwell theorem : unbiased estimator $\p$, sufficient $T$ for $\t$, $var(\p^*)\le var(\p)$ with $\p^*=E[\p\mid T]$, equality iff $P_\t(\p^*=\p)=1$
  - $\p_T^*$, $\p_S^*$, $T=h(S)$ implies $var(\p^*_T)\le var(\p^*_S)$
- likelihood : $L(\t)=F(Y_1,\ldots,Y_n;\t)$, if iid $L(\t)=\Pi_{i=1}^n f(Y_i;\t)$, joint density/frequency
  - discrete case : probability of observing our sample as function of $\t$
  - continuous case : probability of observing something in neighbourhood of our sample as function of $\t$
- maximum likelihood estimator MLE : $\p$ s.t. $L(\t)\le L(\p)$ $\forall\t\in\Theta$, unique $\arg\max_{\t\in\Theta}L(\t)$
  - equivariance : $\p$ MLE of $\t$, $g$ bijection, $g(\p)$ MLE of $g(\t)$
  - if differentiable : $\nabla_\t L(\t)=0$ 
  - check maximum : $-\nabla^2_t L(\t)|_{\t=\p}>0$
  - loglikelihood : $l(t)=\log L(\t)$
  - consistency
    - $\t\in\R$ : yes, if regular enough and MLE unique
    - $\t\in R^p$ : need more info such as concavity + existence (exponential families)
- asymptotic distribution of MLE : iid, regular enough, MLE existence and consistency implies $\sqrt{n}(\p_n-\t)\overset{d}{\to}N(0,\frac{\I_1(\t)}{\mathcal J^2_1(\t)})$, interpreted as $\p_n\overset{d}{\approx}N(\t,\frac{1}{n\I_1(\t)})\equiv N(\theta,\frac{1}{\I_n(\t)})$ 
  - meaning. MLE is approximately normally distributed, unbiased and achieving Cramér-Rao lower bound
  - regularity conditions
    - $\Theta$ open subset
    - support of $suppf$ independent of $\t$
    - $f$ thrice continuously differentiable w.r.t. $\t$
    - $E_\t[l'(X_i;\t)]=0\;\forall\t$, $var_\t[l'(X_i;\t)]=\I_1(\t)\in(0,\infty)\;\forall\t$
    - $-E_\t[l''(X_i;\t)]=\mathcal J_1(\t)\in(0,\infty)\;\forall\t$
    - $\exists M(x)>0$ and $\delta > 0$ s.t. $E_{\t_0}[M(X_i)]<\infty$ and $\abs{\t-\t_0}<\delta$ implies $\abs{l'''(x;\t)}\le M(x)$
  - for any r.v. $\t^*_n$ on segment $\p_n$ and $\t_0$, $R_n=(\p_n-\t)\frac{1}{2n}\sum_{i=1}^n l'''(X_i;\t^*_n)\overset{p}\to 0$
- James-Stein estimator : $\bs Y\sim N(\bs \mu,\bs I_{n\times n})$, $\bs\mu\in\R^n$,  $\tilde{\bs\mu}_a=(1-\frac{a}{\norm{\bs Y}^2})$ $\bs Y=(1-\frac{a}{\norm{\hat{\bs\mu}}^2})\hat{\bs\mu}$, $n\ge 3$
  - $\forall a\in(0,2n-4)$, $MSE(\tilde{\bs\mu}_a,\bs\mu)\le MSE(\hat{\bs\mu},\bs\mu)$
  - for $a=n-2$, $MSE(\tilde{\bs\mu}_{n-2},0)<MSE(\tilde{\bs\mu},0)$
  - $\forall\bs\mu\in\R^n$ and $\forall a\in(0,2n-4)$, $MSE(\tilde{\bs\mu}_{n-2},\bs\mu)\le MSE(\tilde{\bs\mu}_a,\bs\mu)$ 
- loss function : $\L(\p,\t)$ convex measure of performance, remplace $\norm{\p-\t}$
  - risk : expected loss $R(\p,\t)=E[\L(\p,\t)]$
  - can avoid skewed penalization, MSE on positive domain bound underestimation error
- decision theory : decision rules should be compared by their risk functions
  - family of distribution $\mathcal F$, game variant 
  - parameter space $\Theta$, parameterize family
  - data space $\mathcal Y^n$, space of possible outcomes
  - action space $\mathcal A$, possible actions or decisions available
  - loss function $\L:\Theta\times \mathcal A\to\R^+$, how much to pay when losing
  - set $\mathcal D$ of decision rules : any $\delta\in\mathcal D$ measurable function $\delta:\mathcal\Y^n \to\mathcal A$, possible strategies, risk $R(\delta,\theta)=E[\L(\delta(\bs Y),\theta)]$
  - comparisons
    - uniform : hard, seek dominance everywhere
    - minimax : relaxed, compare worst-case risks, $sup_{\t\in\theta}R(\t,\delta)\le\sup_{\t\in\Theta}R(\t,\delta')$, overly conservative
    - $\pi$-bayes : relaxed, compare average risk, $r(\pi,\delta)=\int_\Theta R(\t,\delta)\pi(\t)d\t=\int_\Theta\int_\chi L(\t,\delta(y))f_\t(y)dy\pi(\t)d\t$ with prior $\pi$, cannot be uniformly dominated

### Hypothesis testing and confidence intervals

- context : disjoint regions $\Theta_0$ and $\Theta_1$
  - null hypothesis : $H_0$ states $\t\in\Theta_0$
  - alternative hypothesis : $H_1$ states $\t\in\Theta_1$
- test function : $\delta:\mathcal Y^n\to\{0,1\}$ as $\delta(Y_1,\ldots,Y_n)=1\{T(Y_1,\ldots,Y_n)\in C\}$ where $T$ test statistic and $C$ critical region subset of range of $T$
- errors : Bernouilli-like, $\mathcal A=\{0,1\}$
  - action/truth:  $H_0$                $H_1$
  - $0$                      😄                 type II error
  - $1$                      type I error  😄
- $0$$-$1 loss : $\L(a,\t)=\cases{1& \text{if}\;\t\in\Theta_0, a=1\;\text{(type I error)}\\ 1 &\text{if}\;\t\in\Theta_1, a=0\;\text{(type II error)}\\ 0&\text{otherwise}\qquad\quad\!\text{(no error)}}$
- risk : $R(\delta,\t)=P_\t[\delta=1]1\{\t\in\Theta_0\}+P_\t[\delta = 0]1\{\t\in\Theta_1\}$
- Neyman-Pearson framework : in application one type of error is more severe, exploit asymmetry by fixing tolerance ceiling for this error, consider only test function that respect it and focus on minimising the other
  - fix : $\alpha\in(0,1)$
  - test : $\delta\in\mathcal D(\Theta_0,\alpha)=\{\delta: sup_{\t\in\Theta_0} P_\t[\delta=1]\le\alpha\}$, type I error bounded above by $\alpha$
  - minimize : $P_\t[\delta(X)=0]=1-P_\t[\delta(X)=1]$
  - or maximize power : $\beta(\t,\delta)=P_\t[\delta(X)=1]=E_\t[1\{\delta(X)=1\}]=E_\t[\delta(X)]$
- most powerful ML test : continuous case, $H_0:f=f_0$, $H1:f=f_1$, $\Lambda(Y)=f_1(Y)/f_0(Y)$, $\exists k>0$ s.t. $P_0[\Lambda(Y)\ge K]=\alpha$ with test of $H_0$ vs $H_1$ at significance level $\alpha$, $\delta(Y)=1\{\Lambda(Y)\ge k\}$, optimal
  - reject if likelihood of $\t_1$ $k$ times higher than $\t_0$
  - unless continuous, not guarantee to exist
- one sided hypotheses : often uniformly most powerful test depending on model
- likelihood ratio statistic LRT : $H_0:\t\in\Theta_0$, $H_1:\t\in\Theta_1$, $\Lambda(Y)=\frac{sup_{\t\in\Theta}f(Y;\t)}{sup_{\t\in\Theta_0}f(Y;\t)}=\frac{sup_{\t\in\Theta}L(\t)}{sup_{\t\in\Theta_0} L(\t)}$
  - distribution : $dist(\Lambda)$ most often intractable
  - asymptotic approximation : $\Theta$ open subset of $\R^p$, either $\Theta_0=\{\t_0\}$ or open subset $\R^s$ with $s<p$, iid, restrict attention to $H_0:\t=\t_0$ vs $H_1:\t\not=\t_0$, give $\Lambda_n(Y)=\Pi_{i=1}^n\frac{f(Y_i;\hat\t_n)}{f(Y_i;\t_0)}$ where $\hat\t_n$ MLE of $\t$
- Wilks' theorem : iid, regular enough with $\I_i(\t)=\mathcal J_1(\t)$, 
  - case $p=1$ : MLE sequence $\hat\t_n$ consistent for $\t$ implies likelihood ratio statistic $\Lambda_n$ for $H_0:\t=\t_0$ satisfying $2\log\Lambda_n\overset{d}{\to} V\sim\chi_1^2$ when $H_0$ true
  - case general $s\le p$ : MLE sequence $\hat\t_n$ consistent for $\t$ implies likelihood ratio statistic $\Lambda_n$ for $H_0:\{\t_j=\t_{j,0}\}_{j=1}^s$ satisfying $2\log\Lambda_n\overset{d}{\to} V\sim\chi_s^2$ when $H_0$ true
- other tests
  - Wald's test
  - Score test
- $p$-value : for $\{\delta_\alpha\}_{\alpha\in(0,1)}$ family of test functions satisfying $\alpha_1<\alpha_2$implies $\{y\in\mathcal Y^n:\delta_{\alpha_1}(y)=1\}\subseteq\{y\in\mathcal Y^n:\delta_{\alpha_2}(y)=1\}$, observed significance level $p(y)=\inf\{\alpha:\delta_\alpha(y)=1\}$
  - small $p$-value : provide evidence against $H_0$
  - large $p$-value : provide no evidence against $H_0$
- confidence interval : statistics $L(Y)<U(Y)$, $100(1-\alpha)$% confidence interval $[L(Y), U(Y)]$ if $P_\t[L(Y)\le\t\le U(Y)]\ge 1-\alpha$
- pivot quantity : $g(Y,\t)$ if function both of $Y$ and $\t$ but its distribution does not depend on $\t$
- confidence region : $R(Y)\subset\Theta$, $100(1-\alpha)$% conficence region for $\t\in\Theta\subset\R^p$ if $P_\t[R(Y)\ni\t]\ge 1-\alpha$
  - duality : $R(Y)=[L_1(Y),U_1(Y)]\times\cdots\times[L_p(Y),U_p(Y)]$, Bonferroni inequality implies $P_\t[R(Y)\ni\t]\ge 1-\sum_{i=1}^p P[\t_i\not\in[L_i(Y),U_i(Y)]]=1-\sum_{i=1}^p(1-q_i)$, thus $\sum_{i=1}^p(1-q_i)=\alpha$
- Bonferroni's procedure : test each hypothesis separately at level $\alpha_t=\alpha/T$, reject $H_0$ if at least one of $\{H_{0,t}\}_{t=1}^T$
- Holm's procedure : reject $H_{0,t}$ for small values of corresponding $p$-value, $p_t$, order $p$-values from most to least significant $p_{(1)}\le\cdots\le p_{(T)}$, starting from $t=1$ going up, reject all $H_{0,(t)}$ s.t. $p_{(t)}$ significant at level $\alpha/(T-t+1)$, stop rejecting at first insignificant $p_{(t)}$
- Yields Sime's procedure : independence, suppose reject $H_{0,j}$ for small values of $p_j$, order $p$-values from most to least significant $p_{(1)}\le\cdots\le p_{(T)}$, if for some $j=1,\ldots,T$, $p$-value $p_{(j)}$ significant at level $\frac{j\alpha}{T}$ thenreject global $H_0$
- Hochberg's procedure : inpdendence, localise Sime, suppose reject $H_{0,j}$ for small values of $p_j$, order $p$-values from most to least significant $p_{(1)}\le\cdots\le p_{(T)}$, starting from $j=T,T-1,\ldots$, accept all $H_{0,(j)}$ s.t. $p_{(j)}$ insignificant at level $\alpha/(T-j+1)$, stop accepting for first $j$ s.t. $p_{(j)}$ significant at level $\alpha/j$ and reject all remaining ordered hypotheses past that $j$ going down

### Nonparametric marginal inference and smoothing

- empirical distribution function EDF : $Y_1,\ldots,Y_n\iid F$, $\hat F_n(y)=\frac{1}{n}\sum_{i=1}^n1\{Y_i\le y\}$
- Glivenko-Cantelli theorem : iid distributed according to $F$, $sup_{x\in\R}\abs{\hat F_n(y)-F(x)}\overset{a.s.}\to 0$
- Dvoretzky-Kiefer-Wolfowitz inequality DKW : iid distributed according to $F$, $P\{sup_{y\in/R}\abs{\hat F_n(y)-F(y)}>\epsilon\}\le 2e^{2n\epsilon^2}$
- estimate parameters : no model assumed, plug-in principle, use $\nu(\hat F_n)$ as estimator of $\nu(F)$
  - mean : $\mu(F)=\int_{-\infty}^\infty y dF(y)$ get $\hat\t=\t(\hat F_n)=\int_{-\infty}^\infty yd\hat F_n(y)=\bar Y$
  - variance : $\sigma^2(F)=\int_{-\infty}^\infty(y-\mu(F))^2 dF(y)$ get $\sigma^2(\hat F_n)=\int_{-\infty}^\infty (y-\int_{-\infty}^\infty ud\hat F_n(u))^2d\hat F_n(y)=\frac{1}{n}\sum_{i=1}^n(Y_i-\bar Y)^2$
  - median : $m(F)=F^{-1}(1/2)$, $n$ odd get $\hat m=m(\hat F_n)=Y_{(\frac{n+1}{2})}$
  - if parametric model assumable, MLE preferable
    - $F$ gaussian, mean estimator lead to same as MLE
    - $F$ Laplace, MLE of mean is median, not mean
- density estimation : $\nu(F)=\frac{d}{dx} F(x)|_{x=x_0}$, when it exists, $F\mapsto\nu(F)$ not well behaved in general
  - smoother estimate : $\tilde F_n(x)=\int_{-\infty}^\infty \Phi(\frac{x-y}{h})d\hat F_n(y)=\frac{1}{n}\sum_{i=1}^n\Phi(\frac{x-Y_i}{h})$ with standard normal CDF and $h>0$ parameters
  - smoothed plug-in estimator : $\hat f(x)=\frac{d}{dx}\tilde F_n(x)=\frac{1}{n}\sum_{i=1}^n\frac{1}{h}\varphi(\frac{x-Y_i}{h})$ for $\varphi(x)=\frac{1}{\sqrt{2\pi}}e^{-x^2/2}$
- kernel density estimator KDE : $\hat f(x)=\frac{1}{nh}\sum_{i=1}^n K(\frac{x-Y_i}{h})$
  - density kernel : $K$
  - bandwith : $h$
  - integrated mean squared error : $IMSE(\hat f,f)=\int_\R E[(\hat f(x)-f(x))^2]dx$
    - bias + variance
- asymptotic risk for KDE : iid, $IMSE(\hat f,f)=\frac{h^4}{4}\int_\R(f''(x))^2dx+\frac{1}{nh}\int_\R K^2(x)dx+o(h^4+\frac{1}{nh})$ as $h\to 0$, bias proportional to curvature of $f$
  - optimal choice of $h$ depends on $f''$ unknown
  - risk of asynptotic order : $n^{-4/5}$
- minimax optimal rates for KDE : $F(m,r)$ subset of $m$-differentiable in an $L^2$ ball of radius $r$ $\int_\R(f^{(m)}(x))^2 dx\le r^2$, $sup_{f\in F(m,r)}E[\int_\R(\hat f_n(x)-f(x))^2 dx]\ge Cn^{-\frac{2m}{2m+1}}$
- bandwith in practice
  - pilot estimator : use parameter family, plug it into optimal bandwith expression
  - least square cross-validation : construct unbiased estimator of $IMSE$, choose $h$ to minimise it
- leave-one-out cross validation : $LSCV(h)=\int_\R\hat f_h(x)dx-\frac{2}{n}\sum_{i=1}^n\hat f_{h,-i}(Y_i)$
  - Stone's theorem : bandwidth selected by cross-validation, $\frac{\int_\R(\hat f_{h_{CV}}(x)-f(x))^2 dx}{\inf_{h> 0}\int_\R (\hat f_h(x)-f(x))^2 dx}\overset{a.s}\to 1$ provided true density bounded
- higher dimension KDE : $\hat f(x)=\frac{1}{n\abs{H}^{1/2}}\sum_{i=1}^n K(H^{-1/2}(x-Y_i))$ with $H\ge 0$ $d\times d$ bandwith matrix and $K(x_1,\ldots,x_n)=\Pi_{j=1}^d\varphi (x_j)$
  - curse of dimensionality : $h\propto n^{-\frac{1}{4d}}$, converge of $n^{-\frac{4}{4+d}}$
- nonparametric : tradeoff flexibility and efficiency, interpretability

## Inference with covariates (regression)

### Gaussian linear models

- regression : $Y$ random whose law influenced by $x$ non-random, $Y_i\overset{\text{independent}}\sim \text{Distribution}\{g(x_i)\}$ where $g(x_i)=\t_i$
  - $x_i$ : continuous, discrete, categorical, vector, randomly, chosen by experimenter
  - $g(\cdot)$ : linear, polynomial, exponential coefficient, cubic spline, neural net
  - distribution/function $g$  $g(x_i^\top)=x_i^\top\beta$        $g$ nonparametric
  - gaussian                          linear regression  smoothing
  - exponential family         GLM                        GAM
- matrix : $\bs Q$ $n\times p$ real
  - column space : range, $\mathcal M(Q)=\{y\in\R^n :\exists\beta\in\R^p, y=Q\beta \}$ subspace of $\R^n$, coordinate system
    - full rank $p$ : coordinates $\beta$ corresponding to $y\in\mathcal M(Q)$ unique
  - null space : kernel, $\ker(Q)=\{x\in\R^p : Qx=0\}$
  - orthogonal complement of $\mathcal M(Q)$ :  $\mathcal M^\bot(Q)=\{y\in\R^n: y^\top Q x=0, \forall x\in\R^p \}=\{y\in\R^n: y^\top v=0, \forall v\in\mathcal M(Q)\}$
  - existence of solution : $y$ element of $\mathcal M(Q)$
  - uniqueness of solution : unique coordinate vector $\beta$
- spectral theorem : $p\times p$ matrix $Q$ symmetric iff exists $p\times p$ orthogonal matrix $U$ and a diagonal matrix $\Lambda$ s.t. $Q=U\Lambda U^\top$
  - eigenvectors : $U=(u_1 \cdots u_p)$ s.t. $Qu_j=\lambda_j u_j$ (unique if eigenvalues distinct)
  - eigenvalues : $\Lambda=diag(\lambda_1,\ldots,\lambda_p)$ real
  - rank of $Q$ : number of non-zero eigenvalues
- singular value decomposition : any $n\times p$ real matrix can be factorised as $Q=U\Sigma V^\top$with $U$ $n\times n$ left unitary singular vectors, $\Sigma$ $n\times p$ diagonal non negative singular values, $V$ $p\times p$ right unitary singular vectors
  - $U$ : eigenvectors of $QQ^\top$, vectors corresponding to non-zero singular values form orthonormal basis $\mathcal Q$
  - $V$ : eigenvectors of $Q^\top Q$, vectors corresponding to zero singular values form orthonormal basis $\mathcal M^\bot(Q)$
  - $\Sigma^2$ : eigenvalues of $QQ^\top$ and $Q^\top Q$
- idempotent matrix : $Q^2=Q$
- orthogonal projection : onto subspace $V$, symmetric idempotent matrix $H$ s.t. $\mathcal (H)=V$, unique
  - eigenvalues of $H$ only $0$ or $1$
  - $I-H$ projection onto $V^\bot$
  - $Hy=y\;\forall y\in V$
  - $x_1,\ldots,x_p$ linearly independent and $span(x_1,\ldots,x_p)=V$ implies $H=X(X^\top X)^{-1}X^\top$ with $X=(x_1 \cdots x_p)$
  - $\norm{x-Hx}\le\norm{x-v}\;\forall v\in V$
  - $V_1\subseteq V\subseteq\R^n$ with $H_1$ projection onto $V_1$ and $H$ onto $V$, $HH_1=H_1=H_1H$
  - $Q$ rank $k$ iff exist orthonormal vectors s.t. $Q=\sum_{j=1}^k v_iv_i^\top$
- non-negative/positive matrix : $p\times p$ real symmetric non-negative definite $\Omega\succeq 0$ or positive definite $\Omega\succ 0$ 
  - quadratic form definition : iff $x\top\Omega x\ge 0$ $\forall x\in\R^p$ or $\forall x\in\R^p\setminus\{0\}$
  - spectral definition : iff eigenvalues non-negative or strictly positive
  - non-negative definite iff $\Omega$ covariance matrix of some random vector $Y$
- principal component analysis PCA : maximise $var(v_1^\top Y)=v_1^\top\Omega v_1=\sum_{i=1}^d\lambda_i(u_i^\top v_1)^2$ over $\norm{v_1}=1$, eivenvectors
- optimal linear dimension reduction : $Y$ mean-zero r.v. with covariance $\Omega$, $H$ project onto span of first $k$ eigenvectors of $\Omega$, $E\norm{Y-HY}^2\le E\norm{Y-QY}^2$ for any $Q$ of rank at most $k$
  - deterministic version : $x_1+\cdots+x_p=0$, $X=(x_1 \cdots x_p)$, best approximating $k$-hyperplane given by span of first $k$ eigenvectors of $XX^\top$, projection $H$ holds $\sum_{i=1}^p\norm{x_i-Hx_i}^2\le\sum_{i=1}^p\norm{x_i-Qx_i}^2$
- multivariate gaussian distribution : iff $\beta^\top Y$ univariate normal distribution, $Y\sim N(\mu,\Omega)$
  - random vector independent : iff joint MGF product of marginal MGF
  - MGF : $M(u)=\exp(u^\top\mu+\frac{1}{2}u^\top\Omega u)$
  - affine transformation : $\t+BY\sim N(\t+B\mu,B\Omega B^\top)$
  - density : assuming $\Omega$ nonsingular $f(y)=\frac{1}{(2\pi)^{p/2}\abs{\Omega}^{1/2}}\exp(-\frac{1}{2}(y-\mu)^\top\Omega^{-1}(y-\mu))$
  - isosurfaces : constant density isosurfaces ellipsoidal
  - coordinate distributions : marginal of gaussian are gaussian (converse not true)
  - $\Omega$ diagonal : independent coordinates $Y_j$
  - $AY$ independent $BY$ :: iff $A\Omega B^\top=0$
- $\chi^2$ distribution : $Z\sim N(0, I_{p\times p})$ $\norm{Z}^2=\sum_{j=1}^pZ_j^2\sim\chi^2_p$
  - $Z\sim N(0,I_{p\times p})$ and projection $H$ of rank $r\le p$, $Z^\top H Z\sim\chi_r^2$
  - $Y\sim N(\mu,\Omega)$ with $\Omega$ nonsingular, $(Y-\mu)^\top\Omega^{-1}(Y-\mu)\sim\chi_p^2$
- $F$ distribution : $V\sim\chi_p^2$ independent $W\sim\chi_q^2$, $(V/p)/(W/q)\sim F_{p,q}$
- linear regression : $Y_i\mid x_i\ind \text{Distribution}\{g(x_i)\}$
  - gaussian : $g(x)=\beta_0+\beta_1 x$, $Y\mid x_i\sim N(\beta_0+\beta_1 x_i,\sigma^2)\iff Y=\beta_0+\beta_1x+\epsilon_i$ with $\epsilon_i\ind N(0,\sigma^2)$
  - $x$ : explanatory variable, covariate
  - $Y$ : response variable
  - linearity : in parameters, not explanatory variable
  - vector : $g(\bs x)=\beta_0+\bs\beta^\top\bs x$
- least squares estimator : $\hat\beta=\arg\max_\beta\{-(Y-X\beta)^\top(Y-X\beta\}=\arg\min\norm{Y-X\beta}^2=(X^\top X)^{-1}X^\top Y$ if $X$ rank $p$
  - likelihood : $Y_i=\beta_0+\beta_1x_{i1}+\cdots+\beta_qx_{iq}+\epsilon_i$ with $\epsilon_i\iid N(0,\sigma^2)$ or $Y=X\beta+\epsilon$ with $\epsilon\sim N(0,\sigma^2 I_{n\times n})$
  - log-likehood maximised : $(Y-X\beta)^\top(Y-X\beta)$ minimised
  - fitted values : $\hat Y=X\hat\beta$
  - biased variance : $\hat\sigma^2=\frac{1}{n}(Y-X\hat\beta)^\top(Y-X\hat\beta)=\frac{1}{n}\norm{\hat Y-Y}^2$
  - unbiased variance $S^2=\frac{1}{n-p}(Y-X\hat\beta)^\top(Y-X\hat\beta)=\frac{1}{n-p}\norm{\hat Y-Y}^2$
  - row geometry : exploratory analysis, observations, scatterplot, data space
  - column geometry : theoretical analysis, variables
  - hat matrix : projection of $Y$ onto $\mathcal M(X)$, $H=X(X^\top X)^{-1}X^\top$ giving $\hat Y=X\hat\beta=HY$
  - residuals : $e=Y-X\hat\beta=(I-H)Y=(I-H)\epsilon$, $\sum e_i^2$ minimised over all $\beta$
  - orthogonaliy : $\hat Y^\top e=0$
  - pythagoras : $Y^\top Y=\hat Y^\top\hat Y+e^\top e=Y^\top HY+\epsilon^\top(I-H)\epsilon$
- weighted least squares : $Y_i\ind N(\beta_0+\beta_1x_{i1}+\cdots+\beta_qx_{iq},\frac{\sigma^2}{w_i})$
  - transformation : $Y^*=W^{1/2}Y$, $X^*=W^{1/2}X$ with $W=diag(w_1,\ldots,w_n)$
  - $\hat\beta=(X^\top W X)^{-1}X^\top W Y$
  - $S^2=\frac{1}{n-p}Y^\top[W-WX(X^\top W X)^{-1}X^\top W]Y$
- sampling distribution LSE under gaussian model : $Y_{n\times 1}=X_{n\times p}\beta_{p\times 1}+\epsilon_{n\times 1}$ with $\epsilon\sim N_n(0,\sigma^2 I_{n\times n})$ full rank $p$ < $n$
  - $HY$ sufficient for $\beta$
  - $\hat\beta\sim N_p\{\beta,\sigma^2(X^\top X)^{-1}\}$, sufficient statistic for $\beta$
  - $\hat\beta$ independent $S^2$, by idempotency
  - $\frac{n-p}{\sigma^2}S^2\sim\chi_{n-p}^2$
- confidence intervals : linear combination $c^\top\hat\beta\sim N_1(c^\top\beta,\sigma^2 c^\top(X^\top X)^{-1}c)=N_1(c^\top\beta,\sigma^2\delta)$
  - $Q=(c^\top\hat\beta -c^\top\beta)/(\sigma\sqrt{\delta})\sim N_1(0,1)$ with $Q^2\sim\chi_1^2$ independent of $S^2$
  - $\frac{n-p}{\sigma^2}S^2\sim \chi_{n-p}^2$
  - $\frac{Q^2 / 1}{\frac{n-p}{\sigma^2}S^2/(n-p)}=(\frac{c^\top\hat\beta -c^\top\beta}{\sqrt{S^2 c^\top(X^\top X)^{-1}c}})^2\sim F_{1,n-p}$
  - for real $W$, $W^2\sim F_{1,n-p}\iff W\sim t_{n-p}$
  - 100$(1-\alpha)$% CI : $c^\top\hat\beta\pm t_{n-p}(\alpha/2)\sqrt{S^2c^\top(X^\top X)^{-1}c}$
  - $r$th coordinate : $\beta_r=c_r^\top\beta$ with $c_r=1$ only at $r$th position, $\hat\beta_r\pm t_{\alpha/2}\sqrt{S^2v_{rr}}$ with $v_{r,s}$ $r$, $s$ element of $(X^\top X)^{-1}$ 
- prediction intervals : confidence bounds on potential response, $Y_+=x_+^\top\hat\beta+\epsilon_+$
  - base : $\frac{x_+^\top\hat\beta-Y_+}{\sqrt{S^2\{1+x_+^\top(X^\top X)^{-1}x_+\}}}\sim t_{n-p}$
  - CI : $x_+^\top\hat\beta\pm t_{n-p}(\alpha/2)\sqrt{S^2\{1+x_+^\top(X^\top X)^{-1}x_+\}}$
- coefficient of determiniation 
  - measure of fit, $R^2_0=\frac{\norm{\hat Y}^2}{\norm{Y}^2}$, more natural
  - centred : empirical variance $R^2=\frac{\sum_{i=1}^n \hat Y_i^2 - n\bar Y^2}{\sum_{i=1}^n Y_i^2-n\bar Y^2}=\frac{\norm{\hat Y}^2-\norm{\bar Y 1}^2}{\norm{Y}^2-\norm{\bar Y 1}^2}=\frac{\norm{(I-1(1^\top 1)^{-1})\hat Y}^2}{\norm{(I-1(1^\top 1)^{-1} 1)Y}^2}$, statistically more relevant
  - adjusted $R^2​$ : take into account number of variable, $R^2_a=1-(1-R^2)\frac{n-1}{n-p}​$
  - centred adjusted : $R_{0a}^2=1-(1-R_0^2)\frac{n}{n-p}$
- unbiasedness under moment assumptions : assume only $E[\epsilon]=0$, $var[\epsilon]=\sigma^2 I$ instead of $\epsilon\sim N(0,\sigma^2 I)$ following remains true
  - $E[\hat\beta]=\beta$
  - $cov[\hat\beta]=\sigma^2(X^\top X)^{-1}$
  - $E[S^2]=\sigma^2$
- Gauss-Markov : $Y_{n\times 1}=X_{n\times p}\beta_{p\times 1}+\epsilon_{n\times 1}$ with $p<n$, $E[\epsilon]=0$, $cov[\epsilon]=\sigma^2 I$, implies $\hat\beta =(X^\top X)^{-1}X^\top Y$ best linear unbiased estimator of $\beta$, only for unbiased estimator
- large sample distribution of $\hat\beta$ : $Y_n=X_n\beta+\epsilon_n$, $X_n$ full rank $p$, $\max_{1\le i\le n}[x^\top_i(X_n^\top X_n)^{-1} x_i]\overset{n\to\infty}\to 0$, $E[\epsilon_n]=0$, $cov[\epsilon_n]=\sigma^2 I_{n\times n}$ implies $\hat\beta_n=(X_n^\top X_n)^{-1}X_n^\top Y_n$ satisfies $(X_n^\top X_n)^{1/2}(\hat\beta_n -\beta)\overset{d}\to N_p(0,\sigma^2 I_{p\times p})$
- assumptions : if one fail, gaussian linear regression inappropriate
  - linearity : $E[Y]$ is linear in $X$
  - homoskedasticity : same spread, $var[\epsilon_j]=\sigma^2$
  - gaussian distribution : errors normally distributed
  - independent errors
  - isolated problemes : might affect or not model validity
    - outliers
    - influential observations
  - cannot prove assumption : can only provide evidence in favour or against
- correct model : $e\sim N(0,\sigma^2(I-H))$, residuals ancillary
- standardised (studentized) residuals : $r_i=\frac{e_i}{s\sqrt{1-h_{ii}}}$ as residual correlated and unequal variances, reduce variance to $1$
- checking for linearity : no correlation should appear between explanatory variables and residuals, by linearity $X^\top e=0$
  - plot standardised residuals $r$ against each covariate : no systematic patterns should appear
  - plot standardised residuals $r$ against covariates left out of model : no systematic patterns should appear
- checking for homoskedasticity : plot $r$ againt fitted values $\hat Y$, random scatter should appear with approximately constant spread, check also for linearity
- checking for normality : compare empirical vs theoretical quantiles
  - theoretical $\alpha$-quantile : $F^-(\alpha)=\inf\{t\in\R:F(t)\ge\alpha\}$
  - empirical $\alpha$-quantile : $\hat F^-(\alpha)=\inf\{t\in\R :\hat F(t)\ge\alpha\}=\inf\{t\in\R :\frac{\#\{W_i\le t\}}{n}\ge\alpha\}$
  - quantile plot : plot ordered empirical quantile against theoretical $N(0,1)$, expect points to fall close to 45° line (outliers, skewness, heavy tails easily revealed)
  - empirical quantiles of unstandardardised residuals : compare against line with slope of $stdev(e)$ and intercept $0$
- check for independence : difficulte, clustering might suggest dependence (identify groups of related individual), when time-ordered look at correlation $corr[r_t,r_{t+k}]$ or partial correlation $corr[r_t,r_{t+k}\mid r_{t+1},\ldots,r_{t+k-1}]$
- identifying influential observation : possibly affect
  - outlier : faillaing far from surrounding, visually checked by regression scatter plot or residual plots
  - leverage point $h_{jj}$ : unusual values in $x$-dimension, $var(Y_j-\hat Y_j)=var(e_j)=\sigma^2(1-h_{jj})$
    - $h_{jj}\approx 1$ implies model constrained so $\hat Y_j=x_j^\top\hat\beta\approx Y_j$, need separate parameter entirely devoted to fit this observation
    - since $trace(H)=\sum_{j=1}^n h_{jj}=p$ : cannot have low leverage for all cases, balanced design corresponds to $h_{jj}\approx p/n$ for all $j$
    - rule of thumb : $h_{jj}> 2p/n$ need further scrutiny, fitting again without $j$ and study
  - cook's distance : $C_j=\frac{1}{ps^2}(\hat Y-\hat Y_{-j})^\top(\hat Y-\hat Y_{-j})=\frac{r^2_j h_{jj}}{p(1-h_{jj})}$, measure scaled distance between $\hat Y$ and $\hat Y_{-j}$ with $j$ dropped
    - rule of thumb : $C_j > 8/(n-2p)$
    - plot $C_j$ against index and compare with $8/(n-2p)$ level
- residual sums of squares : $RSS(\hat\beta)=\norm{e}^2$
- comparing nested models : $Y=X\beta+\epsilon=(X_1\; X_2)(\beta_1\; \beta_2)+\epsilon=X_1\beta_1+X_2\beta_2+\epsilon$
  - pythagoras : $\norm{Y-\hat Y_1}^2=RSS(\hat\beta_1)=\norm{e_1}^2=\norm{Y-\hat Y}^2+\norm{\hat Y-\hat Y_1}^2=RSS(\hat\beta)+(RSS(\hat\beta_1)-RSS(\hat\beta))$
  - likelihood ratio test statistic : $(RSS(\hat\beta_1)-RSS(\hat\beta))/RSS(\hat\beta)$
- sampling distribution for sums of squares
  - $e-e_1\bot e$
  - $\norm{e}^2=RSS(\hat\beta)$ and $\norm{e_1-e}^2=RSS(\hat\beta_1)-RSS(\hat\beta)$ independent
  - $\norm{e}^2\sim\sigma^2\chi_{n-p}^2$
  - under hypothesis $H_0:\beta_2=0$, $\norm{e_1-e}^2\sim\sigma^2\chi_{p-q}^2$ 
    - test statistic : $T=\frac{(RSS(\hat\beta_1)-RSS(\hat\beta))/(p-q)}{RSS(\hat\beta)/(n-p)}\sim F_{p-q,n-p}$
    - reject $H_0$ if $p\le \alpha$ : $p=P_{H_0}[T(Y)\ge\tau]=P[F_{p-q,n-p}\ge\tau]$ for $T=\tau$
- analysis of variance : groups of columns s.t. $X=(1\; X_1\cdots X_r)$ of size $1\times 1, 1\times q_1,\ldots, 1\times q_r$, $\beta=(\beta_0\;\beta_1\cdots\beta_r)$ of size $n\times 1,n\times q_1,\ldots,n\times q_r$, 
  - proceed as before $\norm{e_0}^2=\norm{e_r}^2+\sum_{k=0}^{r-1}\norm{e_{k+1}-e_k}^2=RSS_r+\sum_{k=0}^{r-1}(RSS_k-RSS_{k+1})$ with $RSS_k$ for $\hat Y_k$ with $v_k$ degree of freedom
  - $F$-statistic : $F_k=\frac{(RSS_{k-1}-RSS_k) / (v_{k-1}-v_k)}{RSS_r/v_r}\sim F_{v_{k-1}-v_k,v_r}$
  - anova table
  - significance : order dependent unless orthogonal terms
  - in pratice : most appropriate subset of columns, parsimony (sparingness, simplicity and least number of requisites and assumptions, frugality)
- automatic model selection : $X$ with $p$ variables, $2^p$ possibilities
  - true model : contains only columns for which $\beta_r\not =0$
  - correct model : true model plus extra columns
  - wrong model : does not contain all columns of true model
  - expected prediction error : $f^*=\arg\min_{f\in 2^X}\frac{1}{n}E\{\norm{Y_+-\hat Y(f)}^2\}=\arg\min\Delta(f)$ with $\hat Y$ fitted values, new independent responses $Y_+$ same setup
    - train-test split : $\hat\Delta=(n')^{-1}\norm{Y'-X'\hat\beta^*}^2$ with $X^*$ train, $X'$ test
    - leave-one-out cross validation : $n\hat\Delta_{CV}=CV=\sum_{j=1}^n (Y_j-x_j^\top\hat\beta_{-j})^2=\sum_{j=1}^n\frac{(Y_j-x_j^\top\hat\beta)^2}{(1-h_{jj})^2}$ by perturbation theory
    - stable CV : generalised $GCV=\sum_{j=1}^n\frac{(Y_i-x_j^\top\hat\beta)^2}{(1-trace(H)/n)^2}$ with $E[GCV]\approx n\Delta$
  - Akaike information critera : minimise information distance, estimated by $AIC=-2\hat l+2p$ ( $\equiv n\log\hat\sigma^2+2p$ in linear model) with $\hat l$ maximised log likelihood for given model, tend to choose too complicated models
    - improved/corrected verson : $AIC_c=AIC+\frac{2p(p+1)}{n-p-1}$ for regression
    - Bayes' information criterion : $BIC=-2\hat l+p\log n$ model selection consistent
    - mallows : $C_p=\frac{SS_p}{s^2}+2p-n$ with $SS_p$ is RSS for fitted model and $s^2$ estimate $\sigma^2$ under full model
- automatic model building : little theoretical basis, lack objective function
  - forward selection : start from model with constant only, add each term separately, if none significant stop otherwise update model with most significant new term
  - backward selection : start from model with all terms, if all terms significant, stop otherwise update model dropping term with smallest $F$-statistic
  - stepwise : consider three options (add term, delete term, swap term), choose most significant option, if model unchanged stop otherwise repeat
- danger of big model : adding more variables enlarges $\mathcal M(X)$
- multicollinearity : when $p$ covariates concentrate around subspace of dimension $q<p$ (simplest case, correlated pairs of variables), $det[(X^\top X)^{-1}]\approx 0$ (almost not invertible)
  - causes : poor design or inherent relationships
  - results : huge variances of estimator (flip signs for different data), individual coefficient insignificant (t-test $p$-values inflated)
  - diagnosing : scatterplots, correlation matrix
  - variance inflation factors : $VIF_j=\frac{var(\hat\beta_j)\norm{X_j}^2}{\sigma^2}=\norm{X_j}^2[(X^\top X)^{-1}]_{jj}=\frac{1}{1-R^2_j}$ with $R_j^2=\frac{\norm{X_{-j}(X^\top_{-j}X_{-j} )^{-1} X^\top_{-j}X_{-j}}^2}{\norm{X_j}^2}$ coefficient of determination for regression of $X_j$ on $\{X_1,\ldots,X_{j-1},X_{j+1},\ldots, X_p\}$, large value indicated linear dependence (rule of thumb $VIF_j>5$ or $10$)
  - spectral : $X^\top X=U\Lambda U^\top$ with $\Lambda =diag\{\lambda_1,\ldots,\lambda_p\}$, $rank(X^\top X)=\#\{j:\lambda_j\not = 0\}$ and $det(X^\top X)=\Pi_{j=1}^p\lambda_j$
    - condition index : $CI_j(X^\top X)=\sqrt{\lambda_{max}/\lambda_j}$, small $\lambda_j$ mean almost reduced rank revealing effect of collinearity
    - condition number : $CN(X^\top X)=\sqrt{\lambda_{max}/\lambda_{min}}$, global instability, rule of thumb $CN>30$ moderate collinearity, $CN>100$ severe
  - remedies : redesign, variable deletion, choose orthogonal basis for $\mathcal M(X)$ (loose interpretability, prediction ok), introduce bias
- standardise design matrix : $X=(1\; W)$, $\beta=(\beta_0\;\gamma)^\top$
  - recentre/rescale : $Z_j=\frac{1}{\sqrt{n} sd(W_j)}(W_j-1\bar W_j)$
  - $\beta_j$ interpretation : not mean impact on response per unit change of explanatory variable but per unit deviation of explanatory variable from its mean
  - estimate $\beta_0$ and $\gamma$ by different regression : $Z=V\Lambda U^\top$
    - least-square estimator : $\hat\beta_0=\bar Y$, $\hat\gamma =(Z^\top Z)^{-1}Z^\top Y$
      - $\hat\gamma=\sum_{j=1}^q\frac{1}{\lambda_j}(V_j^\top Y)U_j$
    - ridge regression : replace $Z^\top Z$ by $Z^\top Z+\lambda I_{p\times p}$, $\hat\beta_0=\bar Y$, $\hat\gamma=(Z^\top Z+\lambda I)^{-1}Z^\top Y$ with ridge parameter $\lambda$ stabilizing, minimize $\norm{Y-\beta 1 - Z\gamma}^2_2+\lambda\norm{\gamma}_2^2$ (unique minimiser)
      - $\hat\gamma=\sum_{j=1}^q\frac{\lambda_j}{\lambda_j^2+\lambda_j}(V_j^\top Y)U_j$, reduce size of $1/\lambda_j$
      - $bias(\hat\gamma,\gamma)=-\lambda(Z^\top Z+\lambda I_{q\times q})^{-1}\gamma$
      - $cov(\hat\gamma)=\sigma^2(Z^\top Z+\lambda I)^{-1}Z^\top Z(Z^\top Z+\lambda I)^{-1}$
- domination over least square : $\tilde\gamma$ LST and $\hat\gamma_\lambda$ ridge, $E\{(\tilde\gamma -\gamma)(\tilde \gamma-\gamma)^\top\}-E\{(\hat\gamma_\lambda-\gamma)(\hat\gamma_\lambda-\gamma)^\top\}\succeq 0$ for $\lambda\in(0,2\sigma^2/\norm{\gamma}^2)$, bit of bias can reduce variance
  - increase $\lambda$ : decrease variance (collinearity) but increase bias
  - descreae $\lambda$ : decrease bias but variance inflated if collinearity exists
  - $trace(cov(\hat\gamma))=\sum_{j=1}^q\frac{\lambda_i}{\lambda_i^2+\lambda}\sigma^2$
- least absolute shrinkage and selection operator LASSO : minimising $\norm{Y-\beta_0 1-Z\gamma}_2^2+\lambda\norm{\gamma}_1$, non-linear in $Y$, no explicit form (needs quadratic programming)
  - orthogonal design : model selection via thresholding
  - unique solution : $\hat\beta_0=\bar Y$, $\tilde\gamma_i=sng(\hat\gamma_i)(\abs{\hat\gamma_i}-\frac{\lambda}{2})$ for $i=1,\ldots,p-1$ with $\hat\gamma$ LSE
  - intuition : $L_1$ norm induces sharp balls
- $L_0$ norm : best subsets selection, $\norm{\gamma}_0=\sum_{j=1}^{p-1}\abs{\gamma_j}^0=\#\{j:\gamma_j\not = 0\}$

### Generalised linear models

- generalised linear models GLM : regression with exponential family responses
  - response vector : $Y$ independent entries with joint law
  - natural parameter : $\phi\in\Phi\subseteq\R^n$ varies a function of covariates $\phi=X_n\beta$ 
  - $f(y)=\Pi_{i=1}^n\exp\{\phi_i y_i-\gamma(\phi_i)+S(y_i)\}=\exp\{\phi^\top y-\sum_{i=1}^n\gamma(\phi_i)+\sum_{i=1}^n S(y_i)\}$
  - main GLM of interest : Gaussian, Bernouilli, Poisson ($\gamma$ invertible for all three)
  - sampling theory results
    - $\mu_i=E[Y_i]=\frac{\partial}{\partial\phi_i}\gamma(\phi_i)$
    - $var[Y_i]=\frac{\partial^2}{\partial\phi_i^2}\gamma(\phi_i)$ or if $\gamma$ invertible $var[Y_i]=\gamma''(\gamma'^{-1}(\mu_i))=V(\mu_i)$
  - link function : $\phi_i=g(\mu_i)=x_i^\top\beta$
    - inverse link function : $h=g^{-1}$
    - natural link function : $g=\gamma'^{-1}$, focus on it from now on
- loglikelihood : $l_n(\beta)=\beta^\top X_n^\top Y-\sum_{i=1}^n\gamma(x_i^\top\beta)$
  - score function $\nabla_\beta l_n(\beta)=X_n^\top(Y-\mu)$
  - covariance equaling information matrix : $cov(\nabla_\beta l_n(\beta))=X_n^\top V(\beta) X_n=-\nabla_\beta^2 l_n(\beta)=\I_n(\beta)$
  - adjusted response : $\tilde Z=X_n^\top\tilde\beta+V^{-1}(\tilde\beta)(Y-\mu(\tilde\beta))$ with guess $\tilde\beta$ near $\hat\beta$
  - weighted least squares estimate : $\hat\beta\approx (X_n^\top V^{-1}(\tilde\beta) X_n)^{-1}X_n^\top V(\tilde \beta)\tilde Z$
- iteratively reweighted least squares IRLS : equivalent to Newton-Raphson iteration, not guaranteed to converge
  - initialize : $x_i^\top\beta^{(0)}=\gamma'^{-1}(Y_i)$ and $Z_i^{(0)}=x_i^\top\beta^{(0)}+\frac{(Y_i-\gamma'(x_i^\top\beta^{(0)}))}{\gamma''(x_i^\top\beta^{(0)})}$
  - update : $\beta^{(j+1)}=(X_n^\top V^{-1}(\beta^{(j)} X_n)^{-1}X_n^\top V(\beta^{(j)})Z^{(j)})$
- approximate sampling distribution of MLE : suppose started iteration at true $\beta$, stopped at $\hat\beta=(X_n^\top V^{-1}(\beta)X_n)^{-1}X_n^\top V(\beta) Z$
  - $Z_i=x_i^\top\beta+\frac{1}{\gamma''(x_i^\top\beta)}(Y_i-\gamma'(x_i^\top\beta))$ so $Z=X_n^\top\beta+V^{(-1)}(\beta)(Y-\mu(\beta))$
  - $\hat\beta=\beta+(X_n^\top V^{-1}(\beta)X_n)^{-1}X_n^\top(Y-\mu(\beta))$
  - $E[\hat\beta]=\beta$ and $cov(\hat\beta)=(X_n^\top V^{-1}(\beta) X_n)^{(-1)}=\I_n^{-1}(\beta)$
  - asymptotic normality of MLE : as $n\to\infty$, provided it exists, MLE $\hat\beta_n$ of $\beta_0$ unique and satisfies $\I_n^{1/2}(\beta_0)(\hat\beta_n-\beta_0)\overset{d}{\to} N(0,I_{p\times p})$ for following
    - $\beta\in B$ open convex subset of $\R^p$
    - $p\times p$ matrix $X_n^\top X_n$ full rank for all $n$
    - information diverges : $\lambda_{min}(\I_n(\beta))\overset{n\to\infty}\to\infty$ for smallest eigenvalue
    - any parameter $\beta\in \R^p$, $\sup_{\alpha\in N_\delta(\beta)}\norm{\I_n^{-1/2}(\beta)\I_n^{1/2}(\alpha)-I_{p\times p}}\to0$ where $N_\delta(\beta)=\{\alpha\in\R^p:(\alpha-\beta)^\top\I_n(\beta)(\alpha-\beta)\le\delta\}$ for $\delta >0$
    - under canonical link : $\I_n(\beta)=X_n^\top V(\beta)X_n$
    - can be read : $\hat\beta_n\overset{d}{\approx} N(\beta,\I_n^{-1}(\beta))$
    - implies : $(\hat\beta_n-\beta)^\top\I_n(\beta)(\hat\beta-\beta)\overset{d}\to\chi_p^2$
- goodness of fit
  - staturated model : #parameters = #observations
  - staturated loglikelihood : $l_n(\eta)=\eta^\top Y+\sum_{i=1}^n\gamma(\eta_i)$ (replace $x_i^\top\beta$ by $\eta_i$)
  - scaled deviance : $D=2(l_n(\hat\eta)-l_n(\hat\beta))=2((\hat\eta-X_n\hat\beta)^\top Y+\sum_{i=1}^n(\gamma(\hat\eta_i)-\gamma(x_i^\top\hat\beta)))\ge 0$, small good fit, sums of squares for gaussian
  - nested model : $\hat\beta^A$ with $p$ free parameters, $\hat\beta^B$ nested for $q<p$ free parameters and $p-q$ fixed ones
    - likelihood ratio test : $2(l_n(\hat\beta^A)-l_n(\hat\beta^B))=D_B-D_A\overset{d}\to\chi_{p-q}^2$ when B correct
- diagnostics : use sums of square and final iterate of IWLS
  - leverage : $h_{jj}$ $j$th diagonal element of $H=V^{1/2}(\hat\beta)X_n(X_n^\top V(\hat\beta)X_n)^{-1}X_n^\top V^{1/2}(\hat\beta)$
  - cook statistic : change in deviance, $2p^{-1}\{l(\hat\beta)-l(\hat\beta_{-j})\}$, approximated by $C_j=\frac{h_{jj}}{p(1-h_{jj})}r^2_{P_j}$ with $r_{P_j}$ standardised Pearson residual
  - deviance residual : $d_j=sgn(\hat\eta_j-x_i^\top\hat\beta_j)[2l_j(\hat\eta)-2 l_j(\hat\beta)]^{1/2}$ with $\sum_{j=1}^n d_j^2=D$
  - peason residual : $p_j=\frac{Y_i-\gamma'(x_i^\top\hat\beta)}{\sqrt{\gamma''(x_i^\top\hat\beta)}}=\frac{Y_i-\hat\mu_i}{\sqrt{V(\hat\mu_i)}}$ so $r_P=V^{-1/2}(\hat\beta)(Y-\mu(\hat\beta))$
  - standardised versions : $r_{Dj}=\frac{d_j}{(1-h_{jj})^{1/2}}$ and $r_{Pj}=\frac{p_j}{(1-h_{jj})^{1/2}}$
- link function : choice of link is choice of error distribution $F_\epsilon$
  - distribution $F_\epsilon(u)$ : link function $g(\pi)$
  - logisitc $e^u/(1+e^u)$ : logit $\log(\pi/(1-\pi))$, symmetric, nice interpretation
  - normal $\Phi(u)$ : probit $\Phi^{-1}(\pi)$, symmetric
  - log weibull $1-\exp(-\exp(u))$ : log-log $-\log(-\log(\pi))$, asymmetric
  - gumbel $\exp(-\exp(-u))$ : complementary log-log $\log(-\log(1-\pi))$, asymmetric


- binomial GLM : $R_j\mid x_j\ind\exp[m_j\{\frac{r}{m_j}\log(\frac{\pi_j}{1-\pi_j})+\log(1-\pi_j)\}+\log{m_j\choose r}]$ with $\sum_j m_j=N$, $m_j=\abs{M_j}$ and $g(\pi_i)=x_i^\top\beta$, $M$'s called covariate classes
- logistic regression for binary data : bernouilli GLM with natural link $g(\pi_i)=\log(\frac{\pi_i}{1-\pi_i})=x_i^\top\beta$
- sparseness : covariate classes $\{M_j\}^n_{j=1}$ small ($n$ of order $N$)
  - affect : interpretability of deviance
  - rule of thumb : sparseness when $m_k\le 5$ for several classes
  - solution : grouping data
- jittered quantile residuals : for binary responses
  - continuous : $\hat U=F(Y\mid\hat\t)\overset{d}\approx Unif(0,1)$ if $\hat\t\approx\t$, $R_i=\Phi^{-1}(F(Y_i;\hat\t))\overset{d}\approx N(0,1)$
  - discrete : $\hat U_i^{(1)}\sim Unif(0,\hat\pi_i)$, $\hat U_i^{(2)}\sim Unif(\hat\pi_i, 1)$, $\Phi^{-1}(\hat U_i^{(1)}Y_i+\hat U_i^{(2)}(1-Y_i))\overset{d}\approx N(0,1)$
- complete separation : logistic regression MLE does not exist if there exist hyperplane that perfectly separate, $\sup_{\beta\R^p}L(\beta)=1$, IWLS fail to converge, standard errors blow up
  - remedies : keep track of likelihood and parameters values while iterating
  - regularised logistic regression : add penalty, standardized data, $\sum_{i=1}^n Y_i(\gamma_0+x_i^\top\gamma)-\log(1+\exp(\gamma_0+x_i^\top\gamma))+\lambda\norm{\gamma}_q^2$
- overlapping regime : full rank and intercept term, MLE exist uniquely iff covariate overlap
- 2x2 contingency tables : special case of Bernouilli/Binomial
  - independent individuals, $m_0$ and $m_1$ persons
  - $\pi_0=\frac{e^\lambda}{1+e^\lambda}$ and $\pi_1=\frac{e^{\lambda+\psi}}{1+e^{\lambda+\psi}}$
  - likelihood : $\L(\psi,\lambda)\propto\frac{e^{r_0+r_1}\lambda+r_1\psi}{(1+e^{\lambda+\psi})^{m_1}(1+e^\lambda)^{m_0}}$
  - does treatment affect success probability : $\pi_1\overset{?}=\pi_0$
  - log odds : $\psi=\log\frac{\pi_1}{1-\pi_1}-\log\frac{\pi_0}{1-\pi_0}$
  - simpson paradox : often inapproprate marginalisation
- loglinear regression for count data : poisson GLM with natural link $g(\mu_i)=\log\mu_i=x_i^\top\beta$
  - flavors 
    - unconstrained responses $Y_i\ind Poisson(\mu_i)$
    - constrained responses $(Y_1,\ldots,Y_d)$ subject to $\sum_{j=1}^d Y_j=m$ having multinomial distribution with probability $(\pi_1,\ldots,\pi_d)$ and denominator $m$
    - constrained responses $(Y_1,\ldots,Y_d)$ subject to $\sum_{j\in I_k} Y_j=m_k$ for disjoint partition sets having product multinomial
  - conditional distribution of $(Y_1,\ldots, Y_n)$ given $\sum_{k=1}^d Y_i=m$ : with poisson iid with means $\mu_1,\ldots,\mu_d$ correspond to multinomial with denominator $m$ and probabilities $\pi_i=\mu_i/\sum_j\mu_j$
  - count events : up to time $T_i$ (offset term), $E[Y_i]=\mu_i=\lambda_iT_i$, in this case $g(\mu_i)=\log\mu_i=x_i^\top\beta+\log T_i$
  - more general contingency tables
    - poisson : just collect data, arrange into table, poisson distribution foreach cell
    - multinomial : keep collecting until $m$ reached, multinomial distribution for table entries
    - product multinomial : fix row totals, treat row categories as independent, independent multinomial for tables entries of each row
    - multinomial loglikelihood : $l_{Mult}(\beta;y\mid \sum_c Y_{rc}=m_r)=\sum_{r,c} Y_{rc}\log\pi_{rc}=\sum_r(\sum_c Y_{rc}x_{rc}^\top\beta-m_r\log(\sum_c \exp(x_{rc}^\top\beta)))$
    - unconstrained loglikelihood : $l_{Poisson}(\beta,\gamma)=\sum_{rc} Y_{rc}\log\mu_{rc}-\mu_{rc}=\sum_r(M_r\gamma_r+\sum_c Y_{rc}x_{rc}^\top\beta-\exp^{\gamma_r}\sum_c \exp(x_{rc}^\top\beta))$ with $M_R=\sum_c Y_{rc}$
      - alternative $l_{Poisson}(\beta,\tau)=(\sum_r M_r\log\tau_r-\tau_r)+\sum_r(\sum_c Y_{rc}X_{rc}^\top\beta-M_r\log(\sum_c\exp(X_{rc}^\top\beta)))$ with $\tau_r=\sum_c\mu_{rc}=e^{\gamma_r}\sum_c e^{X_{rc}^\top\beta}=E[M_r]$ and $\gamma_r=\log\tau_r-\log(\sum_c\exp(x_{rc}^\top\beta))$
  - $\beta$ : estimate using either loglinear or logistic model
  - Bayes : $l_{Poisson}(\beta,\tau)=l_{Poisson}(\tau; m)+l_{Mult}(\beta;Y\mid M=m)$, hence inference on $\beta$ using multinomial equvalent to poisson provided $\gamma_r$ included
- perfect separation : also affect multinomial regression, MLE for a perfect class fail to exist, can penalise or watch for parameters/likelihood convergence

### Nonparametrics regression and regularisation

- more flexible dependence : $Y_i\mid x_i^\top\ind Dist[\phi_i]\to\cases{\phi_i=g(x_i^\top)\\ g\in F\subset L^2(\R^p)}$ with $g:\R^p\to\R$ unknown
- kernel smoothing : $\hat g(x_0)=\frac{1}{\sum_{i=1}^n K(\frac{x_i-x_0}{\lambda})}\sum_{i=1}^n  Y_i K(\frac{x_i-x_0}{\lambda})=\frac{1}{\sum_{i=1}^n w_i}\sum_{i=1}^n w_i Y_i$ with bandwidth $\lambda$ and $K$ kernel (standard gaussian $K(x)=\varphi(x)$)
- natrual cubic spline : unique explicit solution to MLE
  - MLE : $\sum_{i=1}^n(Y_i-h(x_i))^2+\lambda\int_I h''(t)^2 dt=fit+roughness$
  - piecewise polynomials of degree 3
  - basis function : $B_j$ as $s(x)=\sum_{j=1}^n\gamma_j B_j(x)$
  - penalized likelihood : $\min (Y-B\gamma)^\top(Y-B\gamma)+\lambda\gamma^\top\Omega\gamma$ with $B_{ij}=B_j(x_i)$ and $\Omega_{ij}=\int B_i''(x)B_j''(x)dx$
  - smoothing matrix : $S_\lambda=B(B^\top B+\lambda\Omega)^{-1}B^\top$
    - $trace(S_\lambda)$ : monotone decreasing, $trace(S_\lambda)\overset{\lambda\to\infty}\to 2$, $trace(S_\lambda)\overset{\lambda\to 0}\to n$
  - equivalent degree of freedom of smoother : $edf=trace(S_\lambda)$, easy interpretation of roughness
  - bias/variance : $E(\norm{g-\hat g}^2)=\frac{trace(S_\lambda S_\lambda^\top)}{n}\sigma^2+\frac{(g-S_\lambda g)^\top(g-S_\lambda g)}{n}$
  - cross validation : $CV(\lambda)=\sum_{j=1}^n(Y_j-\hat Y_j^-)^2=\sum_{j=1}^n(\frac{Y_j-\hat Y_j}{1-S_{jj}(\lambda)})^2$ with $S_{jj}(\lambda)$ $j,j$ element of $S_\lambda$
  - generalised cross-validation : $GCV=\sum_{j=1}^n(\frac{Y_j-\hat Y_j}{1-trace(S_\lambda)/n)})^2$
- orthogonal series : parametrising the problem
  - Hilbert space : $g(x)=\sum_{k\in\mathcal Z}\beta_k\psi_k(x)$
  - Fourier series expansion : $\beta_k=\frac{1}{2\pi}\int_{-\pi}^\pi g(x)e^{-ikx}dx$
  - truncate series : reduce to linear regression, $Y_i=\sum_{\abs{k}<\tau}\beta_k\psi_k(x_i)+\epsilon_i$ 
  - Dirichlet kernel : $D_\tau(u)=\sin((\tau+1/2)u)/\sin(u/2)$
  - kernel smoothing : $\hat g(x_0)=\frac{1}{c}\int_I y(x)K_\lambda(x-x_0)dx$
- curse of dimensionality : neighbourhoods with fixed number of points become less local as dimension increase
- multidimensionality : fitted/interpreted variable-by-variable else curse of dimensionality too strong
  - additive model : $Y_i=\alpha_i+\sum_{k=1}^p f_k(x_{ik})+\epsilon_i$ with $f_k$ univariate smooth function
  - generalised additive model : $Y_i\mid x_i^\top\ind \exp\{\alpha_i y+y\sum_{k=1}^p f_k(x_{ik})-\gamma(\alpha_i+\sum_{k=1}^p f_k(x_{ik}))+S(y)\}$
  - backfitting algorithm : know how to fit each $f_k$ individually well, take advantage
    - initialise : $\alpha=\bar Y$, $f_k=f_k^0$
    - cycle : get $f_k$ by 1D smoothing of partial residual scatterplot, $\{(Y_i-\alpha-\sum_{m\not =k} f_m(x_{im}), x_{ik})\}^n_{i=1}=\{e_{ik},x_{ik}\}^n_{i=1}$ 
  - projection pursuit regression : additively decompose $g$ into smooth functions $h_k:\R\to\R$, projection directions to be chosen for best fit, each $h_k$ is ridge function of $x_i^\top$
    - likelihood : $\min_{h_1\in C^2[0,1],\norm{\beta}=1}\{\sum_{i=1}^n(Y_i-h_1(x_i^\top\beta))^2+\int_0^1(h_1''(t))^2dt\}$
    - smooth : given direction $\beta$, fitting $h_1(x_i^\top\beta)$ 1D
    - pursue : given $h_1$, have non-linear regression problem w.r.t. $\beta$
- nonlinear sigmoidal approximation : $\Psi:\R\to[0,1]$ strictly increasing distribution, $g:[0,1]^p\to\R$ continuous, $\sup_{x\in[0,1]^d}\abs{g(x)-\sum_{k=1}^K\alpha_k\Psi(t_k+x^\top\beta_k)}<\epsilon$ for $\epsilon >0$ and $K<\infty$, neural network layer
  - derived covariates : $w_k(x^\top)\approx\sum_{m=1}^{M_j}\delta_{m,j}\Psi(s_{m,j}+x^\top\gamma_{m,j})$, learn transformation
  - nonlinear : $Y_i=\sum_{k=1}^K\alpha_k\Psi(t_k+(w_i(x_1^\top),\ldots,w_i(x_n^\top))\beta_k)+\epsilon_i$









