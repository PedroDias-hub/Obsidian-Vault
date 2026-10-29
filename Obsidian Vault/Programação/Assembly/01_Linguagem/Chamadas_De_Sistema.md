# Chamadas de Sistema (Syscalls)

## O problema que syscalls resolvem
Um programa comum roda em **modo usuário** (user mode) — por segurança, ele não tem permissão de acessar hardware diretamente (disco, tela, rede). Só o **kernel** do sistema operacional roda em **modo privilegiado** (kernel mode) e pode fazer isso de fato. Uma **syscall** é o mecanismo formal para um programa em modo usuário pedir ao kernel para fazer algo em seu nome — abrir um arquivo, escrever na tela, alocar memória, etc.

## Como funciona no Linux x86-64
1. Você coloca o **número da syscall** desejada em `RAX`.
2. Coloca os argumentos da syscall em `RDI`, `RSI`, `RDX`, `R10`, `R8`, `R9` (nessa ordem — repare que é quase igual à convenção de chamada normal, exceto que o 4º argumento vai em `R10`, não `RCX`).
3. Executa a instrução `syscall`.
4. O kernel processa o pedido e devolve o resultado em `RAX`.

```asm
mov rax, numero_da_syscall
mov rdi, arg1
mov rsi, arg2
mov rdx, arg3
syscall
```

## Syscalls mais usadas para começar (Linux x86-64)
| Número (RAX) | Nome | O que faz | Argumentos (RDI, RSI, RDX...) |
|---|---|---|---|
| 0 | `read` | lê de um descritor de arquivo | fd, buffer, tamanho |
| 1 | `write` | escreve em um descritor de arquivo | fd, buffer, tamanho |
| 2 | `open` | abre um arquivo | caminho, flags, modo |
| 3 | `close` | fecha um descritor de arquivo | fd |
| 60 | `exit` | encerra o programa | código de saída |

## Exemplo: escrever texto na tela (`write`)
```asm
section .data
    msg db "Ola, mundo!", 10   ; 10 = '\n'
    tam equ $ - msg              ; $ = endereço atual; calcula o tamanho da string

section .text
    global _start

_start:
    mov rax, 1        ; syscall write
    mov rdi, 1          ; fd = 1 → stdout (saída padrão)
    mov rsi, msg         ; endereço do texto
    mov rdx, tam          ; quantidade de bytes
    syscall

    mov rax, 60         ; syscall exit
    mov rdi, 0            ; código de saída 0 (sucesso)
    syscall
```

Esse é, essencialmente, o "Hello World" mais puro possível — sem depender de nenhuma biblioteca C, só o kernel diretamente. Ver [[../02_Pratica/Primeiro_Programa|Seu primeiro programa]] para rodar isso de verdade.

## Descritores de arquivo padrão
```
0 → stdin  (entrada padrão)
1 → stdout (saída padrão)
2 → stderr (saída de erro)
```
Esses três já existem automaticamente para qualquer processo — não precisa "abrir" pra usar.

## Syscall direta vs. usando a libc (`printf`, `malloc`, etc)
Você pode chamar syscalls diretamente (como acima) ou usar funções da **libc** (biblioteca padrão C, como `printf`) — que, por baixo, **também acabam fazendo syscalls**, só que com muito mais conveniência (formatação de string, buffers, tratamento de erro) por cima. Programas em C sempre passam pela libc; assembly "puro" pode escolher ir direto no kernel, como no exemplo acima.

## `int 0x80` vs. `syscall` — uma nota histórica
Em sistemas 32 bits antigos, syscalls eram feitas com a instrução `int 0x80` (uma interrupção de software). Em x86-64, existe a instrução dedicada `syscall`, mais rápida — é o padrão a ser usado hoje. Você ainda pode encontrar `int 0x80` em material antigo ou em código 32 bits.

## Ver também
- [[../02_Pratica/Primeiro_Programa|Seu primeiro programa]]
- [[Funcoes_E_Convencoes_De_Chamada|Funções e convenções de chamada]]
