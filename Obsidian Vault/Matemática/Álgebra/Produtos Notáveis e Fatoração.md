# Produtos Notáveis e Fatoração

## Conceito
**Produtos notáveis** são multiplicações que aparecem tanto que vale decorar o resultado. **Fatorar** é o caminho inverso: transformar uma soma em produto. As duas ideias são a mesma igualdade lida em direções opostas:

$$\underbrace{(a+b)^2}_{\text{produto}}\ \xleftrightarrow{\ \text{expandir / fatorar}\ }\ \underbrace{a^2+2ab+b^2}_{\text{soma}}$$

Fatorar é a habilidade mais valiosa da álgebra para Cálculo: **simplifica frações, resolve equações e destrava limites** ([[Cálculo I/Limites]]).

## Produtos notáveis
| Nome | Fórmula |
|---|---|
| Quadrado da soma | $(a+b)^2=a^2+2ab+b^2$ |
| Quadrado da diferença | $(a-b)^2=a^2-2ab+b^2$ |
| Produto da soma pela diferença | $(a+b)(a-b)=a^2-b^2$ |
| Cubo da soma | $(a+b)^3=a^3+3a^2b+3ab^2+b^3$ |
| Cubo da diferença | $(a-b)^3=a^3-3a^2b+3ab^2-b^3$ |
| Soma de cubos | $a^3+b^3=(a+b)(a^2-ab+b^2)$ |
| Diferença de cubos | $a^3-b^3=(a-b)(a^2+ab+b^2)$ |
| Quadrado de trinômio | $(a+b+c)^2=a^2+b^2+c^2+2ab+2ac+2bc$ |

**Por que o "$2ab$"?** Geometricamente, um quadrado de lado $a+b$ se divide em um quadrado $a^2$, um quadrado $b^2$ e **dois** retângulos $a\times b$. Por isso o termo do meio é $2ab$ — e por isso $(a+b)^2\ne a^2+b^2$.

## Técnicas de fatoração
Procure sempre **nesta ordem**:

### 1. Fator comum
$$6x^3-9x^2=3x^2(2x-3)$$

### 2. Agrupamento
$$ax+ay+bx+by=a(x+y)+b(x+y)=(a+b)(x+y)$$

### 3. Diferença de quadrados
$$x^2-9=(x-3)(x+3)\qquad 2x^2-8=2(x^2-4)=2(x-2)(x+2)$$
Pode ser aplicada em sequência: $x^4-16=(x^2-4)(x^2+4)=(x-2)(x+2)(x^2+4)$. (O fator $x^2+4$ **não** fatora nos reais.)

### 4. Trinômio quadrado perfeito
$$x^2+6x+9=(x+3)^2$$
Teste: o termo do meio deve ser $\pm2\cdot$ (raiz do 1º) $\cdot$ (raiz do último).

### 5. Trinômio $x^2+Sx+P$
Procure dois números com **soma $S$** e **produto $P$**:
$$x^2-5x+6=(x-2)(x-3)\quad(\text{soma }5,\ \text{produto }6)$$
Para $ax^2+bx+c$ geral, use as raízes ([[Equações do 2º Grau]]): $ax^2+bx+c=a(x-x_1)(x-x_2)$.

### 6. Soma e diferença de cubos
$$x^3-8=(x-2)(x^2+2x+4)\qquad x^3+27=(x+3)(x^2-3x+9)$$
O fator de segundo grau (quadrático) **não** fatora mais nos reais.

### 7. Completar quadrados
$$x^2+6x+5=(x^2+6x+9)-9+5=(x+3)^2-4$$
Vale ouro para equações, para achar o vértice de uma parábola, e para integrais.
Receita: some e subtraia $\left(\dfrac b2\right)^2$.

### Exemplo combinado
$$x^3-3x^2+2x=x(x^2-3x+2)=x(x-1)(x-2)$$
(fator comum, depois trinômio $x^2+Sx+P$).

## Verificação
Sempre **multiplique de volta** (ou substitua um valor): se a expansão não devolve a expressão original, a fatoração está errada.

## Erros comuns
- $(a+b)^2=a^2+b^2$ ❌ e $(a-b)^2=a^2-b^2$ ❌.
- $a^2+b^2=(a+b)^2$ ❌ — e $a^2+b^2$ **não fatora** nos reais.
- Esquecer o sinal do termo do meio em $(a-b)^2$.
- Fatorar parcialmente e parar antes da hora (confira se cada fator ainda fatora).
- $x^3+8=(x+2)^3$ ❌ (é $(x+2)(x^2-2x+4)$).

## Conexões
[[Álgebra - Índice]] · [[Álgebra básica]] · [[Expressões Algébricas e Polinômios]] · [[Frações Algébricas e Racionalização]] · [[Equações do 2º Grau]] · [[Polinômios - Divisão e Raízes]]
