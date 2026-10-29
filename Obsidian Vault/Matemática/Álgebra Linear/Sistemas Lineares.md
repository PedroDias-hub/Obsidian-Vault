# Sistemas Lineares

## Conceito
Um sistema linear é um conjunto de equações em que as incógnitas aparecem só com expoente 1 e sem produtos entre si:

$$
\begin{cases}x+y+z=6\\2x-y+z=3\\x+2y-z=2\end{cases}
$$

Em forma matricial: $A\vec x=\vec b$, onde $A$ é a **matriz dos coeficientes**. A **matriz aumentada** é $[A\,|\,\vec b]$.

## Intuição geométrica
- Em $\mathbb R^2$: cada equação é uma reta; a solução é onde elas se cruzam (um ponto, nenhum se paralelas, infinitos se coincidentes).
- Em $\mathbb R^3$: cada equação é um plano; a solução é a interseção dos planos.

## Classificação
| Tipo | Soluções | Sigla |
|---|---|---|
| Possível e determinado | exatamente uma | SPD |
| Possível e indeterminado | infinitas (há variáveis livres) | SPI |
| Impossível | nenhuma | SI |

## Operações elementares (não mudam a solução)
1. Trocar duas linhas.
2. Multiplicar uma linha por $k\ne0$.
3. Somar a uma linha um múltiplo de outra.

## Escalonamento (eliminação de Gauss)
Use as operações para zerar tudo abaixo de cada **pivô**, chegando a uma forma "em escada". Depois resolva de baixo para cima (*substituição retroativa*). **Gauss–Jordan** continua até zerar também acima dos pivôs (forma escalonada reduzida).

### Exemplo resolvido (SPD)
$$
\left(\begin{array}{ccc|c}1&1&1&6\\2&-1&1&3\\1&2&-1&2\end{array}\right)
$$

- $L_2\leftarrow L_2-2L_1$ e $L_3\leftarrow L_3-L_1$:
$$\left(\begin{array}{ccc|c}1&1&1&6\\0&-3&-1&-9\\0&1&-2&-4\end{array}\right)$$
- Troca $L_2\leftrightarrow L_3$, depois $L_3\leftarrow L_3+3L_2$:
$$\left(\begin{array}{ccc|c}1&1&1&6\\0&1&-2&-4\\0&0&-7&-21\end{array}\right)$$
- De baixo para cima: $z=3$; $y-2z=-4\Rightarrow y=2$; $x+y+z=6\Rightarrow x=1$.

Solução: $(x,y,z)=(1,2,3)$. Confira substituindo nas três equações originais.

### Exemplo SPI
$$\begin{cases}x+y+z=3\\x-y+z=1\end{cases}$$
Somando/subtraindo: $y=1$ e $x+z=2$. A variável $z$ fica **livre**: $z=t$, $x=2-t$. Solução: $(2-t,\,1,\,t)$ com $t\in\mathbb R$ — uma reta de soluções.

### Exemplo SI
$$\begin{cases}x+y=1\\x+y=2\end{cases}$$
Escalonando aparece a linha $(0\;0\,|\,1)$, isto é, $0=1$. Absurdo: sem solução.

## Posto (rank) e o teorema de Rouché–Capelli
O **posto** de $A$ é o nº de pivôs após escalonar. Para um sistema com $n$ incógnitas:

- $\operatorname{posto}(A)=\operatorname{posto}([A|b])=n$ → SPD
- $\operatorname{posto}(A)=\operatorname{posto}([A|b])<n$ → SPI (com $n-\text{posto}$ variáveis livres)
- $\operatorname{posto}(A)<\operatorname{posto}([A|b])$ → SI

## Sistema homogêneo
$A\vec x=\vec 0$ **sempre** tem a solução trivial $\vec x=\vec 0$. Tem soluções não triviais exatamente quando há variável livre (posto $<n$). O conjunto das soluções é o **núcleo** de $A$ (ver [[Transformações Lineares]]).

## Erros comuns
- Multiplicar uma linha por 0 (a operação exige $k\ne0$).
- Trocar sinal ao somar linhas e não propagar o erro para a coluna $b$.
- Ver uma linha de zeros e concluir "sem solução" (só é SI se a linha for $0\,0\,0\,|\,c$ com $c\neq0$).

## Na computação
`numpy.linalg.solve(A, b)` resolve $A\vec x=\vec b$ por uma variante de Gauss (decomposição LU). O custo é da ordem de $n^3$ operações. Aplicações: circuitos (leis de Kirchhoff), balanceamento químico, interpolação polinomial, equilíbrio de redes.

## Conexões
[[Equações e inequações]] · [[Matrizes]] · [[Determinantes]] (regra de Cramer) · [[Matriz Inversa]] · [[Independência Linear e Base]] · [[Álgebra Linear - Índice]]
