# Vetores no Espaço Euclidiano

## Conceito
Um vetor em $\mathbb R^n$ é uma lista ordenada de $n$ números:

$$
\vec v=(v_1,v_2,\dots,v_n)
$$

Duas leituras, e você precisa das duas:
- **Geométrica**: uma seta com direção, sentido e comprimento (em $\mathbb R^2$ e $\mathbb R^3$).
- **Computacional**: um array de $n$ números. Um pixel RGB é um vetor de $\mathbb R^3$; um usuário descrito por 200 características é um vetor de $\mathbb R^{200}$.

## Operações básicas
$$
\vec u+\vec v=(u_1+v_1,\dots,u_n+v_n)\qquad
\alpha\vec v=(\alpha v_1,\dots,\alpha v_n)
$$

Somar = "andar uma seta depois da outra". Multiplicar por escalar = esticar, encolher ou inverter o sentido.

## Norma (comprimento)
$$
\|\vec v\|=\sqrt{v_1^2+v_2^2+\cdots+v_n^2}
$$

É o teorema de Pitágoras em $n$ dimensões. Um **vetor unitário** tem norma 1; para normalizar: $\hat v=\dfrac{\vec v}{\|\vec v\|}$.

## Produto escalar
$$
\vec u\cdot\vec v=u_1v_1+\cdots+u_nv_n=\|\vec u\|\,\|\vec v\|\cos\theta
$$

O resultado é um **número**, não um vetor. Ele mede "o quanto os dois apontam para o mesmo lado":
- $\vec u\cdot\vec v>0$: ângulo agudo
- $\vec u\cdot\vec v=0$: **perpendiculares (ortogonais)**
- $\vec u\cdot\vec v<0$: ângulo obtuso

Ângulo entre vetores:
$$
\cos\theta=\frac{\vec u\cdot\vec v}{\|\vec u\|\,\|\vec v\|}
$$

**Exemplo.** $\vec u=(1,2,2)$ e $\vec v=(2,0,1)$: $\vec u\cdot\vec v=2+0+2=4$, $\|\vec u\|=3$, $\|\vec v\|=\sqrt5$. Logo $\cos\theta=\dfrac{4}{3\sqrt5}\approx0{,}596$ e $\theta\approx53{,}4^\circ$.

## Projeção ortogonal
A "sombra" de $\vec v$ sobre a direção de $\vec u$:
$$
\operatorname{proj}_{\vec u}\vec v=\frac{\vec v\cdot\vec u}{\vec u\cdot\vec u}\,\vec u
$$

**Exemplo.** Projetar $(2,3)$ sobre $(1,1)$: $\dfrac{5}{2}(1,1)=\left(\tfrac52,\tfrac52\right)$.

## Desigualdades importantes
- **Cauchy–Schwarz**: $|\vec u\cdot\vec v|\le\|\vec u\|\,\|\vec v\|$
- **Triangular**: $\|\vec u+\vec v\|\le\|\vec u\|+\|\vec v\|$

## Produto vetorial (só em $\mathbb R^3$)
$$
\vec u\times\vec v=(u_2v_3-u_3v_2,\; u_3v_1-u_1v_3,\; u_1v_2-u_2v_1)
$$

- O resultado é um **vetor perpendicular aos dois** (sentido pela regra da mão direita).
- $\|\vec u\times\vec v\|=\|\vec u\|\,\|\vec v\|\,\sin\theta$ = **área do paralelogramo** formado por $\vec u$ e $\vec v$.
- $\vec u\times\vec v=\vec 0$ quando são paralelos.
- Anticomutativo: $\vec u\times\vec v=-(\vec v\times\vec u)$.

**Exemplo.** $(1,2,3)\times(4,5,6)=(-3,6,-3)$, de norma $\sqrt{54}=3\sqrt6$ (a área do paralelogramo).

**Produto misto**: $\vec u\cdot(\vec v\times\vec w)$ dá o volume (com sinal) do paralelepípedo — é um [[Determinantes|determinante]] 3×3.

## Erros comuns
- Achar que $\|\vec u+\vec v\|=\|\vec u\|+\|\vec v\|$. Só vale se tiverem a mesma direção e sentido.
- Chamar o produto escalar de vetor. É número.
- Tentar usar produto vetorial fora de $\mathbb R^3$ (existem generalizações, mas não esta fórmula).
- Dividir por $\vec u\cdot\vec u$ errado na projeção (é $\vec u\cdot\vec u$, não $\|\vec u\|$).

## Na computação
Similaridade por cosseno (buscas, embeddings, recomendação) é exatamente a fórmula do ângulo acima. Ver [[Álgebra Linear na Computação]].

## Conexões
[[Vetores - introdução]] · [[Vetores]] (versão de Cálculo III) · [[Matrizes]] · [[Produto Interno e Ortogonalidade]] · [[Álgebra Linear - Índice]]
