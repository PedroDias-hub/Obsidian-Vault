# Polinômios — Divisão e Raízes

## Conceito
Dividir polinômios funciona como dividir inteiros ("$17=5\cdot3+2$"): sempre dá um **quociente** e um **resto**, e o resto é "menor" que o divisor. Essa ideia leva a um dos resultados mais úteis da álgebra: **achar uma raiz equivale a achar um fator**.

## Algoritmo da divisão
Para polinômios $p(x)$ e $d(x)\ne0$ existem únicos $q(x)$ e $r(x)$ com
$$p(x)=d(x)\,q(x)+r(x),\qquad \operatorname{grau}(r)<\operatorname{grau}(d)\ \text{ ou }\ r=0$$

Se $r=0$, a divisão é **exata** e $d(x)$ é um **fator** de $p(x)$.

## Dispositivo de Briot–Ruffini (divisor $x-a$)
Atalho para dividir por $x-a$. Escreva os coeficientes de $p$, "desça" o primeiro, e repita: **multiplique por $a$ e some ao próximo**.

**Exemplo.** $p(x)=2x^3-3x^2+x-5$ dividido por $x-2$ (aqui $a=2$):

```
 2 |  2   -3    1   -5
   |       4    2    6
   -----------------------
      2    1    3 |  1
```
Quociente $q(x)=2x^2+x+3$ e resto $r=1$. Ou seja,
$$2x^3-3x^2+x-5=(x-2)(2x^2+x+3)+1$$

## Teorema do resto e teorema de D'Alembert
- **Teorema do resto:** o resto da divisão de $p(x)$ por $x-a$ é $p(a)$.
- **D'Alembert:** $x-a$ é fator de $p(x)\iff p(a)=0$.

No exemplo, $p(2)=16-12+2-5=1$, que é exatamente o resto encontrado. Isso permite saber o resto **sem dividir**.

## Achando raízes
Para $p(x)=a_nx^n+\cdots+a_0$ com coeficientes **inteiros**, toda raiz racional $\dfrac pq$ (irredutível) tem $p\mid a_0$ e $q\mid a_n$ (**teorema das raízes racionais**). Isso gera uma lista finita de candidatos para testar.

**Exemplo completo.** Resolver $x^3-6x^2+11x-6=0$.
- Candidatos: divisores de $-6$ (como $a_n=1$): $\pm1,\pm2,\pm3,\pm6$.
- $p(1)=1-6+11-6=0$ ✓, então $x-1$ é fator.
- Briot–Ruffini com $a=1$ dá o quociente $x^2-5x+6$.
- $x^2-5x+6=(x-2)(x-3)$.

Resultado: $x^3-6x^2+11x-6=(x-1)(x-2)(x-3)$, raízes $1,\,2,\,3$.

## Teorema fundamental da álgebra
Todo polinômio de grau $n\ge1$ tem exatamente $n$ raízes **complexas** (contando multiplicidade). Logo $p(x)=a_n(x-r_1)(x-r_2)\cdots(x-r_n)$. Nos reais, raízes complexas aparecem em **pares conjugados** ($a+bi$ e $a-bi$), por isso um polinômio de grau ímpar sempre tem pelo menos uma raiz real.

**Multiplicidade:** em $(x-2)^3(x+1)$, a raiz $2$ tem multiplicidade 3. No gráfico, raiz de multiplicidade **par** *toca* o eixo e volta; de multiplicidade **ímpar** *atravessa*.

## Relações de Girard (soma e produto das raízes)
Para $ax^3+bx^2+cx+d=0$ com raízes $r_1,r_2,r_3$:
$$r_1+r_2+r_3=-\frac ba\qquad r_1r_2+r_1r_3+r_2r_3=\frac ca\qquad r_1r_2r_3=-\frac da$$

Conferindo com $x^3-6x^2+11x-6$ (raízes $1,2,3$): soma $=6=-\frac{-6}{1}$ ✓; soma dos produtos dois a dois $=2+3+6=11$ ✓; produto $=6=-\frac{-6}{1}$ ✓.
(Para grau 2 é o conhecido $S=-b/a$, $P=c/a$ de [[Equações do 2º Grau]].)

## Erros comuns
- Esquecer **coeficientes zero** no Briot–Ruffini: para $x^3-1$ escreva $1,\ 0,\ 0,\ -1$.
- Usar $x-a$ com sinal trocado (para dividir por $x+3$, use $a=-3$).
- Achar que só existem raízes reais.
- Esquecer o sinal em Girard ($-b/a$, não $b/a$).

## Conexões
[[Álgebra - Índice]] · [[Expressões Algébricas e Polinômios]] · [[Produtos Notáveis e Fatoração]] · [[Equações do 2º Grau]] · [[Funções polinomiais]] · [[Autovalores e Autovetores]] (polinômio característico)
