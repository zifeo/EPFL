# MATH101

> [GNU General Public License v3.0](https://github.com/zifeo/EPFL/blob/master/LICENSE) licensed. Source available on [github.com/zifeo/EPFL](https://github.com/zifeo/EPFL).

Fall 2013: Analysis I

[TOC]

### Sets

- subsets
- sets operations

### Functions

- vertical line test
- properties
  - even(symetric y-axis)/odd(symetric origine)
    - increasing/decreasing/monotone(in. or de.)
- important functions
  - constant/linear
    - polynomial
    - power
    - rational
    - exponential/logarithm
    - trigonometric : sin, cos, tan, csc, sec, cot
- linear transformation of functions
  - strech vertically : $cf(x)$
    - reflect about y-axis : $-f(x)$
    - shift vertically $f(x)+d$
    - shrink horizontally $f(cx)$
    - reflect about x-axis $f(-x)$
    - shift horizontally $f(x+d)$
- inverse function
  - one-to-one : never takes twice the same value
  - onto : every vale in the codomain is hit at least once
  - bijective : both
- piecewise defined function
- composite function
- some identities
  - $\sin 2x=2\sin x\cos x$
  - $\cos 2x=1-2\sin^2 x$
    - $x^3+y^3=(x+y)(x^2-xy+y^2)$
    - $\sqrt{b}-\sqrt{a}=\frac{b-a}{\sqrt{b}+\sqrt{a}}$
    - $\frac{1}{2}+\frac{1}{2^2}+\frac{1}{2^3}+\cdots+\frac{1}{2^n}=1-\frac{1}{2^n}$
    - $\tan^2 x +1=\frac{1}{\cos^2 x}$
    - $\cot^2 x +1=\frac{1}{\sin^2 x}$
    - $\sin(a+b)=\sin a\cos b+\cos a\sin b$
    - $\cos(a+b)=\cos a\cos b-\sin a\sin b$

### Sequences
- convergence
- properties
    - increasing/decreasing/monotone(in. or de.)

### Limits
A limit exists iff both sided limits exist.

- limits rules
- squeeze theorem
- bounds
- sequence definition of limits <=> eplison-delta defintion
- infinite limits
  - $e^x = \lim_{n\to \infty} (1+\frac{x}{n})^n$
- limits laws for functions

### Continuity
Continus if the limit exists at each point.

- intermediate value theorem :
  suppose $f$ continuous on $[a,b]$ and $f(a)\not =f(b)$, let $N$ be a number between $f(a)$ and $f(b)$, then there exist a $c$ such that $f(c)=N$.

- continuity of an inverse function
- discontinuities
  - removable discontinuities (one point displaced, sided limits equivalent)
    - jump discontinuities (sided limits differ)
    - infinite discontinuities (one sided limit does not exist)
    - be careful of absolute value when simplification
    - simplification does not change the discontinuities
- asymptotes
  - vertical $x \to a, f(x) \to \infty$
  - horizontal $x \to \infty, f(x) \to a$
    - $\frac{ax-b}{x+c}$ h-asy at $a$, v-asy at $-c$, x-intercept at $x=\frac{b}{a}$
    - slope of the obl-asy $=\lim_{x\to\infty} \frac{f(x)}{x}$

### Derivatives
$f'(x)=\lim_{x\to a}\frac{f(x)-f(a)}{x-a}$ ou

$f'(x)=\lim_{h\to 0}\frac{f(x+h)-f(x)}{h}$

- tagent line
- differentiable :
  differentiale except if there is a corner, a discontinuity or a vertical tangent.

- rules of differentiation
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
    - $\ln'g(x) = \frac{g'(x)}{g(x)}$
    - $\log_a'x = \frac{1}{x\ln a}$
    - chain rule
- derivative of inverse function :
  $(f^{-1})'(a)=\frac{1}{f'(f^{-1}(a))}$ ou
  $(f^{-1})'(f(a))=\frac{1}{f'(a)}$.

- extreme value theorem :
  if $f$ continuous on $[a,b]$, then $f$ attains an absolute maximum and an absolute minimum on some number in that interval.

- Bolzano-Weierstress theorem :
  every bounded sequence has a convergent subsequence.

- Fermat's theorem :
  if $f$ has a local extremum at $c$ and $f'(c)$ exists, then $f'(c)=0$.

- critical numbers/points :
  a **critcal number** of a function $f$ is a number $c$ in the domain of $f$ such that either $f'(c)=0$ or $f(c)$ does not exist. Can also be a vertical tangent but it has to be defined in the domain.

- local maximum/minimum near a point
- absolute/global maximum/minimum
- closed interval method :
  find the values of $f$ at the critical numbers on $[a,b]$ **and** at the endpoints of the interval, then the largest is the maximum and vice versa.

- Rolle's theorem :
  if $f$ continuous on $[a,b]$ and differentiable on $(a,b)$ and $f(a)=f(b)$, then there is a number $c$ in $(a,b)$ such that $f'(c)=0$.

- mean value theorem :
  if $f$ continuous on $[a,b]$ and differentiable on $(a,b)$, then there is a number $c$ in $(a,b)$ such that $f'(c)=\frac{f(b)-f(a)}{b-a}$.

- function increasing/decreasing
- 1st derivative test :
  - if $f'$ changes from postive to negative at $c$, it is a local maximum
    - if $f'$ changes from negative to positive at $c$, it is a local maximum
    - if $f'$ does not change sign at $c$, nothing
    - if $\forall x > c, f'(x)>0$ and $\forall x < c, f'(x)<0$, then $f(c)$ is the absolute maximum
    - if $\forall x > c, f'(x)<0$ and $\forall x < c, f'(x)>0$, then $f(c)$ is the absolute minimum
- function bendings (inflexion points)
- concavity test :
  - if $\forall x \in I, f''(x) > 0$, the function is concave upward on I :)
    - if $\forall x \in I, f''(x) < 0$, the function is concave downward on I :(
- Cauchy's mean value theorem :
  let $f$,$g$ be continuous on $[a,b]$ and differentiable in $(a,b)$, then $\frac{f'(c)}{g'(c)}=\frac{f(b)-f(a)}{g(b)-g(a)}$.

- De l'Hospital's rule :
  suppose $f$ and $g$ are differentiable and $g'(x)\not = 0$ on an open interval $I$ that contains $a$. If the limit $f$ and the limit $g$ go both to $0$ or $\infty$ as $x\to a$, then $\lim_{x\to a} \frac{f'(x)}{g'(x)}$. 

### Series
- arithmetic series :
  converge to $\sum_{n=1}^\infty n=\frac{n(n+1)}{2}$

- geometric series :
  converge to $\sum_{n=1}^\infty ar^{n-1}=\frac{a}{1-r}$ if $|r|<1$

- Riemann series :
  $\sum_{n=1}^\infty \frac{1}{p^\alpha}$ converges if $\alpha >1$
- laws of sequences
- sequences and series :
  if the series $\sum a_n$ is convergent, then $\lim a_n=0$.

- find the terms :
  $S_n - S_o = a_n$ where $S_o$ is the one before $S_n$.

- convergences tests
  - divergence test : if $\lim a_n$ does not exist or is not equal to $0$, then the series is divergent.
    - limit test : (both positive) if $\lim_{n\to \infty} \frac{a_n}{b_n}=c$ where $c$ is a finite number bigger than $0$, then either both converge or diverge.
  - comparison test
    - alternating series test : if for all postive the next is smaller than the previous one and $\lim_{n\to \infty} b_n=0$, then the series converge.
  - ratio test : $\lim_{n\to \infty} |\frac{next}{previous}|$ gives less than $1$, it is convergent, divergent if bigger than $1$, else inconclusive.
    - root test : $\lim_{n\to \infty} \sqrt[n]{|a_n|}$, same conclusion as ratio test.
    - integral test : for continuous, positive, deacreasing function on $[1,\infty)$, the series is convergent iff $\int_1^\infty f(x)dx$ is convergent.
- alternating series
- absolute convergence (conditionnaly) :
  a series $\sum a_n$ is called **absolutely** convergent if $\sum |a_n|$ converges, it is conditionnaly convergent.

- power series : $\sum_{n=0}^\infty c_n(x-a)^n$ is called centered at $a$.
  - radius of convergence : series could converge only when $x=a$, for all $x$ or for a positive number $R$ such that the series converges if $|x-a|<R$. Apply ratio test to find it.
    - infinite many times differentiable
    - derivative/integration
- Taylor series (called Mclaurin series if centered at $0$) : $\sum_{n=0}^\infty \frac{f^{(n)}(a)}{n!}(x-a)^n$
- analyctic functions
  - $\frac{1}{1-ax}=\sum_{n=0}^\infty (ax)^n=1+ax+ax^2+ax^3+\cdots$
    - $\frac{1}{1+x}=\sum_{n=0}^\infty (-x)^n=1-x+x^2-x^3+\cdots$
    - $\frac{1}{(1-x)^2}=\sum_{n=0}^\infty (n+1)x^n=1+2x+3x^2+4x^3+\cdots$
    - $\sin x=\sum_{n=0}^\infty (-1)^n \frac{x^{2n+1}}{(2n+1)!}=x-\frac{x^3}{3!}+\frac{x^5}{5!}-\cdots$
    - $\cos x=\sum_{n=0}^\infty (-1)^n \frac{x^{2n}}{(2n)!}=1-\frac{x^2}{2!}+\frac{x^4}{4!}-\cdots$
    - $\tan^{-1} x=\sum_{n=0}^\infty (-1)^n \frac{x^{2n+1}}{2n+1}=x-\frac{x^3}{3}+\frac{x^5}{5}-\cdots$
    - $ln(1+x)=\sum_{n=1}^\infty (-1)^n \frac{x^n}{n}=x-\frac{x^2}{2}+\frac{x^3}{3}-\cdots$

### Integral
- Riemann sum :
  $\lim_{x\to \infty} \sum_0^n f(x_i^*)\Delta x$
- rules of integration
  - $\int \frac{1}{x}dx=\log x$
  - $\int \frac{1}{x\log x}dx=\log (\log x)$
  - $\int \frac{1}{x\log^2 x}dx=-\frac{1}{\log x}$
- fundamental theorem of calculus :
  if $f$ is continuous on $I$ then the function $g$ is continuous, differentiable and definded by $g(x)=\int_a^x f(t)dt$ and $g'(x)=f(x)$.
  if $f$ in continous on $I$, then $\int_a^b f(x)dx = F(b)-F(a)$.