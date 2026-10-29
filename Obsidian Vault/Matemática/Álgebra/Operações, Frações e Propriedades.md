# Operações, Frações e Propriedades

## Ordem das operações
Resolva, nesta ordem:
1. **Parênteses** (de dentro para fora)
2. **Potências e raízes**
3. **Multiplicação e divisão** (da esquerda para a direita, mesma prioridade)
4. **Soma e subtração** (da esquerda para a direita)

Exemplo: $2+3\cdot4^2=2+3\cdot16=2+48=50$ (não $5\cdot16$).

## Propriedades fundamentais
Valem para quaisquer reais $a,b,c$:

| Propriedade | Soma | Produto |
|---|---|---|
| Comutativa | $a+b=b+a$ | $ab=ba$ |
| Associativa | $(a+b)+c=a+(b+c)$ | $(ab)c=a(bc)$ |
| Elemento neutro | $a+0=a$ | $a\cdot1=a$ |
| Inverso | $a+(-a)=0$ | $a\cdot\dfrac1a=1$ $(a\ne0)$ |
| **Distributiva** | $a(b+c)=ab+ac$ | |

A distributiva é a propriedade mais usada em álgebra: ela liga soma e produto, e **fatorar** é usá-la "de trás para frente" ($ab+ac=a(b+c)$).

## Regra dos sinais
$(+)(+)=+$ · $(-)(-)=+$ · $(+)(-)=-$ · $(-)(+)=-$.
Subtrair é somar o oposto: $a-(b-c)=a-b+c$ (o sinal de menos **troca todos** os sinais dentro dos parênteses).

## Frações
**Equivalência e simplificação:** $\dfrac ab=\dfrac{ak}{bk}$ ($k\ne0$). Simplificar é dividir numerador e denominador por um **fator comum**.

**Soma e subtração:** leve ao mesmo denominador (use o MMC).
$$\frac23+\frac34-\frac16=\frac8{12}+\frac9{12}-\frac2{12}=\frac{15}{12}=\frac54$$

**Produto:** numerador com numerador, denominador com denominador: $\dfrac ab\cdot\dfrac cd=\dfrac{ac}{bd}$.

**Divisão:** multiplique pelo inverso: $\dfrac ab\div\dfrac cd=\dfrac ab\cdot\dfrac dc$.
$$\frac34\div\frac58=\frac34\cdot\frac85=\frac{24}{20}=\frac65$$

## MDC e MMC
- **MDC**: maior divisor comum. Ex.: $\text{MDC}(12,18)=6$.
- **MMC**: menor múltiplo comum. Ex.: $\text{MMC}(4,6)=12$.
- Relação: $\text{MDC}(a,b)\cdot\text{MMC}(a,b)=a\cdot b$.

Calcule fatorando em primos: $12=2^2\cdot3$ e $18=2\cdot3^2$. MDC = primos comuns com **menor** expoente ($2\cdot3=6$); MMC = todos os primos com **maior** expoente ($2^2\cdot3^2=36$).

(Computação: o MDC é calculado pelo **algoritmo de Euclides**: $\text{MDC}(a,b)=\text{MDC}(b,\ a\bmod b)$, um clássico de programação.)

## Erros comuns (os mais caros em Cálculo)
| Errado ❌ | Certo ✅ |
|---|---|
| $\dfrac{a}{b+c}=\dfrac ab+\dfrac ac$ | $\dfrac{a+b}{c}=\dfrac ac+\dfrac bc$ (a divisão só distribui sobre o **numerador**) |
| $\dfrac{a+b}{a}=1+b$ | $\dfrac{a+b}{a}=1+\dfrac ba$ |
| cancelar **parcelas**: $\dfrac{x+2}{x}=2$ | só se cancelam **fatores**: $\dfrac{2x}{x}=2$ |
| $\dfrac{1}{a}+\dfrac1b=\dfrac{1}{a+b}$ | $\dfrac1a+\dfrac1b=\dfrac{a+b}{ab}$ |
| $-3^2=9$ | $-3^2=-9$ e $(-3)^2=9$ |

## Conexões
[[Álgebra - Índice]] · [[Conjuntos Numéricos e Intervalos]] · [[Potenciação e radiciação]] · [[Produtos Notáveis e Fatoração]] · [[Frações Algébricas e Racionalização]]
