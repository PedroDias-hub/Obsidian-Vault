# Determinantes

## Conceito
O determinante associa um **número** a cada matriz **quadrada**. Esse número responde: *esta transformação preserva ou colapsa o espaço?* — e por quanto ela escala áreas/volumes.

## Intuição geométrica
- Em $2\times2$: $|\det A|$ é a **área do paralelogramo** formado pelas colunas de $A$.
- Em $3\times3$: $|\det A|$ é o **volume do paralelepípedo** formado pelas colunas.
- O **sinal** indica orientação (se negativo, a transformação "espelha").
- $\det A=0$: as colunas estão no mesmo plano/reta — o espaço **colapsa** e a informação se perde (não há volta).

## Cálculo
**$2\times2$:**
$$\det\begin{pmatrix}a&b\\c&d\end{pmatrix}=ad-bc$$

**$3\times3$ (regra de Sarrus — só vale para 3×3):** soma dos produtos das três diagonais "para baixo" menos os das três diagonais "para cima".

**Geral — expansão de Laplace (cofatores)**, pela linha $i$:
$$\det A=\sum_{j}a_{ij}\,C_{ij},\qquad C_{ij}=(-1)^{i+j}M_{ij}$$
onde $M_{ij}$ é o determinante da matriz sem a linha $i$ e a coluna $j$. Escolha a linha ou coluna com mais zeros.

**Exemplo.**
$$A=\begin{pmatrix}2&1&3\\0&-1&4\\1&0&2\end{pmatrix}$$
Pela primeira linha:
$$\det A=2\,(-1\cdot2-4\cdot0)-1\,(0\cdot2-4\cdot1)+3\,(0\cdot0-(-1)\cdot1)=-4+4+3=3$$

## Propriedades
- $\det(AB)=\det A\cdot\det B$
- $\det(A^T)=\det A$
- Trocar duas linhas **muda o sinal**.
- Multiplicar uma linha por $k$ multiplica o determinante por $k$.
- **Somar a uma linha um múltiplo de outra não altera** o determinante.
- Linha (ou coluna) nula, ou duas linhas proporcionais → $\det=0$.
- Matriz triangular: o determinante é o **produto da diagonal**.
- $\det(kA)=k^n\det A$ (para $A$ de ordem $n$).
- $\det(A^{-1})=\dfrac1{\det A}$

Isso dá um jeito eficiente de calcular: escalone usando só a operação que não altera o determinante, e multiplique a diagonal.

## O teorema que amarra tudo
Para $A$ quadrada, estas afirmações são **equivalentes**:

$\det A\ne0$ ⟺ $A$ é invertível ⟺ $A\vec x=\vec b$ tem solução única ⟺ as colunas são LI ⟺ posto $=n$.

Ver [[Matriz Inversa]], [[Sistemas Lineares]], [[Independência Linear e Base]].

## Regra de Cramer
Se $\det A\ne0$, a solução de $A\vec x=\vec b$ é $x_i=\dfrac{\det A_i}{\det A}$, onde $A_i$ é $A$ com a coluna $i$ trocada por $\vec b$.

**Exemplo.** $\begin{cases}2x+y=5\\x-y=1\end{cases}$: $\det A=-3$, $\det A_x=\begin{vmatrix}5&1\\1&-1\end{vmatrix}=-6$, $\det A_y=\begin{vmatrix}2&5\\1&1\end{vmatrix}=-3$. Logo $x=2$, $y=1$.

É elegante, mas **ineficiente** para sistemas grandes; na prática usa-se eliminação.

## Aplicações rápidas
- Testar se 3 pontos são colineares (determinante da matriz de coordenadas = 0).
- Área de triângulo: $\tfrac12|\det|$.
- Mudança de variáveis em integrais ([[Integrais Duplas]]): o **Jacobiano** é um determinante.
- Polinômio característico em [[Autovalores e Autovetores]].

## Erros comuns
- Usar Sarrus em matriz $4\times4$ (não funciona).
- Achar que $\det(A+B)=\det A+\det B$ (falso).
- Esquecer o fator $k^n$ em $\det(kA)$.
- Errar o sinal $(-1)^{i+j}$ nos cofatores.

## Conexões
[[Matrizes]] · [[Vetores no Espaço Euclidiano]] (produto misto) · [[Álgebra Linear - Índice]]
