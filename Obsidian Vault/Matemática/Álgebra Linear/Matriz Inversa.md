# Matriz Inversa

## Conceito
A inversa de $A$ é a matriz $A^{-1}$ que "desfaz" o que $A$ faz:

$$
AA^{-1}=A^{-1}A=I
$$

Só existe para matrizes **quadradas** com $\det A\ne0$ (as chamadas **invertíveis** ou não singulares). Se existe, é única.

## Intuição
Se $A$ é uma transformação (girar, esticar, cisalhar), $A^{-1}$ é a transformação que volta ao ponto de partida. Se $A$ colapsa o espaço ($\det A=0$), informação foi perdida e não há como desfazer.

## Fórmula para $2\times2$
$$
\begin{pmatrix}a&b\\c&d\end{pmatrix}^{-1}=\frac1{ad-bc}\begin{pmatrix}d&-b\\-c&a\end{pmatrix}
$$

**Exemplo.** $A=\begin{pmatrix}2&1\\5&3\end{pmatrix}$, $\det A=1$:
$$A^{-1}=\begin{pmatrix}3&-1\\-5&2\end{pmatrix}$$
Conferindo: $AA^{-1}=\begin{pmatrix}2\cdot3+1\cdot(-5)&2\cdot(-1)+1\cdot2\\5\cdot3+3\cdot(-5)&5\cdot(-1)+3\cdot2\end{pmatrix}=I$ ✓

## Método geral: Gauss–Jordan
Escreva $[A\,|\,I]$ e use operações elementares até obter $[I\,|\,A^{-1}]$. Se no meio do caminho aparecer uma linha de zeros no lado esquerdo, $A$ não é invertível.

$$
\left(\begin{array}{cc|cc}2&1&1&0\\5&3&0&1\end{array}\right)
\to
\left(\begin{array}{cc|cc}1&\tfrac12&\tfrac12&0\\0&\tfrac12&-\tfrac52&1\end{array}\right)
\to
\left(\begin{array}{cc|cc}1&0&3&-1\\0&1&-5&2\end{array}\right)
$$

(Passos: $L_1\leftarrow L_1/2$; $L_2\leftarrow L_2-5L_1$; $L_2\leftarrow 2L_2$; $L_1\leftarrow L_1-\tfrac12L_2$.)

## Fórmula com a adjunta (teórica)
$$A^{-1}=\frac1{\det A}\operatorname{adj}(A)$$
onde $\operatorname{adj}(A)$ é a transposta da matriz de cofatores. Boa para entender, ruim para calcular matrizes grandes.

## Propriedades
- $(A^{-1})^{-1}=A$
- $(AB)^{-1}=B^{-1}A^{-1}$ — ordem **invertida** (como se tirasse meias e sapatos: o último a colocar é o primeiro a tirar)
- $(A^T)^{-1}=(A^{-1})^T$
- $\det(A^{-1})=1/\det A$

## Para que serve
Resolver $A\vec x=\vec b$ dá $\vec x=A^{-1}\vec b$. **Mas na prática não se calcula a inversa** para resolver sistemas: eliminação/LU é mais rápida e numericamente mais estável. A inversa é mais útil como conceito e para fórmulas teóricas.

## Erros comuns
- Tentar inverter matriz não quadrada ou com $\det=0$.
- Escrever $(AB)^{-1}=A^{-1}B^{-1}$.
- Confundir $A^{-1}$ com $1/A$ (não existe divisão de matrizes).
- Trocar sinal errado na fórmula $2\times2$ (troca $a\leftrightarrow d$ e **muda o sinal** de $b$ e $c$).

## Conexões
[[Determinantes]] · [[Sistemas Lineares]] · [[Matrizes]] · [[Transformações Lineares]] · [[Álgebra Linear - Índice]]
