$$
\def\R{\mathbb R}
\def\C{\mathbb C}
\def\Z{\mathbb Z}
\def\N{\mathbb N}
\def\F{\mathcal F}
\def\T{\mathcal T}
\def\S{\mathcal S}
\def\Im{\operatorname{Im}}
\def\Re{\operatorname{Re}}
\def\Arg{\operatorname{Arg}}
\def\Log{\operatorname{Log}}
\def\f#1#2#3#4#5{\begin{align} #1 : #2 &\to #3 \\\ #4 &\mapsto #5 \end{align}}
\def\abs#1{\lvert\,#1\,\rvert}
\def\tl{\text{ tel que }}
\def\zz{z_0\in U}
\def\uz{U\setminus\{z_0\}}
\def\ztzz{\limits{z\to z_0}}
\def\cu{\in C^1(U,\C)}
\def\d{\text{ d}}
\def\cnst{\text{constante}}
\def\inte{\text{int }}
\def\long{\text{longueur }}
\def\res{\text{Rés}}
\def\otpi{\frac{1}{2\pi i}}
\def\sumi{\sum_{n=0}^\infty}
\def\inti{\int _{-\infty}^\infty}
$$

# MATH207

> [GNU General Public License v3.0](https://github.com/zifeo/EPFL/blob/master/LICENSE) licensed. Source available on [github.com/zifeo/EPFL](https://github.com/zifeo/EPFL).

Sping 2015: Analyse IV 

[TOC]

## 1 Fonctions complexes et équations de Cauchy-Riemann

### 1. Introduction

- analyse réel : $f:A\to\R^m$ où $A\subseteq\R^n$
- analyse complexe : $f:A\to\C^{(m)}$ où $A\subseteq\C^{(n)}$
- fonctions réeles s'étendent naturement sur les complexes

### 2. Fonctions complexes : définitions

- **fonction complexe** : $\f{f}{A}{\C}{z=x+iy}{f(z)=u(x,y)+iv(x,y)}$ où $\emptyset\not=z\in A\subseteq\C$
- **partie réele** : $\Re z = x\in\R$ et $\Re f=u\in\R$
- **partie imaginaire** : $\Im z = y\in\R$ et $\Im F=v\in\R$
- abus de notation : $A$ est souvent vu comme un sous-ensemble de $\R^2$

### 3. Exemples

- conjugé : $f(z)=\bar z=x-iy$
- inverse : $\displaystyle f(z)=\frac{1}{z}=\frac{1}{x+iy}=\frac{x-iy}{x^2+y^2}=\frac{x}{x^2+y^2}+i\frac{(-y)}{x^2+y^2}$

### 4. Argument

- **module** : $\abs z=\sqrt{x^2+y^2}\in[0,\infty)$
- **argument** : $\arg z=\theta\in\R$ défini à $2k\pi$ près où $k=\Z$
- forme cartésienne : $z=x+iy$
- **forme polaire** : $z=\abs z (\cos \theta +i\sin\theta)=\abs z e^{i\theta}$
- **fonction multivoque** : plusieurs valeurs de sortie pour une valeur d'entrée (par ex. définition à $2\pi k$ près)
- pas de convention : pour $z\in\C\setminus(-\infty,0]$, on note $\Arg z\in(-\pi,\pi]$ mais $\Arg z=\pi$ ou $\Arg z=-\pi$ selon les auteurs
- **différence** : $\Arg (zw)\not=\Arg z+\Arg w$

### 5. Exponentiel

- $e^z=e^{x+iy}=e^xe^{iy}=e^x(\cos y+i\sin y)$
- $e^z=u(x,y)+iv(x,y)$ où $u(x,y)=e^x\cos y$ et $v(x,y)=e^x\sin y$

### 6. Propriétés

- si $z\in\R$ alors $z=x$ et $e^z=e^x$
- $e^{z+w}=e^ze^w$ pour tous $z,w\in\C$
- pour $k\in\Z$, $e^{z+2k\pi i}=e^z$ (exponentiel périodique)
- $\abs {e^z}=e^x=e^{\Re z}>0$ (ni injectif, ni surjectif)
- $y$ est une valeur possible de l'argument : $\arg z = y$
- une droite fixée $\{x+iy : x\in\R\}$ est envoyée sur injectivement sur la demi droite $\{e^x(\cos y+i\sin y) : x\in\R\}$
- $f : A\to\C\setminus(-\infty,0]$ avec $A=\{x+iy : x\in\R, y\in(-\pi,\pi)\}$ est une bijection
- les droites $\{x\pm i\pi : x\in\R\}$ sont envoyées les deux sur $(-\infty, 0)$

### 7. Logarithme

- $\log z =\log\abs z +i \arg z$ avec $z\in\C^*$ (multivoque défini uniquement à $2k\pi i$ près)
- si précisé, la détermination du logarithme est notée $\Log z$ pour $z\in\C\setminus(-\infty,0]$ et $-\pi<\Arg z<\pi$
- lorsque $z\in(0,\infty)$, on a $\log z\in\R$ sauf mention du contraire
- $\Log(zw)\not=\Log z + \Log w$

### 8. Propriétés

- soient $z\in\C^*$ et $w\in\C$ alors $w$ est une valeur possible de $\log z\iff z=e^w$
- pour $\theta\in(-\pi,\pi)$ fixé : la demi-droite $\{re^{i\theta} : r > 0\}$ est envoyée sur la droite $\{\log r +i\theta : r > 0\}=\{s+i\theta: s\in\R\}$

### 9. Limites, continuité, dérivée

- **ouvert** : $U$ est ouvert si $\forall z_0\in U\quad \exists \delta > 0 \tl \forall z\in\C \abs{z-z_0}<\delta \Rightarrow z\in U$
- **limite** : $U$ ouvert et $f:U\setminus\{z_0\}\to\C$ possède $\lim_\limits{z\to z_0}f(z)=l\in\C$ en $\zz$ si $\forall\epsilon >0\;\exists\delta > 0\tl\forall z\in U\setminus\{z_0\}\quad\abs{z-z_0}<\delta\Rightarrow\abs{f(z)-l}<\epsilon$
- **continu** : $U$ ouvert et $f$ vue comme définie sur $\uz$ possède la limite $f(z_0)=\lim_\limits{z\to z_0} f(z)$
- **dérivable** : $U$ ouvert et la dérivée $\displaystyle f'(z_0)=\lim_\ztzz \frac{f(z)-f(z_0)}{z-z_0}$ existe dans $\C$
- **holomorphe (analytique)** : $U$ ouvert et si dérivable en tout point de $U$

### 10. Règles de dérivation

- **analogue au cas réel si holomorphe** : addition, multiplication
- division : si $g$ ne s'annule pas sur $U$, alors $\displaystyle(f/g)'=\frac{f'g-fg'}{g^2}$
- composition : si holomorphe $(f\circ g)'=(f'\circ g)g'$

### 11. Théorème de la continuité de la dérivée

- soit $f$ holomorphique sur $U$ ouvert, alors $f'\cu$ (continue)

### 12. Equations de Cauchy-Riemann et théorème d'équivalence

- **équivalence** : $f$ holomorphique sur $U$ et $f'\cu$, alors $z=x+iy$ où $x=u(x,y)$ et $y=v(x,y)$ satisfait les équations de Cauchy-Riemann
- **équations de Cauchy-Riemann** : $\forall (x,y)\in U\quad u_x(x,y)=v_y(x,y)\quad u_y(x,y)=-v_x(x,y)$
- **matrice jacobienne** : pour $\tilde{f}(x,y)=\begin{pmatrix}u(x,y)\\\ v(x,y)\end{pmatrix}$, on a $\begin{pmatrix}u_x& u_y\\\ v_x & v_y\end{pmatrix}$ doit être de la forme $\begin{pmatrix}a& b\\\ -b & a\end{pmatrix}$
- **formule de dérivation** : si $f'\cu$ et matrice jacobienne alors $f'(z)=u_x(x,y)+i v_x(x,y)=v_y(x,y)-i u_y(x,y)$

### 13. Exemples

- $f(z)=e^z=e^x(\cos y + i\sin y)$ donne $u_x=e^x\cos y=v_y\quad u_y=-e^x\sin y=-v_x$ et $f'(z)=u_x+i v_x = e^x\cos y+i e^x\sin y=e^z$
- $f(z)=\log z=\log\sqrt{x^2+y^2}+i\arctan{\frac{x}{y}}$ donne $\displaystyle u_x=\frac{x}{x^2+y^2}=v_y\quad u_y=\frac{y}{x^2+y^2}=-v_x$ et $\displaystyle f'(z)=u_x+iv_x=\frac{x-iy}{x^2+y^2}=z^{-1}$

### 14. Preuve de l'équivalence

- 1 => 2
  - supposons $f$ analytique sur $U$ ouvert
  - fixons $z_0=x_0+i y_0\in U$ avec $x_0,y_0\in\R$
  - par hypothèse $\displaystyle \lim_\ztzz\frac{f(z)-f(z_0)}{z-z_0}$ existe dans $\C$
  - considérant $z$ de la forme $z=x+iy_0$ alors $\displaystyle f'(z_0)=\lim_\limits{x\to x_0}\frac{[u(x,y_0)-u(x_0,y_0)]+i[v(x,y_0)-v(x_0,y_0)]}{(x+iy_0)-(x_0+iy_0)}=\lim _\limits{x\to x_0}\frac{u(x,y_0)-u(x_0,y_0)}{x-x_0}+i\lim _\limits{x\to x_0}\frac{v(x,y_0)-v(x_0,y_0)}{x-x_0}=u_x(x_0,y_0)+i v_x(x_0,y_0)$
  - considérant $z$ de la forme $z=x_0+iy$ alors $\displaystyle f'(z_0)=\lim_\limits{y\to y_0}\frac{[u(x_0,y)-u(x_0,y_0)]+i[v(x_0,y)-v(x_0,y_0)]}{(x_0+iy)-(x_0+iy_0)}=-i \lim _\limits{y\to y_0}\frac{u(x_0,y)-u(x_0,y_0)}{y-y_0}+\lim _\limits{y\to y_0}\frac{v(x_0,y)-v(x_0,y_0)}{y-y_0}=-i u_y(x_0,y_0)+v_y(x_0,y_0)$
  - comme $f'\cu$ par hypothèse $u_x,u_y,v_x,v_y$ aussi
- 2 => 1
  - supposons $u,v\cu$ et équations de Cauchy-Riemann satisfaitent
  - fixons $z_0=x_0+i y_0\in U$ avec $x_0,y_0\in\R$
  - on a $u(x,y)=u(x_0,y_0)+u_x(x_0,y_0)(x-x_0)+u_y(x_0,y_0)(y-y_0)+R_1(x,y)$ où $\displaystyle \frac{R_1(x,y)}{\sqrt{(x-x_0)^2+(y-y_0)^2}}\to 0$ lorsque $(x,y)\to(x_0,y_0)$
  - on a $v(x,y)=v(x_0,y_0)+v_x(x_0,y_0)(x-x_0)+v_y(x_0,y_0)(y-y_0)+R_2(x,y)$ où $\displaystyle \frac{R_2(x,y)}{\sqrt{(x-x_0)^2+(y-y_0)^2}}\to 0$ lorsque $(x,y)\to(x_0,y_0)$
  - d'où $f(z)=u(x,y)+iv(x,y)=u(x_0,y_0)+iv(x_0,y_0)+(x-x_0)[u_x(x_0,y_0)+i v_x(x_0,y_0)]+(y-y_0)[u_x(x_0,y_0)+i v_x(x_0,y_0)]+R_1(x,y)+iR_2(x,y)$ $=f(z_0)+[u_x(x_0,y_0)+iv_x(x_0,y_0)][(x-x_0)+i(y-y_0)]$
  - d'où $\displaystyle \lim_\ztzz\frac{f(z)-f(z_0)}{z-z_0}=u_x(x_0,y_0)+iv_x(x_0,y_0)$ car $\displaystyle \frac{R_1(x,y)+iR_2(x,y)}{\abs{z-z_0}}\to 0$
  - comme $u_x,v_x\cu$ par hypothèse $f'$ aussi

## 2. Théorème de Cauchy & formule de Cauchy

### 1. Courbres dans $\C$

- **définition** : soit $a<b$ dans $\R$ on a $\f{g}{[a,b]}{\C}{t}{g(t)=g_1(t)+ig_2(t)}$ où $g_1,g_2:[a,b]\to\R$
- **continuité** : $g\in C^n([a,b])$ et $g_1,g_2\in C^n([a,b])$
- **par morceaux** : $a=t_0<\cdots<t_n=b$
- **continue** : $\gamma\in C^1([t_k,t_{k+1}])$
- **régulière** : $\gamma'(t)\not = 0\quad\forall t\in[t_k,t_{k+1}]$
- **paramétrisation** : $\gamma:[a,b]\to\Gamma\subset\C$

### 2. Intégrale le long d'une courbe

- **définition classique** : $\int_a^b g(t)\d t=\int_a^b g_1(t)\d t+i\int_a^b g_2(t)\d t$
- **défintion** : $\displaystyle \int_\Gamma f(z)\d z = \int_a^b f(\gamma(t))\gamma'(t)\d t$

### 3. Exemples

- $f(z)=z^2$ avec $\gamma(\theta)=e^{i\theta}\in C^1([0,\pi])$ et $\gamma'(\theta)=ie^{i\theta}$, on a donc $\int_\Gamma f(z)\d z=\int_0^\pi ie^{3i\theta}\d\theta=-2/3$

### 4. Courbe simple, fermée, domain simplement connexe

- **simple** : restreinte à $[a,b)$ ou $(a,b]$ et injective
- **fermée** : $\gamma(a)=\gamma(b)$
- **connexe (domaine)** : si $z_1,z_2\in U$ ouvert et $\exists \Gamma\in C^1\tl \gamma(a)=z_1\quad\gamma(b)=z_2\quad\gamma'=\cnst$
- **théorème de Jordan** : si $\Gamma$ est une coubre simple fermée alors $\C\setminus\Gamma$ est l'union de deux ouverts connexes disjoints dont l'un est borné ($\inte\Gamma$)
- **domain simplement connexe** : $\forall\Gamma\subset D\quad \forall\inte\Gamma\subset D$ (courbes fermées et simples)
- **adhérence** : $\overline{\inte\Gamma}=\inte\Gamma\cup\Gamma$

### 5. Théorème de Cauchy

- soit $U$ ouvert, $f\cu$ holomorphique et une coubre simple fermée régulière par morceaux $\Gamma\tl\inte\Gamma\subset U$, alors $\int_\gamma f(z)\d z = 0$
- si $U$ simplement connexe, alors $\int\Gamma\subset U$ est automatique 

### 6. Exemples

- $f(z)=1/z$ : pas simplement connexe
- avec $\gamma(\theta)=2+e^{i\theta}$ on obtient $\int_\gamma 1/z\d z=0$

### 7. Formule intégrale de Cauchy

- soit $U$ ouvert, $f\cu$ holomorphique et une coubre simple fermée régulière par morceaux $\Gamma\tl\inte\Gamma\subset U$ orienté positivement (intérieur à gauche), alors $\displaystyle f(z)=\frac{1}{2\pi i}\int \frac{f(\xi)}{\xi-z}\d \xi\quad\forall z\in\inte\Gamma$

### 8 Exemple

- $\int_\gamma \frac{\cos(2z)}{z}\d z$
  - 1er cas $0\in\inte\Gamma$ : $g(\xi)=\cos 2\xi$ et $g(0)=\frac{1}{2\pi i}\int_\gamma\frac{g(\xi)}{\xi - 0}\d\xi$ donne $\int _\gamma\frac{\cos 2\xi}{\xi}\d\xi=2\pi i g(0)=2\pi i$
  - 2e cas $0\not\in\overline{\inte\Gamma}$ : théorème de Cauchy $=0$
  - 3e cas $0\in\overline{\inte\Gamma}$ : intégrale pas bien définie

### 9. Preuve du théorème de Cauchy

- supposons $\Gamma$ avec un seul morceau
- écrivons $f(z)=u(x,y)+iv(x,y)$ avec $z=x+iy\in U$ et $\gamma(z)=\gamma_1(t)+i\gamma_2(t)$ avec $t\in[a,b]$
- on obient $\displaystyle \int_\gamma f(z)\d z=\int_a^b f(\gamma(t))\gamma'(t)\d t=\int_a^b [u(\gamma_1,\gamma_2)+iv(\gamma_1,\gamma_2)](\gamma_1'+i\gamma_2') \d t=\int_a^b [u(\gamma_1,\gamma_2)\gamma_1'-v(\gamma_1,\gamma_2)\gamma_2']\d t+i\int_a^b [u(\gamma_1,\gamma_2)\gamma_2'+v(\gamma_1,\gamma_2)\gamma_1']\d t$
- posons $\Omega=\inte\Gamma$, $F(x,y)=\begin{pmatrix}u(x,y)\\\ -v(x,y)\end{pmatrix}$ et $G(x,y)=\begin{pmatrix}v(x,y)\\\ u(x,y)\end{pmatrix}$ pour $(x,y)\in U$
- alors $\displaystyle \int_\gamma f(z)\d z =\int _{\d\Omega}F·\d l+i\int _{\d\Omega}G·\d l=\int _\Omega(\frac{\partial F_2}{\partial x}-\frac{\partial F_1}{\partial y})\d x\d y+i\int _\Omega(\frac{\partial G_2}{\partial x}-\frac{\partial G_1}{\partial y})\d x\d y=\int _\Omega (-v_x-u_y)\d x\d y+i\int _\Omega (u_x-v_y)\d x\d y=0$
- en utilisant le théorème de Green et les équations de Cauchy-Riemann

### 10. Généralisation du théorème de Cauchy

- soit $U$ ouvert, $f\cu$ et $\Omega\subset\overline{\Omega}\subset U$ ouvert connexe (avec $\Gamma_i$ orienté positivement), alors $\sum_{j=0}^m\int_{\Gamma_j} f(z)\d z = 0$

### 11. Formule de majoration & preuve

- soit $U$ ouvert, $f\cu$ et une courbe par morceaux, alors $\displaystyle \abs{\int_\gamma f(z)\d z}\le\int_a^b\abs{f(\gamma(t))}\abs{\gamma'(t)}\d t\le\long(\gamma)\max _{z\in\Gamma}\abs{f(z)}$
- écrivons $\int_\gamma f(z)\d z=re^{i\theta}$ avec $r\in[0,\infty)$ et $\theta\in(-\pi,\pi]
- si $\gamma$ a un seul morceau, alors $\displaystyle \abs{\int_\gamma f(z)\d z}=r=e^{-i\theta} \int f(z)\d z=\int e^{-i\theta} f(z)\d z=\int_a^b e^{-i\theta} f(\gamma(t))\gamma'(t)\d t=\Re [\int_a^b e^{-i\theta} f(\gamma(t))\gamma'(t)\d t]=\int_a^b \Re [e^{-i\theta} f(\gamma(t))\gamma'(t)]\d t$ $\displaystyle \le \int_a^b \abs{e^{-i\theta} f(\gamma(t))\gamma'(t)}\d t\le\int_a^b \abs{f(\gamma(t))}\abs{\gamma'(t)}\d t\le \max _{z\in\Gamma}\abs{f(z)}\int_a^b\abs{\gamma'(t)}\d t$

### 12. Lemme

- soit $U​$ ouvert, $f\cu​$, $z_0\in U​$, pour $\epsilon > 0​$ et définissons $\gamma_\epsilon:[0,2\pi]\to\Gamma _\epsilon\in\C​$ par $\gamma _\epsilon(\theta)=z_0+\epsilon e^{i\theta}​$, alors $\displaystyle \lim _\limits{\epsilon\to 0}\abs{\otpi\int _{\gamma _\epsilon} \frac{f(z)}{z-z_0}\d z - f(z_0)}=0​$

### 13. Preuve de la formule intégrale de Cauchy

- fixons $z\in\inte\gamma$ et définissons $\gamma_\epsilon:[0,2\pi]\to\Gamma _\epsilon\in\C$ par $\gamma _\epsilon(\theta)=z_0+\epsilon e^{i\theta}$ avec $\epsilon > 0$ petit
- considérons $\Omega=\{\xi\in\inte\gamma : \abs{\xi - z} > \epsilon\}$
- observons que $\gamma_\epsilon$ est orienté négativement par rapport à $\Omega$
- par le théorème de Cauchy généralisé à $\Omega$ et à $\xi\to g(\xi)=\otpi \frac{f(\xi)}{\xi - z}$, on a $\displaystyle \int_\gamma g(\xi)\d\xi -\int _{\gamma _\epsilon} g(\xi)\d\xi = 0$
- d'où $\displaystyle \otpi\int_\gamma\frac{f(\xi)}{\xi-z}\d\xi=\otpi\int _{\gamma _\epsilon}\frac{f(\xi)}{\xi-z}\d\xi$ pour tout $\epsilon > 0$ petit
- ainsi $\displaystyle \abs{\otpi\int_\gamma\frac{f(\xi)}{\xi-z}\d\xi -f(z)}=\abs{\otpi\int _{\gamma _\epsilon}\frac{f(\xi)}{\xi-z}\d\xi - f(z)}\to 0$ lorsque $\epsilon\to 0$
- d'où $\displaystyle \otpi\int_\gamma\frac{f(\xi)}{\xi-z}\d\xi=f(z_0)$

### 14. Formule intégrale de Cauchy pour les dérivées

- soit $U$ ouvert, $f\cu$, alors $f$ est infiniment dériable sur $U\in\C$
- pour toute courbe simple, fermée, régulière par morceaux, orientée positivement telle que $\inte \Gamma\subset U$, on a $\displaystyle f^{(n)}(z)=\frac{n!}{2\pi i}\int_\gamma\frac{f(\xi)}{(\xi - z)^{n+1}}\d\xi\quad\forall z\in\inte\gamma$ ($n$ positif)

### 15. Exemple

- $\int_\gamma \frac{e^{z+2}}{(z-2)^3}\d z$
  - 1er cas $2\in\inte\Gamma$ : $g(\xi)=e^{\xi+2}$ et $g''(2)=e^4$ donne $2!\int _\gamma\frac{e^{\xi+2}}{(\xi-2)^3}\d\xi=2\pi i g''(2)=i\pi e^4$
  - 2e cas $2\not\in\overline{\inte\Gamma}$ : théorème de Cauchy $=0$
  - 3e cas $2\in\overline{\inte\Gamma}$ : intégrale pas bien définie

### 16. Lemme

- soit $U$ ouvert, une courbe $\gamma\cu$ par morceaux et $g\cu$, alors $\f{h_n}{\C\setminus\Gamma}{\C}{z}{h_n(z)=\int_\gamma\frac{g(\xi)}{(\xi - z)^n}\d\xi}$ pour $n\ge 1$ holomorphe et $h _n'(z)=n h _{n+1}(z)$ 

### 17. Preuve de la formule intégrale de Cauchy pour les dérivées

- soit $U$ ouvert, $f\cu$ et appliquons à $g=\frac{f}{2\pi i}$ le lemme précédent et $z\in\inte\gamma$
- d'où $\displaystyle f(z)=\otpi\int_\gamma\frac{f(\xi)}{\xi - z}\d\xi=\int _\gamma\frac{g(\xi)}{\xi-z}\d\xi=h_1(z)$ (infiniment dérivable)

## 3. Développement en série

### 1. Limite d'une suite dans $\C$

- soit une suite $\{z_n\}_{n=0}^\infty$, elle tend/converge vers la limite $l\in\C$ si $\lim _\limits{n\to\infty}\abs{z_n-l}=0$

### 2. Théorèment du développement en série de Taylor

- **polynome de Taylor** : $\displaystyle T_Nf(z)=\sum_{n=0}^N \frac{f^{(n)}(z_0)}{n!}(z-z_0)^n$ autour de $z_0$
- **rayon de convergence** : $R\in(0,\infty)\tl \{z\in\C : \abs{z-z_0}<R\}\subset U$
- si $\abs{z-z_0}<R$ alors $\displaystyle Tf(z)=\sum_{n=0}^\infty \frac{f^{(n)}(z_0)}{n!}(z-z_0)^n=f(z)$
- **formule intégrale** : $\displaystyle \frac{f^{(n)}(z_0)}{n!}=\otpi\int_ \gamma\frac{f(\xi)}{(\xi - z_0)^{n+1}}\d\xi$
- **reste (formule intégrale)** : $\displaystyle f(z)-T_Nf(z)=\frac{(z-z_0)^{N+1}}{2\pi i}\int_\gamma\frac{f(\xi)}{(\xi-z_0)^{N+1}(\xi-z)}\d\xi$

### 3. Exemple

- $e^z=\lim_\limits{N\to\infty}\sum _{n=0}^N\frac{1}{n!}z^n$ avec $z_0=0$ et $R=\infty$
- $\frac{1}{1-z}=\sum_{n=0}^\infty z^n$ avec $z_0=0$ et $R=1$

### 4. Développement en série de Laurent

- soit $U$ ouvert, $z_0\in U$ et $f:U\setminus\{z_0\}\to\C$ holomorphe à dérivées continues
- **singularité isolée** : $f$ n'est pas nécessairement définie en $z_0$
- **polynome de Laurent** : $\displaystyle L_Nf(z)=\sum_{n=-N}^N C_n(z-z_0)^n$ avec $\displaystyle C_n=\otpi\int _\gamma\frac{f(\xi)}{(\xi-z_0)^{n+1}}\d\xi$ autour de $z_0$
- **rayon de convergence** : $R\in(0,\infty)\tl \{z\in\C : \abs{z-z_0}<R\}\subset U$
- si $0<\abs{z-z_0}<R$ alors $\displaystyle Lf(z)=\sum_{n=-\infty}^\infty C_n(z-z_0)^n=f(z)$
- si $0<s_1<s_2<R$ alors $\lim_\limits{N\to\infty}\max\{\abs{f(z)-L_Nf(z)} : s1\le\abs{z-z_0}\le s_2\}$
- **partie régulière** : $0$ à $\infty$
- **partie singulière (ou principale)** : $-\infty$ à $-1$
- **si défini en $z_0$** : $\displaystyle C_n=\otpi\int_\gamma f(\xi)(\xi-z_0)^{-n-1}\d\xi=0\quad\forall n\ge 1$ (car théorème de Cauchy et Taylor équivalent)

### 5. Définition

- **si partie singulière nulle** : $z_0$ point régulier
- **si $m\ge 1$ pour $\displaystyle \sum_ {n=-m}^N C_n(z-z_0)^n$** : $z_0$ pôle d'ordre $m\quad\forall k\ge m + 1\tl C_{-k}=0$
- **si partie singulière entière non-nulle** : singularité essentielle isolée
- r**ésidu de $f$ en $z_0$** : $\displaystyle \res_ {z_0}(f)=\res(f;z_0)=C_{-1}=\otpi\int _\gamma f(\xi)\d\xi$

### 6. Singularité éliminable

- supposons qu'il est possible de définir $f$ en $z_0$ de telle manière que $f$ soit continue en $z_0$
- dans ce cas $z_0$ : singularité éliminable (supprimable, apparente ou articielle) avec partie singulière nulle

### 7. Exemples

- $f(z)=\frac{1}{z}$ en $z_0=0$ : $U=\C$, $R=\infty$, $Lf(z)=\frac{1}{z}+0$, $\res_0(f)=1$, pôle d'ordre $1$
- $f(z)=\frac{1}{z}$ en $z_0=1$ : $U=\C^*$, $R=1$, $Lf(z)=Tf(z)$, défini
- $f(z)=\frac{1}{z^2}$ en $z_0=0$ : $U=\C$, $R=\infty$, $Lf(z)=\frac{1}{z^2}+0$, $\res_0(f)=0$, pôle d'ordre $2$
- $f(z)=\frac{1}{z^3}+\frac{2}{z}$ en $z_0=0$ : $U=\C$, $R=\infty$, $Lf(z)=\frac{1}{z^3}+\frac{2}{z}+0$, $\res_0(f)=2$, pôle d'ordre $3$
- $f(z)=\frac{1}{z^2+z}=\frac{1}{z}-\frac{1}{z+1}$ en $z_0=0$ : $U=\C\setminus\{-1\}$, $R=1$, $Lf(z)=\frac{1}{z}-\frac{1}{1-(-z)}=\frac{1}{z}-\sum_{n=0}^\infty (-z)^n$, $\res_0(f)=1$, pôle d'ordre $1$
- $f(z)=e^{1/z}$ en $z_0=0$ : $U=\C$, $R=\infty$, $Lf(z)=\sumi\frac{(1/z)^n}{n!}=1+\sum_{n=1}^\infty \frac{1}{n!}z^{-n}$, $\res_0(f)=\frac{1}{1!}=1$, singularité essentielle isolée
- $f(z)=\frac{\sin z}{z}$ en $z_0=0$ : singularité éliminable
- $f(z)=\tan\frac{1}{z}$ en $z_0=0$ : singularité non isolée car $U=\C\setminus\{\frac{1}{\pi/2+k\pi} : k\in\Z\}$

### 8. Remarque

- tout point défini est une singularité éliminable et ainsi la théorie des fonctions analytiques s'applique
- **si $z_0$ singularité supprimable** : $\tilde f (z)=\begin{cases}f(z)&z\not=z_0\\\ C_0&z=z_0\end{cases}$ holomorphe
- **zéro d'ordre $m\in\N$** : si $C_k=0\quad\forall k < m$ et $C_m\not=0$

### 9. Critère du quotient

- **pour $f(z)=P(z)/Q(z)$ où $P$ et $Q$ holomorphe** : $P$ zéro d'ordre $k$ en $z_0$ et $Q$ zéro d'ordre $l$ en $z_0$
  - $l>k$ : $f$ pôle d'ordre $l-k$
  - $l<k$ : $f$ zéro d'ordre $k-l$
  - $l=k$ ; $f$ singularité supprimable
- **règle de l'Hospital pour $l\le k$**

### 10. Critère de la limite

- **si $\lim_\ztzz (z-z_0)^m f(z)=a\in C\not = 0$**
  - pôle d'ordre $m$ si $m> 0$
  - singularité supprimable si $m\le 0$
  - zéro d'ordre $-m$ si $m\le -1$
- **si $\lim_\ztzz \abs{f(z)}=\infty$** : pôle
- **si $\lim_\ztzz \abs{f(z)}$ n'existe pas dans $\R _+\cup\{\infty\}$** : singularité essentielle (réciproque vrai)

### 11. Méthode pour calculer les résidus

- **si singularité supprimable** : $\res(f,z_0)=0$
- **si pôle d'orde $1$** : $\res(f,z_0)=\lim_\ztzz [(z-z_0)f(z)]$
- **si critère du quotient et zéro simple de $Q$** : $\res(f,z_0)=P(z_0)/Q'(z_0)$
- **si pôle d'ordre $m\ge 2$** : $\displaystyle \res(f,z_0)=\lim_\ztzz\frac{1}{(m-1)!}\frac{\d^{m-1}}{\d z ^{m-1}}[(z-z_0)^mf(z)]$
- ou trouver la série de Laurent

### 12. Exemple

- $f(z)=\frac{\sqrt{z}}{(z-1)^2}=\frac{e^{\log(z)/2}}{(z-1)^2}$ en $z_0=1$ : critère de la limite donne pôle d'ordre $2$ et $\res(f,1)\lim_\limits{z\to1}\frac{\d}{\d z}[(z-1)^2f(z)]=1/2$

### 13. Théorème de Liouville

- soit $f$ holomorphe : si $f$ est bornée sur $\C$, alors $f$ est constante

### 14. Théorème fondamental de l'algèbre

- tout polynôme non constant admet au moins un zéro

### 15. Preuve du développement en série de Laurent

## 4. Théorème des résidus

### 1. Résidus & preuve

- soit $U$ ouvert, coubre $\gamma$ simple, fermée, régulière par morceaux, orientée positivement
- soient des complex distincts $z_0,\ldots,z_m\in\inte\gamma$ et $f\in C^1(U\setminus\{z_0,\ldots,z_m\},\C)$
- alors $\int_\gamma f(z)\d z=2\pi i\sum _{k=1}^m\res _{z_k}(f)$
- calcul de l'intégrale se rampne à celui des résidus pour singularités isolées de $f$ comprise dans $\inte\gamma$
- supposons courbe $\f{\gamma_k}{[0,2\pi]}{\Gamma_k\in\C}{\theta}{\gamma_k(\theta)=z^k+\epsilon e^{i\theta}}$
- si $\epsilon >0$ assez petit, $\overline{\inte \gamma_k}\in U$ et disjoint deux à deux
- par le théorèmede Cauchy généralisé appliqué à $\Omega=\inte\gamma\setminus\bigcup_\limits{k=1}^m\overline{\inte \gamma_k}$
- on a $\displaystyle \int_\gamma f(z)\d z-\sum _{k=1}^m\int _{\gamma _k} f(z)\d z=0$ car $\gamma_k$ orienté négativement par rapport à $\Omega$
- d'où $\displaystyle \int_\gamma f(z)\d z=\sum _{k=1}^m\int _{\gamma _k} f(z)\d z=\sum _{k=1}^m 2\pi i \int _{\gamma _k} \frac{f(z)}{2\pi i}\d z=2\pi i\sum _{k=1}^m \res _{z_k}(f)$

### 2. Exemple

- $\int_\gamma (\frac{2}{z}+\frac{3}{z-1}+\frac{1}{z^2})$ : 2 singularité, $z_0=0$ pôle d'ordre $2$ avec $\res(f,0)=2$, $z_0=1$ pôle d'ordre $1$ avec $\res(f,1)=3$
  - 1er cas $0\in\inte\gamma$ et $1\in\inte\gamma$ : $\int_\gamma f(z)\d z = 2\pi i (2+3) = 10\pi i$
  - 2e cas $0\not\in\overline{\inte\gamma}$ et $1\in\inte\gamma$ : $\int_\gamma f(z)\d z = 4\pi i$
  - 3e cas $0\in\inte\gamma$ et $1\not\in\overline{\inte\gamma}$ : $\int_\gamma f(z)\d z = 6\pi i$
  - 4e cas $0\not\in\overline{\inte\gamma}$ et $1\not\in\overline{\inte\gamma}$ : $\int_\gamma f(z)\d z = 0$ (Cauchy)
  - 5e cas $0\in\Gamma$ ou $1\in\Gamma$ : pas bien défini

### 3. Calcul de $\displaystyle \int_0^{2\pi} f(\cos \theta,\sin\theta)\d\theta$

- supposons la forme $f(x,y)=P(x,y)/Q(x,y)$ des polynômes et $Q\not=0\quad\forall\theta\in[0,2\pi]$
- posons $z=e^{i\theta}$ : $\displaystyle \int_0^{2\pi} f(\frac{e^{i\theta}+e^{-i\theta}}{2},\frac{e^{i\theta}-e^{-i\theta}}{2i})\frac{(e^{i\theta})'}{ie^{i\theta}}\d\theta=\int_\gamma f(\frac{z+z^{-1}}{2},\frac{z-z^{-1}}{2i})\frac{1}{iz}\d z$ avec $\gamma:[0,2\pi]\to\C=\int_gamma \tilde f(z)\d z$ donné par $\gamma(\theta)=e^{i\theta}$
- on obtient $\displaystyle \int_0^{2\pi} f(\cos \theta,\sin\theta)\d\theta=2\pi i\sum_{k=1}^m\res _{z_k}(\tilde f)$

### 4. Exemple

- $\int_0^{2\pi}\frac{1}{2+\cos\theta}\d\theta=\int_\gamma\frac{2}{4+z+z^{-1}}\frac{1}{iz}\d z$
- $\tilde f(z)=\frac{1}{i(2z+z^2/2+1/2)}=\frac{2}{i((z+2)^2-3)}=\frac{2}{i(z+2+\sqrt{3})(z+2+\sqrt{3})}$
- deux pôles d'ordre 1 : $z_1=-2-\sqrt(3)$ et $z_2=\sqrt{3}-2$
- donc $\int_\gamma \tilde f(z)\d z=2\pi i\res _{z_2}(\tilde f)=2\pi i  \tilde P(z_2) = \frac{1}{i\sqrt{3}}$ car critère du quotient et $\tilde P(z)=\frac{2}{i(z+2+\sqrt{3})}$

### 5 Calcul de $\displaystyle \int_\R R(x)e^{i\alpha x}\d x$ avec $\alpha \ge 0$

- supposons $\alpha\in[0,\infty)$, $R(x)=P(x)/Q(x)\in\C$ polynôme ($Q\not=0$) et $\deg Q -\deg P\ge 2$
- prenons le demi-cercle supérieur avec le rayon tendant vers l'infini : la partie courbée tend vers $0$
- ainsi $\int_{-\infty}^\infty R(x)e^{i\alpha x}\d x=2\pi i\sum _{k=1}^m\res _{z_k}(R(z)e^{i\alpha z})$
- si $R(-x)=R(x)$ : $\int_{-\infty}^\infty R(x)e^{i\alpha x}\d x=\int _{-\infty}^\infty R(x)\cos(\alpha x)\d x$
- si $R(-x)=-R(x)$ : $\int_{-\infty}^\infty R(x)e^{i\alpha x}\d x=i\int _{-\infty}^\infty R(x)\sin(\alpha x)\d x$
- si $R(x)\in\R$ : $\int_{-\infty}^\infty R(x)e^{i\alpha x}\d x=\int _{-\infty}^\infty R(x)\cos(\alpha x)\d x+i\int _{-\infty}^\infty R(x)\sin(\alpha x)\d x=\int _{-\infty}^\infty R(x)e^{-i\alpha x}\d x$
- si $\alpha < 0$ : similaire mais avec le demi-plan inférieur

### 6. Exemple

- $\int_{-\infty}^\infty\frac{x^2}{16+x^4}\d x$ avec $\alpha = 0\quad P(x)=x^2\quad Q(x)=16+x^4$
- 4 zéros de $Q$ : lorsque $z=2e^{\pi/4+n\pi/2}$ on a $z_1=2e^{i\pi/4}\quad z_2=2e^{i3\pi/4}\quad z_3=2e^{i5\pi/4}\quad z_4=2e^{i7\pi/4}$
- d'où $\int_{-\infty}^\infty\frac{x^2}{16+x^4}\d x=2\pi i[\frac{\sqrt{2}}{16}(1-i)+\frac{\sqrt{2}}{16}(-1-i)]=\frac{\pi\sqrt{2}}{4}$
- parfois nécessaire de passer par la série de de Laurent

## 5. Distribution tempérée

### 1. Introduction

- **concept de fonction généralisé**
- notion d'impulsion (fonction delta)

### 2. L'espace de Schwartz

- **fonction de Schwartz** : $\varphi\in C^\infty(\R):\R\to\C$ à décroissance rapide telle que $\lim_\limits{x\to\pm\infty}x^n\varphi^{(m)}(x)=0\quad\forall n,m\ge 0$
- **toutes les dérivées tendent très rapidement vers $0$** : plus rapidement que $\frac{1}{x^n}\quad\forall n\ge 0$
- implique $\inti\abs{\varphi(x)}\d x <\infty$
- **espace de fonctions de Schwartz** : $S$

### 3. Exemples & contre exemples

- $\varphi(x)=e^{-x^2}$ : $\abs{x}^n e^{-x^2}\le\abs{x}^n \frac{1}{(x^2)^{n+1} / (n+1)!}\to 0$ lorsque $x\to\pm\infty$
  - récurrence sur polynôme de degrée $m$ : $\varphi^{(m+1)}(x)=(e^{-x^2}p_m(x))'=e^{-x^2}p_{m+1}(x)$
- $\psi(x)=e^{-1/x}$ lorsque $x>0$ : non à décroissance rapide car limite $=1\not=0$
- $\varphi(x)=\psi(x-a)\psi(x-b)$ avec $a<b$

### 4. Fonctions à croissance lente

- **continue croissance lente (CCL)** : $f:\R\to\C$ avec $\displaystyle \lim_\limits{x\to\pm\infty}\frac{f(x)}{x^n}=0\quad\forall n\ge 0$

### 5. Fonctionnelle sur $S$

- **application linéaire** : $T:S\to\C$
- **fonction à l'entrée ($\varphi\in S$) et un nombre complexe la sortie ($T(\varphi)$)**
- notation alternative $<T,\varphi>$ ou $T\{\varphi\}$
- **fonctionnelle associée à $f$ CCL** : $\displaystyle T_f(\varphi)=\inti f(x)\varphi(x)\d x=\int _\R \Re[f(x)\varphi(x)]\d x+i\int _\R \Im[f(x)\varphi(x)]\d x$
- intégrale bien définie et linéaire

### 6. Exemples

- **dirac** : $\delta:S\to\C$ définie par $\delta(\varphi)=\varphi(0)$
- **heaviside** : $H:\R\to\R$ défini par $0$ si négative $1$ sinon, alors $T_H(\varphi)=\int_\R H(x)\varphi(x)\d x=\int_0^\infty\varphi(x)\d x$

### 7. Distribution tempérées

- DT : fonctionnelle sous la forme $\displaystyle T^{(n)}_f(\varphi)=(-1)^n\inti f(x)\varphi^{(n)}(x)\d x$
- ensemble des DTs : $S'$

### 8. Proposition

- si $f$ et $f'$ CCL : $T_f^{(n+1)}=T^{(n)}_{f'}$ en particuler $T_f^{(1)}=T _{f'}^{(0)}=T _{f'}$

### 9. $S'$ espace vectoriel

- $(aT)(\varphi)=aT(\varphi)$
- $(T_1+T_2)(\varphi)=T_1(\varphi)+T_2(\varphi)$

### 10. Dérivée d'une distribution tempérée

- $(T_f^{(n)})'=T_f^{(n+1)}$ plus spécifiquement $T_f'=T_{f'}$
- dérivation des distributions est compatible/cohérente avec celle des fonctions

### 11. Caractérisation intrinsèque de la dréivée d'une distrubution tempérée

- $T'(\varphi)=-T(\varphi')$

### 12. Exemples

- rampe : $r:\R\to\R$ définie par $0$ si négative $x$ sinon, $T_r(\varphi)=\inti r(x)\varphi(x)\d x=\int_0^\infty x\varphi(x)\d x$
- heaviside : $T_H=T_r^{(1)}=-\int_0^\infty x\varphi'(x)/d x=-\lim_\limits{r\to\infty}[x\varphi(x)_0^r-\int_0^\infty\varphi(x)\d x]=\int_0^\infty \varphi(x)\d x=T_H(\varphi)$
- $\delta=T_r^{(2)}=T_H^{(1)}=(T_H)'$
- DT fonctionnelle de Heaviside : $T_H$
- DT fonctionnelle de Dirac : $\delta$

### 13. Transformée de Fourier d'une distribution tempérée

- **fonctionnelle** : $\F T:S\to\C$ définie par dualité $<\F T,\varphi>=<T,\F\varphi>$ (ou $(\F T)(\varphi)=T(\F\varphi)$)
- $\F \varphi(\alpha)=\frac{1}{\sqrt{2\pi}}\inti e^{-i\alpha x}\varphi(x)\d x$ bien définie
- **si $f$ CCL et bornée** : $\F(T_f)=T_{\F f}$
- transformation de Fourier des distributions est compatible/cohérente avec celle des fonctions

### 14. Autres opérations sur une distribution tempérée

- **réflections** : $\displaystyle T^\vee(\varphi)=T(\varphi^\vee)$ et $(T_f)^\vee=T_{f^\vee}$ avec ($\displaystyle (f^\vee(x)=f(-x))$)
- **translations** : $\displaystyle (\T_a T)(\varphi)=T(\T_{-a}\varphi)$ et $\T_aT_f=T _{\T_a f}$ avec ($\displaystyle (\T_a f)(x)=f(x+a)$)
- **changements d'échelle** : $\displaystyle (\S_a T_f)(\varphi)=T(\frac{1}{\abs{a}}\S_{\frac{1}{a}}\varphi)$ et $\displaystyle \S_aT_f=T _{\S_af}$ avec ($\displaystyle (\S_a f)(x)=f(ax)$)
- **multiplication par une fonction C$\infty$CL** : $\displaystyle (gT)(\varphi)=T(g\varphi)$ et $\displaystyle gT_f=T_{gf}$

### 15. Exemples

- $\delta_a(\varphi)=\varphi(a)$
- $\F\delta_a=T_f$ où $f(x)=\frac{1}{\sqrt{2\pi}}e^{-iax}$
- $\F(e^{iax})=\sqrt{2\pi}\delta_a$
- $\F(\cos x)=\sqrt{\pi/2}(\delta_{-1}+\delta_1)$ et $\F(\sin x)=i\sqrt{\pi/2}(\delta _{-1}+\delta_1)$

### 16. Propriété des transformations de Fourier

### 17. Convolution $T*\varphi$

### 18. Exemples

### 19. Convolution $T_1*T_2$





























