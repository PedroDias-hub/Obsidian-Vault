# ARM vs. x86 vs. RISC-V — Comparação Detalhada

Agora que os fundamentos de x86-64 estão firmes, vale ver como os mesmos conceitos aparecem (com outra roupagem) em outras arquiteturas — principalmente porque ARM está cada vez mais presente (Apple Silicon, celulares, servidores em nuvem).

## A mesma soma simples, nas três arquiteturas
C: `c = a + b;`, com `a`, `b`, `c` já em registradores.

**x86-64 (Intel syntax)** — pode operar direto com um dos operandos vindo de memória, se precisar:
```asm
mov eax, [a]
add eax, [b]
mov [c], eax
```

**ARM (AArch64)** — arquitetura *load-store*: instruções aritméticas só operam entre registradores, nunca direto com memória:
```asm
ldr w0, [a]      ; load — traz "a" da memória pro registrador w0
ldr w1, [b]        ; load — traz "b" pro registrador w1
add w2, w0, w1       ; soma acontece só entre registradores (3 operandos!)
str w2, [c]            ; store — escreve o resultado de volta na memória
```

**RISC-V** — mesmíssima filosofia load-store do ARM, sintaxe um pouco diferente:
```asm
lw t0, 0(a0)       ; load word
lw t1, 0(a1)
add t2, t0, t1        ; soma só entre registradores
sw t2, 0(a2)             ; store word
```

## Diferenças estruturais principais

| | x86-64 | ARM (AArch64) | RISC-V |
|---|---|---|---|
| Filosofia | CISC | RISC | RISC |
| Tamanho das instruções | Variável | Fixo (4 bytes) | Fixo (4 bytes, ou 2 no modo comprimido) |
| Aritmética direto com memória? | Sim | Não (load-store) | Não (load-store) |
| Nº de operandos em `add` | 2 (`add dst, src` — dst também é operando) | 3 (`add dst, src1, src2` — separados) | 3 (igual ARM) |
| Registradores de propósito geral | 16 | 31 | 32 |
| Convenção de chamada (1º arg) | `RDI` | `X0` | `a0` |
| Nome do stack pointer | `RSP` | `SP` | `sp` |
| Instrução de retorno | `ret` | `ret` (na prática, `br x30`) | `ret` (na prática, `jalr x0, ra, 0`) |

## Por que instruções de 3 operandos (ARM/RISC-V) são "mais limpas"
Em x86, `add eax, ebx` sobrescreve `eax` — o valor original de `eax` se perde. Em ARM, `add w2, w0, w1` guarda o resultado num terceiro registrador separado, preservando `w0` e `w1` intactos. Isso é uma consequência direta da filosofia RISC: instruções mais previsíveis e uniformes, ao custo de precisar de mais registradores (por isso ARM e RISC-V têm bem mais registradores de propósito geral que x86).

## O que muda ao migrar mentalmente de x86 pra ARM
Se você já entendeu bem tudo neste vault, migrar pra ARM significa reaprender:
- Os nomes dos registradores (`X0`-`X30` em vez de `RAX`-`R15`).
- Que toda instrução aritmética/lógica só trabalha com registradores — memória exige `ldr`/`str` explícito.
- A convenção de chamada específica (AAPCS64 no lugar da System V AMD64 ABI).

Mas os **conceitos** — pilha crescendo pra baixo, endereço de retorno guardado ao chamar função, flags atualizadas por comparações, saltos condicionais, prólogo/epílogo de função — são exatamente os mesmos. É por isso que vale a pena aprender x86 (ou qualquer arquitetura) a fundo primeiro: o transporte de conhecimento pra outra ISA é muito mais rápido do que aprender do zero.

## Ver também
- [[../00_Fundamentos/Arquiteturas_e_ISAs|Arquiteturas e ISAs]]
- [[../01_Linguagem/Funcoes_E_Convencoes_De_Chamada|Funções e convenções de chamada]]
