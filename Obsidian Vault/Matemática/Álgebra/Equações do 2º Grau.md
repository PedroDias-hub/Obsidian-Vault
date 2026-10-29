# Equações do 2º Grau

## Conceito
Equação do 2º grau é toda equação que pode ser escrita como
$$ax^2+bx+c=0\qquad(a\ne0)$$
Graficamente, as soluções são os pontos onde a **parábola** $y=ax^2+bx+c$ cruza o eixo $x$.

## Fórmula de Bhaskara
$$\Delta=b^2-4ac\qquad x=\frac{-b\pm\sqrt\Delta}{2a}$$

**De onde vem?** De [[Produtos Notáveis e Fatoração#7. Completar quadrados|completar quadrados]]. Divida por $a$ e complete:
$$x^2+\frac bax=-\frac ca\ \Rightarrow\ \left(x+\frac b{2a}\right)^2=\frac{b^2-4ac}{4a^2}\ \Rightarrow\ x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}$$
Saber isso evita decorar a fórmula "no escuro" e mostra que o discriminante $\Delta$ é o que está dentro da raiz.

## O discriminante decide
| $\Delta$ | Raízes reais | Parábola |
|---|---|---|
| $\Delta>0$ | duas, distintas | corta o eixo $x$ em 2 pontos |
| $\Delta=0$ | uma (dupla) | toca o eixo $x$ no vértice |
| $\Delta<0$ | nenhuma real (duas complexas) | não toca o eixo $x$ |

## Exemplos
- $x^2-5x+6=0$: $\Delta=25-24=1$, $x=\dfrac{5\pm1}2\Rightarrow x=3$ ou $x=2$.
- $2x^2+3x-2=0$: $\Delta=9+16=25$, $x=\dfrac{-3\pm5}4\Rightarrow x=\dfrac12$ ou $x=-2$.
- $x^2+2x+5=0$: $\Delta=4-20=-16<0$: sem raízes reais (as complexas são $-1\pm2i$).

## Soma e produto das raízes
Se $x_1,x_2$ são as raízes:
$$S=x_1+x_2=-\frac ba\qquad P=x_1x_2=\frac ca$$
Dá um atalho: em $x^2-5x+6=0$, procure dois números de soma 5 e produto 6 → $2$ e $3$. E permite **montar** uma equação a partir das raízes: $x^2-Sx+P=0$.

Forma fatorada: $ax^2+bx+c=a(x-x_1)(x-x_2)$.

## Casos incompletos (não precisam de Bhaskara)
- $b=0$: $x^2-9=0\Rightarrow x=\pm3$.
- $c=0$: $x^2+3x=0\Rightarrow x(x+3)=0\Rightarrow x=0$ ou $x=-3$. **Não** divida por $x$ (perderia a raiz $0$).

## Vértice da parábola
$$x_v=-\frac b{2a}\qquad y_v=-\frac\Delta{4a}$$
Se $a>0$: concavidade para cima, vértice é **mínimo**; se $a<0$: para baixo, vértice é **máximo**. Ver [[Funções polinomiais]] e, em Cálculo, [[Aplicações da Derivada]].

## Equações que viram do 2º grau
**Biquadrada** (troca de variável): $x^4-5x^2+4=0$. Faça $y=x^2$: $y^2-5y+4=0\Rightarrow y=1$ ou $y=4\Rightarrow x=\pm1$ ou $x=\pm2$.

**Irracional** (eleve ao quadrado e **teste as soluções**): $\sqrt{x+2}=x$.
$$x+2=x^2\ \Rightarrow\ x^2-x-2=0\ \Rightarrow\ x=2\ \text{ou}\ x=-1$$
Teste: $x=2$: $\sqrt4=2$ ✓. $x=-1$: $\sqrt1=1\ne-1$ ✗ (**raiz estranha**, criada ao elevar ao quadrado). Solução: $x=2$.

## Erros comuns
- Errar o sinal de $-b$ ou de $-4ac$ (use parênteses ao substituir: $b^2=(-5)^2=25$).
- Esquecer o "$2a$" no denominador inteiro (ele divide **toda** a expressão do numerador).
- Não testar soluções em equações com raiz ou denominador.
- Dividir os dois lados por $x$ e perder a solução $x=0$.

## Conexões
[[Álgebra - Índice]] · [[Produtos Notáveis e Fatoração]] · [[Equações do 1º Grau e Sistemas]] · [[Inequações e Estudo de Sinal]] · [[Equações e inequações]] · [[Funções polinomiais]]
