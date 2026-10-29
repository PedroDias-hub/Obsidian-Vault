# Transformações Lineares

## Conceito
Uma transformação linear é uma função entre espaços vetoriais que **respeita soma e multiplicação por escalar**. Geometricamente: ela mantém retas como retas, mantém a origem fixa e mantém linhas paralelas paralelas (a grade fica "esticada/girada", mas continua uma grade).

## Definição
$T:V\to W$ é linear se, para todos $u,v\in V$ e $\alpha\in\mathbb R$:
$$T(u+v)=T(u)+T(v)\qquad T(\alpha v)=\alpha\,T(v)$$

Consequência imediata: $T(\vec 0)=\vec 0$. **Teste rápido de não linearidade:** se $T(\vec 0)\ne\vec 0$, não é linear.

## Toda transformação linear é uma matriz
Para $T:\mathbb R^n\to\mathbb R^m$ existe uma única matriz $A$ ($m\times n$) tal que $T(\vec x)=A\vec x$. As **colunas de $A$ são $T(e_1),\dots,T(e_n)$** — o que a transformação faz com cada vetor da base canônica.

**Exemplo.** $T(x,y)=(2x+y,\;x-y)$ tem $A=\begin{pmatrix}2&1\\1&-1\end{pmatrix}$ e $T(1,2)=(4,-1)$.

## Transformações clássicas em $\mathbb R^2$
| Transformação | Matriz |
|---|---|
| Escala | $\begin{pmatrix}s_x&0\\0&s_y\end{pmatrix}$ |
| Rotação de $\theta$ (anti-horária) | $\begin{pmatrix}\cos\theta&-\sin\theta\\\sin\theta&\cos\theta\end{pmatrix}$ |
| Reflexão no eixo $x$ | $\begin{pmatrix}1&0\\0&-1\end{pmatrix}$ |
| Cisalhamento horizontal | $\begin{pmatrix}1&k\\0&1\end{pmatrix}$ |
| Projeção no eixo $x$ | $\begin{pmatrix}1&0\\0&0\end{pmatrix}$ |

Exemplo: rotação de $90^\circ$ leva $(1,0)$ em $(0,1)$, pois $\begin{pmatrix}0&-1\\1&0\end{pmatrix}\begin{pmatrix}1\\0\end{pmatrix}=\begin{pmatrix}0\\1\end{pmatrix}$.

## Composição = produto de matrizes
Aplicar $T_1$ e depois $T_2$ corresponde a $A_2A_1$ (a **ordem se lê da direita para a esquerda**).

Exemplo: girar $90^\circ$ e depois refletir no eixo $x$:
$$\begin{pmatrix}1&0\\0&-1\end{pmatrix}\begin{pmatrix}0&-1\\1&0\end{pmatrix}=\begin{pmatrix}0&-1\\-1&0\end{pmatrix}$$
Conferindo com $(1,0)$: gira para $(0,1)$, reflete para $(0,-1)$, e a matriz dá $(0,-1)$ ✓.

Por isso o produto de matrizes não é comutativo: girar e depois esticar não é o mesmo que esticar e depois girar.

## Núcleo e imagem
- **Núcleo**: $N(T)=\{v:T(v)=\vec 0\}$ — o que a transformação "apaga".
- **Imagem**: $\operatorname{Im}(T)=\{T(v)\}$ — tudo o que ela consegue "alcançar" (é o espaço coluna de $A$).

**Teorema do posto–nulidade:**
$$\dim N(T)+\dim\operatorname{Im}(T)=\dim V$$

**Exemplo.** $T(x,y,z)=(x+y,\;y+z)$ com $A=\begin{pmatrix}1&1&0\\0&1&1\end{pmatrix}$.
- Núcleo: $x+y=0$ e $y+z=0\Rightarrow(x,-x,x)$, isto é, $N(T)=\operatorname{span}\{(1,-1,1)\}$, dimensão 1.
- Imagem: as colunas geram $\mathbb R^2$, dimensão 2.
- Confere: $1+2=3=\dim\mathbb R^3$.

## Injetora, sobrejetora, isomorfismo
- Injetora $\iff N(T)=\{\vec 0\}$ (nada é apagado).
- Sobrejetora $\iff\operatorname{Im}(T)=W$.
- Bijetora (**isomorfismo**) $\iff$ a matriz é quadrada e invertível ([[Matriz Inversa]]).

## O que **não** é linear
Translação: $T(x,y)=(x+1,\,y)$ move a origem, então não é linear. Isso é um problema em computação gráfica, resolvido com **coordenadas homogêneas** (ver [[Álgebra Linear na Computação]]).

## Erros comuns
- Montar a matriz com $T(e_i)$ nas **linhas** em vez de colunas.
- Inverter a ordem ao compor transformações.
- Achar que "função com $x$ e $y$ somados" é automaticamente linear (confira $T(0)=0$ e as duas propriedades).

## Conexões
[[Matrizes]] · [[Espaços Vetoriais]] · [[Independência Linear e Base]] · [[Autovalores e Autovetores]] · [[Trigonometria]] · [[Álgebra Linear - Índice]]
