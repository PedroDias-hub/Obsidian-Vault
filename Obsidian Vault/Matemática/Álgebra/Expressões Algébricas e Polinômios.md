# Expressões Algébricas e Polinômios

## Conceito
Uma **expressão algébrica** combina números e letras (variáveis) com operações. Um **polinômio** é o tipo mais importante: uma soma de **monômios** com expoentes inteiros não negativos.

$$p(x)=a_nx^n+a_{n-1}x^{n-1}+\cdots+a_1x+a_0\qquad(a_n\ne0)$$

- **Monômio**: coeficiente × parte literal, como $5x^3$ ou $-2xy^2$.
- **Grau de um monômio**: soma dos expoentes ($-2xy^2$ tem grau 3).
- **Grau do polinômio**: o maior grau entre seus termos ($a_n\ne0$). O polinômio $3x^4-x+7$ tem grau 4.
- **Termos semelhantes**: mesma parte literal; só eles se somam ($3x^2+5x^2=8x^2$, mas $3x^2+5x$ não se simplifica).
- **Valor numérico**: substituir a variável. Para $p(x)=2x^2-3x+1$: $p(2)=8-6+1=3$.

## Casos particulares
| Grau | Nome | Forma |
|---|---|---|
| 0 | constante | $a$ |
| 1 | afim | $ax+b$ |
| 2 | quadrático | $ax^2+bx+c$ |
| 3 | cúbico | $ax^3+\cdots$ |

Ver [[Funções polinomiais]] para o lado gráfico.

## Operações
**Soma e subtração:** some os coeficientes dos termos semelhantes.
$$(3x^2-2x+1)+(x^2+5x-4)=4x^2+3x-3$$
Cuidado com o sinal de menos: $-(x^2-2x)=-x^2+2x$.

**Multiplicação:** distributiva termo a termo (e propriedade $x^m\cdot x^n=x^{m+n}$).
$$(x+2)(x^2-3x+1)=x^3-3x^2+x+2x^2-6x+2=x^3-x^2-5x+2$$
O grau do produto é a **soma** dos graus.

**Divisão:** ver [[Polinômios - Divisão e Raízes]] (algoritmo da divisão, Briot–Ruffini, teorema do resto).

## Igualdade de polinômios
Dois polinômios são iguais quando têm **os mesmos coeficientes, grau a grau**. Isso dá o método dos **coeficientes a determinar**:

$$a(x+1)+b(x-1)=3x+5\ \Rightarrow\ (a+b)x+(a-b)=3x+5\ \Rightarrow\ \begin{cases}a+b=3\\a-b=5\end{cases}\Rightarrow a=4,\ b=-1$$

Essa técnica reaparece em frações parciais (Cálculo II).

## Raiz de um polinômio
$r$ é raiz de $p$ quando $p(r)=0$. Raízes de $p$ são os pontos onde o gráfico cruza o eixo $x$ e as soluções da equação $p(x)=0$.

## Erros comuns
- Somar termos que não são semelhantes ($x+x^2=x^3$ ❌).
- Esquecer de distribuir o sinal negativo.
- Multiplicar só o primeiro termo: $2(x+3)=2x+3$ ❌ (é $2x+6$).
- Confundir $x^2\cdot x^3=x^5$ (expoentes **somam**) com $(x^2)^3=x^6$ (expoentes **multiplicam**).

## Conexões
[[Álgebra - Índice]] · [[Produtos Notáveis e Fatoração]] · [[Polinômios - Divisão e Raízes]] · [[Equações do 2º Grau]] · [[Potenciação e radiciação]]
