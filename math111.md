# MATH111

> [GNU General Public License v3.0](https://github.com/zifeo/EPFL/blob/master/LICENSE) licensed. Source available on [github.com/zifeo/EPFL](https://github.com/zifeo/EPFL).

Fall 2013: Linear Algebra

[TOC]

### Linear equation
- system of linear equation
- row reduction and echelon forms
  1. substracting one equation from another
  2. multiplying an eq by $c\not=0$
  3. changing order of equations
    $$A\vec{x}=\vec{b} \to \stackrel{augmented\:matrix}{(A\;|\;\vec{b})} \stackrel{1,2,3}{\to} \stackrel{echelon\:form}{\left(\begin{array}{ccc|c} .&.&.&. \newline 0&.&.&. \newline 0&0&.&. \end{array}\right)} \stackrel{1,2,3}{\to} \stackrel{reduced\:echelon\:form}{\left(\begin{array}{ccc|c} 1&0&0&. \newline 0&1&0&. \newline 0&0&1&. \end{array}\right)}$$
    - gives no solution if row $(0\;0\;0\;|\;.)$
    - gives 1 solution if $\#pivots = \#variables$
    - gives $\infty$ solutions if $\#pivots < \#vars$
      - $\#vars-\#pivots=\#free\:vars$ (dimension solution set)
- vector equations and matrix equations
- solutons sets of linear systems
- linear independence
  $\{\vec{v_1},\ldots,\vec{v_k}\} \subseteq V \iff c_1\vec{v}_1+\cdots+c_k\vec{v}_k=0$ is only statisfied with all $c_i=0$.
- linear transformations :
  $T\;:\;V\to W$ ($V,W$ vector spaces) such that $T(\vec{0})=\vec{0}$, $T(\vec{u}+\vec{v})=T(\vec{u})+T(\vec{v})$ and $T(c\vec{v})=cT(\vec{v})$.

- matrix of a linear transformation
  $T_A\;:\;\mathbb{R}^n\to \mathbb{R}^m$, $T_A(x)=Ax$
  - $T$ is one-to-one iff $T(\vec{x})=0$ has only the trivial solution
    - $T$ is one-to-one iff columns of $A$ are linearly independent
    - $T$ is onto iff for every $\vec{y}\in\mathbb{R}^m$ there is at least one $\vec{x}\in\mathbb{R}^n$ such that $T(\vec{x})=\vec{y}$
- span : set of all linear combination $span(\vec{v_1},\ldots,\vec{v_k})=\sum_1^k c_i \vec{v_i}$.

### Matrix algebra
- matrix operations
  - $AB\not=BA$
  - $(A+B)^T=A^T+B^T$
  - $(AB)^T=B^TA^T$
  - $(AB)^{-1}=B^{-1}A^{-1}$
  - $(A^T)^{-1}=(A^{-1})^T$
- inverse of a matrix
  - the product of invertible matrices is invertible
- characterization of invertible matrices
  - $A$ is invertible
    - $A$ is row equivalent to $n\times n$ identity matrix
    - $A$ has n pivot positions
    - $A\vec{x}=0$ has only the trivial solution
    - columns of $A$ form a linearly independent set
    - linear transformation $\vec{x}\mapsto A\vec{x}$ is one-to-one
    - $A\vec{x}=\vec{b}$ has at least one solution for each $\vec{b}\in\mathbb{R}^n$
    - columns of $A$ span $\mathbb{R}^n$
    - linear transformation $\vec{x}\mapsto A\vec{x}$ maps $\mathbb{R}^n$ onto $\mathbb{R}^n$
    - there is an $n\times n$ matrix $C$ such that $CA=I$
    - there is an $n\times n$ matrix $D$ such that $AD=I$
    - $A^T$ is an invertible matrix
    - columns of A form a basis of $\mathbb{R}^n$
    - $Col(A)=\mathbb{R}^n$
    - $dim(Col(A))=n$
    - $rank(A)=n$
    - $Nul(A)=\{\vec{0}\}$
    - $dim(Nul(A))=0$
    - $det(A)\not = 0$
- partitionned matrices
- subspace is a subset of $\mathbb{R}^n$ with
  - $\vec{0}$ is in $H$
    - $\vec{u}+\vec{v}$ is in $H$
    - $c\vec{u}$ is in H
    - the number 0 is not an eigenvalue of $A$
- basis :
  a basis for a subspace $h$ is a linearly independent set in $H$ that spans $H$. Any linearly independent set of exactly $p$ elements in $H$ is automatically a basis for $H$.

- dimension of a nonzero subspace $H$ is the number of vectors in any basis for $H$ but $dim(\vec{0})=0$.

- rank
  $rank(A)=dim(Col(A))$.
  - $A_{m\times n}\;rank(A)+dim(Nul(A))=dim(Col(A))+dim(Nul(A))=n$

### Determinants
$det(A)=\sum_1^n (-1)^{k+i} a_i det(A_i)$ with respect to a row or a column $k$. If we have a triangular matrix, the determinant is the product of diagonal entries.
- row reduction impacts :
  1. substracting one equation from another does not change the determinant
  2. multiplying an eq by $c\not=0$ multiply the determinant by $c$
  3. changing order of equations multiply the determinant by $-1$
- properties of determinants :
  - $det(AB)=det(A)det(B)$
    - $det(A^T)=det(A)$
    - $det(A^{-1})=\frac{1}{det(A)}$
- Cramer's rule :
  if $A_{n\times n}$ is invertible, for any $\vec{b}$ in $\mathbb{R}^n$, the unique solution $\vec{x}$ of $A\vec{x}=\vec{b}$ has entries given by $x_i=\frac{det(A_i(\vec{b}))}{det(A)}$ where $A_i(\vec{b})=[\vec{a_1},\ldots,\vec{a_i}=\vec{b},\ldots,\vec{a_n}]$ and $\vec{x}=(x_1,\ldots,x_n)^T$.

- Cramer's inversion :
  if $A_{n\times n}$ is invertible, then $A^{-1}=\frac{1}{det(A)}adj(A)=\frac{1}{det(A)}\begin{pmatrix} {A_1}_1&-{A_1}_2&{A_1}_3 \newline -{A_2}_1&{A_2}_2&-{A_2}_3 \newline {A_3}_1&-{A_3}_2&{A_3}_3 \end{pmatrix}^T$ where the adjugate $adj(A)=C^T$ which is the cofactor matrix such that ${C_i}_j=(-1)^{i+j}{A_i}_j$ and ${A_i}_j$ are the intermediate determinant.

- area and volumes
  $=|det(A)|$ where A is a $2\times 2$ or $3\times 3$ matrix.

- linear transformations : the determinant of the transformation describe how the area or the volume is affected by it $area(T(S))=|det(A)|area(S)$.

### Vector spaces
set $V$ with 2 operations $u,v\in V\; c\in \mathbb{R}\quad u+v\quad cv$ satisfaying 10 conditions.

- conditions
  1. $\vec{u}+\vec{v} \in V$
    2. $\vec{u}+\vec{v}=\vec{v}+\vec{u}$
    3. $(\vec{u}+\vec{v})+\vec{w}=\vec{u}+(\vec{v}+\vec{w})$
    4. $\vec{0} \in V$ such that $\vec{u}+\vec{0}=\vec{u}$
    5. there is $\vec{-u}$ such that $\vec{u}+(\vec{-u})=\vec{0}$
    6. $c\vec{u} \in V$
    7. $c(\vec{u}+\vec{v})=c\vec{u}+c\vec{v}$
    8. $(c+d)\vec{u}=c\vec{u}+d\vec{u}$
    9. $c(d\vec{u})=(cd)\vec{u}$
    10. $1\vec{u}=\vec{u}$

- null spaces
  $Nul(A)=Ker(T_A)=$ subspace of $\vec{x}\in \mathbb{R}^n$ such that $A\vec{x}=\vec{0}$. The dimension of the null space is the number of free variables in the equation $A\vec{x}=\vec{0}$.

- column spaces
  $Col(A)=Im(T_A)=$ subspace of $\vec{y}\in \mathbb{R}^m$ such that $A\vec{x}=\vec{y}$ for some $\vec{x}\in \mathbb{R}^n$. The dimension of column space is the number of pivot columns in $A$.

- linearly independent sets, bases :
  basis of $V$ is $\beta = \{\vec{b_1},\ldots,\vec{b_k}\} \subseteq V$ such that every $\vec{v}\in V$ can be described in only one way $\vec{v}=\sum_1^k c_i \vec{b_i}$. Moreover it must be linearly independent and $span(\beta)=V$.

- coordinates systems :
  suppose $\beta=\{\vec{b_1},\ldots,\vec{b_n}\}$, the coordinates systems of $x$ relative to the basis $\beta$ are the weights $c_1,\ldots,c_n$ such that $\vec{x}=c_1\vec{b_1}+\ldots+c_n\vec{b_n}$.
  $$[\vec{x}]\beta=\begin{bmatrix} c_1 \\ \vdots \\ c_n\end{bmatrix}$$

- change of basis :
  let $\beta=\{\vec{b_1},\ldots,\vec{b_n}\}$ and $\epsilon=\{\vec{e_1},\ldots,\vec{e_n}\}$ be bases of a vector space $V$, then there is a unique $n\times n$ matrix $P\epsilon\gets\beta=[[b_1]\epsilon,\ldots,[b_n]\epsilon]$ such that $[\vec{x}]\epsilon=P\epsilon\gets\beta \;[\vec{x}]\beta$ where $[\vec{e_1},\ldots,\vec{e_n}][b_i]\epsilon=\vec{b_i}$ and $[\vec{e_1},\ldots,\vec{e_n}\;|\;\vec{b_1},\ldots,\vec{b_n}]\to[I\;|\;P\epsilon\gets\beta]$

- row spaces :
  if two matrices are row equivalent, then their row spaces are the same. It is the span of all nonzero horizontal vector in the echelon form of $A$.

### Eigenvalues and eigenvectors
- eigenvalues and eigenvectors :
  an eigenvector of $A_{n\times n}$ is a nonzero vector $\vec{x}$ such that $A\vec{x}=\lambda\vec{x}$ for some $\lambda$ scalar. The scaler is called the corresponding eigenvalue. The set of eigenvalues is linearly independent if eigenvectors have distinct eigenvalues.

- eigenspace :
  eigenspace of $\lambda$ is the set of all eigenvectors for $\lambda_i$ or $Eig(\lambda_i)=Nul(A-\lambda_i I)$

- triangular matrices :
  the eigenvalue are the entries of the diagonal.

- characteristic equation :
  $det(A-\lambda I)=0$, two matrix are similar if they have the same characteristic polynomial

- eigenvectors and linear transformation

- complex eigenvalues :
  $\mathbb{C}=\{a+bi\;|\;a,b\in\mathbb{R}\}$
  - addition $(a+bi)+(c+di)=(a+c)+(b+d)i$
    - multiplication $(a+bi)(c+di)=(ac-bd)+(ad-bc)i$
    - division $\frac{1}{a+bi}=\frac{a-bi}{a^2+b^2}$
    - complement of $a+bi$ is $a-bi$
    - real part $Re(a+bi)=a$
    - imaginary part $Im(a+bi)=b$
    - a complex eigenvalue has always its complement being an eigenvalue too
  - $A_{2\times 2}$ with eigenvalue $\lambda=a-bi$ with an associated eigenvector $\vec{v}$ then, $A=PCP^{-1}$ where $P=[Re(\vec{v}),Im(\vec{v})]$ and $C=\begin{bmatrix}a&-b\\b&a\end{bmatrix}$. This correspond to a rotation matrix.

### Orthogonality and least squares
- inner product :
  $\vec{u}\cdot \vec{v}=u_1v_1+\cdots+u_nv_n$
  1. $\vec{u}\cdot \vec{v} = \vec{v} \cdot \vec{u}$
    2. $(\vec{u}+\vec{v})\cdot\vec{w}=\vec{u}\cdot \vec{w}+\vec{v}\cdot\vec{w}$
    3. $(c\vec{u})\cdot \vec{v}=c(\vec{u}\cdot\vec{v})$
    4. $\vec{u}\cdot\vec{u}\ge 0$ and $\vec{u}\cdot\vec{u}=0$ iff $\vec{u}=0$
- norm (length) :
  $||\vec{v}||=\sqrt{\vec{v}\cdot\vec{v}}=\sqrt{v_1^2+\cdots+v_n^2}$ and $||\vec{v}||^2=\vec{v}\cdot\vec{v}$

- distance :
  distance between two vectors is written as $dist(\vec{u},\vec{v})=||\vec{u}-\vec{v}||$

- orthogonality :
  two vectors are orthogonal if $\vec{u}\cdot\vec{v}=0$. A vector $\vec{v}=\vec{\hat v}+\vec{v^\ast}$ can be decomposed in two components, one parallel $\vec{\hat v}=\frac{v\cdot u}{u\cdot u}\vec{u}$ and one orthogonal $\vec{v^\ast}=\vec{v}-\frac{v\cdot u}{u\cdot u}\vec{u}$ to $\vec{u}$.

- orthogonal sets :
  a vector is in $W^\bot$ iff it is orthogonal to every vector in a set that spans $W$. $W^\bot=\{v\in W | v\cdot w=0 \;\forall w\in W\}$ when $W\subseteq V$.

- orthogonal complement :
  the orthonal complement $(Row(A))^\bot=Nul(A)$ and $(Col(A))^\bot=Nul(A^T)$

- orthogonal projection :
  $proj_\vec{u}(\vec{v})=\vec{\hat v}$. In general if $\{\vec{u_1},\ldots,\vec{u_m}\}$ is an orthogonal basis of $W$, then $proj_W(\vec{v})=\sum_1^m \frac{v\cdot u_i}{u_i \cdot u_i}\vec{u_i}$

- orthonormal :
  $U_{m\times n}$ matrix has orthonormal columns iff $U^TU=I$
  - $||U\vec{x}||=||\vec{x}||$
    - $(U\vec{x})\cdot(U\vec{y})=x\cdot y$

- orthonormal projection :
  $proj_W(\vec{y})=(y\cdots u_1)\vec{u_1}+\cdots+(y\cdots u_p)\vec{u_p}=UU^T\vec{y}$ where $U=[\vec{u_1},\ldots,\vec{u_p}]$

- Gram-Schmidt process : given a basis $\{\vec{v_1},\ldots,\vec{v_n}\}$ find an orthogonal basis $\{\vec{u_1},\ldots,\vec{u_n}\}$ by doing $\vec{u_1}=\vec{v_1} \quad W=span(\vec{u_1})$, then 
  $\vec{u_2}=\vec{v_2}-proj_W(\vec{v_2}) \quad W=span(\vec{u_1},\vec{u_2})$
  et ceterae.

- least-squares problems :
  solutions of $A\vec{x}=\vec{b}$ is $\vec{\hat x}$ such that $||A\vec{\hat x}-\vec{b}||$ is as small as possible. If $\vec{b}\in Col(A)$ then $\vec{\hat x}=\vec{b}$, else $\vec{\hat b}=proj_{Col(A)}(b)$ and $A^TA\vec{\hat x}=A^T\vec{b}$. If $A^TA$ is invertible, then $\vec{\hat x}=(A^TA)^{-1}A^T\vec{b}$. Moreover if A=QR, then $\vec{\hat x}=R^{-1}Q^T\vec{b}$.

### Symmetric Matrices and quadratic forms
- diagonalization of symmetric matrices :
  if symmetric, then any two eigenvectors from different eigenspaces are orthogonal.

- spectral theorem for symmetric matrices $n\times n$
  - $A$ has $n$ real eigenvalues, couting multiplicities
    - Dimension of the eigenspace for each eigenvalue $\lambda$ equals the multiplicity of $\lambda$ as a root of the characteristic eqution
    - eigenspaces are mutually orthogonal, in the sense that eigenvectors corresponding to different eigenvalues are orthogonal
    - $A$ is orthogonally diagonalizable

- spectral decomposition :
  $A_{n\times n}$ symmetric, then $A=PDP^{-1}=PDP^T$ where $P=(\vec{u_1},\ldots,\vec{u_n})$, $D=\lambda I$ and $A=\lambda_1 \vec{u_1}\vec{u_1^T}+\ldots+\lambda_n \vec{u_n}\vec{u_n^T}$

- quadratics forms :
  $Q(\vec{x})=\vec{x^T}A\vec{x}$ with orthogonally diagonizable $A=QDQ=QDQ^T$, change of variable $\vec{x}=Q\vec{y}$, we get $\vec{x^T}A\vec{x}=(Q\vec{y})^TA(Q\vec{y})=\vec{y^T}(Q^TAQ)\vec{y}=\vec{y^T}D\vec{x}=\lambda_1y_1^2+\cdots+\lambda_ny_n^2$.
- quadractic classification
  - positive definite if $Q(\vec{x})>0\;\forall\vec{x}\not=\vec{0} \iff \forall \lambda_i > 0$
    - negative definite if $Q(\vec{x})<0\;\forall\vec{x}\not=\vec{0} \iff \forall \lambda_i < 0$
  - indefinite otherwise
    - positive or negative semidefinite if $\ge 0$ or $\le 0$
***

### Tools / How to
- row reduction
  - check **linear independence** :
    $\{\vec{v_1},\ldots,\vec{v_k}\} \to A=[\vec{v_1},\ldots,\vec{v_k}]$, take $(A\;|\;\vec{o})$, if 1 solution it is independent, if more it is not.

  - check $\vec{b}\in span(\vec{v_1},\ldots,\vec{v_k})$ or $\vec{b}\in Col(A)$ :
    $A=[\vec{v_1},\ldots,\vec{v_k}]\: or\: A=A\to(A\;|\;\vec{b})$, if 1 or more solution it belongs to, if no solution it does not.

  - find **inverse** of $A$ if it exists :
    $(A\;|\;I)\to(I\;|\;B)\;B=A^{-1}$

  - find $dim(Nul(a)$ :
    $(A\;|\;\vec{0})\to\#vars-\#pivots=dim(Nul(A))$

  - find $dim(Col(a)=dim(span(\vec{v_1},\ldots,\vec{v_k}))$ when $A=[\vec{v_1},\ldots,\vec{v_k}]$ :
    $(A\;|\;\vec{y})\to\#pivots=dim(Col(A))$

- determinants
  - checking invertibility :
    $invertible\iff det(A)\not=0$

  - finding eigenvalue :
    $\lambda \iff det(A-\lambda I)=0$

  - volumes of parallelepiped :
    $area=det[\vec{v_1},\vec{v_2}]$

### Rewrite matrices
- $LU$ factorization $A=LU$
  $$\begin{pmatrix} a&.&. \newline b&.&. \newline c&.&. \end{pmatrix}\to\begin{pmatrix} a&.&. \newline 0&d&. \newline 0&e&. \end{pmatrix}\to\begin{pmatrix} a&.&. \newline 0&d&. \newline 0&0&f \end{pmatrix}=U$$
  $$L= \begin{pmatrix} a/a&0&0 \newline b/a&d/d&0 \newline c/a&e/d&f/f \end{pmatrix}\quad a=(E_1^{-1}\ldots E_k^{-1})U=LU$$
  - $A_{n\times n}$
    - can get echelon form without interchanging rows
    - $L$ stands for lower triangular, $U$ for upper
    - solve faster $L\vec{y}=\vec{b}$ then $U\vec{x}=\vec{y}$
- $QR$ factorization $A=QR$<br>
  $A=[\vec{u_1},\ldots,\vec{u_n}]$, orthogonalize $\vec{u_1},\ldots,\vec{u_n} \to \vec{v_1},\ldots,\vec{v_n}$, then normalize $\vec{v_1},\ldots,\vec{v_n}\to\vec{w_1},\ldots,\vec{w_n}$ (this is orthonormal basis for $\mathbb{R}^n$).
  $$Q=[\vec{w_1},\ldots,\vec{w_n}] \quad R=Q^TA\qquad QQ^T=I$$
  - $A_{m\times n}$
  - $rank(A)=n$
    - $Q$ orthogonal, $R$ uppertriangular (invertible, positive diagonal)
    - least-square
- Diagonalisation $A=PDP^{-1}$<br>
  find eigenvalue $det(A-\lambda I)=p(x)=\prod_1^n (\lambda-d_i) \quad d_i\in\mathbb{C}$, $d_i$, find eigenvectors ≈ such that $Nul(det(A-\lambda_i I))$, if $geom(\lambda_i)=dim(Nul(A-\lambda_i I))=alg(\lambda_i)$ where $alg(\lambda_i)$ is the number of time the eigenvalue has been found, then the diagonalisation exist.
  $$P=[\vec{v_1},\ldots,\vec{v_n}] \quad D=\begin{pmatrix} \lambda_1&0&0 \newline 0&\lambda_2&0 \newline 0&0&\lambda_3 \end{pmatrix}$$
  - $A_{n\times n}$
    - $P$ invertible
    - $D$ diagonal
    - powers $A^k=PD^kP^{-1}$
- Orthodiagonalisation $A=QDQ^{-1}$<br>
  Same as above, but $\vec{v_1},\ldots,\vec{v_n}$ has to be normalized $\to \vec{w_1},\ldots,\vec{w_n}$
  $$P=[\vec{w_1},\ldots,\vec{w_n}] \quad D=\begin{pmatrix} \lambda_1&0&0 \newline 0&\lambda_2&0 \newline 0&0&\lambda_3 \end{pmatrix}$$
  - $A_{n\times n}$ and symmetric
    - $Q$ orthogonal ($\iff Q^TQ=I \iff$ columns forms an orthognal basis of $\mathbb{R}^n$)
    - $D$ diagonal
    - quadratic forms