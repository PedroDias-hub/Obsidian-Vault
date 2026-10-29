# Flags e Comparações

## O registrador RFLAGS
Depois de (quase) toda instrução aritmética ou lógica, a CPU atualiza automaticamente um conjunto de **bits de estado** dentro do registrador `RFLAGS`. Cada bit responde a uma pergunta sobre o resultado da última operação. São essas flags que permitem tomar decisões (`if`, `while`) em assembly.

## As flags mais importantes
| Flag | Nome | Significado |
|---|---|---|
| **ZF** | Zero Flag | Ligada (1) se o resultado da última operação foi **zero** |
| **SF** | Sign Flag | Ligada se o resultado foi **negativo** (bit mais significativo = 1) |
| **CF** | Carry Flag | Ligada se houve "vai um"/"empresta um" — usado em aritmética **sem sinal** |
| **OF** | Overflow Flag | Ligada se o resultado **estourou** a capacidade do tipo com sinal (ex: somar dois positivos grandes e "virar" negativo) |

## `cmp` — a instrução de comparação
```asm
cmp rax, rbx
```
Isso faz **internamente a mesma conta que `sub rax, rbx`** (RAX - RBX), só que **descarta o resultado** — o único efeito é atualizar as flags. É assim que a CPU "sabe" se RAX é maior, menor ou igual a RBX: olhando as flags depois desse subtração descartada.

## `test` — comparação bit a bit
```asm
test rax, rax
```
Faz internamente um `and rax, rax`, descartando o resultado, só atualizando flags. `test rax, rax` é a forma idiomática de perguntar **"RAX é zero?"** (se for, ZF fica ligada) — muito mais comum do que `cmp rax, 0`.

## Como as flags viram decisões: saltos condicionais
Depois de um `cmp`, um salto condicional (`jXX`) olha as flags e decide se pula ou não. A tabela completa está em [[Saltos_E_Estruturas_De_Controle|Saltos e estruturas de controle]], mas os pares mais usados:

| Depois de `cmp a, b` | Salta se... | Instrução |
|---|---|---|
| igual | `a == b` | `je` |
| diferente | `a != b` | `jne` |
| maior (sem sinal) | `a > b` | `ja` |
| maior (com sinal) | `a > b` | `jg` |
| menor (sem sinal) | `a < b` | `jb` |
| menor (com sinal) | `a < b` | `jl` |

## Por que existe "com sinal" e "sem sinal" separados
Isso é um dos pontos mais sutis de x86: a CPU não sabe, olhando os bits crus, se um valor é "um número negativo" ou "um número positivo muito grande" — ela só sabe os bits. É o **programa** (ou o assembly gerado pelo compilador) que decide qual interpretação faz sentido, escolhendo `ja`/`jb` (sem sinal, baseadas em `CF`) ou `jg`/`jl` (com sinal, baseadas em `SF` e `OF`) de acordo com o tipo da variável original (`unsigned int` vs `int`, por exemplo).

## Exemplo completo
```asm
mov rax, 10
mov rbx, 20
cmp rax, rbx      ; calcula RAX - RBX = -10 (descartado), atualiza flags
jl  rax_menor     ; ZF/SF/OF dizem que RAX < RBX (com sinal) → salta

; código se RAX >= RBX (não executa neste exemplo)
jmp fim

rax_menor:
; código se RAX < RBX (este é o executado)

fim:
```

## Ver também
- [[Saltos_E_Estruturas_De_Controle|Saltos e estruturas de controle]]
- [[Instrucoes_Aritmeticas_E_Logicas|Instruções aritméticas e lógicas]]
