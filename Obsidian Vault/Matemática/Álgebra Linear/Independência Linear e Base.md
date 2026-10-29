# Independência Linear e Base

## Combinação linear
Um vetor $w$ é combinação linear de $v_1,\dots,v_k$ se
$$w=\alpha_1v_1+\cdots+\alpha_kv_k$$
para alguns escalares $\alpha_i$. Perguntar "$w$ está no span de $v_1,\dots,v_k$?" é o mesmo que perguntar "o sistema $\sum\alpha_iv_i=w$ tem solução?" — ver [[Sistemas Lineares]].

## Independência linear
Os vetores $v_1,\dots,v_k$ são **linearmente independentes (LI)** se a única solução de
$$\alpha_1v_1+\cdots+\alpha_kv_k=\vec 0$$
é $\alpha_1=\cdots=\alpha_k=0$. Caso contrário são **linearmente dependentes (LD)**.

**Intuição:** LD significa que há vetor *redundante* (algum é combinação dos outros, não acrescenta direção nova). LI significa que cada vetor traz uma direção nova.

### Teste prático
Monte a matriz com os vetores como **colunas** e escalone.
- Pivô em **todas** as colunas → LI.
- Alguma coluna sem pivô → LD.
- Para $n$ vetores em $\mathbb R^n$: LI $\iff\det\ne0$ (ver [[Determinantes]]).

### Exemplos
- $(1,2),(2,4)$: LD (o segundo é o dobro do primeiro).
- $(1,2,3),(4,5,6),(7,8,9)$: LD, pois $2(4,5,6)-(1,2,3)=(7,8,9)$; o determinante é 0 e o posto é 2.
- $(1,0,1),(0,1,1),(1,1,0)$: LI, pois o determinante é $-2\ne0$.
- Qualquer conjunto contendo $\vec 0$ é LD.

## Base
Uma **base** de $V$ é um conjunto de vetores que é **LI e gera $V$**. É o "sistema de coordenadas mínimo e suficiente": nada falta, nada sobra.

Exemplo: a **base canônica** de $\mathbb R^3$ é $e_1=(1,0,0),\ e_2=(0,1,0),\ e_3=(0,0,1)$.

## Dimensão
Todas as bases de $V$ têm o **mesmo número de vetores**; esse número é $\dim V$.

| Espaço | Dimensão | Uma base |
|---|---|---|
| $\mathbb R^n$ | $n$ | $e_1,\dots,e_n$ |
| $P_2$ (grau $\le2$) | 3 | $1,\ x,\ x^2$ |
| $M_{2\times2}$ | 4 | as 4 matrizes com um único 1 |

Consequências úteis em um espaço de dimensão $n$:
- mais de $n$ vetores são sempre **LD**;
- $n$ vetores LI **formam uma base**;
- um plano pela origem em $\mathbb R^3$ tem dimensão 2; uma reta, dimensão 1.

## Coordenadas em uma base
Fixada uma base $B=\{b_1,\dots,b_n\}$, todo $v$ se escreve de forma **única** como $v=\alpha_1b_1+\cdots+\alpha_nb_n$. Os $\alpha_i$ são as coordenadas $[v]_B$.

**Exemplo.** Em $B=\{(1,1),(1,-1)\}$, o vetor $v=(3,1)$ satisfaz $a+b=3$ e $a-b=1$, logo $[v]_B=(2,1)$.

A mesma "seta" tem coordenadas diferentes em bases diferentes. Escolher uma boa base simplifica o problema — essa é a ideia por trás de [[Diagonalização]].

## Posto e dimensão do núcleo
Para uma matriz $m\times n$: $\operatorname{posto}(A)=\dim(\text{espaço coluna})$ e
$$\operatorname{posto}(A)+\dim N(A)=n$$
(teorema do posto–nulidade, visto em [[Transformações Lineares]]).

## Erros comuns
- Achar que $n$ vetores de $\mathbb R^n$ são sempre base (só se forem LI).
- Confundir "gerar" com "ser LI": a base precisa dos dois.
- Esquecer que coordenadas dependem da base escolhida.

## Conexões
[[Espaços Vetoriais]] · [[Sistemas Lineares]] · [[Transformações Lineares]] · [[Álgebra Linear - Índice]]
