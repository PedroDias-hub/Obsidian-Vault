# Módulo e Equações Modulares

## Conceito
O **módulo** (valor absoluto) de um número é sua **distância até a origem** na reta real. Distância nunca é negativa.

$$|x|=\begin{cases}x,&x\ge0\\-x,&x<0\end{cases}$$

Exemplos: $|5|=5$, $|-5|=5$, $|0|=0$. Note que $-x$ é **positivo** quando $x<0$ — por isso $|x|\ge0$ sempre.

## Interpretação geométrica
$|x-a|$ é a **distância entre $x$ e $a$**. Então:
- $|x-3|=2$: os pontos a distância 2 de 3, isto é, $x=1$ ou $x=5$.
- $|x-3|<2$: pontos a menos de 2 de 3, isto é, $1<x<5$.

## Propriedades
$$|ab|=|a||b|\qquad\left|\frac ab\right|=\frac{|a|}{|b|}\qquad|a|^2=a^2\qquad\sqrt{a^2}=|a|$$
$$|a+b|\le|a|+|b|\ \ \text{(desigualdade triangular)}$$
**Atenção:** $|a+b|\ne|a|+|b|$ em geral (teste $a=3,\ b=-3$).

## Equações modulares
Para $k>0$:
$$|f(x)|=k\iff f(x)=k\ \text{ ou }\ f(x)=-k$$

**Exemplo.** $|2x-1|=5$: $2x-1=5\Rightarrow x=3$ ou $2x-1=-5\Rightarrow x=-2$.

**Quando os dois lados têm $x$:** $|A|=B$ exige $B\ge0$.
$$|x-1|=2x+3$$
Condição: $2x+3\ge0\Rightarrow x\ge-\tfrac32$. Casos:
- $x-1=2x+3\Rightarrow x=-4$ → viola a condição ($2(-4)+3=-5<0$) ✗
- $x-1=-(2x+3)\Rightarrow3x=-2\Rightarrow x=-\tfrac23$ ✓ ($|-\tfrac23-1|=\tfrac53=2(-\tfrac23)+3$)

Solução: $x=-\dfrac23$.

## Inequações modulares
Para $k>0$:

| Inequação | Equivale a | Forma |
|---|---|---|
| $\lvert f(x)\rvert<k$ | $-k<f(x)<k$ | **"entre"** (interseção) |
| $\lvert f(x)\rvert>k$ | $f(x)<-k$ **ou** $f(x)>k$ | **"fora"** (união) |

**Exemplos.**
- $|x-3|<2\iff-2<x-3<2\iff1<x<5$.
- $|x+1|\ge3\iff x+1\le-3$ ou $x+1\ge3\iff x\le-4$ ou $x\ge2$.

Mnemônico: "**menor** → **entre**" e "**maior** → **fora**".

## O módulo e a função
O gráfico de $y=|x|$ é um "V" com vértice na origem. Em $y=|f(x)|$, as partes do gráfico abaixo do eixo $x$ são **espelhadas** para cima. O módulo não é derivável em $x=0$ (bico), um exemplo clássico em [[Cálculo I/Continuidade]] e [[Cálculo I/Derivada]].

## Erros comuns
- $|x|=-3$ tem solução? **Não** (módulo nunca é negativo).
- Resolver $|x|<k$ com $k\le0$ (sem solução se $k\le0$; $|x|>k$ vale sempre se $k<0$).
- Escrever $\sqrt{x^2}=x$ (é $|x|$).
- Esquecer de testar as soluções quando há $x$ nos dois lados.

## Conexões
[[Álgebra - Índice]] · [[Inequações e Estudo de Sinal]] · [[Potenciação e radiciação]] · [[Conjuntos Numéricos e Intervalos]] · [[Funções - visão geral]]
