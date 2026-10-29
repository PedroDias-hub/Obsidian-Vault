			'[
			
	   4RG BHVC4RFV C\4dx5V5\# Limites

## 📖 Conceito

Um **limite** descreve o valor que a função $f(x)$ se aproxima quando a variável $x$ se aproxima de um ponto $a$ (ou de $\pm\infty$). Formalmente:

$$\displaystyle \lim_{x\to a} f(x) = L$$

significa que, para valores de $x$ suficientemente próximos de $a$, $f(x)$ fica arbitrariamente próximo de $L$.

---

## 🎯 Aplicações

- **Continuidade** – $f$ é contínua em $a$ se $\lim_{x\to a}f(x)=f(a)$.
- **Derivada** – definição: $f'(a)=\displaystyle \lim_{h\to 0}\frac{f(a+h)-f(a)}{h}$.
- **Análise de comportamento assintótico** – estudar o crescimento de funções quando $x\to\infty$ ou $x\to -\infty$.
- **Cálculo de áreas e volumes** – limites de somas de Riemann.

---

## 📈 Gráficos e tipos de limites

| Tipo de limite         | Descrição                                       | Exemplo visual                                                                            |
| ---------------------- | ----------------------------------------------- | ----------------------------------------------------------------------------------------- |
| **Limite finito**      | $\lim_{x\to a}f(x)=L$ com $L$ finito.           | ![Limite finito](file:///C:/Users/Rosan/.gemini/antigravity/brain/9b9e48ff-4285-4819-96d1-8ae739ee136f/limite_finite_1793206534754.jpg) |
| **Limite infinito**    | $\lim_{x\to a}f(x)=\pm\infty$.                  | ![limite infinito](file:///C:/Users/Rosan/.gemini/antigravity/brain/9b9e48ff-4285-4819-96d1-8ae739ee136f/limite_infinite_1793206569435.jpg)                                           |
| **Limite lateral**     | $\lim_{x\to a^-}f(x)$ ou $\lim_{x\to a^+}f(x)$. | ![limite lateral](file:///C:/Users/Rosan/.gemini/antigravity/brain/9b9e48ff-4285-4819-96d1-8ae739ee136f/limite_lateral_1793208428183.jpg)                                             |
| **Limite no infinito** | $\lim_{x\to\pm\infty}f(x)=L$.                   | ![limite no infinito](file:///C:/Users/Rosan/.gemini/antigravity/brain/9b9e48ff-4285-4819-96d1-8ae739ee136f/limite_no_infinito_1793209005880.jpg)                                     |

---

## 📏 Assíntotas

### Assíntota vertical

Ocorrer quando $\lim_{x\to a}f(x)=\pm\infty$. A reta $x=a$ é vertical e indica que a função cresce sem limites ao se aproximar de $a$.

### Assíntota horizontal

Quando $\lim_{x\to\pm\infty}f(x)=L$. A reta $y=L$ descreve o valor ao qual a função tende para valores extremos de $x$.

### Assíntota oblíqua (ou inclinada)

Se $\displaystyle \lim_{x\to\pm\infty}\bigl(f(x)-mx-b\bigr)=0$, então $y=mx+b$ é uma assíntota oblíqua.

---

## 🛠 Técnicas de cálculo de limites

- **Substituição direta** (quando a função é contínua).
- **Fatoração** e cancelamento de termos.
- **Racionalização** de radicais.
- **Mudança de variável** (ex.: $x=1/t$ para limites no infinito).
- **Regra de L'Hôpital** (para formas $0/0$ ou $\infty/\infty$).
- **Limites laterais** para pontos de descontinuidade.

---

## 📚 Referências adicionais

- [[Continuidade]] – ligação direta com limites.
- [[Derivada]] – definição baseada em limite.
- [[Tipos de Limites]] – capítulo específico com exemplos.
- [[Exercícios de Limites]] – lista de questões para prática.
- **Khan Academy – Limites**: https://pt.khanacademy.org/math/calculus-1/calc1-limits-and-continuity
- **3Blue1Brown – “Essence of Calculus” – Episódio 2**: https://www.youtube.com/watch?v=7ZpLLV6tL9s

---

> **Dica de estudo**: ao analisar um gráfico, identifique primeiro as assíntotas (verticais, horizontais e oblíquas). Elas dão pistas valiosas sobre o comportamento do limite.
