# Conjuntos Numéricos e Intervalos

## Conceito
Os números foram "inventados" em etapas, cada uma para resolver um problema que a anterior não resolvia. Cada conjunto contém o anterior.

| Conjunto | Símbolo | Elementos | Problema que resolve |
|---|---|---|---|
| Naturais | $\mathbb N$ | $0,1,2,3,\dots$ | contar |
| Inteiros | $\mathbb Z$ | $\dots,-2,-1,0,1,2,\dots$ | subtrair ($3-5$) |
| Racionais | $\mathbb Q$ | $\dfrac pq$, com $p,q\in\mathbb Z$, $q\ne0$ | dividir ($1\div3$) |
| Irracionais | $\mathbb I$ | decimais infinitos **não** periódicos ($\sqrt2,\pi,e$) | medir a diagonal do quadrado |
| Reais | $\mathbb R$ | $\mathbb Q\cup\mathbb I$ | completar a reta numérica |
| Complexos | $\mathbb C$ | $a+bi$, com $i^2=-1$ | $x^2+1=0$ |

$$\mathbb N\subset\mathbb Z\subset\mathbb Q\subset\mathbb R\subset\mathbb C$$

## Racionais: decimais finitos ou periódicos
Todo racional tem representação decimal **finita** ou **dízima periódica**; todo decimal desses tipos é racional.

**Dízima periódica → fração.** Para $x=0{,}7272\ldots$ (período de 2 dígitos): $100x=72{,}7272\ldots$, subtraindo $100x-x=72$, logo $x=\dfrac{72}{99}=\dfrac8{11}$. Do mesmo modo, $0{,}333\ldots=\dfrac13$.

(Curiosidade: $0{,}999\ldots=1$. Pelo mesmo método, $10x-x=9\Rightarrow x=1$.)

## Irracionais: por que $\sqrt2$ não é fração
Suponha $\sqrt2=\dfrac pq$ com $\dfrac pq$ irredutível. Então $p^2=2q^2$, logo $p^2$ é par, logo $p$ é par: $p=2k$. Substituindo, $4k^2=2q^2\Rightarrow q^2=2k^2$, e $q$ também é par. Mas então $p$ e $q$ têm fator 2 em comum, contradizendo "irredutível". Portanto $\sqrt2\notin\mathbb Q$. (Esse é o modelo de **demonstração por absurdo**.)

## A reta real e a ordem
Os reais ficam em correspondência com os pontos de uma reta. Para $a<b$: $a$ está à esquerda de $b$. Propriedades da ordem usadas em inequações:
- $a<b\Rightarrow a+c<b+c$
- $a<b$ e $c>0\Rightarrow ac<bc$
- $a<b$ e $c<0\Rightarrow ac>bc$ (**o sentido inverte!**)

## Intervalos
| Notação | Significado | Na reta |
|---|---|---|
| $[a,b]$ | $a\le x\le b$ | bolinha **cheia** nos dois extremos |
| $(a,b)$ | $a<x<b$ | bolinha **aberta** nos dois |
| $[a,b)$ | $a\le x<b$ | cheia em $a$, aberta em $b$ |
| $[a,+\infty)$ | $x\ge a$ | cheia em $a$, vai ao infinito |
| $(-\infty,b)$ | $x<b$ | aberta em $b$ |

$\pm\infty$ **nunca** entra com colchete (não é número).

### União e interseção
- $[1,5]\cap[3,8]=[3,5]$ (o que está nos dois)
- $[1,3)\cup[2,6]=[1,6]$ (o que está em pelo menos um)
- $(-\infty,2)\cap(0,+\infty)=(0,2)$

## Erros comuns
- Escrever $\sqrt2=1{,}41$ como se fosse igualdade (é aproximação).
- Usar colchete em $\infty$.
- Esquecer de inverter a desigualdade ao multiplicar por negativo.
- Achar que $\mathbb Z$ contém frações como $\tfrac12$.

## Conexões
[[Álgebra - Índice]] · [[Operações, Frações e Propriedades]] · [[Inequações e Estudo de Sinal]] · [[Funções - visão geral]] (domínio e imagem são intervalos)
