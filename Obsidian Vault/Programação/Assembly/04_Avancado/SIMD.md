# SIMD e Vetorização

## O que é SIMD
**SIMD** = Single Instruction, Multiple Data. É a ideia de uma única instrução aplicar a **mesma operação a vários valores ao mesmo tempo**, em vez de um valor por vez.

Exemplo conceitual: somar dois arrays de 4 inteiros.
```
Escalar (normal):        SIMD:
a[0]+b[0]                [a0,a1,a2,a3] + [b0,b1,b2,b3]
a[1]+b[1]                        ↓ (1 instrução só)
a[2]+b[2]                [a0+b0, a1+b1, a2+b2, a3+b3]
a[3]+b[3]
(4 instruções)            (1 instrução)
```

## Os registradores SIMD em x86
São registradores separados dos de propósito geral, cada geração maior que a anterior:
| Conjunto | Registradores | Tamanho |
|---|---|---|
| **SSE** | `XMM0`–`XMM15` | 128 bits (ex: 4 floats de 32 bits, ou 2 doubles de 64 bits) |
| **AVX** | `YMM0`–`YMM15` | 256 bits (o dobro — 8 floats de uma vez) |
| **AVX-512** | `ZMM0`–`ZMM31` | 512 bits (16 floats de uma vez) |

## Exemplo de instrução SSE
```asm
movaps xmm0, [array1]    ; carrega 4 floats de uma vez em XMM0
movaps xmm1, [array2]    ; carrega mais 4 floats em XMM1
addps  xmm0, xmm1         ; soma os 4 pares simultaneamente
movaps [resultado], xmm0    ; guarda os 4 resultados de uma vez
```
(`addps` = "add packed single-precision" — soma 4 floats de 32 bits "empacotados" no registrador de uma vez.)

## Por que isso importa
Multiplicar matrizes, processar áudio/imagem, machine learning — tudo isso é, no fundo, fazer a **mesma conta simples repetidas vezes** sobre muitos dados. SIMD é uma das razões pelas quais código "vetorizado" pode ser 4x, 8x ou mais rápido que o equivalente escalar, sem mudar a frequência do processador.

## Você provavelmente já usa SIMD sem saber
Compiladores modernos (`gcc -O3`, por exemplo) tentam **auto-vetorizar** loops simples automaticamente — pegar um `for` somando um array e gerar instruções `addps`/`addpd` sozinhos, sem você escrever assembly nenhum. Isso é uma das grandes diferenças que aparecem ao comparar `-O0` com `-O3` — ver [[../03_Assembly_E_C/Lendo_Assembly_Do_Compilador|Lendo o assembly gerado por um compilador]].

## Onde isso aparece "por trás"
- Bibliotecas de álgebra linear (NumPy, BLAS) usam SIMD pesadamente por baixo.
- Codecs de vídeo/áudio.
- Engines de jogos (cálculos de vetores 3D/matrizes 4x4 mapeiam perfeitamente em registradores de 128 bits).

## Este é um tópico pra depois
SIMD tem suas próprias regras de alinhamento de memória, conjuntos de instruções concorrentes (SSE, SSE2, AVX, AVX2, AVX-512, cada um com instruções específicas), e não é o primeiro lugar pra começar. Mas vale saber que existe e o motivo de existir assim que os fundamentos (registradores comuns, memória, pilha) estiverem confortáveis.

## Ver também
- [[../00_Fundamentos/Registradores|Registradores]]
- [[../03_Assembly_E_C/Lendo_Assembly_Do_Compilador|Lendo o assembly gerado por um compilador]]
