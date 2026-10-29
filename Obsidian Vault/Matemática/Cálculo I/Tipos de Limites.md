# Tipos de Limites

Classificação completa dos tipos de limite, agrupados pelo que varia: o ponto para onde $x$ tende e o valor para onde $f(x)$ tende.

## 1. Quanto ao ponto finito x → a

### 1.1 Limite finito num ponto finito
$$\lim_{x \to a} f(x) = L$$
![](file:///C:/Users/Rosan/.gemini/antigravity/brain/9b9e48ff-4285-4819-96d1-8ae739ee136f/limite_finite_1793206534754.jpg)
Caso mais comum — geralmente resolvido por substituição direta quando $f$ é contínua em $a$.

### 1.2 Limites laterais
- **Limite à esquerda**: $\lim_{x \to a^-} f(x)$ — $x$ se aproxima de $a$ por valores menores.
- **Limite à direita**: $\lim_{x \to a^+} f(x)$ — $x$ se aproxima de $a$ por valores maiores.
- O limite bilateral $\lim_{x \to a} f(x)$ **só existe** se os dois laterais existirem e forem iguais.
- Muito usado em funções definidas por partes e em pontos de descontinuidade de salto (ver [[Continuidade]]).

### 1.3 Limite infinito num ponto finito
$$\lim_{x \to a} f(x) = \pm\infty$$
A função "explode" perto de $a$ — indica uma **assíntota vertical** em $x = a$.
Exemplo: $\lim_{x \to 0^+} \dfrac{1}{x} = +\infty$
![](file:///C:/Users/Rosan/.gemini/antigravity/brain/9b9e48ff-4285-4819-96d1-8ae739ee136f/limite_infinite_1793206569435.jpg)

## 2. Quanto ao ponto no infinito x → ±∞

### 2.1 Limite finito no infinito
$$\lim_{x \to \pm\infty} f(x) = L$$
Indica uma **assíntota horizontal** em $y = L$.
Exemplo: $\lim_{x \to \infty} \dfrac{1}{x} = 0$

### 2.2 Limite infinito no infinito
$$\lim_{x \to \pm\infty} f(x) = \pm\infty$$
Comportamento de crescimento/decrescimento sem limite — comum em polinômios e exponenciais.
Exemplo: $\lim_{x \to \infty} x^2 = +\infty$
![](file:///C:/Users/Rosan/.gemini/antigravity/brain/9b9e48ff-4285-4819-96d1-8ae739ee136f/limite_infinito_no_infinito_1793212312359.jpg)

## 3. Quanto à técnica de resolução

### 3.1 Por substituição direta
Válido quando $f$ é contínua em $a$: $\lim_{x \to a} f(x) = f(a)$.

### 3.2 Com indeterminação (singularidades)
Formas que não podem ser resolvidas por substituição direta e exigem manipulação algébrica ou a [[6 - Regra de L'Hôpital|Regra de L'Hôpital]]:

| Forma | Exemplo |
|---|---|
| $0/0$ | $\lim_{x \to 2} \dfrac{x^2-4}{x-2}$ |
| $\infty/\infty$ | $\lim_{x \to \infty} \dfrac{3x^2+1}{x^2-5}$ |
| $\infty - \infty$ | $\lim_{x \to \infty} (\sqrt{x^2+x} - x)$ |
| $0 \cdot \infty$ | $\lim_{x \to 0^+} x \ln x$ |
| $1^\infty$ | $\lim_{x \to \infty} \left(1+\frac{1}{x}\right)^x$ |
| $0^0$ | $\lim_{x \to 0^+} x^x$ |
| $\infty^0$ | $\lim_{x \to \infty} x^{1/x}$ |

Técnicas comuns para resolver: fatoração, racionalização (multiplicar pelo conjugado), divisão pelo termo de maior grau, L'Hôpital.

### 3.3 Limites fundamentais (notáveis)
Resultados clássicos usados como "atalho":
- $\lim_{x \to 0} \dfrac{\sin x}{x} = 1$ (fundamental trigonométrico)
- $\lim_{x \to \infty} \left(1+\dfrac{1}{x}\right)^x = e$ (fundamental exponencial)
- $\lim_{x \to 0} \dfrac{e^x - 1}{x} = 1$
- $\lim_{x \to 0} \dfrac{\ln(1+x)}{x} = 1$

## 4. Quanto à existência

### 4.1 Limite que existe
Os limites laterais coincidem (ou, no caso de funções contínuas, coincide com $f(a)$).

### 4.2 Limite que não existe
- Limites laterais diferentes (salto).
- Função oscila sem se estabilizar — ex.: $\lim_{x \to 0} \sin\left(\dfrac{1}{x}\right)$ não existe (oscila infinitamente).
- Diverge para $+\infty$ de um lado e $-\infty$ do outro.

## 5. Outros contextos
- **Limite de sequência**: $\lim_{n \to \infty} a_n$, quando $n \in \mathbb{N}$ — base para séries (ver [[Cálculo II/README|Cálculo II]]).
- **Limite de função de várias variáveis**: $\lim_{(x,y) \to (a,b)} f(x,y)$ — precisa valer para **qualquer caminho** de aproximação (ver [[Cálculo III/README|Cálculo III]]).

## Ver também
- [[Exercícios de Limites|Exercícios — 5 para cada tipo]]
- [[Limites|Limites — visão geral]]
- [[Continuidade]]
- [[Derivada]]
- [[2 - Limites|UNIP — Unidade I, Tópico 2]]
