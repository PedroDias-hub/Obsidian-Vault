# Seu Primeiro Programa: Hello World

## O código completo
```asm
; hello.asm
section .data
    msg db "Ola, mundo!", 10    ; texto + '\n' (10 = código ASCII de nova linha)
    tam equ $ - msg               ; calcula o tamanho da string automaticamente

section .text
    global _start

_start:
    ; syscall write(fd=1, buffer=msg, count=tam)
    mov rax, 1        ; número da syscall "write"
    mov rdi, 1          ; primeiro argumento: fd = 1 (stdout)
    mov rsi, msg         ; segundo argumento: endereço do buffer
    mov rdx, tam           ; terceiro argumento: quantidade de bytes
    syscall

    ; syscall exit(code=0)
    mov rax, 60         ; número da syscall "exit"
    mov rdi, 0            ; código de saída
    syscall
```

## Rodando de verdade (Linux, x86-64)
```bash
nasm -f elf64 hello.asm -o hello.o
ld hello.o -o hello
./hello
```
Saída esperada:
```
Ola, mundo!
```

## Dissecando linha por linha

**`msg db "Ola, mundo!", 10`** — define uma sequência de bytes na seção `.data`: os caracteres da string, seguidos do byte `10` (o caractere `\n`). Cada letra vira seu código ASCII automaticamente pelo NASM.

**`tam equ $ - msg`** — `$` significa "o endereço atual, aqui nesta linha". Subtraindo o endereço de `msg`, o resultado é exatamente o tamanho em bytes da string (incluindo o `\n`). Isso evita contar caracteres na mão (e recontar toda vez que o texto mudar).

**`global _start`** — declara `_start` como ponto de entrada visível para o linker. Diferente de programas em C, que começam em `main` (chamado por código de inicialização da libc por trás dos panos), um executável "cru" como este começa direto em `_start` — não existe nada rodando antes.

**As duas syscalls**: a primeira imprime o texto (ver [[../01_Linguagem/Chamadas_De_Sistema|Chamadas de sistema]] para a explicação completa de `write`); a segunda encerra o processo com `exit`. **Isso é essencial**: sem o `exit`, o processador continuaria "executando" o que vier depois na memória (lixo, ou a próxima seção), quase certamente causando um crash (`Segmentation fault`).

## Verificando o código de saída
```bash
./hello
echo $?    # mostra o código de saída do último comando — deve imprimir "0"
```

## Variação: sem usar `_start`, usando a libc e `main`
Se preferir integrar com C (por exemplo, para poder usar `printf` depois):
```asm
extern printf
section .data
    msg db "Ola, mundo!", 10, 0    ; agora termina com 0 (null-terminator), como toda string C

section .text
    global main

main:
    push rbp
    mov rbp, rsp

    lea rdi, [msg]     ; primeiro argumento de printf: o texto
    xor eax, eax          ; printf usa variádicos; eax = número de registradores XMM usados (0 aqui)
    call printf

    mov rsp, rbp
    pop rbp
    ret
```
Compilar com `gcc` (que já resolve o link com a libc):
```bash
nasm -f elf64 hello2.asm -o hello2.o
gcc hello2.o -o hello2 -no-pie
./hello2
```

## Ver também
- [[Ferramentas|Ferramentas]]
- [[../01_Linguagem/Chamadas_De_Sistema|Chamadas de sistema]]
- [[Exercicios|Exercícios progressivos]]
