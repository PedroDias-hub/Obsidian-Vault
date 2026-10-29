# Registradores

## O que são
Registradores são **pequenos espaços de armazenamento dentro da própria CPU** — não é RAM, é memória fisicamente dentro do processador. Por isso são absurdamente mais rápidos de acessar que a RAM (ordens de grandeza), mas também extremamente limitados em quantidade (poucos, cada um com 64 bits em x86-64).

Quase toda operação em assembly acontece **entre registradores**, ou entre um registrador e a memória — a CPU não "opera direto na RAM" na maioria dos casos; ela primeiro traz o dado para um registrador, opera, e depois (se precisar) manda o resultado de volta pra memória.

## Os registradores de propósito geral (x86-64)
| 64 bits | 32 bits | 16 bits | 8 bits | Uso convencional |
|---|---|---|---|---|
| `RAX` | `EAX` | `AX` | `AL` | Acumulador — resultados de operações, valor de retorno de função |
| `RBX` | `EBX` | `BX` | `BL` | Base — uso geral |
| `RCX` | `ECX` | `CX` | `CL` | Contador — usado em loops (`loop`), deslocamentos de bits |
| `RDX` | `EDX` | `DX` | `DL` | Dados — uso geral, divisão/multiplicação estendida |
| `RSI` | `ESI` | `SI` | `SIL` | Source Index — origem em operações com strings/blocos de memória |
| `RDI` | `EDI` | `DI` | `DIL` | Destination Index — destino em operações com strings/blocos |
| `RBP` | `EBP` | `BP` | `BPL` | Base Pointer — referencia o início do frame da função atual |
| `RSP` | `ESP` | `SP` | `SPL` | Stack Pointer — aponta pro topo da pilha |
| `R8`–`R15` | `R8D`–`R15D` | `R8W`–`R15W` | `R8B`–`R15B` | Registradores extras (só existem em 64 bits) |

## A hierarquia de tamanhos — um ponto que confunde muita gente
`RAX`, `EAX`, `AX`, `AL` **não são 4 registradores diferentes** — são o **mesmo espaço físico**, visto com tamanhos diferentes:

```
RAX (64 bits)
┌───────────────────────────────┐
│              EAX (32 bits)    │
│              ┌────────────────┤
│              │    AX (16 bits)│
│              │    ┌───────────┤
│              │    │ AH  │  AL │  ← AH = byte alto, AL = byte baixo
└──────────────┴────┴─────┴─────┘
```

Isso significa: se você escreve `mov al, 5`, só o byte mais baixo de `RAX` muda — o resto do registrador fica como estava. Já `mov eax, 5` **zera automaticamente** a parte alta de `RAX` (comportamento específico de x86-64 ao escrever em um registrador de 32 bits).

## Registradores especiais

### `RIP` — Instruction Pointer
Aponta para o endereço de memória da **próxima instrução** a ser executada. Você não manipula `RIP` diretamente com `mov` — ele muda como efeito colateral de instruções de salto (`jmp`, `call`, `je`, etc). É literalmente o "estamos aqui" do ciclo fetch-decode-execute.

### `RFLAGS` — registrador de flags
Um registrador onde cada **bit individual** guarda o resultado de uma condição da última operação (foi zero? deu overflow? foi negativo?). Fundamental para saltos condicionais — ver [[../01_Linguagem/Flags_E_Comparacoes|Flags e comparações]].

### `RSP` e `RBP` merecem nota à parte
Tecnicamente são "de propósito geral", mas na prática são quase sempre reservados para gerenciar a pilha (stack) — ver [[../01_Linguagem/Stack_Pilha|A pilha]].

## Registradores de ponto flutuante e vetoriais
x86-64 tem um conjunto separado de registradores para números de ponto flutuante e operações vetoriais: `XMM0`–`XMM15` (128 bits, usados por SSE), `YMM0`–`YMM15` (256 bits, AVX), `ZMM0`–`ZMM31` (512 bits, AVX-512). Esses não fazem parte dos registradores "de propósito geral" e são usados por instruções específicas — ver [[../04_Avancado/SIMD|SIMD e vetorização]].

## Por que só uns poucos registradores?
Espaço físico no chip é caro, e cada registrador extra custa área e complexidade de decodificação. É justamente por isso que a pilha e a memória RAM existem como "extensão" — quando os registradores acabam, os dados vão pra memória (mais lenta, mas praticamente ilimitada).

## Ver também
- [[Memoria_E_Enderecamento|Memória e endereçamento]]
- [[../01_Linguagem/Instrucoes_De_Movimentacao|Instruções de movimentação de dados]]
- [[../01_Linguagem/Flags_E_Comparacoes|Flags e comparações]]
