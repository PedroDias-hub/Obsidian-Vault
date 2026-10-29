# Logaritmos

## Conceito
O logaritmo responde a uma pergunta: **"a que expoente preciso elevar a base para obter este número?"** É a operação inversa da potenciação ([[Potenciação e radiciação]]), do mesmo jeito que a subtração é inversa da soma.

Definição:

$$
\log_a b=c \iff a^c=b
$$

Exemplos: $\log_28=3$ (pois $2^3=8$); $\log_{10}0{,}001=-3$ (pois $10^{-3}=0{,}001$); $\log_5 1=0$; $\log_77=1$.

Condições:

$$
a>0,\quad a\neq1,\quad b>0
$$

**Por quê?** $b>0$ porque nenhuma potência de base positiva dá resultado negativo ou zero; $a\ne1$ porque $1^c=1$ para todo $c$ (não identificaria expoente algum); $a>0$ para a potência real estar bem definida.

## Casos particulares e bases notáveis
$$\log_a1=0\qquad\log_aa=1\qquad a^{\log_ab}=b\qquad\log_aa^k=k$$
- **Logaritmo decimal**: $\log b=\log_{10}b$.
- **Logaritmo natural**: $\ln b=\log_eb$, com $e\approx2{,}718$.
- **Em computação**: $\log_2$ aparece em tudo ("quantos bits para representar $n$ valores?" $\to\lceil\log_2n\rceil$; busca binária; árvores balanceadas).

## Propriedades

$$
\log_a(xy)=\log_a x+\log_a y
$$

$$
\log_a\left(\frac{x}{y}\right)=\log_a x-\log_a y
$$

$$
\log_a(x^r)=r\log_a x
$$

Mudança de base:

$$
\log_a b=\frac{\ln b}{\ln a}
$$

(vale com qualquer base no lugar de $\ln$: $\log_ab=\dfrac{\log_cb}{\log_ca}$.)

**Por que o produto vira soma?** Porque $a^m\cdot a^n=a^{m+n}$: logaritmo "enxerga" expoentes. Foi exatamente por isso que logaritmos foram inventados: transformar multiplicações difíceis em somas (era a base das réguas de cálculo).

## Equações exponenciais
Tente **igualar as bases**; se não der, aplique logaritmo.
- $2^x=32\Rightarrow2^x=2^5\Rightarrow x=5$
- $3^{x+1}=27=3^3\Rightarrow x+1=3\Rightarrow x=2$
- $5^x=7\Rightarrow x=\log_57=\dfrac{\ln7}{\ln5}$

## Equações logarítmicas
Passos: (1) imponha as **condições de existência**; (2) use propriedades para chegar a $\log_a(\cdot)=\log_a(\cdot)$ ou $\log_a(\cdot)=k$; (3) resolva; (4) **teste** com as condições.

**Exemplo.** $\log_2x+\log_2(x-2)=3$.
- Existência: $x>0$ e $x-2>0$, isto é, $x>2$.
- $\log_2[x(x-2)]=3\Rightarrow x(x-2)=8\Rightarrow x^2-2x-8=0\Rightarrow x=4$ ou $x=-2$.
- $x=-2$ não satisfaz $x>2$ ✗. Solução: $x=4$ (confira: $\log_24+\log_22=2+1=3$ ✓).

## Inequações exponenciais e logarítmicas
Se a base $a>1$, a função é **crescente** e o sentido da desigualdade se mantém; se $0<a<1$, é **decrescente** e o sentido **inverte**.
- $2^x>8\iff x>3$
- $\left(\tfrac12\right)^x>\tfrac18\iff x<3$ (base entre 0 e 1 inverte)

## Erros comuns
- $\log(x+y)=\log x+\log y$ ❌ (a soma vem do **produto**: $\log(xy)$).
- $\dfrac{\log x}{\log y}=\log(x-y)$ ❌ (o quociente de logs é mudança de base: $\log_yx$).
- $(\log x)^2=2\log x$ ❌ (a propriedade é para $\log(x^2)$).
- Esquecer as condições de existência (o clássico "raiz estranha").
- Dizer que $\log_a0$ ou $\log_a(-3)$ existe.

## Conexões
[[Álgebra - Índice]] · [[Funções exponenciais e logarítmicas]] · [[Potenciação e radiciação]] · [[Equações do 2º Grau]] · [[Cálculo I/Derivada]] (derivada de $\ln x$ e $e^x$)
