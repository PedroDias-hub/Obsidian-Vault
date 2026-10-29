# Fórmulas — Álgebra Linear

Consulta rápida. Para entender **por que** cada coisa vale, vá à nota indicada ([[Álgebra Linear - Índice]]).

## Vetores — [[Vetores no Espaço Euclidiano]]
$$\|\vec v\|=\sqrt{v_1^2+\cdots+v_n^2}\qquad\vec u\cdot\vec v=\sum u_iv_i=\|\vec u\|\|\vec v\|\cos\theta$$
$$\operatorname{proj}_{\vec u}\vec v=\frac{\vec v\cdot\vec u}{\vec u\cdot\vec u}\vec u\qquad\|\vec u\times\vec v\|=\|\vec u\|\|\vec v\|\sin\theta$$

## Matrizes — [[Matrizes]]
$$(AB)_{ij}=\sum_ka_{ik}b_{kj}\qquad(AB)^T=B^TA^T\qquad\operatorname{tr}A=\sum a_{ii}$$
$AB\ne BA$ em geral.

## Sistemas — [[Sistemas Lineares]]
SPD: posto$(A)$ = posto$([A|b])$ = $n$ · SPI: posto$(A)$ = posto$([A|b])$ < $n$ · SI: posto$(A)$ < posto$([A|b])$

## Determinantes — [[Determinantes]]
$$\det\begin{pmatrix}a&b\\c&d\end{pmatrix}=ad-bc\qquad\det(AB)=\det A\det B\qquad\det(kA)=k^n\det A$$
$$\det A=\sum_ja_{ij}(-1)^{i+j}M_{ij}\qquad x_i=\frac{\det A_i}{\det A}\ \text{(Cramer)}$$

## Inversa — [[Matriz Inversa]]
$$\begin{pmatrix}a&b\\c&d\end{pmatrix}^{-1}=\frac1{ad-bc}\begin{pmatrix}d&-b\\-c&a\end{pmatrix}\qquad(AB)^{-1}=B^{-1}A^{-1}\qquad\det A^{-1}=\frac1{\det A}$$

## Espaços e bases — [[Independência Linear e Base]]
$$\dim\mathbb R^n=n\quad\dim M_{m\times n}=mn\quad\dim P_n=n+1\qquad\operatorname{posto}A+\dim N(A)=n$$

## Transformações — [[Transformações Lineares]]
$$R_\theta=\begin{pmatrix}\cos\theta&-\sin\theta\\\sin\theta&\cos\theta\end{pmatrix}\qquad T(x)=Ax,\ \text{colunas}=T(e_j)$$
Composição $T_2\circ T_1\leftrightarrow A_2A_1$.

## Autovalores — [[Autovalores e Autovetores]] · [[Diagonalização]]
$$A\vec v=\lambda\vec v\qquad\det(A-\lambda I)=0\qquad\sum\lambda_i=\operatorname{tr}A\qquad\prod\lambda_i=\det A$$
$$A=PDP^{-1}\qquad A^k=PD^kP^{-1}\qquad A=Q\Lambda Q^T\ \text{(simétrica)}$$

## Ortogonalidade — [[Produto Interno e Ortogonalidade]]
$$u_j=v_j-\sum_{i<j}\frac{\langle v_j,u_i\rangle}{\langle u_i,u_i\rangle}u_i\qquad Q^TQ=I\qquad A^TA\hat x=A^T\vec b$$
