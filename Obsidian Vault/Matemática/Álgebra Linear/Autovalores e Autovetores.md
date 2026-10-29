# Autovalores e Autovetores

## Conceito
Quando uma matriz $A$ transforma vetores, quase todos mudam de **direção**. Os **autovetores** são as direções especiais que $A$ só **estica, encolhe ou inverte** — sem girar. O fator de esticamento é o **autovalor**.

## Definição
$\lambda$ é autovalor de $A$ e $\vec v\ne\vec 0$ é um autovetor associado se
$$A\vec v=\lambda\vec v$$

(O vetor nulo não conta, senão qualquer $\lambda$ serviria.)

## Como calcular
$A\vec v=\lambda\vec v\iff(A-\lambda I)\vec v=\vec 0$. Há solução não nula só se $A-\lambda I$ não é invertível:
$$\det(A-\lambda I)=0$$
Essa é a **equação característica** (o lado esquerdo é o **polinômio característico**). Passos:
1. Resolva $\det(A-\lambda I)=0$ para achar os autovalores.
2. Para cada $\lambda$, resolva $(A-\lambda I)\vec v=\vec 0$ ([[Sistemas Lineares]]) para achar os autovetores. O conjunto de soluções é o **autoespaço** de $\lambda$.

### Exemplo completo
$$A=\begin{pmatrix}4&1\\2&3\end{pmatrix}$$
$$\det(A-\lambda I)=(4-\lambda)(3-\lambda)-2=\lambda^2-7\lambda+10=(\lambda-5)(\lambda-2)$$
Autovalores: $\lambda=5$ e $\lambda=2$.

- $\lambda=5$: $\begin{pmatrix}-1&1\\2&-2\end{pmatrix}\vec v=\vec 0\Rightarrow v_1=v_2$, autovetor $(1,1)$. Confere: $A(1,1)=(5,5)=5(1,1)$ ✓
- $\lambda=2$: $\begin{pmatrix}2&1\\2&1\end{pmatrix}\vec v=\vec 0\Rightarrow 2v_1+v_2=0$, autovetor $(1,-2)$. Confere: $A(1,-2)=(2,-4)=2(1,-2)$ ✓

## Propriedades úteis
- **Soma dos autovalores = traço** ($5+2=7=4+3$).
- **Produto dos autovalores = determinante** ($5\cdot2=10=4\cdot3-1\cdot2$).
- Em matriz **triangular**, os autovalores são os elementos da diagonal.
- $0$ é autovalor $\iff\det A=0\iff A$ não é invertível.
- Autovetores de autovalores **distintos** são LI.
- Qualquer múltiplo não nulo de um autovetor ainda é autovetor.
- Matriz **simétrica real**: autovalores reais e autovetores ortogonais.

## Autovalores complexos
A rotação de $90^\circ$, $\begin{pmatrix}0&-1\\1&0\end{pmatrix}$, dá $\lambda^2+1=0$, isto é, $\lambda=\pm i$. Faz sentido: rotação não mantém nenhuma direção real fixa.

## Multiplicidades
- **Algébrica**: quantas vezes $\lambda$ é raiz do polinômio característico.
- **Geométrica**: dimensão do autoespaço de $\lambda$ (sempre $\le$ a algébrica).

Quando a geométrica é menor que a algébrica, a matriz não é diagonalizável ([[Diagonalização]]).

## Aplicações
- **PageRank**: a importância das páginas é o autovetor dominante da matriz de links.
- **PCA**: componentes principais = autovetores da matriz de covariância.
- Vibrações, estabilidade de sistemas dinâmicos, Fibonacci (ver [[Diagonalização]]).

## Erros comuns
- Aceitar $\vec v=\vec 0$ como autovetor.
- Parar no autovalor e esquecer de calcular os autovetores.
- Errar o sinal em $A-\lambda I$ (subtrai-se $\lambda$ **só da diagonal**).

## Conexões
[[Determinantes]] · [[Sistemas Lineares]] · [[Transformações Lineares]] · [[Diagonalização]] · [[Álgebra Linear na Computação]] · [[Álgebra Linear - Índice]]
