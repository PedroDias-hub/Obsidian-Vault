# Potenciação e radiciação

## Conceito
Potência é multiplicação repetida: $a^n=\underbrace{a\cdot a\cdots a}_{n\text{ vezes}}$. Raiz é a operação inversa: $\sqrt[n]{a}$ é o número que elevado a $n$ dá $a$. As duas ficam unificadas quando se percebe que **raiz é potência com expoente fracionário**.

## Propriedades das potências
$$
a^m a^n=a^{m+n}
$$

$$
\frac{a^m}{a^n}=a^{m-n}
$$

$$
(a^m)^n=a^{mn}
$$

$$
a^{-n}=\frac1{a^n}
$$

$$
\sqrt[n]{a}=a^{1/n}
$$

Além dessas:
$$
(ab)^n=a^nb^n\qquad\left(\frac ab\right)^n=\frac{a^n}{b^n}\qquad a^0=1\ (a\ne0)\qquad a^{m/n}=\sqrt[n]{a^m}
$$

**Por que $a^0=1$ e $a^{-n}=1/a^n$?** Para que a regra $\dfrac{a^m}{a^n}=a^{m-n}$ continue valendo: $\dfrac{a^3}{a^3}=a^{0}$, e como qualquer número dividido por ele mesmo é 1, $a^0=1$. O mesmo raciocínio com $\dfrac{a^2}{a^5}=a^{-3}=\dfrac1{a^3}$ justifica o expoente negativo. Não são "convenções soltas": são as únicas definições que mantêm as propriedades consistentes.

### Exemplos
- $2^3\cdot2^4=2^7=128$
- $(3^2)^3=3^6=729$
- $2^{-3}=\dfrac18$ e $\left(\dfrac13\right)^{-2}=3^2=9$
- $8^{2/3}=\left(\sqrt[3]8\right)^2=2^2=4$

## Radicais
**Propriedades** (para radicandos onde as raízes estão definidas):
$$
\sqrt[n]{ab}=\sqrt[n]a\cdot\sqrt[n]b\qquad\sqrt[n]{\dfrac ab}=\dfrac{\sqrt[n]a}{\sqrt[n]b}\qquad\sqrt[m]{\sqrt[n]a}=\sqrt[mn]a
$$

**Simplificar** = tirar do radical os fatores que são potências perfeitas:
- $\sqrt{72}=\sqrt{36\cdot2}=6\sqrt2$
- $\sqrt[3]{54}=\sqrt[3]{27\cdot2}=3\sqrt[3]2$

**Somar radicais:** só os **semelhantes** (mesmo índice e mesmo radicando) se somam.
$$\sqrt{18}+\sqrt8=3\sqrt2+2\sqrt2=5\sqrt2$$

### Raiz quadrada e módulo
$$\sqrt{x^2}=|x|\quad(\text{não }x!)$$
Por exemplo, $\sqrt{(-3)^2}=\sqrt9=3=|-3|$. Isso importa ao resolver equações e inequações ([[Módulo e Equações Modulares]]).

## Notação científica
$N=m\times10^k$ com $1\le m<10$. Exemplos: $3\,000\,000=3\times10^6$; $0{,}00042=4{,}2\times10^{-4}$. Em computação: $2^{10}=1024\approx10^3$, o que explica por que 1 KiB ≈ mil bytes.

## Erros comuns
- $(a+b)^2=a^2+b^2$ ❌ — o correto é $a^2+2ab+b^2$ ([[Produtos Notáveis e Fatoração]]).
- $\sqrt{a+b}=\sqrt a+\sqrt b$ ❌ (teste: $\sqrt{9+16}=5\ne3+4$).
- $a^m+a^n=a^{m+n}$ ❌ (a regra é para **produto**).
- $-3^2=9$ ❌ (é $-9$); $(-3)^2=9$.
- $2^{3^2}$ é $2^{(3^2)}=2^9=512$, e não $(2^3)^2=64$.

## Conexões
[[Álgebra - Índice]] · [[Operações, Frações e Propriedades]] · [[Frações Algébricas e Racionalização]] · [[Logaritmos]] (o inverso da potenciação) · [[Funções exponenciais e logarítmicas]]
