# PHYS101

> [GNU General Public License v3.0](https://github.com/zifeo/EPFL/blob/master/LICENSE) licensed. Source available on [github.com/zifeo/EPFL](https://github.com/zifeo/EPFL).

Fall 2013: Physique générale I

[TOC]

## Cinématique

- référentiel : 
  ensemble de plus de 3 points non coplanaires, immobiles les uns par rapport aux autres

- point matériel (**PM**) : 
  point géometrique auquel on attribue la masse de l'objet

- trajectoire : 
  lieu géometrique du **PM** au cours de son temps par rapport au référentiel

- equation horaire : 
  soit $O$ l'origine du référentiel et $P$ la position du **PM** à un temps donné, notons le vecteur $\vec{OP}=\vec{r}$, alors $\vec{r}(t)$ est la position du **PM** en tout temps $t$

- vitesse vectorielle instantanée : $\vec{v}=\frac{d\vec{r}}{dt}=\frac{m}{s}$

- accérération vectorielle :
  $\vec{a}=\frac{d\vec{v}}{dt}=\frac{m}{s^2}$

- repère :
  $(A,\hat{x_1},\hat{x_2},\hat{x_3})$ est un repère $A$ avec ses trois vecteurs unités (leur norme vaut 1) souvent orthonormé

- grandeur extensive :
  la valeur de cette grandeur est additive (par opposition à grandeur intensive, ex. température)

- masse d'inertie : 
  dans la mécanique newtonnienne, la masse est une grandeur conservée (sans perte)

- produit scalaire :
  $\vec{a}\cdot\vec{b}=ab\cos\theta$

- produit vectoriel :
  $\vec{a}\land \vec{b}=\begin{vmatrix}\hat x_1 & a_1 & b_1\\\ \hat x_2 & a_2 & b_2\\\ \hat x_3 & a_3 & b_3\end{vmatrix}$ (determinant par rapport avec la première colonne !). Si $(\vec{a}\land\vec{b})\cdot\vec{c}$, $\vec{c}$ prend la place de $\vec{\hat x}$. La norme vaut $|\vec{a}\land\vec{b}|=ab|\sin\theta|$ et le produit est perpendiculaire au plan décrit par $\vec{a}$ et $\vec{b}$ (règle des 3 doigts)

- projection d'un vecteur sur un axe :
  $\vec{AP}\cdot\hat u=AP\cos\theta$

### Lois de Newton

#### Première loi de Newton et référentiel d'intertie
> Tout corps persévère dans l'état de repos ou de mouvement uniforme en ligne droite à moins que quelque force n'agisse sur lui et ne le contraigne à changer d'état.

- référentiel d'intertie : référentiel où le principe d'intertie est vérifié

#### Deuxième loi de Newton pour le point matériel
> Les changements de mouvement sont proportionnels à la force motrice (force appliqué sur un temps), et se font dans la ligne droite dans laquelle cette force est imprimée à l'objet.

- quantité de mouvement :
  $\vec{p}=m\vec{v}$

- changement de mouvement :
  $\frac{d\vec{p}}{dt}=\vec{F}$, dans le cas où la masse $m$ est constante $\vec{F}=m\vec{a}$

#### Action et réaction
> A toute action, il y a toujours une réation égale qui lui est opposée.

- conservation de quantité de mouvement :
  dans un système isolé la résultante des forces est nulle

## Dynamique

- marche à suivre :
  1. choix du référentiel
    - choix du repère
    - choix du système de coordonées (condition initiales)
    - modèle de force (bilan)
    - loi de la dynamique (équation accélération)
    - équations du mouvement
    - intégration des équations du mouvement

### Accélération normale et tangentielle

- abscisse curviligne :
  $s=R\phi$

- vitesse scalaire :
  $v=\frac{d\vec{r}}{dt}=\frac{d\vec{r}}{ds}\frac{ds}{dt}=v\frac{d\vec{r}}{ds}$ car $v=\frac{ds}{dt}$ et $\frac{d\vec{r}}{ds}=1$ ($arc\approx secante$)

- accélération tangentielle :
  accélération classique $a=\frac{dv}{dt}\hat \tau$

- accélération normale :
  perpendiculaire à la tangente $a=v\frac{d\hat\tau}{dt}=v\frac{d\hat\tau}{ds}\frac{ds}{dt}=v^2\frac{d\hat\tau}{ds}=\frac{v^2}{R}$ car $\frac{d\hat\tau}{ds}=\frac{1}{R}$

- accélération vectorielle (complète) :
  avec $\hat n$ étant le vecteur unité perpendiculaire, $\vec{a}=\frac{dv}{dt}\hat \tau+\frac{v^2}{R}\hat n$

- vitesse et vitesse angulaire :
  $v=R\omega=\frac{ds}{dt}=R\dot \phi$

- angle :
  $\phi=\omega t$

- accélération centripète :
  $a=R\omega^2$

### Coordonnées cylindriques et sphériques

- cylindriques :
  $x_1=\rho\cos\phi \quad x_2=\rho\sin\phi \quad x_3=z$ en fonction de $\rho,\phi,z$

- sphérique :
  $x_1=r\sin\theta\cos\phi \quad x_2=r\sin\theta\sin\phi \quad x_3=r\cos\theta$ en fonction de $r,\theta,\phi$

- vitesse et accélération :
  voir formulaire

- ligne de coordonnées :
  lieu géometrique des points qui ont deux coordonnées fixes

- force de liaison et contrainte

### Rotations

- formules de Poisson :
  $\frac{d\hat{e_i}}{dt}=\vec{w}\land\hat{e_i}$ ainsi $\vec v=\frac{d\vec r}{dt}=\vec\omega\land\vec r$ et $a=\frac{d\vec v}{dt}=\frac{d}{dt}(\vec\omega\land\vec r)=\vec\omega\land\frac{d\vec r}{dt}=\vec\omega\land(\vec\omega\land\vec r)$ (centripète)

- vitesse angulaire :
  $\vec{w}=\frac{2\Pi}{T}=\frac{v}{R}$ (perpendiculaire au plan de rotation)

### Energie, puissance, travail

- forces :
  $F=\frac{kg\,m}{s^2} newton$

- puissance instantanée :
  $P=\vec{F}\cdot\vec{v}=\frac{kg\,m^2}{s^3} watt$

- travail de la force :
  $W=\int P(t)dt= \int \vec{F}(t)\cdot\vec{v}\,dt=\frac{kg\,m^2}{s^2} joule$

- énergie cinétique :
  $T=\frac{1}{2}m\vec{v^2}$

- énergie potentiel :
  $V(\vec{r})=\int_\vec{r}^{\vec{r}_s}\vec{F}\cdot d\vec{r}=V(\vec{r})-V(\vec{r_s})$

- énérgie mécanique totale :
  $E=T+V$

- conservation de l'énergie :
  si toutes les forces sont conservatives, l'énergie mécanique est conservée

- collision élastique : si l'énergie cinétique est conservée, inélastique sinon (ou mou) $T_i+Q=T_f$ où $Q$ est l'énergie libérée par la collision

### Moment cinétique et moment de force

- moment cinétique :
  $L_0=\vec{OP}\land\vec{p}$

- moment de la force :
  $M_0=\vec{OP}\land\vec{F}$

- théorème du moment cinétique pour un **PM** :
  $\frac{d\vec{L_0}}{dt}=\vec{M_0}$

- 3ème loi de Kepler :
  $\frac{T^2}{a^3}=\frac{4\pi^2m}{K}$ est une constante où $a$ est le demi-grand axe et $K$ une constante

### Autres forces et frottements

- force de gravitation :
  $\vec{F_g}=G\frac{m_1m_2}{d^2}\hat u$ où $G\approx 6.67\times 10^{-11}$

- force de Coulomb :
  $\vec{F_c}=\frac{1}{4\pi\epsilon_0}\frac{q_1q_2}{r^2} \hat u$ où $\frac{1}{4\pi\epsilon_0}=8.988\times 10^9$

- champ électrique :
  $\vec{F_e}=q\vec{E}$ où $\vec{E}$ est un champ électrique

- force de Lorentz :
  $\vec{F_l}=q\vec{v}\land\vec{B}$ où $\vec{B}$ est un champ d'induction

- friction statique :
  pour un solide indéformable $F_{max}=\mu_sN$ où $\mu_s$ est le coefficient de frottement statique et $N$ la force de réaction de la surface

- frottement avec glissement :
  $\vec{F_f}=-\mu_c|N|\hat v$ où $\mu_c$ est le coefficient de frottement cinétique

- frottements visqueux :
  $\vec{F_v}=-k\eta\vec{v}$ où $\eta$ est le coefficient de viscosité et $k$ un facteur géometrique

## Pratique

### Balistique

- loi dynamique :
  $\vec{F}=m\vec{a}$

- modèle de force :
  $\vec{F}=m\vec{g}$ où $\vec{g}=9.8$ avec $\vec{g}$  de direction verticale vers le bas

- choix de coordonnées :
  $Oxyz$ avec $x(0)=x_0 \quad y(0)=y_0 \quad z(0)=z_0\\\ vx(0)=vx_0 \quad vy(0)=vy_0 \quad vz(0)=vz_0 \\\ a_x=\ddot{x} \quad a_y=\ddot y \quad a_z=\ddot z$

- équation du mouvement :
  $m\ddot x=0 \quad m\ddot y=0 \quad m\ddot z=-mg$

- intégration en tenant compte des conditions initiales :
  $x(t)=v0_xt+x_0 \quad y(t)=v0_yt+y_0 \quad z(t)=-\frac{1}{2}gt^2+v0_zt+z_0$

### Ballistique avec résistance de l'air

- modèle de force :
  $\vec F=m\vec g-b\vec v$

- équation du mouvement :
  $m\ddot x=-b\dot x \quad m\ddot y=-b\dot y \quad m\ddot z=-mg-b\dot z$

- intégration en $x$ :
  $\ddot x=-\frac{b}{m}\dot x \quad \dot x(t)=\dot x(0)e^{-bt/m} \quad x(t)=\dot x(0)(\frac{-m}{b})e^{-bt/m}+\frac{m}{b}\dot x(0)$ avec $\frac{m}{b}=\tau$, on a alors $x(t)=\dot x(0)\tau(1-e^{-t/\tau})$

- intégration en $z$ :
  $\dot z =-\tau g-\tau g e^{-t/\tau} \quad z=-\tau gt+\tau^2g(1-e^{-t/\tau})$

### Oscillateur harmonique

- modèle de force :
  $F=-kx$ (force de rappel)

- équation du mouvement :
  $m\ddot x=-kx \quad \dot x =-\omega\cos(\omega t) \quad x=-\omega^2\cos(\omega t)$ avec $\omega=\sqrt{\frac{k}{m}}=\frac{2\pi}{T}$

### Oscillateur harmonique amorti

- modèle de force :
  $\vec F = -kx-b\vec v$

- équation du mouvement :
  $\sqrt{\frac{k}{m}}=\omega_0$ et $\frac{b}{2m}=\gamma$, ainsi $\ddot x+2\gamma\dot x+\omega_0^2x=0$ dont la fonction d'essai est $x=e^{\lambda t}$

- si amortissement faible $\gamma^2<<\omega_0^2$ :
  la solution est irréele mais peut s'écrire $x(t)=e^{-\gamma t}C\cos(\omega_1t+\phi)$ avec $\omega_1=\sqrt{\omega_0^2-\gamma^2}$

- si amortissement critique $\gamma^2=\omega_0^2$ :
  $x(t)=e^{-\omega_0 t}(x_0+t(x_0\omega_0+\dot x_0))$

### Pendule mathématique plan

- référentiel, repère, coordonnées :
  $Oxy$ dont $O$ est le point d'attache avec coordonnées cylindriques

- bilan des forces :
  pesenteur $F$ et liaison $T$

- cinématique :
  $\ddot\rho=\dot\rho=0 \quad z=0$ et $\vec a=(-l\dot\phi^2)\vec {e\rho} +(l\ddot\phi)\vec{e\phi}$

- équation du mouvement :
  $-ml\dot\phi^2=mg\cos\phi-T$ et $\ddot\phi=-\frac{g}{l}\sin\phi$

- intégration (qualitative) si $\phi<<1$ :
  on peut approximer $\sin\phi\approx\phi$ ainsi $\ddot\phi=-\frac{g}{l}\phi$ qui est l'équation d'un osciallateur harmonique de période $2\pi\sqrt{l/g}$

### Résonance

- équation du mouvement avec un oscillateur :
  $m\ddot x=-kx-b\dot x+F(t)$

- équation du mouvement :
  $\ddot x +\frac{1}{\tau}\dot x+\omega_0^2x=\alpha_0\cos(\omega t)$ avec $\alpha_0=\frac{f}{m}$
