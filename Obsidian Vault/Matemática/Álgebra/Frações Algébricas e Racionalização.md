# Frações Algébricas e Racionalização

## Conceito
Fração algébrica é uma fração em que numerador e/ou denominador têm letras, como $\dfrac{x^2-9}{x^2-3x}$. Tudo o que vale para frações numéricas vale aqui — com um cuidado extra: **o denominador não pode ser zero**.

## Condição de existência
Antes de simplificar, anote os valores proibidos (os que zeram o denominador original). Para $\dfrac{x^2-9}{x^2-3x}$: $x^2-3x=x(x-3)\ne0\Rightarrow x\ne0$ e $x\ne3$.

## Simplificação: fatore primeiro
Só se cancelam **fatores**, nunca parcelas. Por isso o primeiro passo é fatorar ([[Produtos Notáveis e Fatoração]]):
$$\frac{x^2-9}{x^2-3x}=\frac{(x-3)(x+3)}{x(x-3)}=\frac{x+3}{x}\qquad(x\ne0,\ x\ne3)$$

(Note que a simplificação **mantém** a restrição $x\ne3$, mesmo que ela tenha "sumido" da fração final. Esse "buraco" é exatamente uma descontinuidade removível — ver [[Cálculo I/Continuidade]].)

## Operações
**Produto e divisão:** fatore tudo, cancele fatores comuns; na divisão, multiplique pelo inverso.
$$\frac{x^2-4}{x+3}\cdot\frac{x+3}{x-2}=\frac{(x-2)(x+2)}{x+3}\cdot\frac{x+3}{x-2}=x+2$$

**Soma e subtração:** MMC dos denominadores (fatorados).
$$\frac1{x-1}+\frac1{x+1}=\frac{(x+1)+(x-1)}{(x-1)(x+1)}=\frac{2x}{x^2-1}$$

**Fração de fração:** multiplique tudo pelo MMC dos denominadores internos.
$$\frac{1+\frac1x}{1-\frac1x}=\frac{x\left(1+\frac1x\right)}{x\left(1-\frac1x\right)}=\frac{x+1}{x-1}$$

## Racionalização de denominadores
**Objetivo:** eliminar raízes do denominador, multiplicando numerador e denominador pela mesma coisa (isto é, multiplicando por 1).

**Denominador com uma raiz:**
$$\frac1{\sqrt2}=\frac{1}{\sqrt2}\cdot\frac{\sqrt2}{\sqrt2}=\frac{\sqrt2}{2}$$

**Denominador com soma/diferença (use o conjugado):** o conjugado de $a+b$ é $a-b$, e o produto $(a+b)(a-b)=a^2-b^2$ elimina as raízes.
$$\frac3{\sqrt5-\sqrt2}\cdot\frac{\sqrt5+\sqrt2}{\sqrt5+\sqrt2}=\frac{3(\sqrt5+\sqrt2)}{5-2}=\sqrt5+\sqrt2$$

$$\frac{2}{\sqrt3+1}=\frac{2(\sqrt3-1)}{3-1}=\sqrt3-1$$

## O truque do conjugado em limites
Muitos limites $\dfrac00$ com raízes se resolvem multiplicando pelo conjugado:
$$\lim_{x\to0}\frac{\sqrt{x+1}-1}{x}=\lim_{x\to0}\frac{(x+1)-1}{x\left(\sqrt{x+1}+1\right)}=\lim_{x\to0}\frac1{\sqrt{x+1}+1}=\frac12$$
Ver [[Cálculo I/Limites]] e [[Tipos de Limites]].

## Erros comuns
- Cancelar parcelas: $\dfrac{x+3}{x}=3$ ❌.
- Esquecer as restrições do domínio original.
- Somar frações somando denominadores: $\dfrac1a+\dfrac1b=\dfrac1{a+b}$ ❌.
- No conjugado, trocar o sinal errado, ou multiplicar só o denominador (é preciso multiplicar **os dois**).

## Conexões
[[Álgebra - Índice]] · [[Operações, Frações e Propriedades]] · [[Potenciação e radiciação]] · [[Módulo e Equações Modulares]] · [[Cálculo I/Limites]]
