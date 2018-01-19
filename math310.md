$$
\def\N{\mathbb N}
\def\Z{\mathbb Z}
\def\Q{\mathbb Q}
\def\R{\mathbb R}
\def\C{\mathbb C}
\def\F{\mathbb F}
\def\tq{\text{ tel que }}
\def\Ker{\,\text{Ker}}
\def\Im{\,\text{Im}}
\def\deg{\,\text{deg}}
\def\ZmZ{\Z/m\Z}
$$

# MATH310

> [GNU General Public License v3.0](https://github.com/zifeo/EPFL/blob/master/LICENSE) licensed. Source available on [github.com/zifeo/EPFL](https://github.com/zifeo/EPFL).

Fall 2015: Algèbre

[TOC]

## Arithmétique

- **nomenclature**
  - entiers naturels : $\N=\{1,2,\ldots\}$
  - entiers (relatifs) : $\Z=\{\ldots,-1,0,1,\ldots\}$
  - nombres rationnels : $\Q=\{\frac{a}{b}\mid a,b\in\Z\}$
  - nombres rées : $\R$ développement décimal infini
  - nombres complexes : $\C=\{a+ib\mid a,b\in\R\cap i^2=-1\}$
  - inclusions : $\N\subset\Z\subset\Q\subset\R\subset\C$
- **divisibilité** : $a|b\tq aq=b\; a,b,q\in\N$ ($a$ divise $b$)
  - division euclidienne : $b=aq+r\tq a,b,q,r\in\N_0$ avec quotient $q$ et reste $r<a$
- **nombre premier** : deux diviseurs $1$ et lui-même ($1$ non premier)
  - premier entre eux : $(a,b)=1$
  - premier deux à deux : $(a_i,a_j)=1\quad\forall i\not =j$
  - théorème d'Euclide : nombres premiers infini
- **PGCD** (plus grand commun diviseur) : $(a,b)$ tel que $d|a$, $d|b$, $d'|a$, $d'|b$ avec $d'\le d$
  - $e|a$ et $e|b\implies e|(a,b)$
  - si $a|bc$ et $(a,b)=1\implies a|c$
- **PPCM** (plus petit commun multiple) : $[a,b]$ tel que $a|m$, $b|m$, $\forall n$ multiple commun $m\le n$
  - $a|n$ et $b|n\implies [a,b]|n$
- **algorithm d'euclide** : $a,b\in\N$ avec $b\ge a$ et $r_n=(a,b)$ (dernier reste non nul)
  $\begin{align} b&=aq_1+r_1\\ a&=r_1q_2+r_2\\ r_1&=r_2q_3+r_3\\ &\quad\vdots\\ r_{n-2}&=r_{n-1}q_n+r_n\\ r_{n-1}&=r_nq_{n+1}+0\end{align}$
- **identité de Bezout** : existe $r,s\in\Z\tq d=as+br$ avec $d=(a,b)$ (non unique)
- **factorisation** : tout nombre entier s'écrit comme un produit de nombres premiers $a=p_1^{e_1}\cdots p_n^{e_n}$ (unique)
  - $a=p_1^{e_1}\cdots p_n^{e_n}$
  - $b=p_1^{f_1}\cdots p_n^{f_n}$
  - $a$ divise $b$ sii $e_i\le f_i\;\forall i$
  - $(a,b)=d=p_1^{h_1}\cdots p_n^{h_n}$ où $h_i=\min(e_i,f_i)$
  - $[a,b]=d=p_1^{k_1}\cdots p_n^{k_n}$ où $k_i=\max(e_i,f_i)$
  - $a\cdot b=[a,b]\cdot (a,b)$

## Congruences et classes de congruence

- **congruence modulo $m$** : $a\equiv b\mod m$ tel que $b=a+km$ pour $a,0\ge b<m,m>1,k\in\Z$
  - $a$ et $b$ sont congrus modulo $m$ (modulus)
  - ensemble : ${b+km\mid k\in\Z}$
  - relation d'équivalence : reflexive, transitive, symétrique
  - $a+a'\equiv b+b'\mod m$
  - $aa'\equiv bb'\mod m$
  - pas de simplification classique
- **changement de modulus**
  - $a\equiv b\mod m$ et $d|m\implies a\equiv b\mod d$
  - $a\equiv b\mod r$ et $a\equiv b\mod s\implies a\equiv b\mod [r,s]$
  - $ra\equiv rb\mod m\implies a\equiv b\mod\frac{m}{(r,m)}$
- **classe de congruence** : $[a]_m$ ensemble des entiers congrus à $a$ modulo $m$
  - ensemble des classes modulo $m$ : $\Z/m\Z$
  - $b\in [a]_m$ ssi $a\equiv b\mod m$
  - $[a]_m=[b]_m$ ssi $a\equiv b\mod m$
  - $m$ différentes classes : $[0]_m,\ldots,[m-1]_m$
  - représentant : entier dans une classe
  - élément neutre addition : $[0]_m$
  - élément neutre multiplication : $[1]_m$
- **unité** : $[a]_m$ possède un inverse $[b]_m\in\ZmZ\tq[a]_m[b]_m=[1]_m$ ssi $(a,m)=1$
- **indicatrice d'Euler** : $\varphi(m)$ nombre d'entiers naturels $a<m$ premiers à $m$
  - $(m,n)=1\implies \varphi(mn)=\varphi(m)\varphi(n)$
  - $\varphi(p^k)=(p-1)p^{k-1}$ avec $p$ premier

## Anneaux et corps

- **anneau** : $(R,+,\cdot,0,1)$ avec ensemble, deux opérations internes, deux éléments particuliers distincts
  - $+$
    - associatif : $(a+b)+c=a+(b+c)$
    - commutatif : $a+b=b+a$
    - neutre : $a+0=a$
    - existence opposé : $a+(-a)=0$
  - $\cdot$
    - associatif : $(a\cdot b)\cdot c=a\cdot(b\cdot c)$
    - identité : $a\cdot 1=a$
  - distributif : $a\cdot(b+c)=a\cdot b +a\cdot c$
  - propriétés
    - $a+b=a+c\implies b=c$
    - $0\cdot a=0$
    - $(-1)\cdot a=-a$
- **sous-anneau** : $S\subset R$
  - identité : $1_R\in S$
  - inverse : $a\in S\implies -a\in S$
  - fermé $+$ : $a,b\in S\implies a+b\in S$
  - fermé $\cdot$ : $a,b\in S\implies a\cdot b\in S$
- **anneau commutatif** : $a\cdot b=b\cdot a$
- **anneau intègre** : ssi $a\cdot b=b\cdot a=0$ implique $a=0$ ou $b=0$
- **diviseur de zéro** : ssi $\exists a\not =0\not =b$ tel que $a\cdot b=0$
- **unités d'un anneau** : $a$ est une unité si $a\cdot b=b\cdot a=1$ ($b$ unique)
  - ensemble des unités : $R^*$
- **anneau $\ZmZ$**
  - $m|a\implies [a]_m=[0]_m$
  - $(m,a)=1\implies [a]_m$ unité
  - $1<(a,m)<m\implies [a]_m$ diviseur de zéro
- **application** : $f:A\to B$
  - injective si $f(a)=f(a')\implies a=a'$ : au plus une pré-image
  - surjective si $\exists a\tq f(a)=b$ : au moins une pré-image
  - bijective si injective et surjective
- **homomorphisme d'anneaux** : $f:R\to S$ avec $R,S$ anneaux
  - $f(a+b)=f(a)+f(b)$
  - $f(ab)=f(a)f(b)$
  - $f(1_R)=1_S$
  - propriétés
    - $f(0)=0$
    - $f(-a)=-f(a)$
    - $a$ unité $\implies f(a)$ unité ($f(a)^{-1}=f(a^{-1})$)
  - isomorphe ($R\cong S$) si homorphisme bijectif
  - noyau : $\Ker(f)=f^{-1}(0)=\{r\in R\mid f( r)=0\}$ (pas sous-anneau mais idéal)
  - injectif ssi $\Ker(f)=\{0\}$ ($f(\{0\})=0$)
  - existe un seul homomorphisme de $\Z$ dans $R$ quelconque : $f(n)=n\cdot 1_R$
- **idéal** : $I\subset R$ commutatif
  - fermé $+$ : $a+a'\in I$
  - stable $\cdot$ : $ra\in I$ pour $r\in R$
  - triviaux : $I=\{0\}$ et $I=R$ ($1\in I\implies I=R$)
  - $( r)=rR=\{rx\mid x\in R\}$
  - principal : $\exists r\in R\tq ( r)=I\not = R$ (seul unique élément)
  - $m\Z\subset d\Z$ ssi $d|m$
- **anneau principal** : tous les idéaux principaux
  - tous les anneaux possédant division euclidienne : $\Z$
- **caractéristique** : plus petit entier positif $m$ tel que $m\cdot 1_R=0$ (si pas = injectif, caractéristique nulle)
  - caractéristique anneau intègre ou corps : $0$ ou $p$
- **corps** : anneau commutatif dont tous les éléments non nuls sont unités
  - $\Z/p\Z$ est noté $\F_p$ ($p$ premier), corps à $p$ éléments
  - corps ssi $R$ possède que les idéaux triviaux
  - tout homomorphisme de $R$ corps est injectif
- **factorisation homomorphisme** : soit $f:\Z\to R$ et $m\Z\in\Ker(f)$ alors cela induit $\bar f:\ZmZ\to R$ avec $[a]_m\mapsto f(a)$
  - si $m\Z=\ker(f)$ alors $\bar f$ injectif
  - $f=\bar f\circ\pi_m$
  - réciproque
  - $g:\ZmZ\to\Z/d\Z$ ssi $d|m$

## Théorème d'Euler et de Fermat

- **ordre d'un entier $\mod m$** : plus petit entier positif $n$ tel que $a^n\equiv 1\mod m$ avec $(a,m)=1$
- **théorème d'Euler** : $a^{\varphi(m)}\equiv 1\mod m$ avec $(a,m)=1$
  - inverse de $[a]_m$ : $[a]_m^{\varphi(m)-1}$
- **petit théorème de Fermat** : $a^{p-1}\equiv 1\mod p$ avec $p$ premier ne divisant pas $a$

## Groupes

- **groupe** : $(G,*,e)$ avec ensemble, une loi interne et un élément distingé
  - $G\times G\to G$ avec $(g,h)\mapsto g*h$
  - associatif : $(g*h)*k=g*(h*k)$
  - neutre : $g*e=g$
  - existence inverse : $g*g^{-1}=e$
- **groupe commutatif (abélien)** : $g*h=h*g$
- **ordre d'un groupe** : $|G|=\#G$ nombre fini d'éléments
- **ordre d'un élément** : plus petit entier positif non nul $n$ tel que $g^n=g*\cdots *g=e$ (si pas, ordre infini)
  - $g$ même ordre que $g^{-1}$
- **sous-groupe** : sous-ensemble non vide $H$ de $G$
  - fermé $*$ : $g*h\in H$
  - inverse : $h^-1\in H$
  - propriétés
    - $e\in H$
- **sous-groupe engendré par $g$** : $<g>=\{g^n\mid n\in\Z\}$
- **groupe cyclique** : $<g>=G$ avec élément $g$ générateur du groupe, forcément abélien
  - $\ZmZ\times\Z/n\Z$ cyclique ssi $(m,n)=1$
  - si fini : ordre générateur = ordre groupe
  - $G\cong\Z/n\Z$ avec $g^k\mapsto [k]_n$
  - groupe cyclique d'ordre $n$ : $C_n$
  - tout groupe d'ordre premier est cyclique
  - sous-groupe aussi cyclique
  - $(g^k)^a=e_G$ ssi $a$ multiple de $d$ sachant $G=<g>$ cyclique d'ordre $n$ et $n=kd$
  - existe sous-groupe de $G$ d'ordre $d$ sachant $G$ cyclique d'ordre $n$ et $d|n$
  - $G$ a exactement $\varphi(n)$ générateurs sachat $G$ cyclique d'ordre $n$
- **théorème de Lagrange** : l'ordre d'un sous-groupe $H$ divise l'ordre du groupe fini $G$
  - $g^{|G|}=e$
  - élément d'ordre $d$ : sachant $g^n=e$, $d|n$
- **homomorphisme de groupes** : $f:G\to H$
  - $f(g*g')=f(g)\circ f(g')$
  - $f(e_G)=e_H$
  - propriétés
    - $f(g^{-1})=f(g)^{-1}$
  - isomorphe ($G\cong H$) si homorphisme bijectif
  - $f:\ZmZ\to\Z/d\Z$ d'anneaux se restreint aux unités : $\bar f : (\ZmZ)^*\to(\Z/d\Z)^*$
  - noyau : $\Ker(f)=\{g\in G\mid f(g)=e_H\}$
  - injectif ssi $\Ker(f)=\{e_G\}$
  - image : $\Im(f)=\{h\in H\mid \exists g\in G\text{ avec } f(g)=h\}$
- **théorèmes de structure des groupes abéliens d'ordre $n$ finis** : tous produit de groupes cycliques
  - $G\cong C_{d_1}\times\cdots\times C_{d_r}$ où $d_1|\cdots|d_r\in\N$
  - $G\cong C_{d_1^{k_1}}\times\cdots\times C_{p_r^{k_r}}$ où $n=p_1^{k_1}\cdots p_r^{k_r}$ premiers

## Théorème des restes chinois

- **théorème des restes chinois I**
  - $m_1,\ldots,m_r$ des entiers premiers deux à deux
  - $ \begin{align}x&\equiv a_1\mod m_1\\ &\vdots\\    x&\equiv a_r\mod m_r\end{align}$
- avec comme solution $x$ et $x'$ où $x\equiv x'\mod M$ et $M=m_1\cdots m_r$
- **théorème des restes chinois II**
  - $m_1,\ldots,m_r$ des entiers premiers deux à deux
  - $M=m_1\cdots m_r$
  - $f:\Z/M\Z\to\Z/m_1\Z\times\cdots\times\Z/m_r\Z$ avec $[a]_M\mapsto ([a]_{m_1},\ldots,[a]_{m_r})$
  - cette homorphisme d'anneaux est un isomorphisme 
- **1ère méthode**
  - $$\begin{align}x_i&\equiv 0\mod m_1\\ &\vdots\\
    x_i&\equiv 1\mod m_i\\ &\vdots\\ x_i&\equiv 0\mod m_r \end{align}$$
  - $k_i=m_1\cdots m_{i-1}m_{i+1}\cdots m_r$
  - $1=rk_i+sm_i$ avec $rk_i=x_i$
  - $x=a_1x_1+\cdots+a_rx_r$
- **2ème méthode**
  - $\begin{align} x&\equiv a_1\mod m_1\\  x&\equiv a_2\mod m_2\\ \end{align}$
- remplacer deux premières équatios par $x\equiv b\mod m_1m_2$ 
  - ainsi $m_1u-m_2t=a_2-a_1$ via Bezout
  - $x=m_1u+a_1=b$
  - récursivement

## Anneau de polynômes

- **anneau de polynôme** : $f(X)=a_nX^n+\cdots+a_1X+a_0$ avec $a_i\in R$ et $a_n\not =0$
  - degré de $f$ : $\deg(f)=n$
  - ensemble des polynômes à coéficients dans $R$ : $R[X]$
  - polynôme constant : $f(X)=r$ de degré nul
  - règle des degrés : si intègre $\deg(fg)=deg(f)+deg(g)$
    - au plus $n$ racine
    - unitaire si $a_n=1$
    - associé si $f(X)=a\cdot g(X)$ avec $a\in K*$ corps
  - unité : $f(X)=r\in R^*$
  - homomorphisme d'anneau : $\phi: A[X]\to B[X]$ avec $\phi(f)(X)=\phi(a_n)X^n+\cdots+\phi(a_1)X+\phi(a_0)$
- **division euclidienne** : $g(X)=f(X)q(X)+r(X)$ avec $f,g\in K[X]$ des corps et $\deg( r)<\deg(f)$
- **division** : $f$ divise $g$ si $g=fq$
- **anneau $K[X]$ principal**
- **PGCD** : $p$ si $p|f$ et $p|g$ avec $p$ de degré maximal
  - non unique, associé
  - unique pgcd unitaire $(f,g)=p$
- **identité de Bézout** : $p$ pgcd de $f$ et $g$, alors $r\cdot f+s\cdot g=p$
- **polynôme irréductible** : $\deg(f)>0$ et $f=g\cdot h$ implique que $g,h\in K^*$ (attention au corps)
  - pour degré $2$ et $3$ : irrdécutible ssi aucune racine dasn $K$
  - analogue aux nombres premiers dans $\Z$
- **décomposition en produit d'irréductibles** : $f=a\cdot p_1\cdots p_r$ avec $a\in K^*$ unité et $p_1,\ldots p_r$ des polynômes irréductibles (unique)
- **congruences modulo un polynôme** : $f\equiv g\mod m$
  - $[f]_m+[g]_m=[f+g]_m$
  - $[f]_m\cdot [g]_m=[fg]_m$
- **classe** $\mod m$ : $\xi$
  - $\R[X]/(X^2+1)\cong\C$
- **classe de congruence** : $K[X]/(m)=K[\xi]$
- **corps** : ssi $m(X)$ irréductible dans $K[X]/(m)$
- **homomorphisme de corps** : deux corps dans $\phi:F[X]\to L$ avec l'idéal $f$ inclus dans $\Ker(\phi)$ $\bar\phi:F[X]/(f)\to L$ (si $f$ irréductible, injectif)
- **théorème des restes chinois**
  - $K[X]/(f\cdots g)\cong K[X]/(f)\times\cdots\times K[X]/(g)$ avec $f,\ldots,g$ polynômes premiers deux à deux
  - $\begin{align}F&\equiv g_1\mod f_1\\ &\vdots\\ F&\equiv g_n\mod f_n\end{align}$

## Corps finis

- **corps finis** : $\F_p[X]/(f)$ a $p^n=p^{\deg(f)}$ éléments avec $f$ irréductible
  - corps fini à $p$ élément : $K\cong \F_p\cong \Z/p\Z$
  - sous-corps à $p$ éléments : si corps de caractéristique $p$
  - $L$-espace vectoriel : $L$ corps et $K$ sous-corps, même addition et multiplication que le corps
  - caractéristique $p$ : $K$ possède $p^n$ élément
- **racine multiple** : $f=(X-\alpha)^ng$ ssi $f'(\alpha)=0$ (le plus grand $n$ s'appelle la multiplicité de $\alpha$)
- **dérivée** : $f'(X)=na_nX^{n-1}+\cdots+2a_2X+a_1$ (attention au corps)
- **existence corps à $p^n$** : pour tout $p$ premier et $n$ entier
- **ordre maximal d'un élément de groupe abélien** : $x^m=1$ pour tout $m$
- **sous groupe $G$ de corps $K^*$** : $G$ cyclique (corps fini, $K^*$ groupe cyclique)
- **polynôme minimal** : polynôme minial qui annule $f(\alpha)=0$, diviseur de $f$
- **plus petit sous-corps contenant $\alpha$** : $K(\alpha)=\{\frac{f(\alpha)}{g(\alpha)}\mid f,g\in K[X], g(\alpha)\not =0\}$
- **existence polynôme irréductible de degré $n$** : $f\in\F_p[X]$ dans $\Q$
  - $n|m\implies f|X^{p^m}-X$
- **$\C$ algébriquement clos** : seul polynôme de degrée $1$ sont irréductibles (dans $\R$, de degré $1$ ou $2$)
- **corps à $p^n$ éléments unique à isomorphisme près** : $\F_q$ avec $q=p^n$ de caractéristique $p$
- **isomorphismes de Frobenius** : $K\to K$ avec $x\mapsto x^p$ (si fini)
  - automorphisme : $\phi^{\circ n}=\phi\circ\cdot\circ\phi=\text{Id.}$ pour $q=p^n$

## Exemples

- anneaux
  - $(\Z,+,\cdot,0,1)$, $\Q$, $\R$, $\C$, intégre
  - $\ZmZ$, corps si $m$ premier
  - $M_{nn}(\R)$ : ensemble des matrices carrées sur $\R$, non commutatif
  - $R[X]$ : ensemble des polynômes à coefficients dans un anneau $R$, constante $c$ est unité, idéal sans terme constant
  - $(\text{End(V)},+,\circ,0,id_V)$ : ensemble des applications linéaires avec $V$ un $\R$-espace vectoriel (si fini peut être identifié à $M_{nn}(\R)$ moyennant une base)
- homomorphisme d'anneaux
  - $\pi_m:\Z\to\ZmZ$ avec $a\mapsto [a]_m$
  - $f:\Q[X]\to Q$ avec $p(X)\mapsto p(0)$
  - sous-anneau vers anneau
- groupe
   - $(\Z, +, 0)$
    - $(R,+,0)$ et $(R^*,\cdot,1)$ si $R$ anneau
    - $GL_n(\R)​$ : matrices carrés avec produit matriciel et matrice identité, non commutatif
