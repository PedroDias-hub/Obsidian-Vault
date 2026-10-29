# Diagonalização

## Conceito
Diagonalizar é escolher uma **base de autovetores**, na qual a transformação vira simplesmente "esticar cada eixo por um fator". Em termos de matriz: trocar a base transforma $A$ em uma matriz diagonal, muito mais fácil de manipular.

## Definição
$A$ ($n\times n$) é **diagonalizável** se existem $P$ invertível e $D$ diagonal tais que
$$A=PDP^{-1}$$
- as **colunas de $P$** são autovetores de $A$;
- os elementos da diagonal de $D$ são os **autovalores correspondentes**, na mesma ordem.

**Condição:** $A$ é diagonalizável $\iff$ tem $n$ autovetores LI. Basta que os $n$ autovalores sejam distintos, mas não é necessário.

## Exemplo
Continuando [[Autovalores e Autovetores]], com $A=\begin{pmatrix}4&1\\2&3\end{pmatrix}$:
$$P=\begin{pmatrix}1&1\\1&-2\end{pmatrix},\quad D=\begin{pmatrix}5&0\\0&2\end{pmatrix},\quad P^{-1}=\begin{pmatrix}\tfrac23&\tfrac13\\\tfrac13&-\tfrac13\end{pmatrix}$$
e vale $A=PDP^{-1}$.

## Por que isso vale ouro: potências
$$A^k=PD^kP^{-1}$$
porque os $P^{-1}P$ do meio se cancelam. E $D^k$ é só elevar cada elemento da diagonal.

**Exemplo.** $D^5=\operatorname{diag}(3125,\,32)$, então
$$A^5=P\begin{pmatrix}3125&0\\0&32\end{pmatrix}P^{-1}=\begin{pmatrix}2094&1031\\2062&1063\end{pmatrix}$$
Sem diagonalizar, seriam quatro multiplicações de matrizes.

## Quando **não** dá
$A=\begin{pmatrix}1&1\\0&1\end{pmatrix}$ tem $\lambda=1$ com multiplicidade algébrica 2, mas o autoespaço tem dimensão 1 (só o autovetor $(1,0)$). Faltam autovetores, logo **não é diagonalizável**.

## Teorema espectral (matrizes simétricas)
Toda matriz **simétrica real** é diagonalizável com autovetores ortogonais:
$$A=Q\Lambda Q^T,\qquad Q^TQ=I$$
É a base de PCA e de muitos métodos numéricos. Ver [[Produto Interno e Ortogonalidade]].

## Aplicação: Fibonacci em tempo logarítmico
$$\begin{pmatrix}1&1\\1&0\end{pmatrix}^n=\begin{pmatrix}F_{n+1}&F_n\\F_n&F_{n-1}\end{pmatrix}$$
Por exemplo, a potência 6 dá $\begin{pmatrix}13&8\\8&5\end{pmatrix}$, com $F_6=8$. Os autovalores são $\frac{1\pm\sqrt5}2$ (o primeiro é a razão áurea) — por isso $F_n$ cresce como potências dela. Elevar uma matriz a $n$ por exponenciação rápida custa $O(\log n)$ multiplicações.

Outra aplicação: **cadeias de Markov** (o comportamento de longo prazo é determinado pelo autovalor dominante).

## Erros comuns
- Colocar autovetores em $P$ numa ordem e autovalores em $D$ em outra.
- Esquecer de checar se há $n$ autovetores LI.
- Trocar $PDP^{-1}$ por $P^{-1}DP$ (a ordem importa).

## Conexões
[[Autovalores e Autovetores]] · [[Matriz Inversa]] · [[Independência Linear e Base]] · [[Álgebra Linear na Computação]] · [[Álgebra Linear - Índice]]
