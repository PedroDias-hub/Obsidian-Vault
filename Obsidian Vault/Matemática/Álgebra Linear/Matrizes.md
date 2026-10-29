# Matrizes

## Conceito
Uma matriz $m\times n$ é uma tabela com $m$ linhas e $n$ colunas. O elemento da linha $i$, coluna $j$ é $a_{ij}$.

$$
A=\begin{pmatrix}a_{11}&a_{12}&a_{13}\\a_{21}&a_{22}&a_{23}\end{pmatrix}\quad(2\times3)
$$

Dois jeitos úteis de enxergar uma matriz: uma **tabela de números** (dados) ou uma **função** que transforma vetores (ver [[Transformações Lineares]]). O segundo é o que torna a álgebra linear poderosa.

## Tipos importantes
| Tipo | Característica |
|---|---|
| Quadrada | $m=n$ |
| Identidade $I$ | 1 na diagonal, 0 fora; $AI=IA=A$ |
| Nula | todos os elementos 0 |
| Diagonal | só a diagonal principal é não nula |
| Triangular | zeros acima (ou abaixo) da diagonal |
| Simétrica | $A^T=A$ |
| Antissimétrica | $A^T=-A$ |

## Soma e multiplicação por escalar
Elemento a elemento; a soma exige **mesmo tamanho**.

## Produto de matrizes
$$
(AB)_{ij}=\sum_{k}a_{ik}\,b_{kj}
$$

Cada elemento é o **produto escalar da linha $i$ de $A$ com a coluna $j$ de $B$**.

**Condição**: nº de colunas de $A$ = nº de linhas de $B$. Se $A$ é $m\times n$ e $B$ é $n\times p$, então $AB$ é $m\times p$.

**Exemplo.**
$$
A=\begin{pmatrix}1&2\\3&4\end{pmatrix},\;
B=\begin{pmatrix}0&1\\1&0\end{pmatrix}
\;\Rightarrow\;
AB=\begin{pmatrix}2&1\\4&3\end{pmatrix},\;
BA=\begin{pmatrix}3&4\\1&2\end{pmatrix}
$$

$AB\neq BA$: **o produto de matrizes não é comutativo**. (Multiplicar por $B$ à direita troca as colunas; à esquerda troca as linhas.)

### A leitura que mais ajuda
$A\vec x$ é uma **combinação linear das colunas de $A$**, com os pesos sendo as coordenadas de $\vec x$:
$$
\begin{pmatrix}1&2\\3&4\end{pmatrix}\begin{pmatrix}5\\6\end{pmatrix}=5\begin{pmatrix}1\\3\end{pmatrix}+6\begin{pmatrix}2\\4\end{pmatrix}=\begin{pmatrix}17\\39\end{pmatrix}
$$

## Transposta
$A^T$ troca linhas por colunas: $(A^T)_{ij}=a_{ji}$.

$$
(A^T)^T=A\qquad(AB)^T=B^TA^T
$$

Note a ordem **invertida**.

## Propriedades
- $(AB)C=A(BC)$ (associativa)
- $A(B+C)=AB+AC$ (distributiva)
- $AB\ne BA$ em geral
- $AB=0$ **não** implica $A=0$ ou $B=0$

## Traço
$\operatorname{tr}(A)=a_{11}+a_{22}+\cdots+a_{nn}$ (soma da diagonal, só para quadradas). Reaparece em [[Autovalores e Autovetores]].

## Erros comuns
- Multiplicar elemento a elemento (isso é outra operação, o produto de Hadamard).
- Esquecer a condição de tamanhos.
- Assumir comutatividade ou cancelamento ($AB=AC\not\Rightarrow B=C$).
- Escrever $(AB)^T=A^TB^T$.

## Na computação
Imagens são matrizes de pixels; em NumPy, `A @ B` é o produto matricial e `A * B` é elemento a elemento. Ver [[Álgebra Linear na Computação]].

## Conexões
[[Vetores no Espaço Euclidiano]] · [[Sistemas Lineares]] · [[Determinantes]] · [[Matriz Inversa]] · [[Álgebra Linear - Índice]]
