# Produto Interno e Ortogonalidade

## Conceito
O produto interno generaliza o produto escalar: é a ferramenta que dá a um espaço vetorial as noções de **comprimento, ângulo e perpendicularidade**. Em $\mathbb R^n$ usa-se $\langle u,v\rangle=u\cdot v$ (ver [[Vetores no Espaço Euclidiano]]).

## Definição
Um produto interno $\langle\cdot,\cdot\rangle$ satisfaz:
1. $\langle u,v\rangle=\langle v,u\rangle$ (simetria)
2. $\langle\alpha u+\beta w,v\rangle=\alpha\langle u,v\rangle+\beta\langle w,v\rangle$ (linearidade)
3. $\langle v,v\rangle\ge0$, e $=0$ só se $v=\vec0$ (positividade)

Dele saem: norma $\|v\|=\sqrt{\langle v,v\rangle}$, ângulo, e a desigualdade de Cauchy–Schwarz. Em espaços de funções, por exemplo, $\langle f,g\rangle=\int_a^b f\,g\,dx$ — a base das séries de Fourier.

## Ortogonalidade
- $u\perp v\iff\langle u,v\rangle=0$.
- Conjunto **ortogonal**: vetores dois a dois perpendiculares (e não nulos) $\Rightarrow$ são **LI**.
- Conjunto **ortonormal**: ortogonal e com todos de norma 1.

**Por que bases ortonormais são ótimas:** as coordenadas saem direto do produto interno, sem resolver sistema:
$$v=\sum_i\langle v,q_i\rangle\,q_i$$

## Projeção ortogonal em um subespaço
Se $q_1,\dots,q_k$ é uma base ortonormal de $W$, a projeção de $v$ em $W$ é
$$\operatorname{proj}_Wv=\sum_{i=1}^k\langle v,q_i\rangle\,q_i$$
É o ponto de $W$ **mais próximo** de $v$; o resto $v-\operatorname{proj}_Wv$ é perpendicular a $W$.

## Processo de Gram–Schmidt
Transforma uma base qualquer $v_1,\dots,v_k$ em uma base ortogonal $u_1,\dots,u_k$:
$$u_1=v_1,\qquad u_j=v_j-\sum_{i<j}\frac{\langle v_j,u_i\rangle}{\langle u_i,u_i\rangle}\,u_i$$
(tira de cada vetor a "sombra" nos anteriores). Depois, divide-se cada $u_j$ pela norma para ficar ortonormal.

**Exemplo.** $v_1=(1,1,0)$, $v_2=(1,0,1)$.
- $u_1=(1,1,0)$.
- $u_2=v_2-\dfrac{v_2\cdot u_1}{u_1\cdot u_1}u_1=(1,0,1)-\dfrac12(1,1,0)=\left(\tfrac12,-\tfrac12,1\right)$.
- Confere: $u_1\cdot u_2=\tfrac12-\tfrac12+0=0$ ✓.
- Normas: $\|u_1\|=\sqrt2$, $\|u_2\|=\sqrt{3/2}=\tfrac{\sqrt6}2$.

## Matrizes ortogonais
$Q$ é **ortogonal** se $Q^TQ=I$, isto é, $Q^{-1}=Q^T$ (inverter é só transpor — barato!). Suas colunas formam uma base ortonormal. Propriedades:
- preserva comprimentos e ângulos: $\|Q\vec x\|=\|\vec x\|$;
- $\det Q=\pm1$;
- rotações e reflexões são matrizes ortogonais. Exemplo: $\begin{pmatrix}0&-1\\1&0\end{pmatrix}$.

## Mínimos quadrados
Quando $A\vec x=\vec b$ **não tem solução** (mais equações do que incógnitas, dados com ruído), busca-se $\hat x$ que minimize $\|A\vec x-\vec b\|$. Isso equivale a projetar $\vec b$ no espaço coluna de $A$, e leva às **equações normais**:
$$A^TA\,\hat x=A^T\vec b$$

**Exemplo (regressão linear).** Ajustar $y=c+dt$ aos pontos $(0,1),(1,2),(2,2)$:
$$A=\begin{pmatrix}1&0\\1&1\\1&2\end{pmatrix},\ \vec b=\begin{pmatrix}1\\2\\2\end{pmatrix}\ \Rightarrow\ A^TA=\begin{pmatrix}3&3\\3&5\end{pmatrix},\ A^T\vec b=\begin{pmatrix}5\\6\end{pmatrix}$$
Resolvendo: $d=\tfrac12$, $c=\tfrac76$. A reta é $y=\tfrac76+\tfrac12t$. Os resíduos $(-\tfrac16,\tfrac13,-\tfrac16)$ somam zero e são ortogonais à coluna de uns — exatamente o que a teoria prevê.

## Erros comuns
- Aplicar Gram–Schmidt e esquecer de normalizar quando se quer base **ortonormal**.
- Usar a fórmula de projeção com base ortogonal **não** normalizada sem dividir por $\langle q,q\rangle$.
- Confundir matriz **ortogonal** (colunas ortonormais) com matriz de colunas apenas ortogonais.

## Conexões
[[Vetores no Espaço Euclidiano]] · [[Independência Linear e Base]] · [[Diagonalização]] · [[Álgebra Linear na Computação]] · [[Álgebra Linear - Índice]]
