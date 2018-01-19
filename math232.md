$$
\displaystyle
\def\card{\mathrm{card}\:}
\def\N{\mathcal N}
\def\abs#1{\left\lvert#1\right\rvert}
\def\or{\;\text{or}\;}
\def\and{\;\text{and}\;}
\def\st{\;\text{such that}\;}
\def\cases#1{\begin{cases}#1\end{cases}}
\def\if{\text{if}}
\def\F{\mathcal F}
\def\indep{\bot\!\!\bot\,}
\def\R{\mathbb R}
\def\d{\;\mathrm{d}}
\def\m#1{\begin{pmatrix}#1\end{pmatrix}}
\def\iid{\stackrel{\text{iid}}{\sim}}
\def\av#1{\overline{#1}}
\def\esti{\tilde{\theta}}
$$

# MATH232

> [GNU General Public License v3.0](https://github.com/zifeo/EPFL/blob/master/LICENSE) licensed. Source available on [github.com/zifeo/EPFL](https://github.com/zifeo/EPFL).

Spring 2015: Probabilities & statistics

[TOC]

## Probabilities

### Sets

- unordered set : $A=\{x_1,\ldots,x_n\}$
- ordered set : $A=(1,2,\ldots)$ but $(1,2)\not = (2,1)$
- subset : $A\subset B$
- universe : $\Omega$
- cardinalité : $\card A=\#A=\abs{A}$ with $\abs\emptyset=0$
- union : $A\cup B=\{x\in\Omega : x\in A\or x\in B\}$
- intersection : $A\cap B=\{x\in\Omega : x\in A\and x\in B\}$
- complement : $A^c=\{x\in\Omega : x\not\in A\}$
- difference : $A\setminus B=A\cap B^c=\{x\in\Omega : x\in A\and x\not\in B\}$
- symmetric difference : $A\Delta B=(A\setminus B)\cup(B\setminus A)$
- boolean operations : distributivity, Morgan's law
- **partition** : $A_j$ such that $A_1\cup\cdots\cup A_n=\Omega$ and $A_i\cap A_j =\emptyset$ for $i\not = j$
- cartesian product : $A\times B=\{(a,b) : a\in A\and b\in B\}$ with $A^n=A_1\times\cdots\times A_n$

### Combinatorics

- multiplication : $\abs{A_1\times\cdots\times A_n}=\abs{A_1}\times\cdots\times\abs{A_n}$
- addition : $\abs{A_1\cup\cdots\cup A_n}=\abs{A_1}\cup\cdots\cup\abs{A_n}$ if $A_j$ disjoint
- **permutation** (ordered selection) : given $n$ distinct object, the number of different permutations (without repetition) of length $r\le n$ is $n!/(n-r)!$
- multinomial coefficient : ${n \choose {n_1,\ldots,n_r}}=\frac{n!}{n_1!\cdots n_r!}$
- **binomial** coefficient : ${n \choose k}=C^k_n=\frac{n!}{k!(n-k)!}$
  - symmetric : ${n\choose r}={n\choose n-r}$ 
  - Pascal's triangle : ${n+1\choose r}={n\choose r-1}+{n\choose r}$ 
  - Vandermonde's formula : $\sum^r_{j=0}{m\choose j}{n\choose r-j}={m+n\choose r}$ 
  - Newton's binomial theorem : $(a+b)^n=\sum_{r=0}^n{n\choose r}a^rb^{n-r}$ 
  - negative binomial series : $(1-x)^{-n}=\sum^\infty_{j=0}{n+j-1\choose j}x^j$ for $\abs x < 1$
  - summation : $\sum^n_{i=1}{n\choose i}=2^n-1$
- **combination** (non ordered selection) : the number of ways of choosing a set of $r$ object from a set of $n$ distinct objects without repetion is $n\choose k$
- **distribution** : the number of wys of distributing $n$ distinct objects into $r$ distinct groups of size $n_1,\ldots,n_r$ where $n=n_1+\cdots+n_r$ is $\frac{n!}{n_1!\cdots n_r!}$
- distinct summation : the number of distinc vector $(n_1,\ldots,n_r)$ of positive integers satisfying $\sum n_i = n$ is $n-1\choose r-1$ (if $0$ included we have $n+r-1\choose n$)
- **geometrics series** : $\sum^n_{i=0}a\theta^i=\cases{a(n+1)&\if&\theta=1\\\ a\frac{1-\theta^{n+1}}{1-\theta}&\if&\theta\not =1\\\ a\frac{1}{1-\theta}&\if&\abs\theta< 1\and n=\infty}$
- **exponential series** : $e^x=\sum^\infty_{n=0}\frac{x^n}{n!}$

### Probability space

- probability of an random experiment : $\frac{\text{# of times event takes place}}{\text{# experiments carried out}}$
- **probability space** : $(\Omega,\F,P)$
  - sample space (universe) : $\Omega$ contains all the possible results $\omega$ (outcomes elementary events)
  - event space : collection of events $\F\subset\Omega$
  - probability distribution : $P : \F\to[0,1]$
- **event space** : $\F$ (if countable, lets take the biggest of powerset cardinality)
  - $\F$ is nonempty
  - if $A\in\F$ then $A^c\in\F$
  - if $\{A_i\}^\infty_{i=1}$ are all elements of $\F$ then $\cup^\infty _{i=1}A_i\in\F$
- **probability distribution** : $P$
  - if $A\in\F$ then $0\le P(A)\le 1$
  - $P(\Omega)=1$
  - if $\{A_i\}^\infty_{i=1}$ are pairwise disjoint then $P(\cup^\infty _{i=1} A_i)=\sum^\infty _{i=1} P(A_i)$
  - $P(\emptyset)=0$
  - $P(A^c)=1-P(A)$
  - $P(A\cup B)=P(A)+P(B)-P(A\cap B)$ as $P(\cup^n_{i=1} A_i)=\sum^n _{r=1}(-1)^{r+1}\sum _{1\le i_1 <\cdots<i _r\le n} P(A _{i_1}\cap\cdots\cap A _{i_r})$
  - $P(\cup^\infty_{i=1} A_i)\le\sum^\infty _{i=1} P(A_i)$
- birthday paradox : $n$ people, probability of all having different birthday $\frac{365!}{(365-n!)}\frac{1}{365!}$

### Conditional probability

- **conditional probability** : $P(A|B)=P(A\cap B)/P(B)$
- law of total probability : $P(A)=\sum^\infty_{i=1} P(A\cap B_i)=\sum^\infty _{i=1} P(A|B_i)P(B_i)$ for $B_i$ pairwise disjoint events
- **Bayes theorem** : $P(B_j|A)=\frac{P(A|B_j)P(B_j)}{\sum^\infty_{i=1}P(A|B_i)P(B_i)}$ for $B_i$ pairwise disjoint events
- multiple conditioning : $P(A_1\cap\cdots\cap A_n)=\Pi^n_{i=2}P(A_i|A_1\cap\cdot\cap A_i-1)\times P(A_1)$ with $P(A_1\cap A_2\cap A_3)=P(A_3|A_1\cap A_2)P(A_2|A_1)P(A_1)$
- **many types of matching problem** : at least $r$ out of $n$ hats are on the right heads is $(n-r)!/n!$

### Independence

- **event independence** : $A\indep B$ iff $P(A\cap B)=P(A)P(B)$
- mutally independent : $P(\cap_{i\in\F}A_i)=\Pi _{i\in\F}P(A_i)$
- pairwise independent : $P(A_i\cap A_j)=P(A_i)P(A_j)$ for $1\le i<j\le n$
- conditonally independent : given $B$ we have $P(\cap_{i\in\F}A_i|B)=\Pi _{i\in\F}P(A_i|B)$
- **series systems** : $A_i\cap A_j$
- **parallel systems** : $A_i\cup A_j$
- Simpson's paradox : forgetting conditionng can change the conclusion of a study

### Random variable

- **random variate** : $X : \Omega\to\R$ is a function from the sample space $\Omega$ taking values in the real numbers
- **support** (image of the function $X$) : $D_X=\{x\in\R : \exists\omega\in\Omega\st X(\omega)=x\}$ countable
- discrete random variable : if the support $D_X$ is countable
- **probability of random variable** : $P(X\in S)=P({\omega\in\Omega : X(\omega)\in S})$
- **indicator variable** (Bernoulli trial) : random variable $I$ that takes only the values $0$ and $1$
- **probability mass/density function** (PMF/PDF) : $f_X(x)=P(X=x)=P(A_x)=P(\{\omega\in\Omega : X(\omega)=x\})$
  - $f_X(x)\ge 0$ and is only positive for $x\in D_X$
  - $\sum_{x_i\in D_x} f_X(x_i)=1$
- **binomial distribution**  $X\sim B(n,p)$ : $f_X(x)={n\choose x}p^x(1-p)^{n-x}$ and $X\sim B(n,p)$ model a number of successes of independent trials
- **geometric distribution** $X\sim Geom(p)$: $f_X(x)=p(1-p)^{x_1}$ model the wait until the first success of independent trials
- lack of memory : if $X\sim Geom(p)$ then $P(X > n+m | X > m)=P(X >n)$
- **negative binomial distribution** $X\sim NegBin(n,p)$ : $f_X(x)={x-1 \choose n-1}p^n(1-p)^{x-n}$ model the wait until the $n$th success in a series of independent trials (when $n=1$ we have $X\sim Geom(p)$)
- **gamma function** : $\Gamma(\alpha)=\int^\infty_0 u^{\alpha-1}e^{-u}\d u$ with $\Gamma(1)=1$, $\Gamma(\alpha+1)=\alpha\Gamma(\alpha)$, $\Gamma(n)=(n-1)!$, $\Gamma(1/2)=\pi$ for $\alpha>0$
- negative binomial distribution gamma version : $f_Y(y)=\frac{\Gamma(y+\alpha)}{\Gamma(\alpha)y!}p^\alpha(1-p)^y$ with $Y=X-n$
- **hypergeometric distribution** : $f_X(x)=\frac{{b \choose x}{n\choose m-x}}{{b+n\choose m}}$ model the number of white balls in drawing $m$ balls without replacement from an urn containg $b$ white and $n$ black balls
- **cumulative distribution function** (CDF) : $F_X(x)=P(X\le x)$
  - $\lim_{x\to -\infty}F_X(x)=0$
  - $\lim_{x\to \infty}F_X(x)=1$
  - $F_X$ is non-decreasing
  - $F_X$ is continuous on the right : $\lim_{t\downarrow 0}F_X(x+t)=F_X(x)$
  - $P(X > x)=1-P(X\le x)=1-F_X(x)$
  - $P(x<X\le y)=F_X(y)-F_X(x)$ for $x<y$
- **uniform distribution** : $f_X(x)=1/(b-a+1)$ for $a<b$
- **poisson distribution** $X\sim Pois(\lambda)$ : $f_X(x)=\frac{\lambda^x}{x!}e^{-\lambda}$ for $\lambda > 0$
- **transformation of discrete random variable** : $Y=g(X)$ and $f_Y(y)=\sum_{g(x)=y}f_X(x)$

### Expectation

- **expected value** (mean value) : $E(X)=\sum_{x\in D_X} x f_X(x)$
  - if not absolutely converge then not well defined
  - linear operator : $E(aX+bY+c)=aE(X)+bE(Y)+c$
  - Cauchy-Schwarz inequality : $E(X)^2\le E(X^2)$
  - $E(X)=\sum_{x=1}^\infty P(X\ge x)$
- **moment of a distribution** : require $\sum_x \abs{x}^r f_X(x) <\infty$
  - $r$th moment of $X$ : $E(X^r)$
  - $r$th central moment of $X$ : $E\{(X-E(X))^r\}$
  - $r$th factorial moment of $X$ : $E\{X(X-1)\cdots(X-r+1)\}$
- **variance** : $var(X)=E\{(X-E(X))^2\}=E(X^2)-E(X)^2$
  - $var(aX+b)=a^2var(X)$
  - $var(X)=0$ means $X$ has probability $1$
- **standard deviation** : $\sqrt{var(X)}$

### Conditional probability distributions

- **conditional probability mass function** : $f_X(x|B)=P(X=x|B)=P(A_x\cap B)/P(B)$
  - $f_X(x|B)\ge 0$
  - $\sum_x f_X(x|B)=1$
- **conditional expected value** : $E(g(X)|B)=\sum_x g(x)f_X(x|B)$
- partionned expected value : $E(X)=E(X|B)P(B)+E(X|B^c)P(B^c)$

### Convergence

- **distribution approximation** $X_n\stackrel{D}{\to}X$ : $F_n(x)\to F(x)$ as $n\to\infty$
- **law of small numbers** : for $X_n\sim B(n, p_n)$ suppose $np_n\to\lambda$ as $n\to\infty$ then $X_n\sim Pois(\lambda)$
- **limiting distribution** : for $X_N$ be hypergeometric suppose $m/N\to p$ as$N,m\to\infty$ then $X_B\sim B(n,p)$

### Continuous random variables

- **support** : $D_X=\{x\in\R:X(\omega)=x,\omega\in\Omega\}$ uncountable
- **cumulative distribution function** : $F_X(x)=P(X\le x)$
- **probability density function** (PDF) : $P(X\le x)=F_X(x)=\int^x_{-\infty} f(u)\d u$
  - $f(x)\ge 0$ and $\int_{-\infty}^\infty f(x)\d x = 1$
  - $f(x)=\d{}F(x)/\d x$
  - $P(x< X\le y)=\int^y_x f(u)\d u$ for $x < y$
- **uniform distribution** $U\sim U(a,b)$ : $f_U(u)=1/(b-a)$ if $a<u<b$ else $0$
  - $F_U(u)=\cases{0&u\le a\\\ (u-a)/(b-a) &a<u\le b\\\ 1 &u>b}$
- **exponential distribution** $X\sim exp(\lambda)$ : $f_X(x)=\lambda e^{-\lambda x}$ if $x>0$ else $0$
  - $F_X(x)=1-e^{-\lambda x}$ if $x>0$ else $0$
- **gamma distribution** : $f_X(x)=\frac{\lambda^\alpha}{\Gamma(\alpha)}x^{\alpha -1}e^{-\lambda x}$ if $x>0$ else $0$ (with $\alpha = 1$ this is the exponential distribution, otherwise this is the Erlang density)
- **Laplace distribution** : $f_X(x)=\frac{\lambda}{2}e^{-\lambda\abs{x-\eta}}$ for $\lambda>0$
  - $F_X(x)=\cases{\frac{1}{2}e^{-\lambda\abs{x-\eta}}&x\le\eta\\\ 1-\frac{1}{2}e^{-\lambda\abs{x-\eta}}&x>\eta}$
  - $F_X(\eta)=1/2$ so $\eta$ is the median
- **Pareto distribution** : $f_X(x)=\frac{\alpha\beta^\alpha}{x^{\alpha+1}}$ if $x\ge\beta$ else $0$
  - $F_X(x)=1-(\frac{\beta}{x})^\alpha$ if $x\ge\beta$ else $0$
- **expectation** : $E(X)=\int^\infty_{-\infty}xf_X(x)\d x$
- **variance** : $var(X)=\int^\infty_{-\infty} (x-E(X))^2f_X(x)\d x=E(X^2)-E(X)^2$
- **conditional densities**
  - $f_X(x|X\in A)=\frac{f_X(x)}{P(X\in A)}$ if $X\in A$ else $0$
  - $F_X(x|X\in A)=P(X\le x|X\in A)=\frac{P(X\le x \cap X\in A)}{P(X\in A)}=\frac{\int_{A_x}f(y)\d y}{P(X\in A)}$
  - $E(g(X)|X\in A)=\frac{E(g(X)I(X\in A))}{P(X\in A)}$

### Further ideas

- **quantile** : $x_p=inf\{x : F(x)\ge p\}$
  - in particular the $0.5$ quantile is called the median
- transformations : consider $Y=g(X)$ and $\beta_y=(-\infty,y]$ then $F_Y(y)=P(Y\le y)=\int_{g^{-1}(\beta_y)}f _X(x)\d x$ where $g^{-1}(\beta_y)=\{x\in R : g(x)\le y\}$
  - in particular if monotone and an inverse exists : $F_Y(y)=F_X(g^{-1}(y))$

### Normal distribution

- **normal distribution** $X\sim\N(\mu,\sigma^2)$ : $f_X(x)=\frac{1}{\sqrt{2\pi}\sigma}e^{-\frac{(x-\mu)^2}{2\sigma^2}}$
- standard normal distribution $Z\sim\N(0,1)$ : $\phi_Z(z)=(2\pi)^{-1/2}e^{-z^2/2}$
  - $F_Z(x)=P(Z\le x)=\Phi(x)=(2\pi)^{-1/2}\int_{-\infty}^x e^{-z^2/2} \d z$
  - $f_X(x)=\sigma^{-1}\phi((x-\mu)/\sigma)$
- interpretation
  - centered at $\mu$ which is the median : most likely value
  - standard deviation $\sigma$ : the spread around $\mu$
    - 68% of the probabilities : $\mu\pm\sigma$
    - 95% of the probabilities : $\mu\pm2\sigma$
    - 99.7% of the probabilities : $\mu\pm3\sigma$
- **properties of standard normal**
  - symmetric density with respect to $z=0$ : $\phi(z)=\phi(-z)$
  - $P(Z\le z)=\Phi(z)=1-\Phi(-z)=1-P(Z\ge z)$
  - standard normal quantiles $z_p=-z_{1-p}$
  - $z^r\phi(z)\to 0$ as $z\to\pm\infty$ thus the moments always exist
  - $\phi'(z)=-z\phi(z)$, $\phi''(z)=(z^2-1)\phi(z)$
  - $E(Z)=0$
  - $var(Z)=1$
  - if $X\sim\N(\mu,\sigma^2)$ then $Z=(X-\mu)/\sigma\sim\N(0,1)$ and $X=\mu+\sigma Z$
- **binomial distribution approximation** : $X_n\sim B(n,p)$ with $\mu_n=E(X_n)=np$ and $\sigma^2_n=var(X_n)=np(1-p)$ so $X_n\sim\N(np,np(1-p))$ as $n\to\infty$
  - poisson is better approximated for small values
  - normal is better approximated for large $n$ and $min(np, n(1-p))\ge 5$
- **continuity correction** : better approximation for $P(X_n\le r)$ when $r$ is replaced by $r+\frac{1}{2}$
  - binomial : $P(X_n\le r)=\Phi(\frac{r+1/2-np}{\sqrt{np(1-p)}})$
- Q-Q plots : quantile vs quantile, better it is to a straight line better the distribution fits the samples

### Several random variables

- **discrete**
  - joint probability mass function : $(X,Y)$ is $f_{X,Y}(x,y)=P((X,Y)=(x,y))$
  - joint cumulative distribution function : $F_{X,Y}(x,y)=P(X\le x,Y\le y)$
- **continuous**
  - joint density : $P((X,Y)\in A)=\iint_{(u,v)\in A}f _{X,Y}(u,v)\d u\d v$
  - joint cumulative distribution function : $F_{X,Y}(x,y)=P(X\le x,Y\le y)=\int^x _{-\infty}\int^y _{-\infty} f _{X,Y}(u,v)\d u\d v$
  - implies $f _{X,Y}(u,v)=\frac{\partial^2}{\partial x\partial y}F _{X,Y}(x,y)$
- **marginal probability mass/density function** :
  - discrete : $f_X(x)=\sum_y f_{X,Y}(x,y)$
  - continuous : $f_X(x)=\int^\infty_{-\infty} f _{X,Y}(x,y)\d y$
- **conditional probability mass/density function** : $f_{Y,X}(y|x)=\frac{f _{X,Y}(x,y)}{f_X(x)}$
- multivariate random variables : same rules
- multinomial distribution of denominator $m$ and probabilities : $f_{X_1,\ldots,X_k}(x_1,\ldots,x_k)=\frac{m!}{x_1!\times\cdots\times x_k!}p_1^{x_1}\cdots p _k^{x_k}$
- **independence** : iff $f_{X,Y}(x,y)=f_X(x)f_Y(y)$

### Dependence

- **expectation**
  - discrete : $E(g(X,Y))=\sum_{x,y} g(x,y)f _{X,Y}(x,y)$ 
  - continuous : $E(g(X,Y))=\iint g(x,y)f_{X,Y}(x,y)\d x\d y$
- **joint moment** : $E(X^rY^s)$
- **joint central moment** : $E\{(X-E(X))^r(Y-E(Y))^s\}$
- **covariance** : $cov(X,Y)=E\{(X-E(X))(Y-E(Y))\}=E(XY)-E(X)E(Y)$
  - $cov(X,X)=var(X)$
  - $cov(a,X)=0$
  - symmertry
  - $cov(a+bX+cY, Z)=bcov(X,Z)+ccov(Y,Z)$
  - $cov(a+bX,c+dY)=bdcov(X,Z)$
  - $var(a+bX+cY)=b^2 var(X)+2bc cov(X,Y)+c^2 var(Y)$
  - Cauchy-Schwarz inequality : $cov(X,Y)^2\le var(X)var(Y)$
- **independence and covariance** : if $X,Y$ independent then $cov(X,Y)=0$ (converse false)
- **correlation** : $corr(X,Y)=\frac{cov(X,Y)}{\sqrt{var(X)var(Y)}}=\rho$
  - $-1\le\rho\le 1$
  - if $\rho=\pm 1$ then $X,Y$ are linearly dependent with probability $1$ : $aX+bY+c=0$
  - if independent $corr(X,Y)=0$
  - $corr(a+bX,c+dY)=sign(bd)corr(X,Y)$
  - correlation mesure linearity not locality (can be wrong)
  - correlation isn't causation
- **conditional expectation**
  - discrete : $E(g(X,Y)|X=x)=\sum_y g(x,y)f_{X,Y}(x,y)$
  - continuous : $E(g(X,Y)|X=x)=\int^\infty_{-\infty} g(x,y)f _{X,Y}(x,y)\d y$
- **expectation in stages** : $E(g(X,Y))=E_X\{E(g(X,Y)|X=x)\}$
- **variation in stages** : $var(g(X,Y))=E_X\{var(g(X,Y)|X=x)\}+var_X\{E(g(X,Y)|X=x)\}$

### Generating functions

- moment generating function (MGF) : $M_X(t)=E[e^{tX}]=\sum_\limits{r=0}^\infty \frac{t^r}{r!}E(X^r)$ (Laplace transform)
  - $M_{a+bX}(t)=e^{at}M_X(bt)$
  - $E(X^r)=\frac{\partial^r M_X(t)}{\partial t^r}\vert_{t=0}$
  - many distributions do not have a MGF ($E(e^{tX})<\infty$ required, not only for $0$)
- characteristic function (alternative) : $\varphi_X(t)=E(e^{itX})$ (Fourrier transform)
  - every random variable has one
  - same cumulative distribution iff same characteristic function : $f(x)=\frac{1}{2\pi}\int_{-\infty}^\infty e^{-itx}\varphi(t)\d{t}$
- cumulant-generating function (CGF) : $K_X(t)=\log M_X(t)$
  - cumulants $k_r=\frac{\partial^r K_X(t)}{\partial t^r}\vert_{t=0}$
  - equivalent to MGF

### Vector probability

- random variable vector : $X=\m{X_1\\\ X_2}$ ($p\times 1$ vector)
- expectation vector : $E(X)_{p\times 1}=\m{E(X_1)\\\ E(X_2)}$
- (co-)variance matrix : $var(X)_{p\times p}=\m{var(X_1) & cov(X_1,X_2)\\\ cov(X_1,X_2) & E(X_2)}$
- MGF : $M_X(t)=E(e^{t^\top X})$
- multivariate normal distribution : for expectation vector $\mu$ and co-variance matrix $\theta$ $\mu^\top X\sim \N(u^\top\mu,u^\top\theta u)$ where $X\sim\N_p(\mu,\theta)$
  - if $X_i\sim\N(\mu,\sigma^2)$ then $X\sim\N_n(\mu1_n,\sigma^2I_n)$
  - MGF $M_X(u)=\exp(u^\top\mu+1/2u^\top\theta u)$
  - density function : $f(x;\mu,\theta)=\frac{1}{(2\pi)^{p/2}\abs{\theta}^{1/2}}\exp{-1/2(x-\mu)^\top\theta^{-1}(x-\mu)}$ for $\theta$ having rank $p$
  - marginal distribution : $X_A\sim\N_q(\mu_A,\theta_A)$ for $\abs{A}=q< p$
  - conditional distribution : $X_A|X_B=x_B\sim\N_q(\mu_A+\theta_{AB}\theta_B^{-1}(x_B-\mu_B),\theta_A-\theta _{AB}\theta _B^{-1}\theta _{BA})$ for $X_B=x_B$
- transformation : $f_{Y_1,Y_2}(y_1,y_2)=f _{X_1,X_2}(x_1,x_2)\times\abs{J(x_1,x_2)}^{-1}\vert _{x_i=h_i(y_1,y_2)}$ where $h_i$ are solutions and $J$ is the Jacobian of $Y_1=g_1(X_1,X_2)$
  - if $S=X+Y$ (scalar), then their PDF is $f_S(s)=f_X*f_Y(s)$
- Risk estimation : $P(S\le s_{1-\alpha})=1-\alpha$ and $P(S>s _{1-\alpha})=\alpha$
  - case $X_1,X_2\sim\N(\mu,\sigma^2)$ with correlation $p$ : $s_{1-\alpha}\le 2z _{1-\alpha}$ (twice the marginal risk, often use in pratice)
  - case $X_1,X_2\sim Pareto(1/2)$ independant : $2z_{1-\alpha} < s _{1-\alpha}$

### Order statistics

- ordered value : $X_1\le\cdots\le X_n$ (no equality if continuous)
  - min/max are bounds
  - median : $X_{m+1}$ when $n=2m+1$ (odd) or $1/2(X_m+X _{m+1})$ when $n=2m$

### Inequalities

- basic : $P(h(X)\ge a)\le E(h(X))/a$ ($h$ non-negative)
- Markov : $P(\abs{X})\ge a)\le E(\abs{X})/a$
- Chebyshov : $P(\abs{X}\ge a)\le E(X^2)/a^2$
- Jensen : $E(g(X))\ge g(E(X))$ ($g$ convexe)
- Hoeffding : $P(Z\ge\epsilon)\le e^{-t\epsilon}e^{t^2(b-a)^2/8}$ for $a\le Z\le b$ constant

### Convergence

- deterministic convergence : $x_n\to x$ iff there $N_\epsilon$ such that $\abs{x_n-x}\le\epsilon$ for $n>N _\epsilon$
- probabilistic convergence : $E(X_n)\to E(X)$ or $P(X_n\le x)\to P(X\le x)$
- convergence
  - almost surely : $X_n\stackrel{a.s.}{\to}X$ if $P(\lim_\limits{n\to\infty} X_n=X)=1$ (need same probability space)
  - in mean square : $X_n\stackrel{2}{\to}X$ if $\lim_\limits{n\to\infty} E((X_n-X)^2)=0$ for finite expectation
  - in probability : $X_n\stackrel{P}{\to}X$ if $P\lim_\limits{n\to\infty} P(\abs{X_n-X}\ge\epsilon)=0$ (implied by first two)
  - in distribution : $X_n\stackrel{D}{\to}X$ if $\lim_\limits{n\to\infty} F_n(x)=F(x)$ (implied by all)
- Slutsky's lemma : if $X_n\stackrel{D}{\to}X$ and $Y_n\stackrel{P}{\to}y_0$, then $X_n+Y_n\stackrel{D}{\to}X+y_0$ and $X_nY_n\stackrel{D}{\to}Xy_0$
- limits for maxima : $M_n=\max\{X_1,\ldots,X_n\}$ and $X_1,\ldots,X_n\iid F$ then $P(M_n\le x)=F(x)^n=0$ if $F(x)<1$ degenerated
- non-degenerate limit : replace with $Y_n=(M_n-b_n)/a_n$ (converge in distribution) with $\{a_n\}>0$ and $\{b_n\}$ sequences of constants 
- generalised extreme-value (GEV) distribution : $\cases{\exp[-\max(0, 1+\xi(y-\eta)/\tau)^{-1/\xi}]&\xi\not=0\\\ \exp[-\exp(-(y-\eta)/\tau))]&\xi=0}$

### Average

- weak laws of large number : if average $\av{X}=n^{-1}(X_1+\cdots+X_n)$ independent identically distributed (iid) with finite expectation $\mu$, then $\av{X}\stackrel{P}{\to}\mu\forall\epsilon>0$ i.e. $P(\abs{\av{X}-\mu}>\epsilon)\to0$ as $n\to\infty$
- strong law of large number : then $\av{X}\stackrel{a.s.}{\to}\mu$ i.e. $P(\lim_\limits{n\to\infty}\av{X}=\mu)=1$
- lemma : if $var(X_j)<\infty$ then $E(\av{X})=\mu$ and $var{\av{X}}=\sigma^2/n$
- central limit theorem : $Z_n=\frac{\av{X}-E(\av{X})}{var{\av{X}}^{1/2}}=\frac{n^{1/2}(\av{X}-\mu)}{\sigma}\stackrel{D}{\to}Z$ as $n\to\infty$ and $Z\sim N(0,1)$
  - sum approximation : $E(\sum X_i)=n\mu$ and $var(\sum X_i)=n\sigma^2$
- delta method : $g(\av{X})\sim N(g(\mu),g'(\mu)^2\sigma^2/n)$ for large $n$
- sample quantile : $r$th order statistic $X_{( r)}$ where $r=\lceil np\rceil$
- asymptotic distribution of order statistics : $\frac{X_{()\lceil np\rceil)}-x_p}{[p(1-p)/(nf(x_p)^2)]^{1/2}}\stackrel{D}{\to}N(0,1)$ as $n\to\infty$

## Statistics

### Introduction

- model - theory - nature
- nature - experiment/observation - data
- data - statistics - model
- statistics : science of collecting, analysing and interpreting data
  - exploratory data analysis : simple, graphical methods to detect structures and suggest hypothesis (to be test on others datas to avoid too much bias)
  - statistical inference : use probability to estimate and use forecasting methods
- data
  - unit (indicidual student)
  - population : entire set of units (set of EPFL student)
  - sample : subset of population (seconds year EPFL students)
  - observation (weight of unit)
- statistical variable
  - quantitative : discrete or continuous (number of childen in a family)
  - qualitative (categorical) : nominal (non-ordered, sex) or ordinal (ordered, evaluation) (weight in kilos)
  - may convert quantitative variable into qualitative : size in centimers to S, M, L categories
- sample order statistics : $x_{(1)}\le\cdots\le x _{(n)}$
- stem-leaf diagram : general branch (16, 17, 18 decimeters) and corresponding number of leaf (002245, 03477, 2 centimeters)
- histogram : loss of information due to the width of the box
- kernel density estimator (KDE) : better than histogram, $\hat f_h(y)=\frac{1}{nh}\sum_\limits{j=1}^n K(\frac{y-y_j}{h})$ with $K$ often $(2\pi)^{-1/2}e^{-u^2/2}$ and window width $h$

### Numerical summaries

- quantitative variables
  - central tendency/location
    - average : $\av{X}$
    - median : $med(x)=x_{(\lceil n/2\rceil)}$ something average on the two most centered for even number of quantile
  - dispersion
  - symmetry/asymmetry
  - number of modes (bumps)
- quantile : $\hat q(\alpha)=x_{(\lceil n\alpha/100\rceil)}$ with inferior quartile $\hat q(25)$, median $\hat q(50)$ and superior quartile $\hat q(75)$
- sample standard deviation : $s=[\frac{1}{n-1}\sum_\limits{i=1}^n(x_i-\av{x})^2]^{1/2}$ (breakdown 0)
- sample variance : $s^2$
- interquartile range IQR : $IQR(x)=\hat q(75)-\hat q(25)$ (breakdowm of 25%)
- sample correlation : with covariance $n^{-1}\sum_\limits{j=1}^n(x_j-\av{x})(y_j-\av{y})$
- box plot : five number summary ($min=x_{(1)},\hat q(25),\text{median},\hat q(75),max=x _{(n)}$)
  - point : min/max outside whiskers bounds
  - median : bold split
  - box bounds : quartiles
  - whiskers bounds : quartiles $\pm 1.5·IRQ(x)$

### Model

- strategy
  - graphical respresentations
  - study global structure (outliers)
  - calculate numerical summaries
  - maybe fit a density function
- check normal distribution fitness : Q-Q plot, graph of $x_{(1)}\le\cdots\le x _{(n)}$ against normal plotting positions $\Phi^{-1}(1/(n+1),\ldots,\Phi^{-1}(n/(n+1))$

### Statistical inference

- statistical inference : inverse probability based on induction instead of probability deduction
- problem addressed
  - specification of model for the data
  - estimation of unknowns (hidden parameters)
  - tests of hypotheses concerning a model
  - planning of data analysis to answer question as effectively as possible
  - decision when faced with uncertainties
  - prediction of future unknowns
  - relevance of the data to question we want to answer
- statistical model : probability distribution $f(y)$ constructed/chosen to learn from observed data (called parametric model if determined by parameter $f(y)=f(y;\theta)$)
- a statistic $T=t(Y)$ : known function of data $Y$
- sampling distribution of a statistic : distribution when $Y\sim f(y)$
- random sample : set of independent identically distributed random variables

### Point estimation

- study population ($F,f$)
  - statisical model : unknown distribution $f$ of $Y$
  - parametric statistical model : distribution of $Y$ is known $f(y)=f(y;\theta)$ except for the values of parameters $\theta$
  - sample : representative of population $y_1,\ldots,y_n$
  - random sample : representative of model $Y_1,\ldots,Y_n\iid f$
  - statistic : any function $T=t(Y_1,\ldots,Y_n)$ of random variables/sample
  - estimator : $\hat\theta$ used to estimate parameter of $f$
- estimation methods : choice depends on ease of calculation, efficiency (precision), robustness (not sensible on outlies)
  - method of moments : simple, but can be inefficient
  - maximum likelihood estimation : general, optimal in many parametric models
  - M-estimation : even more general, robust, but less efficiency
- method of moments : estimate of a parameter $\theta$ is value $\tilde{\theta}$ that matches theoretical and empirical moments
  - with $p$ unknown parameters, set theoretical moments of population equal to empirical moments of sample
  - solve resulting equations : $E(Y^r)=\int y^r f(y;\theta)\d y=n^{-1}\sum_\limits{j=1}^n y_j^r$
  - estimate not unique
- maximum likelihood estimation
  - likelihood : $L(\theta)=f(y_1,\ldots,y_n;\theta)=f(y_1;\theta)\times\cdots\times f(y_n;\theta)$
  - data are treated as fixed
  - maximum likelihood estimate MLE $\tilde\theta$ : $L(\tilde\theta)\ge L(\theta)\forall\theta$
  - simplifiy calculation by maximising $l(\theta)=\log L(\theta)$ (plot if possible)
  - check that $\tilde\theta$ given a maximum : $\d^2 l(\esti)/\d\theta^2 < 0$
- M-estimation : maximize $p(\theta;Y)=\sum_\limits{j=1}^n p(\theta;Y_j)$ where $p$ is concave
  - taking $p(\theta;y)=\log f(y;\theta)$ give maximum likelihood estimator
  - least squares estimator : $p(\theta;y)=(y-\theta)^2$
- bias : $b(\theta)=E(\esti)-\theta$
  - $b(\theta)<0\forall\theta$ : underestimate 
  - $b(\theta)>0\forall\theta$ : overestimate 
  - $b(\theta)=0\forall\theta$ : unbiased 
  - $b(\theta)\approx 0$ on average : right place
- mean square error MSE : average squared distance between estimator and target $MSE(\esti)=E[(\esti-\theta)^2]=var(\esti)+b(\theta)^2$ 
  - with two unbiased estimators, $\esti_1$ is more efficient if $MSE(\esti_1)\ge MSE(\esti_2)$ i.e. $var(\esti_1)\le var(\esti_2)$
- delta method : for $\esti\sim N(\theta,v/n)$ as $n\to\infty$, we have $g(\esti)\sim N(g(\theta)+vg''(\theta)/(2n), vg'(\theta)^2/n)$ which implies $MSE(g(\esti))=[\frac{vg''(\theta)}{2n}]^2+\frac{vg'(\theta)^2}{n}$ (disregard bias for large $n$)

### Interval estimation

- pivot : $Q=q(Y;\theta)$ whose distribution is knows and does not depend on $\theta$
- confidence interval CI : lower $P(\theta < L)=\alpha_L$ and upper $P(U<\theta)=\alpha_U$ confidence bound contains $\theta$ with specified probability (confidence level $1-\alpha_L-\alpha_U$)
  - find pivot
  - obtain quatile of pivot
  - isolate $\theta$ between lower and upper bounds
  - one-sided interval : replace bounds by infinity
- standard error : $V^{1/2}$ where $V=v(Y_1,\ldots,Y_n)$ which is an estimator of $\tau^2_n$ which is itself the variance of the estimator concerned by the error
- CI and normal random sample : $Y_1,\ldots,Y_n\iid\N(\mu,\sigma^2)$
  - $\av{Y}\sim\N(\mu,\sigma^2/n)$
  - $(n-1)S^2=\sum_\limits{j=1}^n(Y_j-\av{Y})^2\sim\sigma^2\chi^2 _{n_1}$
  - $\chi^2_v$ : chi-square distrubition with $v$ degrees of freedom
  - if $\sigma^2$ is known, $Z=\frac{\av{Y}-\mu}{\sqrt{\sigma^2/n}}\sim\N(0,1)$
  - interval : $(L,U)=(\av{Y}-\frac{\sigma}{\sqrt{n}}z_{1-\alpha_L},\av{Y}-\frac{\sigma}{\sqrt{n}}z _{\alpha _U}$

### Hypothesis tests

- plausibility of value $\theta^0$ : hypothesis $\theta^0=\theta$ at significance level $\alpha$
  - if $\theta^0$ lies inside CI, cannot reject
  - if $\theta^0$ lies outside CI, can reject
  - future data could discard theory so we can only reject or not reject but no way to prove
- hypothesis
  - null : $H_0$ represent the model/theory to test ($P_0()$)
  - alternative : $H_1$ represent what happens if $H_0$ is false ($P_1()$)
  - simple : $H_0$ fixes $\theta=\theta^0$
  - composite : $\theta$ not fix
- error
  - type 1 : $H_0$ is true but we wrongly reject it (choose $H_1$)
  - type 2 : $H_1$ is true but we wrongly accept $H_0$
- size of statistical test : probability of type 1 error $P_0(\text{reject} H_0)$
- power of statistical test : probability of type 2 error $P_1(\text{reject} H_0)$
- confidence intervals width : statisfies usually $U-L\propto n^{-1/2}$
- Pearson statistic (chi-square statistic) : $T=\sum_\limits{i=1}^k\frac{(O_i-E_i)^2}{E_i}$ with $O_1,\ldots,O_n$ be the number of observation falling in $k$ categories
- chi-square distribution : $f_W(w)=\frac{1}{2^{v/2}\Gamma(v/2)}w^{v/2-1}e^{-w/2}$ (reminder $\Gamma(a)=\int_0^\infty u^{a-1}e^{-u}\d u$ with $a>0$)
- evidence against $H_0$ : P-value $p_{obs}=P_0(T\ge t _{obs})$ where small value $H_0$ is false or something unlikely has occured
- decision procedure : choose significence level, P-value for rejecting $H_0$ if smaller that $\alpha$
- streng of evidence : weak (0.05), prositive (0.01), strong (0.001), very strong (0.0001)

### Comparison of tests

- parametrics tests
- nonparametrics tests
- receiver operating characteristics curve ROC : true positive against false postive (more in the upper left edge is best)
- standardized distance between models : $\delta=n^{1/2}\frac{\abs{\mu_1-\mu_0}}{\sigma}$
- if $\sigma^2$ is known, most powerful test on $\av{Y}$ is $\Phi(z_\alpha+\delta)$ where $\Phi(z _\alpha)=\alpha$

### Likelihood

- plausibility : $L(\theta_1)/L(\theta_2)=c$ means $\theta_1$ is $c$ times more plausible than $\theta_2$
- relative likelihood : $RL(\theta)=L(\theta)/L(\esti)$

### Scalar parameters

- observed information $J(\theta)=-\frac{\d^2 l(\theta)}{\d\theta^2}$ (measure curvature)
- expected information $I(\theta)=E[J(\theta)]$
- regularity condition : $J(\esti)^{1/2}(\esti-\theta)\stackrel{D}{\to}\N(0,1)$ as $n\to\infty$ thus $\esti\sim\N(\theta,J(\esti)^{-1})$
- likelihood ratio statistic : $W(\theta)=2[l(\esti)-l(\theta)]$
- under regularity condition : $\theta^0$ we have $W(\theta^0)\sim\chi_1^2$ for large $n$
- non-regular situations : one discrete parameters, support depends on $\theta$, true $\theta$ is on limits

### Vector parameters

- MLE : $\frac{\d l(\esti)}{\d\theta}=0_{p\times 1}$
- informations are matrices
- in regular cases : $\esti\sim\N_p(\theta,J(\esti)^{-1})$
- nested models : simplify model (simple model explain as well as general model?)

### Linear regression

- explanatory variable : distribution depends on a variable
- linear deendence : $Y\sim\N(\beta_0+\beta_1x,\sigma^2)$
- residual : if model is good, $r_j=(Y_j-\hat\beta_0-\hat\beta_1x_j)/\hat\sigma\sim\N(0,1)$

### Bayesian inference

- crutial difference : observed data $y$ ais fixed, $\theta$ is regarded as random variable
- prior density : $\pi(\theta)$ (may come from separate data from $y$, objective/subjective notion of what it reasonable to believe about $\theta$)
- posterior density : $\pi(\theta|y)=\frac{f(y|\theta)\pi(\theta)}{f(y)}$ where $f(y)=\int f(y|\theta)\pi(\theta)\d\theta$
- Bayesian updating : prior uncertainty becomes posterior uncertainty with data
- beta density : $\pi(\theta)=\frac{\theta^{a-1}(1-\theta)^{b-1}}{B(a,b)}$ where $a$, $b$ are paremeters and $B(a,b)=\Gamma(a)\Gamma(b)/\Gamma(a+b)$ is the beta function
- posterior expectation : $E(\theta|y)$
- posterior variance : $var(\theta|y)$
- maximum a posteriori estimator MAP : $\esti$ such that $\pi(\esti|y)\ge\pi(\esti|y)\forall\theta$
- loss function : $R(y;\theta)$ (could be absolute difference or square difference)
- expected posterior loss : $E(R(y;\theta)|y)=\int R(y;\theta)\pi(\theta|y)\d\theta$
- conuagte prior density : posterior densisties of same form as prior ones (avoid integrate)

### Bayesian modelling

- noisy : clean by orthogonal transformation (wavelet decomposition)

## Tricks

### Which distribution

- Is $X$ based on independent trials with same probability or draws from a finite set with replacement ?
  - **yes**, is the total number of trials $n$ fixed ?
    - **yes**, use $X\sim B(n,p)$ or $I$ if $n=1$ or even $X\sim Pois(np)$ for $n>>np$
    - **no**, use $X\sim Geom(p)$ for one success or $X$ negative binomial for $n$ successes
  - **no**, use hypergeometric

### Discrete vs continuous

![](img/232-1.png)

### Facts

- **counting**
  - permutation (ordered selection) : $n!/(n-r)!$
  - combination (non ordered selection) : $n\choose k$
- **distribution** (discrete)
  - binomial $X\sim B(n,p)$ : $f_X(x)={n\choose x}p^x(1-p)^{n-x}$
  - geometric $X\sim Geom(p)$ : $f_X(x)=p(1-p)^{x_1}$
  - negative binomial $X\sim NegBin(n,p)$ : $f_X(x)={x-1 \choose n-1}p^n(1-p)^{x-n}$
  - hypergeometric : $f_X(x)=\frac{{b \choose x}{n\choose m-x}}{{b+n\choose m}}$
  - uniform : $f_X(x)=1/(b-a+1)$
  - poisson $X\sim Pois(\lambda)$ : $f_X(x)=\frac{\lambda^x}{x!}e^{-\lambda}$
- **distrubution** (continuous)
  - uniform $U\sim U(a,b)$ : $f_U(u)=1/(b-a)$
  - exponential $X\sim exp(\lambda)$ : $f_X(x)=\lambda e^{-\lambda x}$
  - gamma : $f_X(x)=\frac{\lambda^\alpha}{\Gamma(\alpha)}x^{\alpha -1}e^{-\lambda x}$
  - Laplace : $f_X(x)=\frac{\lambda}{2}e^{-\lambda\abs{x-\eta}}$
  - Pareto : $f_X(x)=\frac{\alpha\beta^\alpha}{x^{\alpha+1}}$
  - normal $X\sim\N(\mu,\sigma^2)$ : $f_X(x)=\frac{1}{\sqrt{2\pi}\sigma}e^{-\frac{(x-\mu)^2}{2\sigma^2}}$
  - standard normal $Z\sim\N(0,1)$ : $\phi_Z(z)=(2\pi)^{-1/2}e^{-z^2/2}$
- **expectation**
  - indicator : $E(I) = p$
  - binomial $X\sim B(n,p)$ : $E(X) = np$
  - poisson $X\sim Pois(\lambda)$ : $E\{X(X-1)\cdots(X-r+1)\}=\lambda^r$ (factorial moment)
  - geometric $X\sim Geom(p)$ : $E(X)=1/p$
  - gamma : $E(X)=\alpha/\lambda$
  - Pareto : $E(X)=\alpha\beta/(\alpha-r)$
- **variance**
  - poisson $X\sim Pois(\lambda)$ : $var(X)=\lambda$
  - geometric $X\sim Geom(p)$ : $var(X)=(1-p)/p^2$
  - gamma : $var(X)=\alpha/\lambda^2$

- **others**
  - Gubel distribution
  - chi
  - student
  - beta

