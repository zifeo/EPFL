# MATH106

> [GNU General Public License v3.0](https://github.com/zifeo/EPFL/blob/master/LICENSE) licensed. Source available on [github.com/zifeo/EPFL](https://github.com/zifeo/EPFL).

Spring 2014: Analysis II

[TOC]

## Reminder Analysis I

### Functions of one variable
- **even** (symetry y-axis) $f(x)=f(-x)$ or **odd** (symetry origine) $f(x)=-f(-x)$
- (monotone) **increasing** or **decreasing**
- **composite function** : $g\cdot f(x)=g(f(x))$
- **injective** (one-to-one) : never takes twice the same value
- **surjective** (onto) : every vale in the codomain is hit at least once
- **bijective** : both one-to-one and onto, if bijective, an inverse function exist

### Sequences & Limites
- sequences ${a_n}_{n=1}^\infty$ converges or diverges
- **limit** exists iff both sided limits exist.
- **continuity** is when the limit exists at each point (caution on absolute sign, ++simplification does not change the discontinuties++)
  - removable discontinuities (one point displaced, sided limits equivalent)
    - jump discontinuities (sided limits differ)
    - infinite discontinuities (one sided limit does not exist)
- **asymptotes**
  - vertical $f(x) \to \infty$ as $x \to a$
  - horizontal $f(x) \to a$ as $x \to \infty$
    - $\frac{ax-b}{x+c}$ has a h-asy at $a$, a v-asy at $-c$ and a x-intercept at $x=\frac{b}{a}$
    - slope of the oblique-asy is $\lim_{x\to\infty} \frac{f(x)}{x}$
- $e^x = \lim_{n\to \infty} (1+\frac{x}{n})^n$

### Series
- **arithmetic series** : converge to $\sum_{n=1}^\infty n=\frac{n(n+1)}{2}$
- **geometric series** : converge to $\sum_{n=1}^\infty ar^{n-1}=\frac{a}{1-r}$ if $|r|< 1$
- **Riemann series** : $\sum_{n=1}^\infty \frac{1}{p^\alpha}$ converges if $\alpha > 1$
- sequences and series : if the series $\sum a_n$ is convergent, then $\lim a_n=0$.
- finding the terms : $S_n - S_o = a_n$ where $S_o$ is the one before $S_n$.
- **convergence tests**
  1. *divergence test* : if $\lim a_n$ does not exist or is not equal to $0$, then the series is divergent.
    2. *limit test* : (both positive) if $\lim_{n\to \infty} \frac{a_n}{b_n}=c$ where $c$ is a finite number bigger than $0$, then either both converge or diverge.
  2. *comparison test*
    4. *alternating series test* : if for all postive the next is smaller than the previous one and $\lim_{n\to \infty} b_n=0$, then the series converge.
  3. *ratio test* : $\lim_{n\to \infty} |\frac{next}{previous}|$ gives less than $1$, it is convergent, divergent if bigger than $1$, else inconclusive.
    6. *root test* : $\lim_{n\to \infty} \sqrt[n]{|a_n|}$, same conclusion as ratio test.
    7. *integral test* : for continuous, positive, deacreasing function on $[1,\infty)$, the series is convergent iff $\int_1^\infty f(x)dx$ is convergent.
- **absolute convergence** : series $\sum a_n$ is called **absolutely** convergent if $\sum |a_n|$ converges, it is conditionnaly convergent.
- **power series** : $\sum_{n=0}^\infty c_n(x-a)^n$ is called centered at $a$ with radius of convergence $R$ and the series converges if $|x-a|< R$ (ratio test to find it)
- **Taylor series** (called Mclaurin series if centered at $0$) : $\sum_{n=0}^\infty \frac{f^{(n)}(a)}{n!}(x-a)^n$

### Derivatives
- **derivatives** $f'(x)=\lim_{x\to a}\frac{f(x)-f(a)}{x-a}=\lim_{h\to 0}\frac{f(x+h)-f(x)}{h}$
- **critcal point** : $c$ such that $f'(c)=0$, $f'(c)=\infty$ (vertical tangent) or $f(c)$ does not exist
- **closed interval method** means looking at the critical numbers on $[a,b]$ **and** at the endpoints of the interval
- **extrema** $f'(x)=0$
  - $f''(x) > 0$ mimimum
  - $f''(x) < 0$ maximum
- **concavity**
  - if $\forall x \in I, f''(x) > 0$, the function is concave upward on I :)
    - if $\forall x \in I, f''(x) < 0$, the function is concave downward on I :(
- **derivative of inverse** function : $(f^{-1})'(a)=\frac{1}{f'(f^{-1}(a))}$ or $(f^{-1})'(f(a))=\frac{1}{f'(a)}$.

### Theorems
- **Intermediate value theorem** : $f$ continuous on $[a,b]$ and $f(a)\not =f(b)$, let $N$ be a number between $f(a)$ and $f(b)$, then there exist a $c$ such that $f(c)=N$
- **Extreme value theorem** : if $f$ continuous on $[a,b]$, then $f$ attains an absolute maximum and an absolute minimum on some number in that interval.
- **Bolzano-Weierstress theorem** : every bounded sequence has a convergent subsequence
- **Fermat's theorem** : if $f$ has a local extremum at $c$ and $f'(c)$ exists, then $f'(c)=0$.
- **Rolle's theorem** : if $f$ continuous on $[a,b]$ and differentiable on $(a,b)$ and $f(a)=f(b)$, then there is a number $c$ in $(a,b)$ such that $f'(c)=0$
- **Mean value theorem** : if $f$ continuous on $[a,b]$ and differentiable on $(a,b)$, then there is a number $c$ in $(a,b)$ such that $f'(c)=\frac{f(b)-f(a)}{b-a}$
- **Cauchy's mean value theorem** : let $f$,$g$ be continuous on $[a,b]$ and differentiable in $(a,b)$, then $\frac{f'(c)}{g'(c)}=\frac{f(b)-f(a)}{g(b)-g(a)}$.
- **De l'Hospital's rule** : suppose $f$ and $g$ are differentiable and $g'(x)\not = 0$ on an open interval $I$ that contains $a$. If the limit $f$ and the limit $g$ go both to $0$ or $\infty$ as $x\to a$, then $\lim_{x\to a} \frac{f'(x)}{g'(x)}$

### Integration
- **fundamental theorem of calculus** : for $f:[a,b]\to \mathbb R$, continuous, $\frac{d}{dx}[\int_a^x f(s)ds]=f(x)$
- $\int_a^b f(x)dx=\int_a^b F'(x)dx=F(b)-F(a)$

## Integration techniques, curves are surfaces

### Strategy
- if $f$ is monotone or continuous, then it is integrable
- **substitution** $\int f(g(x))g'(x) dx= F(g(x))+c$ (always take the biggest one, play with $u=\sqrt{x}\Rightarrow 2udu=dx$, caution on sign)
- **even function** $\int_{-a}^a f(x)= 2 \int_0^a f(x)dx$
- **odd function** $\int_{-a}^a f(x) dx = 0$
- **polynomial division** : $\frac{x^3-2x^2-4}{x^2+x+3}=(x-3)+\frac{1}{x^2+x+3}$
- **partial fractions** : $\frac{1}{x^2+2x-3}=\frac{1}{(x+3)(x-1)}=\frac{A}{x+3}+\frac{B}{x-1}$ where $A(x-1)=1$ and $B(x+3)=1$
- **by part** $\int f' g dx = fg-\int fg'dx$ or $\int fg dx=Fg-\int Fg'dx$ (twice by part should be done in the same derivation way)
- **sin and cos** $\int \sin^n (x) \cos^m (x) dx$
  - if $n$/$m$ is odd use $\sin^2+cos^2=1$ and substitution
  - if $n$/$m$ are even use half angle formulas ($2\sin^2 x=1-\cos 2x$ and $2\cos^2 x =1+\cos 2x$)
- **inproper integrals** : when bounds go to infinity or to a limit, the integral behaves as a Riemann series, use limit to compute it (can converges or not)

### Application
- **areas between curves** : $A=\int_a^b |f(x)-g(x)|dx$ (caution if lines cross, better separate)
- **volumes** $V=\int_a^b A(x)dx$
- **volumes of cylindrical shells** : $V=2\pi\int_a^b x f(x) dx$
- **arc length** : $L=\int_a^b \sqrt{1+(f')^2}dx$
- **surface areas** : $S= 2\pi \int_a^b f(x) \sqrt{1+(f')^2}dx$

## The Euclidian space & functions of several variables

### Vectors
- notation : $\vec{AB}=\vec v = < x_2-x_1,y_2-y_1,z_2-z_1 > $
- length : $L=|\vec v|=\sqrt{(x_2-x_1)^2+(y_2-y_1)^2+(z_2-z_1)^2}$
- $(x,y)$ denotes a point, $< x,y >$ denotes a vector
- basis vector $\hat i= < 1,0,0 >\quad \hat j=< 0,1,0 > \quad \hat k = < 0,0,1>$ use $\vec v = \sum_{i=1}^n v_i \hat e_i$ in $\mathbb R^n$
- unit vector : given $\vec u$, the unit vector is $\vec v = \frac{\vec u}{|\vec u|}$

### Three-Dimensional Coordinate Systems
- euclidian space : $\mathbb R^n$ must follow right hand rule
- **dot product** : $\vec a\cdot \vec b = \sum_{i=1}^n a_i b_i = |\vec a||\vec b|\cos \theta$ 
  - if product is null, then perpendicular
  - if $\vec a\cdot\vec  b= \pm |\vec a||\vec b|$, then $\vec a=c \vec b$ 
  - if product is less than $0$, then the angle is acute, else the angle is obtuse
  - behaves like the multiplication
- **direction angle** : $\cos \alpha_i=\frac{a_i}{|\vec a|}$ and $\sum_{i=1}^n \cos^2 \alpha_i=1$
- distances : $|xy|=\sqrt{\sum_{i=1}^n (x_i-y_i)^2}$
- **sphere** of radius $R$ at $x^c=(x_1^c\,ldots ,x_n^c)$ : $R^2=\sum_{i=1}^n (x_i-x_i^c)^2$
- **scalar projection** : $|\vec c|=\vec n_a \cdot \vec b$ with $\vec n_a=\frac{\vec a}{|\vec a|}$
- **vector projection** : $\vec c = (\vec n_a \cdot \vec b)\vec n_a$ with $\vec n_a=\frac{\vec a}{|\vec a|}$
- **cross product** : $\vec a \times \vec b = < a_2b_3-a_3b_2, b_1a_3-a_1b_3, a_1b_2-a_2b_1$
  - only $\mathbb R^3$
  - product perpendicular to $a$ and $b$
  - $\vec a \times \vec b = \begin{vmatrix} \hat i & \hat j & \hat k \\ a_1&a_2&a_3 \\ b_1&b_2&b_3 \end{vmatrix}$
  - $|\vec a \times \vec b|=|\vec a||\vec b|\sin \theta$
  - if product is null, $\vec a$ and $\vec b$ are parallel
  - the area of the parallelogram spanned is the lenght of the product
  - behaves like the multiplication (but not symmetric nor comutative)
  - $\vec a \cdot (\vec b \times \vec c) = (\vec a \times \vec b)\cdot \vec c $
  - $\vec a \times (\vec b \times \vec c) = (\vec a \cdot \vec c)\vec b -(\vec a \cdot \vec b)\vec c$
  - $\vec a \times \vec b = -\vec b \times \vec a$
- triple product (volume) : $\vec a \cdot (\vec b \times \vec c) = \begin{vmatrix} a_1&a_2&a_3 \\ b_1&b_2&b_3\\c_1&c_2&c_3 \end{vmatrix}$

### Equations & surfaces
- **lines** : $\vec r(t)=\vec r_0 + t \vec v$ or $x(t)=x_0+at\quad y(t)=y_0+bt\quad z(t)=z_0+ct$ and $\frac{x-x_0}{a}=\frac{y-y_0}{b}=\frac{z-z_0}{c}$
- **line segment** : $\vec r(t)=(1-t)\vec r_0+ t\vec r_1$
- **planes** : $\vec n \cdot (\vec r- \vec r_0)=0$ with $\vec r = < x(t),y(t),z(t) >$ and $\vec n = < a,b,c > $
  - $a(x-x_0)+b(y-y_0)+c(z-z_0)=0$
  - can be simplified to $ax+by+cz+d=0$ by expanding
  - normal distance with a point : $D=\frac{|ax_1+by_1+cz_1+d|}{\vec n}$ with $(x_1, y_1, z_1)=P$

### Vector functions
- notation : $\vec r(t)=f(t)\hat i +g(t)\hat j+h(t)\hat k$
- continous if $\lim_{t\to a} \vec(t)=\vec r(a)$
- derivative $\vec r'(t)=\lim_{\alpha \to 0}\frac{\vec r(t+\alpha)-\vec r(t)}{\alpha}$
- **tangent unit vector** $\tau(t)=\frac{r'(t)}{|r'(t)|}$
- integral $\int_a^b \vec r(t) dt=\vec R(b)-\vec R(a)$
- **arc length** $L=\int_a^b \sqrt{(f')^2+(g')^2+(h')^2}dt=\int_a^b |\vec r'(t)|dt$
- curve is smooth if $r'(t)$ is continuous and $r'(t)\not = 0$
- **curvature** $\kappa (s)=\frac{1}{R}=|\frac{d\tau}{ds}|=\frac{|\tau'(t)|}{|\vec r'(t)|}=\frac{|\vec r' \times \vec r''|}{|\vec r'|^3}=\frac{|f''(x)|}{(1+|f'(x)|^2)^{3/2}}$
- **normal vector** $\vec N(t)=\frac{\tau'(t)}{|\tau'(t)|}$
- **binormal vector** $\vec B(t) = \vec T \times \vec N$ 
- **3 planes** : normal ($T$), osculating ($B$), recifying ($N$)
- **level(set) curves** : shape of the function giving a constant

## Differentiation of functions of several variables

### 1st derivative
- functions of n variables : $f:\mathbb R^n \to \mathbb R$
- limits must exist and be unique (same one) for **ALL** paths
  - continuous if $\lim_{(x,y)\to (a,b)}f(x,y)=f(a,b)$
  - can use substituion in limits (polar coordinates) 
- **partial derivative** : $f_x(x,y)=\frac{\partial f}{\partial x}\quad f_y(x,y)=\frac{\partial f}{\partial y}$
- **directional derivative** : $D_{\vec v} f=\lim_{h\to 0}\frac{f(x+ah,y+bh)-f(x,y)}{h}=\nabla f \cdot \vec v$ where $\vec v = < a,b >$ and $|\vec v|=1$
- **gradient** : $\nabla f=< \frac{\partial f}{\partial x},\frac{\partial f}{\partial y} >$
- **tangent plane/linear approximation** : $l(\vec x)=f(\vec x_0)+\nabla f(\vec x_0)\cdot (\vec x-\vec x_0)$
- differentiable at $\vec x_0$ if $l(\vec x)$ exists such that $f(\vec x)=l(\vec x)+r(\vec x)$ and $\lim_{\vec x\to \vec x_0} \frac{r(\vec x)}{|\vec x-\vec x_0|}=0$ or if partial derivatives are contineous
- **direction of maximal increase** $\vec v^+=\frac{\nabla f}{|\nabla f|}$
- **direction of maximal decrease** $\vec v^-=-\frac{\nabla f}{|\nabla f|}$
- **direction of no chance** $\vec v$ is perpendicular to $\nabla f$
- **normal vector/plan** : $\vec n = < \nabla f, -1 >$ or $\vec n = <-\nabla f, 1 >$

### 2nd derivative
- if $f_{xy}$ and $f_{yx}$ are continuous then $f_{xy}=f_{yx}$
- **second derivative** : $D_{\vec w \vec v}f=\vec w^T \vec H \vec v$
- **Hessian** : $\vec H = \begin{bmatrix} f_{xx}&f_{xy}\\ f_{yx}&f_{yy} \end{bmatrix}$ or $\vec H_{ij}=\frac{\partial^2 f}{\partial x_i \partial x_j}$
- **quadratic approximation** : $q(\vec x)=f(\vec x_0)+\nabla f(\vec x_0)\cdot (\vec x-\vec x_0)+\frac{1}{2}\vec (x-\vec x_0)^T \vec H (\vec x_0)(\vec x-\vec x_0)$
- **extrema** $\nabla f(\vec x)=0$
  - if $f_{xx} > 0$ and $|H|=f_{xx}f_{yy}-f_{xy}^2 > 0$, it is a minimum
  - if $f_{xx} < 0$ and $|H|=f_{xx}f_{yy}-f_{xy}^2 > 0$, it is a maximum
  - if $|H|=f_{xx}f_{yy}-f_{xy}^2 < 0$, it is a saddle point
  - do not forget to check if boundaries (lines, circles) are smaller/bigger than critical points
- **eigenvalues** $Q(\vec h)=\frac{1}{2}\vec h^T \vec H \vec h$
  - $Q(h) > 0$ if all eigenvalues of $\vec H$ are positive
  - $Q(h) < 0$ if all eigenvalues of $\vec H$ are negative
  - if all eigenvalues are positive, it is a local minima
  - if all eigenvalues are negative, it is a local maxima
  - if eigenvalues change sign, it is a saddle point

### More
- $C^1$ is the class of functions for which $\nabla f$ exists and is continuous 
- $C^2$ is the class of functions for which $\vec H$ exists and is symmetric 
- **Taylor polynomial** of order $2$ : $T_{x_0}^1(\vec x)=f(\vec x_0)+(\vec x - \vec x_0)\cdot \nabla f(\vec x_0)+\frac{1}{2}(\vec x - \vec x_0)^T \vec H (\vec x - \vec x_0)$
- Taylor $T_{x_0}^j$ exist if $C^j$ exist : $T_{x_0}^j(\vec x)=\sum_{k=0}^j\frac{1}{k!}((\vec x-\vec x_0)\cdot\nabla)^k f(\vec x_0)$
- **chain rule** : $\frac{df}{dt}=\nabla f \cdot \vec x'$ and $\frac{df}{dt_i}=\nabla\cdot \frac{d\vec x}{dt_i}$
- **implicit function theorem** : $f'(x)=-\frac{f_x}{f_y}$
- **constrained optimization** : find $\vec x_0$ such that $\nabla f=\lambda \nabla g$ knowing $g(x,y)=k$
  - Lagrange multiplier $\lambda$
  - multiple constrained $\nabla f = \sum_{i=1}^k \mu_i \nabla g_i$ with $i=1\ldots k \quad g_i(x)=c_i$

## Multi-dimensional integrals

### Integration over a domain
- **Fubine theorem** : if continuous, $\int_a^b \int_c^d f(x,y) dx dy=\int_c^d \int_a^b f(x,y) dy dx$
- variable separation : $f(x,y)=g(x)h(y)\quad \int_a^b \int_c^d f(x,y)dx dy=\int_a^b g(x)dx \int_c^d h(y)dy$
- **variable bounds** : $V=\int_a^b \int_{f(x)}^{g(x)} f(x,y) dx dy$ 
- $(x,y)=[a,b]\times [f(x), g(x)]$ : $\int_{\mathbb D} h(x,y) dx dy = \int_a^b \int_{f(x)}^{g(x)} h(x,y)dxdy$
- $(x,y)=[f(y), g(y)]\times [c,d]$ : $\int_{\mathbb D} h(x,y) dx dy = \int_c^d \int_{f(y)}^{g(y)} h(x,y)dxdy$
- $\int_{\mathbb D} f(\vec x)d\vec x=\int_{\mathbb D_1} f(\vec x)d\vec x+\int_{\mathbb D_2} f(\vec x)d\vec x$
- $\int_E f(\vec x)d \vec x=\int_a^b \int_{g_1(x)}^{g_2(x)} \int_{u_1(x,y)}^{u_2(x,y)} f(x,y,z) dz dy dx$
- caution on boundaries : $x=\sqrt{4-y^2}$ is only a half circle
- caution on axes (y-axis first ?)

### Surface and substitution
- **surface area** : $S=\int_{\mathbb D} \sqrt{1+(f_x)^2+(f_y)^2}d\mathbb A$
- **Jacobian** : $J=|\frac{\partial(x,y)}{\partial(u,v)}|=\begin{vmatrix} \frac{dx}{du}&\frac{dx}{dv} \\ \frac{dy}{du}&\frac{dy}{dv}\end{vmatrix}$
- **substitution** : $\int_{\mathbb D}f(\vec x) d\vec x = \int_S f(T(\vec u)) J d\vec u$
  - polar coordinates : $x = r \cos \theta\quad y = r\sin\theta\quad J=r$ and $\int_{\mathbb D}f(\vec x)d\vec x = \int_a^b \int_{g(\theta)}^{f(\theta)} f(r,\theta)r dr d\theta$
  - cylindrial coordinates : $x = r \cos \theta\quad y = r\sin\theta\quad z=z \quad J=r$
  - spherical coordinates : $x = \rho \sin \phi \cos \theta\quad y = \rho \sin\phi\sin\theta\quad z=\rho\cos\phi \quad J=\rho^2\sin \phi$ where $0 \le \theta \le 2\pi$ and $0\le \phi\le\pi$ (starting on the positive y-axis side)
  - affine transformations : (exemple : barycentric coordinates) $\vec x = \vec v_1 \beta_1 + \vec v_2 \beta_2 \quad 0 \le \beta_i \le 1 \quad \beta_1+\beta_2=1$
  - rotation matrix : $A=\begin{pmatrix} \cos \theta && -\sin \theta \\ \sin \theta && \cos \theta \end{pmatrix}$ 

## Differential equations

### 1st order linear
- **modeling** : $P(0)=P_0\quad P(t)=P_0 e^{kt}$
- **model for world population** : $P'=kP(1-\frac{P}{M})$ 
- **critical points & equilibrium points** $\frac{dp}{dt}=0$
- direction fields : $f(v,t)=v'$ 
- **separable equations** : $\frac{du}{dx}=g(x)f(u) \Rightarrow \int\frac{1}{f(u)}dx=\int g(x)dx$
- **linear equations** : all continuous $\frac{du}{dx}+P(x)u=Q(x) \Rightarrow u(x)=\frac{1}{I(x)}\int I(x)Q(x)dx +C$ where $I=e^{\int P(x) dx}$
- **Picard's theorem** : if $f(u,t)$ is continuous in $t$ and Lipschitz in $u$ (means L exist such that $|f(u,t)-f(v,t)|\le L|u-v|$), then a unique solution exist $u(t)=u(0)+\int_a^b f(u(s), s) ds$
- **stability** : if $|u(0)-u_0|\le \epsilon$, it is stable if there exists $\gamma$ such that $|u(t)-u_0| < \gamma\forall t$
- **linear systems** : $\frac{d\vec u}{dt}=\vec A \vec u$ where $\vec A = \begin{pmatrix}a&b \\ c&d\end{pmatrix}$ (can be the Jacobian)
  - if eigenvalues are positive, it is unstable
  - if eigenvalues are negative, it is stable
  - if the product of eigenvalues is negative, it is a saddle point
- **predator prey models** : prey $R'=kR$ and predator $W'=-rW$ (predator has a negative slope)
- **predator prey solutions** : $R'=kR-aRW\quad W'=-rW+bRW \Rightarrow R=\frac{r}{b}\quad W=\frac{k}{a}$
- prey over predator is non linear : $k\ln W-aW=-r\ln R +bR+C$
- **money rate change model** : $x'=\frac{M-x}{M}$

### 2nd order linear
- $P(x)\frac{d^2u}{dx^2}+Q(x)\frac{du}{dx}+R(x)u=G(x)$
- if $G(x)=0$, it is homogeneous
- if $u_1(x)$ and $u_2(x)$ are linearly independent, then all solutions are expressed as $u(x)=c_1u_1(x)+c_2u_2(x)$
- take the homogeneous, guess the solution $u(x)=\alpha e^{rx}$, find the **characteristic equation**  $ar^2+br+c=0$
- if **delta is postive**, $r_1$ and $r_2$ are real, $u(x)=c_1 e^{r_1x}+c_2 e^{r_2x}$
- if **delta is negative**, solutions are complex, $u(x)=c_1 e^{r_1x}+c_2 e^{r_2x}=e^{\alpha x}(c_1\cos \beta x+c_2 \sin \beta x)$
- if **delta is null**, solutions are the same and real $u(x)=c_1 e^{rx}+c_2 x e^{rx}$
- given a particular solution and the general homogeneous then the **general solution** inhomogeneous is $u(x)=u_p(x)+u_h(x)$
- entered the guessed (polynomial, exponential, trigonometric) general inhomogeneous solution in the equation and solve

## Appendix

### Algebraic identities
- $x^3+y^3=(x+y)(x^2-xy+y^2)$
- $\sqrt{b}-\sqrt{a}=\frac{b-a}{\sqrt{b}+\sqrt{a}}$
- $\frac{1}{2}+\frac{1}{2^2}+\frac{1}{2^3}+\cdots+\frac{1}{2^n}=1-\frac{1}{2^n}$
- $\sqrt{1+x}=1+\frac{x}{2}$ when $x << 1$

### Trigonometric identities
- $\sin x=\frac{e^{ix}-e^{-ix}}{2i}$
- $\cos x=\frac{e^{ix}+e^{-ix}}{2}$
- $2\sin^2 t = 1-\cos 2t$
- $2\cos^2 x = 1+\cos 2x$
- $\sin 2x = 2\sin x \cos x$
- $\sin(a+b)=\sin a\cos b+\cos a\sin b$
- $\cos(a+b)=\cos a\cos b-\sin a\sin b$
- $\tan^2 x +1=\frac{1}{\cos^2 x}$
- $\cot^2 x +1=\frac{1}{\sin^2 x}$
- $\sin 0 = \frac{1}{2}\sqrt{0} = \cos \pi/2 = 0$
- $\sin \pi/6 = \frac{1}{2}\sqrt{1} = \cos \pi/3 = \frac{1}{2}$
  - $\sin \pi/4 =\frac{1}{2}\sqrt{2} = \cos \pi/4 =\frac{\sqrt{2}}{2}$
- $\sin \pi/3 = \frac{1}{2}\sqrt{3} = \cos \pi/6=\frac{\sqrt{3}}{2}$
- $\sin \pi/2 = \frac{1}{2}\sqrt{4} = \cos 0 = 1$

### Quadratic surfaces
- 3D
  - Ellipse $(\frac{x}{a})^2+(\frac{y}{b})^2+(\frac{z}{c})^2=1$
  - Hyperboloid 1 sheet $(\frac{x}{a})^2+(\frac{y}{b})^2-(\frac{z}{c})^2=1$ (nuclear reactor)
  - Hyperboloid 2 sheet $(\frac{x}{a})^2-(\frac{y}{b})^2-(\frac{z}{c})^2=1$ (two bowl)
  - Cone $(\frac{x}{a})^2+(\frac{y}{b})^2-(\frac{z}{c})^2=0$
  - Elliptic paraboloid $(\frac{x}{a})^2+(\frac{y}{b})^2=\frac{z}{c}$ (bowl)
  - Hyperbolic Paraboloid $(\frac{x}{a})^2-(\frac{y}{b})^2=\frac{z}{c}$ (saddle)
- 2D
  - Ellipse $(\frac{x}{a})^2+(\frac{y}{b})^2=1$
  - Hyperboles $(\frac{x}{a})^2-(\frac{y}{b})^2=1$

### Differentiation
- $\tan'x=\sec^2x$
- $\csc'x = -\csc x\cot x$
- $\sec'x = \sec x\tan x$
- $\cot'x = -\csc^2x$
- $\sin'^{-1}x = \frac{1}{\sqrt{1-x^2}}$
- $\cos'^{-1}x = -\frac{1}{\sqrt{1-x^2}}$
- $\tan'^{-1}x = \frac{1}{1+x^2}$
- $\csc'^{-1}x = -\frac{1}{x\sqrt{x^2-1}}$
- $\sec'^{-1}x = \frac{1}{x\sqrt{x^2-1}}$
- $\cot'^{-1}x = -\frac{1}{1+x^2}$

### Integration
- $\int \ln x dx = x \ln x - x$
- $\int x \ln xdx= \frac{1}{4}x^2(2\ln x -1)$
- $\int \frac{1}{x\log x}dx=\log (\log x)$
- $\int \frac{1}{x\log^2 x}dx=-\frac{1}{\log x}$
- $\int \frac{1}{x}dx = \ln |x|$
- $\int a^x dx = \frac{1}{\ln a} a^x$
- $\int \tan x dx = \ln |\sec x| $
- $\int \frac{a}{a^2+x^2}dx = \tan^{-1}\frac{x}{a}$
- $\int \frac{a}{a^2-x^2}dx = \frac{1}{2}\ln\left|\frac{x+a}{x-a}\right|$
- $\int \frac{1}{\sqrt{a^2-x^2}} dx = \sin^{-1} \frac{x}{a}$
- $\int \frac{1}{\sqrt{x^2-a^2}} dx = \cosh^{-1} \frac{x}{a}$
- $\int \frac{1}{\sqrt{x^2+a^2}} dx = \sinh^{-1} \frac{x}{a}$
- $\int \sin^{-1} x dx=\sqrt{1-x^2}+x\sin^{-1} x$
- $\int \cos^{-1} x dx=-\sqrt{1-x^2}+x\cos^{-1} x$
- $\int \tan^{-1} x dx=-\frac{1}{2}\ln(x^2+1)+x\tan^{-1} x$
- $\int \sin x \cos xdx = -\frac{1}{2}\cos^2 x$

### Analytic functions
- $\frac{1}{1-ax}=\sum_{n=0}^\infty (ax)^n=1+ax+ax^2+ax^3+\cdots$
- $\frac{1}{1+x}=\sum_{n=0}^\infty (-x)^n=1-x+x^2-x^3+\cdots$
- $\frac{1}{(1-x)^2}=\sum_{n=0}^\infty (n+1)x^n=1+2x+3x^2+4x^3+\cdots$
- $\sin x=\sum_{n=0}^\infty (-1)^n \frac{x^{2n+1}}{(2n+1)!}=x-\frac{x^3}{3!}+\frac{x^5}{5!}-\cdots$
- $\cos x=\sum_{n=0}^\infty (-1)^n \frac{x^{2n}}{(2n)!}=1-\frac{x^2}{2!}+\frac{x^4}{4!}-\cdots$
- $\tan^{-1} x=\sum_{n=0}^\infty (-1)^n \frac{x^{2n+1}}{2n+1}=x-\frac{x^3}{3}+\frac{x^5}{5}-\cdots$
- $ln(1+x)=\sum_{n=1}^\infty (-1)^n \frac{x^n}{n}=x-\frac{x^2}{2}+\frac{x^3}{3}-\cdots$