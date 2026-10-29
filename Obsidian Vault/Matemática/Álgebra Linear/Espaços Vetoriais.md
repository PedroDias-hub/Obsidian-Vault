# Espaços Vetoriais

## Conceito
Um espaço vetorial é **qualquer conjunto onde faz sentido somar elementos e multiplicá-los por escalares**, desde que as operações se comportem bem. Setas, listas de números, matrizes, polinômios e funções podem ser "vetores" — o que importa é a estrutura, não o formato.

## Definição
Um conjunto $V$ com soma $+$ e multiplicação por escalar $\cdot$ (escalares em $\mathbb R$) é um **espaço vetorial** se, para todos $u,v,w\in V$ e $\alpha,\beta\in\mathbb R$:

1. $u+v=v+u$
2. $(u+v)+w=u+(v+w)$
3. existe $\vec 0$ com $v+\vec 0=v$
4. existe $-v$ com $v+(-v)=\vec 0$
5. $\alpha(u+v)=\alpha u+\alpha v$
6. $(\alpha+\beta)v=\alpha v+\beta v$
7. $(\alpha\beta)v=\alpha(\beta v)$
8. $1\cdot v=v$

Além disso, $u+v\in V$ e $\alpha v\in V$ (o conjunto é **fechado** nas duas operações).

## Exemplos
| Espaço | Elementos | Dimensão |
|---|---|---|
| $\mathbb R^n$ | listas de $n$ reais | $n$ |
| $M_{m\times n}$ | matrizes $m\times n$ | $mn$ |
| $P_n$ | polinômios de grau $\le n$ | $n+1$ |
| $C[a,b]$ | funções contínuas em $[a,b]$ | infinita |

**Contraexemplo.** $\{(x,y)\in\mathbb R^2: x=1\}$ não é espaço vetorial: não contém o vetor nulo e não é fechado na soma ($(1,0)+(1,0)=(2,0)$ sai do conjunto).

## Subespaços
$W\subseteq V$ é um **subespaço** se for ele próprio um espaço vetorial. Basta verificar três coisas:

1. $\vec 0\in W$
2. $u,v\in W\Rightarrow u+v\in W$
3. $v\in W,\ \alpha\in\mathbb R\Rightarrow \alpha v\in W$

**Exemplos de subespaços de $\mathbb R^3$:** a origem sozinha, qualquer **reta pela origem**, qualquer **plano pela origem**, o próprio $\mathbb R^3$.

**Não são subespaços:** reta ou plano que **não passa pela origem**; a união de duas retas distintas pela origem (não é fechada na soma).

**Exemplo clássico.** $W=\{(x,y,z):x+y+z=0\}$ é subespaço (plano pela origem): contém $(0,0,0)$, e a soma e o múltiplo de vetores com soma de coordenadas zero continuam com soma zero.

## Espaço gerado
O conjunto de todas as combinações lineares de $v_1,\dots,v_k$:
$$\operatorname{span}\{v_1,\dots,v_k\}=\{\alpha_1v_1+\cdots+\alpha_kv_k\}$$
É sempre um subespaço — o menor que contém esses vetores.

## Os três espaços de uma matriz $A$
- **Espaço coluna**: span das colunas de $A$ (todos os $A\vec x$ possíveis).
- **Espaço linha**: span das linhas.
- **Núcleo**: $\{\vec x:A\vec x=\vec 0\}$.

Ver [[Transformações Lineares]] para a relação entre eles.

## Erros comuns
- Esquecer de checar o vetor nulo (é o teste mais rápido para reprovar um candidato).
- Achar que "plano" é sempre subespaço — só se passar pela origem.
- Confundir subespaço com subconjunto qualquer.

## Na computação
Vetores de características, polinômios (aproximação, interpolação) e sinais/funções (séries de Fourier) são tratados com as mesmas ferramentas porque todos vivem em espaços vetoriais.

## Conexões
[[Independência Linear e Base]] · [[Transformações Lineares]] · [[Sistemas Lineares]] · [[Álgebra Linear - Índice]]
