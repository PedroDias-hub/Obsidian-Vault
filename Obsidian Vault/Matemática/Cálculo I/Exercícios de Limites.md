# Exercícios — Tipos de Limites

5 exercícios para cada tipo listado em [[Tipos de Limites]]. As respostas ficam em callouts recolhíveis (clique para expandir no Obsidian).

## 1. Limite finito num ponto finito

1. $\lim_{x \to 3} (2x + 1)$
> [!success]- Resposta
> $7$

2. $\lim_{x \to 2} (x^2 - 3x + 4)$
> [!success]- Resposta
> $2$

3. $\lim_{x \to -1} \dfrac{x^2 - 1}{x + 1}$
> [!success]- Resposta
> Fatorar: $\dfrac{(x-1)(x+1)}{x+1} = x - 1 \to -2$

4. $\lim_{x \to 4} \sqrt{x + 5}$
> [!success]- Resposta
> $3$

5. $\lim_{x \to 0} \cos x$
> [!success]- Resposta
> $1$

## 2. Limites laterais

1. Para $f(x) = \dfrac{|x|}{x}$, calcule $\lim_{x \to 0^-} f(x)$.
> [!success]- Resposta
> $-1$
![](file:///C:/Users/Rosan/.gemini/antigravity/brain/9b9e48ff-4285-4819-96d1-8ae739ee136f/limite_lateral_1793208428183.jpg)

2. Para a mesma $f$, calcule $\lim_{x \to 0^+} f(x)$ e conclua sobre o limite bilateral.
> [!success]- Resposta
> $1$. Como os laterais diferem ($-1 \neq 1$), $\lim_{x\to0} f(x)$ não existe.

3. Dado $f(x) = x+1$ se $x<2$, $f(2)=5$, $f(x)=3x-1$ se $x>2$, calcule os limites laterais em $x=2$.
> [!success]- Resposta
> $\lim_{x\to2^-} f(x) = 3$; $\lim_{x\to2^+} f(x) = 5$. Bilateral não existe.

4. $\lim_{x \to 1^-} \lfloor x \rfloor$ e $\lim_{x \to 1^+} \lfloor x \rfloor$ (função piso)
> [!success]- Resposta
> Esquerda: $0$. Direita: $1$. Bilateral não existe.

5. $\lim_{x \to 0^+} \sqrt{x}$
> [!success]- Resposta
> $0$ (só existe o limite à direita, pois o domínio exige $x \geq 0$)

## 3. Limite infinito num ponto finito

1. $\lim_{x \to 0^+} \dfrac{1}{x}$
> [!success]- Resposta
> $+\infty$
![](file:///C:/Users/Rosan/.gemini/antigravity/brain/9b9e48ff-4285-4819-96d1-8ae739ee136f/limite_infinite_1793206569435.jpg)

2. $\lim_{x \to 0^-} \dfrac{1}{x}$
> [!success]- Resposta
> $-\infty$

3. $\lim_{x \to 2} \dfrac{1}{(x-2)^2}$
> [!success]- Resposta
> $+\infty$ (denominador ao quadrado, sempre positivo perto de 2)

4. $\lim_{x \to 3^-} \dfrac{1}{x-3}$
> [!success]- Resposta
> $-\infty$

5. $\lim_{x \to (\pi/2)^-} \tan x$
> [!success]- Resposta
> $+\infty$

## 4. Limite finito no infinito

1. $\lim_{x \to \infty} \dfrac{1}{x}$
> [!success]- Resposta
> $0$

2. $\lim_{x \to -\infty} \dfrac{3x+1}{x}$
> [!success]- Resposta
> $3$

3. $\lim_{x \to \infty} \dfrac{2x^2+1}{x^2-5}$
> [!success]- Resposta
> $2$ (dividir tudo por $x^2$)

4. $\lim_{x \to \infty} \dfrac{5}{x^2}$
> [!success]- Resposta
> $0$

5. $\lim_{x \to -\infty} \left(\dfrac{1}{x} + 2\right)$
> [!success]- Resposta
> $2$

## 5. Limite infinito no infinito

1. $\lim_{x \to \infty} x^2$
> [!success]- Resposta
> $+\infty$
![](file:///C:/Users/Rosan/.gemini/antigravity/brain/9b9e48ff-4285-4819-96d1-8ae739ee136f/limite_infinito_no_infinito_1793212312359.jpg)

2. $\lim_{x \to -\infty} x^3$
> [!success]- Resposta
> $-\infty$
![](file:///C:/Users/Rosan/.gemini/antigravity/brain/9b9e48ff-4285-4819-96d1-8ae739ee136f/limite_x_cubed_minus_inf_1793213938273.jpg)

3. $\lim_{x \to \infty} e^x$
> [!success]- Resposta
> $+\infty$

4. $\lim_{x \to \infty} (x^3 - x)$
> [!success]- Resposta
> $+\infty$ (o termo de maior grau domina)

5. $\lim_{x \to -\infty} (2x^2 + 3x)$
> [!success]- Resposta
> $+\infty$ (o termo $2x^2$ domina e é sempre positivo)

## 6. Indeterminações (uma de cada forma principal)

1. **$0/0$**: $\lim_{x \to 2} \dfrac{x^2-4}{x-2}$
> [!success]- Resposta
> Fatorar: $(x-2)(x+2)/(x-2) = x+2 \to 4$

2. **$\infty/\infty$**: $\lim_{x \to \infty} \dfrac{3x^2+1}{x^2-5}$
> [!success]- Resposta
> $3$

3. **$\infty - \infty$**: $\lim_{x \to \infty} (\sqrt{x^2+x} - x)$
> [!success]- Resposta
> Multiplicar pelo conjugado: $\to \dfrac{1}{2}$

4. **$0 \cdot \infty$**: $\lim_{x \to 0^+} x \ln x$
> [!success]- Resposta
> $0$ (reescrever como $\ln x / (1/x)$ e aplicar L'Hôpital)

5. **$1^\infty$**: $\lim_{x \to \infty} \left(1+\dfrac{2}{x}\right)^x$
> [!success]- Resposta
> $e^2$

## 7. Limites fundamentais

1. $\lim_{x \to 0} \dfrac{\sin x}{x}$
> [!success]- Resposta
> $1$

2. $\lim_{x \to 0} \dfrac{1-\cos x}{x}$
> [!success]- Resposta
> $0$

3. $\lim_{x \to 0} \dfrac{e^x - 1}{x}$
> [!success]- Resposta
> $1$

4. $\lim_{x \to 0} \dfrac{\ln(1+x)}{x}$
> [!success]- Resposta
> $1$

5. $\lim_{x \to \infty} \left(1+\dfrac{1}{x}\right)^x$
> [!success]- Resposta
> $e$

## 8. Limites que não existem

1. $\lim_{x \to 0} \sin(1/x)$
> [!success]- Resposta
> Não existe — oscila entre $-1$ e $1$ infinitas vezes perto de $0$.

2. $\lim_{x \to 0} \dfrac{|x|}{x}$
> [!success]- Resposta
> Não existe — laterais diferentes ($-1$ e $1$).

3. $\lim_{x \to 0} \dfrac{1}{x}$
> [!success]- Resposta
> Não existe — esquerda vai a $-\infty$, direita vai a $+\infty$ (nem convergem para o mesmo valor finito nem para o mesmo infinito).

4. $\lim_{x \to 1} \lfloor x \rfloor$
> [!success]- Resposta
> Não existe — laterais diferentes ($0$ e $1$).

5. $\lim_{x \to 0} \cos(1/x)$
> [!success]- Resposta
> Não existe — oscila entre $-1$ e $1$.

## 9. Limite de sequência

1. $\lim_{n \to \infty} \dfrac{1}{n}$
> [!success]- Resposta
> $0$

2. $\lim_{n \to \infty} \dfrac{n+1}{n}$
> [!success]- Resposta
> $1$

3. $\lim_{n \to \infty} \left(\dfrac{1}{2}\right)^n$
> [!success]- Resposta
> $0$

4. $\lim_{n \to \infty} \dfrac{2n^2+1}{n^2+3}$
> [!success]- Resposta
> $2$

5. $\lim_{n \to \infty} \dfrac{(-1)^n}{n}$
> [!success]- Resposta
> $0$ (o numerador oscila mas é limitado, e o denominador cresce sem parar)

## 10. Limite de função de várias variáveis

1. $\lim_{(x,y) \to (0,0)} (x+y)$
> [!success]- Resposta
> $0$ (função contínua, substituição direta)

2. $\lim_{(x,y) \to (0,0)} \dfrac{xy}{x^2+y^2}$
> [!success]- Resposta
> Não existe — pelo caminho $y=0$ dá $0$; pelo caminho $y=x$ dá $1/2$.

3. $\lim_{(x,y) \to (0,0)} \dfrac{x^2 y}{x^2+y^2}$
> [!success]- Resposta
> $0$ — dá pra provar com coordenadas polares ou teorema do confronto.

4. $\lim_{(x,y) \to (1,2)} (x^2+y^2)$
> [!success]- Resposta
> $5$ (função contínua, substituição direta)

5. $\lim_{(x,y) \to (0,0)} \dfrac{x^2-y^2}{x^2+y^2}$
> [!success]- Resposta
> Não existe — pelo caminho $y=0$ dá $1$; pelo caminho $x=0$ dá $-1$.

## Ver também
- [[Tipos de Limites|Tipos de limites]]
- [[Limites|Limites — visão geral]]
