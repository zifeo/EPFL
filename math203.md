$$
\def\R{\mathbb R}
\def\Rn{\mathbb R^n}
\def\d{\:\mathrm d}
\def\p{\partial}
\def\f#1#2#3#4#5{\begin{align} #1 : #2 &\to #3 \\\ #4 &\mapsto #5 \end{align}}
\def\norm#1{\|\,#1\,\|}
\def\G{\Gamma}
\def\g{\gamma}
\def\O{\Omega}
\def\t{\text}
\def\ouvert{\O\in\Rn}
\def\scalaire{\f f \O \R x {f(x)=f(x_1,\ldots,x_n)}}
\def\vectoriel{\f F \O \Rn x {F(x)=(F_1(x),\ldots,F_n(x))}}
\def\c#1{C^#1(\O)}
\def\C#1{C^#1(\O,\Rn)}
\def\grad{\text{grad }}
\def\div{\text{div }}
\def\rot{\text{rot }}
\def\do{\mathrm d\O}
\def\param{\f \g {[a,b]} \do t {x=\g(t)=(\g_1(t),\ldots,\g_n(t))}}
\def\ppp{,\ldots,}
\def\S{\Sigma}
\def\s{\sigma}
\def\normale{\s_u\wedge\s_v}
\def\peri#1{#1\t{-périodique }}
\def\cases#1{=\begin{cases}#1\end{cases}}
\def\co{\cos(\frac{2\pi n}{T}x)}
\def\si{\sin(\frac{2\pi n}{T}x)}
\def\N{\mathbb N}
\def\ein{i\frac{2\pi n}{T}x}
\def\ff{f:\R\to\R}
\def\F#1{\mathbb F(#1)}
$$

# MATH203

> [GNU General Public License v3.0](https://github.com/zifeo/EPFL/blob/master/LICENSE) licensed. Source available on [github.com/zifeo/EPFL](https://github.com/zifeo/EPFL).

Fall 2014: Analyse III

[TOC]

## 1. Opérateurs différentiels

- **$n$-uplet** : pour $n\in\mathbb N$ tel que $n > 1$, on note $x=(x_1,\ldots,x_n)\in\mathbb R^n$ un $n$-uplet de nombres réels. Par exemple pour $n=2$, on a $(x_1,x_2)=(x,y)$ et pour $n=3$, $(x_1,x_2,x_3)=(x,y,z)$.
- **champ scalaire** : fonction à valeurs réels définies sur $\Omega\subset\mathbb R^n$ : 
  $\scalaire$
- **champ vectoriel** : fonction à valeurs dans $\mathbb R^n$ définie sur $\Omega\subset\mathbb R^n$ : 
  $\vectoriel$ où $F_i$ est un champ scalaire pour $i=1,\ldots,n$
- **classe de régularité** : pour $k\in\mathbb N$ on écrit $f\in C^k(\Omega)$ si toutes les dérivées partielles d'ordre $\le k$ existent et sont continues sur $\Omega$. On écrit $F\in C^k(\Omega,\mathbb R^n)$ si $f_i\in C^k(\Omega)$ pour $i=1,\ldots,n$
- **nabla** : opérateur différentiel vectoriel $\nabla=(\frac{\partial}{\partial x_1}, \ldots, \frac{\partial}{\partial x_n})$
- **gradient** : $\text{grad }f(x)=(\nabla f)(x)=(\frac{\partial f}{\partial x_1}(x),\ldots,\frac{\partial f}{\partial x_n}(x))$ où  $\text{grad }f:\Omega\to\mathbb R^n$ définit un champ vectoriel
- **divergence** : $\text{div }F(x)=(\nabla\cdot F)(x)=\frac{\partial f_1}{\partial x_1}(x)+\cdots+\frac{\partial f_n}{\partial x_n}(x)$ où $\text{div }F:\Omega\to\mathbb R$ est un champ scalaire
- **rotationnel** dans $\R^2$ : $\text{rot }F(x,y)=\frac{\partial f_2}{\partial x}(x, y)-\frac{\partial f_1}{\partial y}(x, y)$ où le résultat est un champ scalaire
- **rotationnel** dans $\R^3$ : $\text{rot }F(x, y, z)=(\nabla\wedge F)(x,y,z)=\begin{vmatrix}\hat e_1 &\hat e_2 & \hat e_3\\\ \frac{\partial}{\partial x} & \frac{\partial}{\partial y} & \frac{\partial}{\partial z}\\\ f_1 & f_2 & f_3 \end{vmatrix}$ où le résultat est un champ vectoriel
- **Laplacien** : $(\Delta f)(x)=(\nabla^2\cdot f)(x)=\frac{\partial^2 f}{\partial x_1^2}(x)+ \cdots+ \frac{\partial^2 f}{\partial x_n^2}(x)$ où $\Delta f:\Omega\to\mathbb R$ est un champ scalaire

## 2. Intégrals curvilignes, champs conservatifs et théorème de Green

- **courbe simple régulière** : $\Gamma\subset\mathbb R^n$ s'il existe un interval $[a,b]\subset\mathbb R^n$ et une paramétrisation $\begin{align}\gamma:[a,b]&\to\mathbb R^n\\\ t&\mapsto \gamma(t)=(\gamma_1(t),\ldots,\gamma_n(t))\end{align}$ telle que
  - $\Gamma=\gamma([a,b])=\{x\in\mathbb R^n: \exists t\in[a,b],x=\gamma(t)\}$
  - $\gamma$ est injective sur $[a,b[$ : $\forall t_1, t_2\in[a,b[, t_1\not=t_2\implies\gamma(t_1)\not=\gamma(t_2)$
  - $\gamma\in C^1([a,b],\mathbb R^n)$
  - $||\gamma'(t)||=\sqrt{\gamma_1'(t)^2+\cdots+\gamma_n'(t)^2}\not=0\;\forall t\in[a,b]$
- **courbe fermée** : $\Gamma\subset\mathbb R^n$ est une courbe simple régulière fermée si en plus $\gamma(a)=\gamma(b)$ (possible car injective sur $[a,b[$)
- **courbe par morceaux** : $\Gamma\subset\mathbb R^n$ est une courbe simple régulière par morceaux s'il existe $\Gamma_1,\ldots,\Gamma_k$ des courbes simples réguilières par morceaux telles que $\Gamma =\cup^k_{i=1} \Gamma_i$.
- **intégrale curviligne** sur champ scalaire : avec$f:\Gamma\to\mathbb R$ continu, on a $\int_\Gamma f \d l=\int_a^b f(\gamma(t))\:\norm{\gamma'(t)}\d t$
- longueur de la courbe : en choissant $f=1$, on a $\t{longueur}(\G)=\int_\G \d l =\int_a^b \norm{\g'(t)}\d t$
- **intégrale curviligne** sur champ vectoriel : avec un champ vectoriel continu, $\int_\G F\cdot\d l=\int_a^b F(\g(t))·\g'(t)\d t$ (donne le travail effectué pour déplacer une particule sommaire au champ de forces $F$ le long de la courbe $\G$)
- intégrale par morceaux : si $\G=\cup^k_{i=1}\G_i$ alors $\int_\G f\d l=\sum^k_{i=1}\int_\G f \d l$ et $\int_{\G_i} F\cdot\d l=\sum^k_{i=1}\int_{\G_i}F\cdot\d l$
- **potentiel** (champ conservatif) : si $F=\grad f$ alors $F$ est appelé un champ conservatif et $f$ s'appelle le poteniel de $F$
- unicité : si un potentiel existe, il est défini à une constante réele près
- **connexe** : $\ouvert$ est convexe si pour tout $x\in\O$ et tout $y\in\O$ le segment de droite joignant $x$ à $y$ est entièrement contenu dans $\O$, c'est-à-dire si pour $t\in[0,1]$ et $\forall x,y \in\O$ on a $x+t(y-x)\in\O$
- **conditions d'existence** :
  - une condition nécessaire : si $F$ dérive d'un potentiel sur $\O$ alors $\frac{\p F_i}{\p x_j}(x)=\frac{\p F_i}{\p x_i}(x)\;\forall i,j=1\ldots n\;\forall x\in\O$ (ne garantit pas un potentiel et équivalente à dire que $\rot F$ est nul)
  - une condition suffisante : $\O$ doit être convexe, simplement connexe (sans trou) pour que $F$ dérive d'un potientiel
- **équivalence** :
  - $F$ dévrive d'un potentiel sur $\O$
  - $\int_{\G_1}F\cdot\d l=\int_{\G_2}F\cdot\d l$ pour toutes courbes simples régulières par morceaux et $\G_1,\G_2$ joignant deux pooints quelconques de $\O$
  - $\int_\G F\cdot\d l=0$ pour toute courbe simple fermée régulière par morceaux $\G\in\O$
- **détermination** :
  - si $\rot F\not= 0$ sur $\O\implies F$ ne dérive pas d'un potentiel
  - si $\rot F = 0$ sur $\O$ convexe $\implies F$ dérive d'un potentiel
  - si $\rot F=0$ sur $\O$ pas convexe $\implies$ aucune information
  - si on trouve une courbe fermée $\G\in\O$ telle que $\int_\G F\cdot\d l \not =0\implies F$ ne dérive pas d'un potentiel (l'inverse n'est pas vrai)
- **bord** : est une courbe simpel fermée régulière par morceaux tel que $\do=\{x\in\R^2:\O\cap D_r(x)\not = \emptyset,\; (\R^2 \backslash\O)\cap D_r(x)\not=\emptyset\;\forall r > 0\}$ où $D_r(x)=\{y\in\R^2 : \norm{y-x}< r \}$ est un disque ouvert de $R^2$ de rayon $r$ centré, on note $\bar\O=\O\cup\do$ l'adhérence de $\O$
- **sens de parcours** : $\do$ est orienté positivement (négativement) si lorsqu'on parcourt $\do$ on laisse le domaine $\O$ à gauche (droite)
- **tagente/normale** : pour une paramétrisation $\param$ de $\do$, le vecteur tangent à $\do$ en $x$ est $\tau=(\g_1'(t),\g_2'(t))$ et le vecteur normal à $\do$ en $x$ donné par $\nu(x)=(\g_2'(t), -\g_1'(t))$ est une normale extérieure $\O$
- **domaine régulier** : on dit qu'un ouvert borné $A\in\R^2$ est un domaine régulier s'il existe des ouverts $A_0,\ldots,A_m\subset\R^2$ tels que :
  - $\d A_j=\G_j$ pour $j=0,\ldots,m$ sont des courbes simples, fermées, régulière par morceaux
  - $\bar A_j\subset A_0$ pour tout $j=1,\ldots,m$
  - $\bar A_i \cap \bar A_j =\emptyset\;\forall i,j=1,\ldots,m$ avec $i\not=j$
  - $A = A_0\backslash \cup^m_{j=1}\bar A_j$
  - on dit que $\d A =\G_0\cup\cdots\cup\G_m$ est orienté positivement si le sens de parcours sur chaque $\G_j$ pour $j=0,\ldots,m$ laisse le domaine $A$ à gauche. C'est-à-dire que le bord $\G_0$ est orienté positivement (son parcours laisse $A_0$ à gauche) tandis que les "trous" $\G_1\ppp\G_m$ sont orientés négativement (leurs parcours laissent $A_1\ppp A_m$ à droite)
- **théorème de Green** : soit $A\subset\R^2$ un domaine régulier dont le bord $\d A$ est orienté positivement et soit $\f F{\bar A}{\R^2}{(x,y)}{F(x,y)}$ un champ vectoriel tel que $F\in C^1(\bar A, \R^2)$ alors :
  $\boxed{\displaystyle\iint_A\rot F(x,y) \d x\d y=\int_{\d A} F\cdot\d l}$
- attention au sens des trous lors de la paramétrisation des bords : pour un disque $A=\{(x,y)\in\R^2 : 1 < x^2+y^2< 4\}$ on a $\G_0 =\{\g_0(t)=(2\cos t,2\sin t)\;t\in[0,2\pi]\}$ et $\G_1 =\{\g_0(t)=(\cos t,\sin t)\;t\in[0,2\pi]\}$ ainsi $\int_{\d A}F\cdot \d l=\int_{\G_0}F\cdot\d l-\int_{\G_1}F\cdot\d l$.
- **théorème de la divergence** dans $\R^2$ : soit $A\subset\R^2$ un domain régulier dont le bord $\d A$ est orienté positivement, soit $\nu:\d A\to\R^2$ un champ de normales unités extérieurs à $A$ et soient $F:\bar A\to\R^2$ un champ vectoriel tel que $F\in C^1(\bar A,\R^2)$ et $f:\bar A\to\R$un champ scalaire tel que $F\in C^2(\bar A)$ alors
  $\boxed{\displaystyle\iint_A \div F(x,y)\d x\d y = \int_{\d A} (F\cdot\nu)\d l}$ et $\boxed{\displaystyle\iint_A \Delta f(x,y)\d x \d y=\int_{\d A}(\grad f\cdot\nu)\d l}$

## 3. Intégrales de surface, théorème de la divergence, théorème de Stokes

- composante : pour une fonction $f:\R^2\to\R^3$, on note $f(x,y)=(f^1(x,y),f^2(x,y),f^3(x,y))$ où $f^i:\R^2\to\R$ (l'indice en haut repère la composante).
- dérivée partielle : pour une fonction $g(x,y)$, on note $\frac{\p g}{\p x}=g_x$ et $\frac{\p g}{\p y}=g_y$ (indices en bas donnent la variable par rapport laquelle on dérive).
- **surface régulipre** : $\S\subset\R^3$ est apelée une surface régulière si :
  - il existe $A\in\R^3$ un ouvert borné tel que le bord $\d A$ soit une courbe simple fermée régulière par morceaux
  - il existe une paramétrisation $\f \s{\bar A}{\R^3}{(u,v)}{\s(u,v)=(\s^1(u,v),\s^2(u,v),\s^3(u,v))}$ satisfaisant $\s\in C^1(\bar A,\R^3)$, $\s(\bar A)=\S$ et $\s$ injective sur $A$ et un vecteur $\s_u \wedge \s_v = \begin{vmatrix}\hat e_1 & \hat e_2 & \hat e_3 \\\ \s_u^1 & \s_u^2 & \s_u^3 \\\ \s_v^1 & \s_v^2 & \s_v^3 \end{vmatrix}$ tel que $\norm{\s_u\wedge\s_v}\not =0\,\forall(u,v)\in A$
- vecteur normal unité : $\nu(u,v)=\frac{\s_u\wedge\s_v}{\norm{\s_u\wedge\s_v}}$ à la surface $\S$ du point $\s(u,v)$
- **surface par morceaux** : on dit que $\S\subset\R^3$ est une surface régulière par morceaux s'il existe $\S_1\ppp\S_k$ des surfaces régulières telles que $\S=\cup^k_{i=1} \sum_i$.
- **orientation** : une surface régulière par morceaux est dite orientable s'il existe un champ de normales unités $\nu:\S\to\R^3$ continu. Un tel champ de normales s'appelle une orientation de $\S$. Une surface $\S$ orientée par un champ de normales est noté $(\S,\nu)$.
- **intégrale de surface** sur champ scalaire (orientable et continu) : $\iint_\S f\d s = \iint_A f(\s(u,v))\;\norm{\normale}\d u\d v$
- aire : $aire(\S)=\iint_\S\norm\normale\d u\d v$
- **intégrale de surface** sur champ vectoriel (orientable et continu) : $\iint_\S F\cdot\d s=\iint_A[F(\s(u,v))\cdot(\normale)]\d u\d v$ (il s'agit du flux de $F$ à travers la surface $\S$ dans la direction $\nu$)
- réécriture avec la normale unité : $\iint_\S F\cdot\d s=\iint_A[F(\s(u,v))\cdot\nu(u,v)]\norm\normale\d u\d v$
- **intégrale par morceaux** : pour une surface régulière par morceaux on définit l'intégrale comme la somme des intégrales des morceaux.
- **domaine régulier** : on dit qu'un ouvert borné $\O\in\R^3$ est un domain régulier s'il existe des ouverts $\O_0\ppp\O_m\subset\R^3$ tels que :
  - $\d\O_j=\S_j$ pour $j=0\ppp m$ sont des surfaces régulières par morceaux orientables avec un champ de normales unités
  - $\bar\O_j\subset\O_0\;\forall j=1\ppp m$
  - $\bar\O_i\cap\bar\O_j=\emptyset\;\forall i,j = 1\ppp m\; i\not = j$
  - $\O =\O_0\backslash \cup^m_{j=1}\bar \O_j$ possède un champ de normales extérieurs (lorsqu'on considère les surfaces "trous" $\S1\ppp\S_m$ elles sont intéreures par rapport aux domains $\O_1\ppp\O_m$)
- **théorème de la divergence** : soit $\O\subset\R^3$ un domain régulier et $\nu:\d\O\to\R^3$ un champ de normales unitées extérieures à $\O$ défini par $\nu=(\nu_1,\nu_2,\nu_3)$, soit $F:\bar\O\to\R^3$ un champ vectoriel tel que $F\in C^1(\bar\O,\R^3)$ défini par $F=(F_1,F_2,F_3)$ alors
  $\boxed{\displaystyle\iiint_\O \div F(x,y,z)\d x\d y\d z =\iint_{\d\O}(F\cdot\nu)\d s}$
- **sens de parcours** :
  - si $\S\subset\R^3$ est une surface régulière et $\s:\bar A\to\S$ est une paramétrisation de $\S$ alors le bord de $\S$ (noté $\d\S$) est donné par $\d\S=\s(\d A)$ est indépendant du choix de la paramétrisation
  - le sens de parcours de $\d\S$ induit par la paramétrisation $\s$ est celui obtenu en parcourant $\d A$ dans le sens sens positif
  - si $\d a$ est une courbe simple fermée régulière par morceaux alors on a $\s(\d A)=\G_1\cup\cdots\cup\G_m$ et pour obtenir le bord de $\S$ on procède de la façon suivante. On supprime de $\s(\d A)$ les courbes $\G_i$ qui se réduisent à un seul point et celles qui sont parcourues deux fois (une fois dans un sens, une fois dans l'autre). Ce qui reste après avoir appliqué ce procédé est le bord de $\S$ désigné par $\d\S$
- **Théorème de Stokes** : soit $\S\subset\R^3$ une surface régulière par morceaux et orientable, soit $F:\S\to\R^3$ un champ vectoriel tel que $F\in C^1(\S,\R^3)$ alors :
  $\boxed{\displaystyle\iint_\S \rot F\cdot\d s=\int_{\d\S}F\cdot\d l}$

## 4. Séries de Fourier

- **périodicité** : une fonction $\f f \R \R x {f(x)}$ est dite $\peri T$ s'il existe $T>0$ tel que $f(x+T)=f(x)\;\forall x\in\R$, de plus a restriction de $f$ à l'interval $[0,T[$ caractérise complétement $f$
  - $\int_a^{a+T}f(x)\d x=\int_0^T f(x)\d x\;\forall a\in\R$
- **continuité par morceaux** : une fonction $f:\R\to\R$ est dite continue par morceaux sur l'interval $[a,b]$ s'il existe des points $\{x_i\}^{n+1}_{i=0}$ avec $a=x_0< x_1 < \cdots < x_n < x_{n+1}=b$ tels que pour $i=0\ppp n$ on ait :
  - $f$ est continue sur chaque interval $]x_i,x_{i+1}[$
  - la limite à droite $\lim_{t > x_i \to x_i} f(t)=f(x_i+0)$ et la limite à gauche $\lim_{t < x_{i+1}\to x_{i+1}}f(t)=f(x_{i+1}-0)$ existent et sont finies
- **régulière par morceaux** : on dit que $f$ est régulière par morceaux sur $[a,b]$ si de plus on a :
  - $f'$ existe et est continue par morceaux sur chaque interval $]x_i,x_{i+1}[$
  - la limite à droite $f'(x_i+0)$ et celle à gauche $f'(x_{i+1}-0)$ existent et sont finies
- **série de Fourier partielle** :  $F_Nf(x)=\frac{a_0}{2}+\sum^N_{n=1}[a_n\co+b_n\si]$où les coefficients de Fourier $a_n$ et $b_n$ de $f$ sont données par
  - $a_n=\frac{2}{T}\int_0^T f(x)\co\d x$ pour $n=0\ppp N$
  - $b_n=\frac{2}{T}\int_0^T f(x)\si\d x$ pour $n=1\ppp N$
- **série de Fourier** : on appelle série de Fourier de $f$ la limite lorsque $N\to\infty$ (si elle existe) de $F_Nf(x)$, on écrit alors $Ff(x)=\lim_{N\to\infty}=\frac{a_0}{2}\sum_{n=1}^\infty a_n\co+b_n\si$.
- **théorème de Dirichlet** : soit $f:\R\to\R$ une fonction $\peri T$ régulière par morceaux alors $Ff(x)=\lim_{N\to\infty}F_Nf(x)$ existe pour tout $x\in\R$ et : $Ff(x)=\frac{f(x+0)+(f(x-0))}{2}$
- **série de Fourier complexe** : sachant $e^{i\phi}=\cos\phi+i\sin\phi$ on peut réécrire la série : $Ff(x)=\sum^\infty_{n=-\infty}c_n e^{\ein}$ où $c_n\in\mathbb C$ donné par $c_n=\frac{1}{T}\int_0^T f(x) e^{-\ein}$
- **propriété des séries de Fourier** :
  - sa série de Fourier est aussi $\peri T$
  - si $f$ est **paire** ($f(-x)=f(x)\;\forall x\in \R$) on a $b_n=0\;\forall n \ge 1$ et sa série de Fourier est aussi une fonction paire
  - si $f$ est **impaire** ($f(-x)=-f(x)\;\forall x\in\R$) on a $a_n=0\;\forall n \ge 0$ et sa série de Fourier est aussi une fonction impaire
  - si régulière par morceaux alors ($a_n$ et $b_n$ sont les coefficients de Fourier) : $\frac{2}{T}\int_0^T[f(x)]^2\d x=\frac{a_0^2}{2}\sum^\infty_{n=1}(a_n^2+b_n^2)$
  - dérivation terme à terme converge pour $x\in\R$ et on a : $\sum^\infty_{n=1}\frac{2\pi n}{T}[-a_n\si+b_n\co]=\frac{1}{2}[f'(x+0)+f'(x-0)]$
- **série de Fourier en cosinus** : soit $f:[0,L]\to\R$ et soit $f'$ continue par morceaux alors $F_cf(x)=\frac{a_0}{2}+\sum^\infty_{n=1}a_n\cos(\frac{\pi n}{L}x)$ où $a_n=\frac{2}{L}\int^L_0f(x)\cos(\frac{\pi n}{L}x)\d x$ pour $n=0,1,...$ converge vers $f$ dans l'interval $[0,L]$ et on a $f(x)=F_cf(x)\;\forall x\in[0,L]$.
- **série de Fourier en sinus** : soit $f:[0,L]\to\R$ une fonction continue avec $f(0)=f(L)=0$ telle que $f'$ soit continue par morceaux alors
  $F_sf(x)=\sum^\infty_{n=1}b_n\sin(\frac{\pi n}{L}x)$ où $b_n=\frac{2}{L}\int^L_0f(x)\sin(\frac{\pi n}{L}x)\d x$ pour $n=1,2,...$ elle converge vers $f$ dans l'interval $[0,L]$ et on a $f(x)=F_sf(x)\;\forall x\in[0,L]$ (la condition $f(0)=f(L)=0$ assure que la fonction doublement étendue est continue)
- **résolution d'équation** : trouver la solution $\peri{T}$ désignée par $y(x)$ d'équation du type $\alpha y(x)+\beta y(x-\pi)=f(x)$ ou $\alpha y''(x)+\beta y'(x)+\gamma y(x)=f(x)$ avec $f(x)$ étant une fonction $\peri{T}$ continue sur $[0,T[$
  1. calcul de $Ff(x)$
  2. on cherche les solutions écrites sous forme de séries de Fourier $y(x)=\frac{A_0}{2}+\sum_1^\infty[A_n\cos(nx)+B_n\sin(nx)]$
  3. on utilise les dérivées des série de Fourier
    - $y(x-\pi)=\frac{A_0}{2}\sum^\infty_1[(-1)^n A_n \cos(nx)+(-1)^nB_n\sin(nx)]$
    - $y'(x)=\sum^\infty_1[-nA_n\sin(nx)+nB_n\cos(nx)]$
    - $y''(x)=\sum^\infty_1[-n^2A_n\cos(nx)-n^2B_n\sin(nx)]$
  4. on intégre les expressiosn de $Ff(x)$, $y(x)$, $y(x-\pi)$, $y'(x)$, $y''(x)$ dans l'équation et on identifie les coefficients respectifs de $\cos(nx)$ et $\sin(nx)$ pour déterminer $A_n$ et $B_n$ en fonction de $a_n$ et $b_n$
- Fourier comme espace vectoriel : on considère $\nu=\{\forall \ff : \peri T \t{continue}\}$, on montre que $\nu$ est un espace vectoriel et on définit le produit sclaire de $f\in\nu$ et de $g\in\nu$ par $(f,g)=\frac{2}{T}\int_0^T f(x)g(x)\d x$ alors l'ensemble des fonctions $\beta=\{\{u_n(x)=\co\},\{v_n(x)=\si\}\}$ est une base orthogonale de $\nu$ car $(u_0,u_0)=2$ et $(u_j,u_k)=\delta_{jk}\cases{1\t{ si }j=k\\\ 0\t{ si }j\not=k}$ (Kronecker) et ainsi la série de Fourier d'une fonction $f\in\nu$ qui s'écrit $Ff(x)=\frac{a_0}{2}U_0(x)+\sum^\infty_1[a_nU_n(x)+b_nV_n(x)]$ peut s'interpréter comme la décomposition de $f$ dans la base $\beta$ car $a_n=(f,U_n)$ et $b_n=(f,V_n)$.

## 5. Transformée de Fourier

- **condition** : soit $\f f \R \R x {f(x)}$ une fonction continue par morceaux telle que $\int^\infty_{-\infty}|f(x)|\d x<\infty$
- **transformée de Fourier** de $f$ : (on écrit aussi $\hat f(\alpha)=\mathbb F(f)(\alpha)$)
  $\f {\hat f}\R{\mathbb C}\alpha{\hat f(\alpha)=\frac{1}{\sqrt{2\pi}}\int^\infty_{-\infty}f(x)e^{-i\alpha x}\d x}$
- **transformée de Fourier inverse** de $f$ :
  $\f {\hat f^{-1}}\R{\mathbb C}x{\hat f^{-1}(x)=\frac{1}{\sqrt{2\pi}}\int^\infty_{-\infty}f(\alpha)e^{i\alpha x}\d\alpha}$
- **théorème de réciprocité** : soit $\ff$ une fonction telle que $f$ et $f'$ soient continues par morceaux avec $\int^\infty_{-\infty}|f(x)|\d x <\infty$ et $\int^\infty_{-\infty}|\hat f(\alpha)|\d\alpha <\infty$ alors pour tout $x\in\R$ on a $\hat f (x)=\frac{1}{\sqrt{2\pi}}\int_{-\infty}^\infty\hat f(\alpha)e^{i\alpha x}\d\alpha=\frac{1}{2}[f(x+0)+f(x-0)]$
- **continuité** : $\F f$ est continue $\forall \alpha\in\R$ et $\lim_{\alpha\to\pm\infty}|\F f (\alpha)|=0$
- **linéarité** : $\F{af+bg}=a\F f + b\F g\;\forall a,b\in\R$
- **produit de convolution** de deux fonctions $f$ et $g$ :
  $\f{f*g}\R\R x {(f*g)(x)=\int_{-\infty}^\infty f(x-t)g(t)\d t}$.
- **transformée de Fourier du produit de convolution** de deux fonctions est égal au produit des transformées de Fourier de chaque fonction $\hat{f*g}=\sqrt{2\pi}\hat f \hat g$
- **transformée de Fourier de la dérivée** : si de $f\in C^n(\R)$ et $\int^\infty_{-\infty}|f^k(x)|\d x <\infty$ pour $k=1\ppp n$ alors $\hat f^k(\alpha)=(i\alpha)^k\,\hat f(\alpha)$
- **identitié de Plancherel** : si $\int^\infty_{-\infty}|[f(x)]^2|\d x <\infty$ alors on a $\int_{-\infty}^\infty[f(x)]^2\d x=\int_{-\infty}^\infty[\F f(\alpha)]^2\d \alpha$
- **parité** :
  - si la fonction $f$ est paire alors on a $\F f(\alpha)=\sqrt{\frac{2}{\pi}}\int_0^\infty f(x)\cos(\alpha x)\d x$ qui est appelée la transformation de Fourier en cosinus de $f$
  - si la fonction $f$ est impaire alors on a $\F f(\alpha)=-i\sqrt{\frac{2}{\pi}}\int_0^\infty f(x)\sin(\alpha x)\d x$ qui est appelée la transformation de Fourier en sinus de $f$

## 6. Appendix

### 6.1 Algebraic identities
- $x^3+y^3=(x+y)(x^2-xy+y^2)$
- $\sqrt{b}-\sqrt{a}=\frac{b-a}{\sqrt{b}+\sqrt{a}}$
- $\frac{1}{2}+\frac{1}{2^2}+\frac{1}{2^3}+\cdots+\frac{1}{2^n}=1-\frac{1}{2^n}$
- $\sqrt{1+x}=1+\frac{x}{2}$ when $x << 1$
- $e^x=\lim_{n\to\infty}(1+\frac{x}{n})^n$
- geometric series : converge to $\sum_{n=1}^\infty ar^{n-1}=\frac{a}{1-r}$ if $|r|<1$
- Riemann series : $\sum_{n=1}^\infty \frac{1}{p^\alpha}$ converges if $\alpha >1$

### 6.2 Trigonometric identities
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
- $\cosh z =\frac{e^z+e^{-z}}{2}$
- $\sinh z =\frac{e^z-e^{-z}}{2}$
- $\cos z =\frac{e^{iz}+e^{-iz}}{2}=\cosh iz$
- $\sin z =\frac{e^{iz}-e^{-iz}}{2i}=\frac{\sinh iz}{i}$
- $e^z=\cosh z +\sinh z=\cos z+i\sin z$
- $e^{-z}=\cosh z -\sinh z$
- $\cosh^2 z -\sinh^2 z = 1$
- $\sin mx\cos nx=\frac{1}{2}[\sin (m+n)x + \sin (m-n)x]$
- $\cos mx\cos nx=\frac{1}{2}[\cos (m+n)x + \cos (m-n)x]$
- $\sin mx\sin nx=\frac{1}{2}[-\cos (m+n)x + \cos (m-n)x]$

### 6.3 Quadratic surfaces
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

### 6.4 Differentiation
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
- inverse function : $(f^{-1})'(a)=\frac{1}{f'(f^{-1}(a))}$ or $(f^{-1})'(f(a))=\frac{1}{f'(a)}$
- $\div\grad f=\Delta f$
- $\rot\grad f=\vec 0$
- $\div\rot F=0$
- $\div(f\grad g)=f\Delta g +\grad f\cdot\grad g$
- $\grad(fg)=f\grad g+g\grad f$
- $\div(fF)=f\div F+F\cdot\grad f$
- $\rot\rot F=-\Delta F +\grad\div F$
- $\rot(fF)=\grad f\wedge F+f\rot F$

### 6.5 Integration
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
- $\displaystyle\int^\pi_{-\pi} 1\cdot \cos (nx)\, dx=\left.\frac{1}{n}\sin (nx)\right|^{\pi}_{-\pi}=0.$
- $\quad\displaystyle\int^\pi_{-\pi} 1\cdot \sin (nx)\,dx=\left.-\frac{1}{n}\cos (nx)\right|^{\pi}_{-\pi}=0.$ 
- $\displaystyle\int^\pi_{-\pi} \sin (nx)\cos (nx)\,dx=\left.\frac{\sin^2 (nx)}{2n}\right|^{\pi}_{-\pi}=0.$ 
- $\displaystyle\int^\pi_{-\pi} \sin (mx)\sin(nx)\,dx=0$ 
- $\displaystyle\int^\pi_{-\pi} \cos (mx)\cos(nx)\,dx=0$
- $\displaystyle\int^\pi_{-\pi} \sin (mx)\cos(nx)\,dx=0$
- $\int_{{0}}^{{\frac{\pi}{2}}} \sin^n x \, dx = \int_{{0}}^{{\frac{\pi}{2}}} \cos^n x \, dx= \begin{cases}\frac{n-1}{n} \cdot \frac{n-3}{n-2} \cdots \frac{3}{4} \cdot\frac{1}{2} \cdot \frac{\pi}{2}, & \text{if }n\text{ is even} \\\ \frac{n-1}{n} \cdot \frac{n-3}{n-2} \cdots \frac{4}{5} \cdot \frac{2}{3} & \text{if }n\text{ is odd and more than 1}\end{cases}$
- $\int_{{-c}}^{{c}}\sin {x}\;\mathrm{d}x = 0 \!$
- $\int_{{-c}}^{{c}}\cos {x}\;\mathrm{d}x = 2\int_{{0}}^{{c}}\cos {x}\;\mathrm{d}x = 2\int_{{-c}}^{{0}}\cos {x}\;\mathrm{d}x = 2\sin {c} \!​$
- $\int_{{-c}}^{{c}}\tan {x}\;\mathrm{d}x = 0 \!$
- $\int_{-\frac{a}{2}}^{\frac{a}{2}} x^2\cos^2 {\frac{n\pi x}{a}}\;\mathrm{d}x = \frac{a^3(n^2\pi^2-6)}{24n^2\pi^2}   \qquad\mbox{(for }n=1,3,5...\mbox{)}\,\!$
- $\int_{\frac{-a}{2}}^{\frac{a}{2}} x^2\sin^2 {\frac{n\pi x}{a}}\;\mathrm{d}x = \frac{a^3(n^2\pi^2-6(-1)^n)}{24n^2\pi^2} = \frac{a^3}{24} (1-6\frac{(-1)^n}{n^2\pi^2})  \qquad\mbox{(for }n=1,2,3,...\mbox{)}\,\!$
- $\int_{{0}}^{{2 \pi}}\sin^{2m+1}{x}\cos^{2n+1}{x}\;\mathrm{d}x = 0 \! \qquad \{n,m\} \in \mathbb{Z}$
- $\int_0^{2\pi} \sin x \cos^2 x \d x=0$
- $\int_0^{2\pi} \sin^2 x \cos x \d x=0$
- $\int_0^{2\pi} \sin^2 x \d x=\pi$
- $\int_0^{2\pi} \cos^2 x \d x=\pi$
- $\int_0^{2\pi} \sin^4 x \d x=\frac{3\pi}{4}$
- $\int_0^{2\pi} \cos^4 x \d x=\frac{3\pi}{4}$
- $\int_0^{2\pi} \sin^2 x \cos^2 x \d x=\frac{\pi}{4}$
- $\int x\sin x\d x=\frac{\sin(n x)-n x \cos(n x)}{n^2}$
- $\int x\cos x\d x=\frac{nx\sin(n x)+ \cos(n x)}{n^2}$
- $\frac{2}{T}\int_0^T\co\cos(\frac{2\pi m}{T}x)\d x=\frac{2}{T}\int_0^T\si\sin(\frac{2\pi m}{T}x)\d x\cases{0 &\t{si }n\not=m\\\ 1 &\t{si }n=m}$
- $\int_0^T\si\cos(\frac{2\pi m}{T}x)\d x=0$

### 6.6 Analytic functions
- $\frac{1}{1-ax}=\sum_{n=0}^\infty (ax)^n=1+ax+ax^2+ax^3+\cdots$
- $\frac{1}{1+x}=\sum_{n=0}^\infty (-x)^n=1-x+x^2-x^3+\cdots$
- $\frac{1}{(1-x)^2}=\sum_{n=0}^\infty (n+1)x^n=1+2x+3x^2+4x^3+\cdots$
- $\sin x=\sum_{n=0}^\infty (-1)^n \frac{x^{2n+1}}{(2n+1)!}=x-\frac{x^3}{3!}+\frac{x^5}{5!}-\cdots$
- $\cos x=\sum_{n=0}^\infty (-1)^n \frac{x^{2n}}{(2n)!}=1-\frac{x^2}{2!}+\frac{x^4}{4!}-\cdots$
- $\tan^{-1} x=\sum_{n=0}^\infty (-1)^n \frac{x^{2n+1}}{2n+1}=x-\frac{x^3}{3}+\frac{x^5}{5}-\cdots$
- $ln(1+x)=\sum_{n=1}^\infty (-1)^n \frac{x^n}{n}=x-\frac{x^2}{2}+\frac{x^3}{3}-\cdots$

### 6.7 Change of coordinates

- **Jacobian** : $J=|\frac{\partial(x,y)}{\partial(u,v)}|=\begin{vmatrix} \frac{dx}{du}&\frac{dx}{dv} \\\ \frac{dy}{du}&\frac{dy}{dv}\end{vmatrix}$
- **substitution** : $\int_{\mathbb D}f(\vec x) d\vec x = \int_S f(T(\vec u)) J d\vec u$
- polar coordinates : $x = r \cos \theta\quad y = r\sin\theta\quad J=r$ and $\int_{\mathbb D}f(\vec x)d\vec x = \int_a^b \int_{g(\theta)}^{f(\theta)} f(r,\theta)r dr d\theta$
- cylindrial coordinates : $x = r \cos \theta\quad y = r\sin\theta\quad z=z \quad J=r$
- spherical coordinates : $x = \rho \sin \phi \cos \theta\quad y = \rho \sin\phi\sin\theta\quad z=\rho\cos\phi \quad J=\rho^2\sin \phi$ where $0 \le \theta \le 2\pi$ and $0\le \phi\le\pi$ (starting on the positive y-axis side)
- affine transformations : (exemple : barycentric coordinates) $\vec x = \vec v_1 \beta_1 + \vec v_2 \beta_2 \quad 0 \le \beta_i \le 1 \quad \beta_1+\beta_2=1$
- rotation matrix : $A=\begin{pmatrix} \cos \theta & -\sin \theta \\\ \sin \theta & \cos \theta \end{pmatrix}$

### 6.8 Comparaison courbes-surfaces
|                           | Courbes $\G$                             | Surface $\S$                             |
| ------------------------- | ---------------------------------------- | ---------------------------------------- |
|                           | $\f\g{[a,b]\subset\R}{\G\subset\R^2}t{\g(t)}$ | $\f\s{\bar A\subset\R^2}{\S\subset\R^3}{(u,v)}{\s(u,v)}$ |
|                           | $\g([a,b])=\G$                           | $\s(\bar A)=\S$                          |
|                           | $\g$ injective sur $[a,b]$               | $\s$ injective sur $\bar A$              |
|                           | $\norm{\g'(t)}\not = 0$                  | $\norm{\s_u\wedge\s_v}\not=0$            |
| Intégrale champ scalaire  | $\int_\Gamma f \d l=\int_a^b f(\gamma(t))\:\norm{\gamma'(t)}\d t$ | $\iint_\S f\d s = \iint_A f(\s(u,v))\;\norm{\normale}\d u\d v$ |
| Intégrale champ vectoriel | $\int_\G F\cdot\d l=\int_a^b F(\g(t))·\g'(t)\d t$ | $\iint_\S F\cdot\d s=\iint_A[F(\s(u,v))\cdot(\normale)]\d u\d v$ |
