# Inequações e Estudo de Sinal

## Conceito
Uma inequação usa $<,\ \le,\ >,\ \ge$ em vez de $=$. A solução normalmente é um **intervalo (ou união de intervalos)**, não um número — por isso este assunto depende de [[Conjuntos Numéricos e Intervalos]].

## A regra que mais gera erro
Ao multiplicar ou dividir por um **número negativo**, o sentido da desigualdade **inverte**:
$$-2x<6\ \Rightarrow\ x>-3$$

## Inequação do 1º grau
$3-2x<7\Rightarrow-2x<4\Rightarrow x>-2$. Solução: $(-2,+\infty)$.

## Inequação do 2º grau
Use o gráfico da parábola: ache as raízes e veja onde ela está acima ou abaixo do eixo $x$.

**Exemplo.** $x^2-x-6\ge0$. Raízes: $x^2-x-6=(x-3)(x+2)=0\Rightarrow x=-2,\ 3$. Com $a>0$ a parábola está **acima** do eixo fora das raízes:
$$x\le-2\ \ \text{ou}\ \ x\ge3\qquad\Longrightarrow\qquad(-\infty,-2]\cup[3,+\infty)$$

**Outro.** $x^2-5x+6<0$: raízes $2$ e $3$; entre elas a parábola está abaixo → $(2,3)$.

Quadro rápido (com $a>0$ e $\Delta>0$, raízes $x_1<x_2$):
| Inequação | Solução |
|---|---|
| $f(x)>0$ | $x<x_1$ ou $x>x_2$ |
| $f(x)<0$ | $x_1<x<x_2$ |

(Com $a<0$ inverte.) Se $\Delta<0$: a parábola nunca cruza o eixo, então o sinal é sempre o de $a$.

## Quadro de sinais (produtos e quocientes)
Método universal para inequações **produto** ou **quociente**:
1. Passe tudo para um lado, deixando $0$ do outro.
2. **Fatore** o que der.
3. Ache os pontos críticos (zeros de cada fator).
4. Estude o sinal de **cada fator** na reta e **multiplique os sinais**.
5. Escolha os intervalos pedidos.

**Exemplo (produto).** $(x+1)(x-2)(x-4)>0$. Pontos críticos: $-1,\ 2,\ 4$.

| | $x<-1$ | $-1<x<2$ | $2<x<4$ | $x>4$ |
|---|---|---|---|---|
| $x+1$ | − | + | + | + |
| $x-2$ | − | − | + | + |
| $x-4$ | − | − | − | + |
| **produto** | − | + | − | + |

Solução: $(-1,2)\cup(4,+\infty)$.

**Exemplo (quociente).** $\dfrac{x-2}{x+1}\le0$. Críticos: $2$ (zera o numerador → **entra**, por causa do $\le$) e $-1$ (zera o denominador → **nunca entra**).
Solução: $(-1,\,2]$.

> [!warning] Não multiplique pelo denominador
> Em $\dfrac{x-2}{x+1}\le0$ você **não pode** "passar $x+1$ multiplicando", porque não sabe se ele é positivo ou negativo (o sentido inverteria ou não). Use o quadro de sinais.

## Interpretação em funções
Resolver $f(x)>0$ é descobrir onde o gráfico está **acima** do eixo $x$. Esse "estudo de sinal" é a base para achar domínio de funções com raiz/denominador e, em Cálculo, o **sinal da derivada** (crescimento, máximos e mínimos): [[Aplicações da Derivada]].

## Erros comuns
- Não inverter o sentido ao dividir por negativo.
- Incluir no conjunto-solução o ponto que zera o **denominador**.
- Resolver só a equação associada e esquecer de ver qual lado serve.
- Cortar um fator comum que pode ser negativo (ou zero).

## Conexões
[[Álgebra - Índice]] · [[Equações do 2º Grau]] · [[Módulo e Equações Modulares]] · [[Conjuntos Numéricos e Intervalos]] · [[Equações e inequações]]
