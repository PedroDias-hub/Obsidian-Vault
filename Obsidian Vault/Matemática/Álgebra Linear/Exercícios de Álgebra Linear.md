# Exercícios de Álgebra Linear

Tente cada um **sem olhar** a resposta (callouts recolhidos: clique para abrir). Quando errar, siga o modelo de [[Exercícios/README|Exercícios]]: registre onde errou e qual conceito faltou.

## Bloco 1 — Vetores
**1.** Calcule $\|(3,4)\|$.
> [!success]- Resposta
> $\sqrt{9+16}=5$

**2.** Calcule $(1,2,3)\cdot(4,-5,6)$.
> [!success]- Resposta
> $4-10+18=12$

**3.** Qual o ângulo entre $(1,0)$ e $(1,1)$?
> [!success]- Resposta
> $\cos\theta=\dfrac{1}{1\cdot\sqrt2}\Rightarrow\theta=45^\circ$

**4.** Calcule $(1,2,3)\times(4,5,6)$ e a área do paralelogramo que eles formam.
> [!success]- Resposta
> $(-3,6,-3)$; área $=\sqrt{9+36+9}=\sqrt{54}=3\sqrt6$.

**5.** Projete $(2,3)$ sobre $(1,1)$.
> [!success]- Resposta
> $\dfrac{2+3}{2}(1,1)=\left(\tfrac52,\tfrac52\right)$

## Bloco 2 — Matrizes
**1.** Para $A=\begin{pmatrix}1&2\\3&4\end{pmatrix}$ e $B=\begin{pmatrix}0&1\\1&0\end{pmatrix}$, calcule $AB$ e $BA$. São iguais?
> [!success]- Resposta
> $AB=\begin{pmatrix}2&1\\4&3\end{pmatrix}$, $BA=\begin{pmatrix}3&4\\1&2\end{pmatrix}$. Não são iguais.

**2.** Calcule $\begin{pmatrix}1&0&2\\-1&3&1\end{pmatrix}\begin{pmatrix}3&1\\2&1\\1&0\end{pmatrix}$.
> [!success]- Resposta
> $\begin{pmatrix}5&1\\4&2\end{pmatrix}$

**3.** Se $A$ é $4\times3$ e $B$ é $3\times5$, qual o tamanho de $AB$? E $BA$ existe?
> [!success]- Resposta
> $AB$ é $4\times5$. $BA$ não existe (5 colunas de $B$ $\ne$ 4 linhas de $A$).

**4.** Transponha $\begin{pmatrix}1&2&3\\4&5&6\end{pmatrix}$.
> [!success]- Resposta
> $\begin{pmatrix}1&4\\2&5\\3&6\end{pmatrix}$

**5.** Verifique $(AB)^T=B^TA^T$ com as matrizes do exercício 1.
> [!success]- Resposta
> $(AB)^T=\begin{pmatrix}2&4\\1&3\end{pmatrix}$ e $B^TA^T=\begin{pmatrix}0&1\\1&0\end{pmatrix}\begin{pmatrix}1&3\\2&4\end{pmatrix}=\begin{pmatrix}2&4\\1&3\end{pmatrix}$ ✓

## Bloco 3 — Sistemas lineares
**1.** Resolva $\begin{cases}x+y=5\\x-y=1\end{cases}$.
> [!success]- Resposta
> $x=3,\ y=2$

**2.** Resolva por escalonamento: $\begin{cases}x+y+z=6\\2x-y+z=3\\x+2y-z=2\end{cases}$
> [!success]- Resposta
> $(1,2,3)$. Detalhes em [[Sistemas Lineares]].

**3.** Classifique: $\begin{cases}x+y=2\\2x+2y=5\end{cases}$
> [!success]- Resposta
> Impossível (SI): a segunda equação dividida por 2 dá $x+y=2{,}5$, contradizendo a primeira.

**4.** Resolva e classifique: $\begin{cases}x+y+z=3\\x-y+z=1\end{cases}$
> [!success]- Resposta
> SPI. $y=1$, $x=2-t$, $z=t$: solução $(2-t,\,1,\,t)$, $t\in\mathbb R$.

**5.** Para qual valor de $k$ o sistema $\begin{cases}x+y=1\\2x+2y=k\end{cases}$ é possível?
> [!success]- Resposta
> $k=2$ (SPI, infinitas soluções). Para $k\ne2$ é impossível.

## Bloco 4 — Determinantes e inversa
**1.** Calcule $\det\begin{pmatrix}3&1\\2&4\end{pmatrix}$.
> [!success]- Resposta
> $12-2=10$

**2.** Calcule $\det\begin{pmatrix}2&1&3\\0&-1&4\\1&0&2\end{pmatrix}$.
> [!success]- Resposta
> $3$

**3.** Calcule $\det\begin{pmatrix}1&2&3\\4&5&6\\7&8&9\end{pmatrix}$ e explique o resultado.
> [!success]- Resposta
> $0$. A terceira linha é $2L_2-L_1$ (linhas LD), então a matriz não é invertível e o posto é 2.

**4.** Encontre a inversa de $\begin{pmatrix}2&1\\5&3\end{pmatrix}$.
> [!success]- Resposta
> $\begin{pmatrix}3&-1\\-5&2\end{pmatrix}$ (o determinante é 1).

**5.** Para quais $k$ a matriz $\begin{pmatrix}k&2\\3&k+1\end{pmatrix}$ **não** é invertível?
> [!success]- Resposta
> $\det=k^2+k-6=(k+3)(k-2)=0\Rightarrow k=-3$ ou $k=2$.

## Bloco 5 — Espaços e bases
**1.** $W=\{(x,y,z):x+y+z=0\}$ é subespaço de $\mathbb R^3$? Qual sua dimensão?
> [!success]- Resposta
> Sim (plano pela origem). Dimensão 2; uma base é $\{(1,-1,0),(0,1,-1)\}$.

**2.** $W=\{(x,y):y=x+1\}$ é subespaço de $\mathbb R^2$?
> [!success]- Resposta
> Não: $(0,0)\notin W$ (é uma reta que não passa pela origem).

**3.** $(1,0,1),(0,1,1),(1,1,0)$ são LI ou LD?
> [!success]- Resposta
> LI: o determinante da matriz formada por eles é $-2\ne0$.

**4.** Ache as coordenadas de $v=(5,1)$ na base $B=\{(1,1),(1,-1)\}$.
> [!success]- Resposta
> $a+b=5$ e $a-b=1\Rightarrow a=3,\ b=2$. Logo $[v]_B=(3,2)$.

**5.** Qual a dimensão de $P_2$ (polinômios de grau $\le2$)? Dê uma base.
> [!success]- Resposta
> Dimensão 3; base $\{1,\,x,\,x^2\}$.

## Bloco 6 — Transformações lineares
**1.** Dê a matriz de $T(x,y)=(2x+y,\,x-y)$ e calcule $T(1,2)$.
> [!success]- Resposta
> $A=\begin{pmatrix}2&1\\1&-1\end{pmatrix}$; $T(1,2)=(4,-1)$.

**2.** Aplique a rotação de $90^\circ$ anti-horária ao vetor $(2,1)$.
> [!success]- Resposta
> $\begin{pmatrix}0&-1\\1&0\end{pmatrix}\begin{pmatrix}2\\1\end{pmatrix}=(-1,2)$

**3.** Para $T(x,y,z)=(x+y,\,y+z)$, ache o núcleo e a dimensão da imagem.
> [!success]- Resposta
> $N(T)=\operatorname{span}\{(1,-1,1)\}$; $\dim\operatorname{Im}(T)=2$ (confere: $1+2=3$).

**4.** $T(x,y)=(x+1,\,y)$ é linear?
> [!success]- Resposta
> Não: $T(0,0)=(1,0)\ne(0,0)$.

**5.** Qual a matriz de "girar $90^\circ$ e depois refletir no eixo $x$"?
> [!success]- Resposta
> $\begin{pmatrix}1&0\\0&-1\end{pmatrix}\begin{pmatrix}0&-1\\1&0\end{pmatrix}=\begin{pmatrix}0&-1\\-1&0\end{pmatrix}$

## Bloco 7 — Autovalores e diagonalização
**1.** Ache os autovalores e autovetores de $\begin{pmatrix}2&0\\0&3\end{pmatrix}$.
> [!success]- Resposta
> $\lambda=2$ com $(1,0)$ e $\lambda=3$ com $(0,1)$ (em matriz diagonal, os autovalores são os elementos da diagonal).

**2.** Ache os autovetores de $\begin{pmatrix}4&1\\2&3\end{pmatrix}$ (já sabendo que $\lambda=5$ e $\lambda=2$).
> [!success]- Resposta
> $\lambda=5$: $(1,1)$; $\lambda=2$: $(1,-2)$.

**3.** Ache os autovalores e autovetores de $\begin{pmatrix}1&2\\2&1\end{pmatrix}$.
> [!success]- Resposta
> $(1-\lambda)^2-4=0\Rightarrow\lambda=3$ ou $\lambda=-1$. Autovetores: $(1,1)$ para $3$ e $(1,-1)$ para $-1$ (ortogonais, como previsto para matriz simétrica).

**4.** Mostre que $\begin{pmatrix}1&1\\0&1\end{pmatrix}$ não é diagonalizável.
> [!success]- Resposta
> O único autovalor é $1$ (multiplicidade algébrica 2), mas $(A-I)\vec v=\vec0$ dá só $v_2=0$: autoespaço de dimensão 1. Faltam autovetores LI.

**5.** Calcule $A^5$ para $A=\begin{pmatrix}4&1\\2&3\end{pmatrix}$ usando $A=PDP^{-1}$.
> [!success]- Resposta
> $A^5=P\,\operatorname{diag}(3125,32)\,P^{-1}=\begin{pmatrix}2094&1031\\2062&1063\end{pmatrix}$

## Bloco 8 — Ortogonalidade e mínimos quadrados
**1.** Verifique que $(1,2,2)\perp(2,1,-2)$.
> [!success]- Resposta
> $2+2-4=0$ ✓

**2.** Aplique Gram–Schmidt a $(1,1,0)$ e $(1,0,1)$.
> [!success]- Resposta
> $u_1=(1,1,0)$ e $u_2=\left(\tfrac12,-\tfrac12,1\right)$.

**3.** $Q=\begin{pmatrix}0&-1\\1&0\end{pmatrix}$ é ortogonal? Qual seu determinante?
> [!success]- Resposta
> Sim: $Q^TQ=I$. $\det Q=1$ (é uma rotação).

**4.** Projete $(1,2,3)$ sobre a reta gerada por $(1,1,1)$.
> [!success]- Resposta
> $\dfrac{6}{3}(1,1,1)=(2,2,2)$

**5.** Ajuste uma reta $y=c+dt$ aos pontos $(0,1),(1,2),(2,2)$ por mínimos quadrados.
> [!success]- Resposta
> $y=\tfrac76+\tfrac12t$ (via $A^TA\hat x=A^T\vec b$).

## Para ir além
Reproduza em NumPy cada resposta numérica (veja as receitas em [[Álgebra Linear na Computação]]). Se a conta à mão e o computador discordarem, o erro quase sempre está na mão — e achar onde é o melhor treino.

## Conexões
[[Álgebra Linear - Índice]] · [[Álgebra Linear - tabela]]
