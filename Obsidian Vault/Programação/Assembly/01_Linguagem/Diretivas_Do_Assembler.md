# Diretivas do Assembler

Diretivas não são instruções de CPU — são **comandos para o assembler** (o programa que monta seu código, o NASM). Elas organizam o programa, mas não geram (diretamente) código de máquina executado em runtime.

## Estrutura básica de um arquivo NASM
```asm
section .data
    ; variáveis inicializadas (com valor definido)

section .bss
    ; variáveis não inicializadas (só reservam espaço)

section .text
    global _start   ; ponto de entrada visível pro linker

_start:
    ; instruções do programa
```

## `section .data`
Onde ficam valores **inicializados** — constantes e variáveis globais com valor definido desde o início:
```asm
section .data
    mensagem db "Ola, mundo!", 0    ; db = define byte(s)
    numero   dd 42                   ; dd = define dword (4 bytes)
    valor64  dq 1000000               ; dq = define qword (8 bytes)
```

Diretivas de definição de dados:
| Diretiva | Tamanho | Nome |
|---|---|---|
| `db` | 1 byte | define byte |
| `dw` | 2 bytes | define word |
| `dd` | 4 bytes | define dword |
| `dq` | 8 bytes | define qword |

## `section .bss`
Onde ficam variáveis **não inicializadas** — só reserva espaço, sem gastar espaço no arquivo executável com valores (o SO zera essa área ao carregar o programa):
```asm
section .bss
    buffer resb 64    ; resb = reserva 64 bytes
    contador resq 1   ; resq = reserva 1 qword (8 bytes)
```

## `section .text`
Onde fica o **código** — as instruções de fato executadas.

## `global` e `extern`
- `global nome`: torna um símbolo (label) visível para o *linker* — necessário para o ponto de entrada (`_start`) e para funções que outros arquivos vão chamar.
- `extern nome`: declara que um símbolo é definido em *outro* arquivo/biblioteca (ex: `extern printf` para usar a `printf` da libc).

```asm
extern printf
global main
```

## Labels (rótulos)
Um label marca um endereço com um nome, usado tanto para dados quanto para pontos do código que você quer "pular para" (ver [[Saltos_E_Estruturas_De_Controle|saltos]]):
```asm
loop_inicio:
    ; código aqui
    jmp loop_inicio     ; salta de volta pro label
```

## Comentários
```asm
; tudo depois de ponto-e-vírgula é comentário, até o fim da linha
mov rax, 5   ; isso também é comentário
```

## Constantes com `equ`
```asm
TAMANHO equ 64
...
mov rcx, TAMANHO    ; o assembler substitui TAMANHO por 64 antes de montar
```
Diferente de uma variável, `equ` não ocupa espaço em memória — é substituição textual em tempo de montagem, mais parecido com um `#define` de C.

## Ver também
- [[../02_Pratica/Primeiro_Programa|Seu primeiro programa]]
- [[../00_Fundamentos/Memoria_E_Enderecamento|Memória e endereçamento]]
