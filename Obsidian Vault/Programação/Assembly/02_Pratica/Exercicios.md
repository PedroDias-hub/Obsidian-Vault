# Exercícios Progressivos

Vá na ordem — cada bloco assume o anterior. Monte, rode e (principalmente) debugue cada um no GDB antes de olhar a resposta. As respostas trazem o código completo, mas o objetivo é você chegar lá sozinho(a) primeiro.

## Bloco 1 — Movimentação e aritmética básica

**1.** Escreva um programa que coloque o valor 15 em `RAX`, some 10, e termine com `exit` usando o valor final de `RAX` como código de saída.
> [!success]- Resposta
> ```asm
> section .text
>     global _start
> _start:
>     mov rax, 15
>     add rax, 10
>     mov rdi, rax
>     mov rax, 60
>     syscall
> ```
> Confira com `echo $?` depois de rodar — deve mostrar 25.

**2.** Troque os valores de `RAX` e `RBX` usando `xchg`, começando com `RAX=1` e `RBX=2`. Confirme no GDB que trocaram.
> [!success]- Resposta
> ```asm
> mov rax, 1
> mov rbx, 2
> xchg rax, rbx    ; agora RAX=2, RBX=1
> ```

**3.** Calcule `(5 + 3) * 2` inteiramente em registradores (sem usar memória), guardando o resultado em `RCX`.
> [!success]- Resposta
> ```asm
> mov rax, 5
> add rax, 3
> mov rcx, rax
> imul rcx, 2      ; RCX = 16
> ```

**4.** Some os valores de `RAX` e `RBX` usando **apenas** `xor`, `and` e `shl` (sem usar `add`) — é possível, mas trabalhoso; é só para forçar entender bit a bit. (Dica: pesquise "adição binária com portas lógicas" se travar — é um exercício conceitual, não algo que se escreve de cabeça.)
> [!success]- Resposta
> Esse é avançado de propósito — a ideia central é que soma binária pode ser feita com `xor` (soma sem considerar "vai um") e `and` + `shl` (calculando o "vai um" e aplicando na posição seguinte), repetindo até não sobrar "vai um". Na prática, ninguém implementa assim — é só para internalizar que `add` "esconde" esse processo. Se quiser ver isso implementado, pesquise "adder using xor and and assembly".

**5.** Use `xor rax, rax` para zerar `RAX`, depois confira no GDB (`info registers rax`) que o valor é 0.
> [!success]- Resposta
> ```asm
> mov rax, 123
> xor rax, rax     ; RAX = 0
> ```
> No GDB: `break` antes do xor, `stepi`, `info registers rax` antes e depois pra comparar.

## Bloco 2 — Memória e endereçamento

**1.** Declare uma variável `numero dd 42` em `.data` e escreva código que a leia para `EAX`.
> [!success]- Resposta
> ```asm
> section .data
>     numero dd 42
> section .text
>     global _start
> _start:
>     mov eax, [numero]
>     mov rdi, rax
>     mov rax, 60
>     syscall
> ```

**2.** Declare um array de 5 inteiros de 32 bits em `.data` e leia o **terceiro** elemento (índice 2) para `EAX`, usando endereçamento base+índice.
> [!success]- Resposta
> ```asm
> section .data
>     array dd 10, 20, 30, 40, 50
> section .text
>     global _start
> _start:
>     mov rbx, array
>     mov eax, [rbx + 2*4]    ; índice 2, cada elemento = 4 bytes
>     ; EAX = 30
>     mov rdi, rax
>     mov rax, 60
>     syscall
> ```

**3.** Repita o exercício acima, mas use um registrador como índice variável (simulando `array[i]` com `i` em `RCX`).
> [!success]- Resposta
> ```asm
> mov rcx, 2            ; i = 2
> mov eax, [array + rcx*4]
> ```

**4.** Use `lea` para calcular o endereço do quarto elemento do array (sem ler seu valor), guardando o endereço em `RDX`.
> [!success]- Resposta
> ```asm
> lea rdx, [array + 3*4]   ; RDX = endereço de array[3], NÃO o valor
> ```

**5.** Escreva o valor 99 diretamente no segundo elemento do array (sem passar por um registrador intermediário).
> [!success]- Resposta
> ```asm
> mov dword [array + 1*4], 99
> ```

## Bloco 3 — Saltos e estruturas de controle

**1.** Escreva um programa que compare `RAX=5` e `RBX=8`, e finalize com código de saída 1 se `RAX < RBX`, ou 0 caso contrário.
> [!success]- Resposta
> ```asm
> mov rax, 5
> mov rbx, 8
> cmp rax, rbx
> jl menor
> mov rdi, 0
> jmp fim
> menor:
> mov rdi, 1
> fim:
> mov rax, 60
> syscall
> ```

**2.** Implemente um loop que some os números de 1 a 10 e termine com esse total como código de saída.
> [!success]- Resposta
> ```asm
> mov rax, 0      ; soma
> mov rcx, 1        ; i
> loop_inicio:
> cmp rcx, 10
> jg loop_fim
> add rax, rcx
> inc rcx
> jmp loop_inicio
> loop_fim:
> mov rdi, rax     ; deve ser 55
> mov rax, 60
> syscall
> ```

**3.** Reimplemente o exercício acima usando a instrução `loop` (com `RCX` como contador regressivo de 10 até 1).
> [!success]- Resposta
> ```asm
> mov rax, 0
> mov rbx, 1        ; próximo valor a somar
> mov rcx, 10        ; contador do loop
> repete:
> add rax, rbx
> inc rbx
> loop repete
> mov rdi, rax     ; 55
> mov rax, 60
> syscall
> ```

**4.** Escreva um programa que percorra o array `dd 3, -1, 7, -5, 2` e conte quantos elementos são negativos, guardando a contagem no código de saída.
> [!success]- Resposta
> ```asm
> section .data
>     array dd 3, -1, 7, -5, 2
> section .text
>     global _start
> _start:
>     mov rcx, 0            ; contador de negativos
>     mov rsi, 0              ; índice
> loop_check:
>     cmp rsi, 5
>     jge fim
>     mov eax, [array + rsi*4]
>     cmp eax, 0
>     jge nao_negativo
>     inc rcx
> nao_negativo:
>     inc rsi
>     jmp loop_check
> fim:
>     mov rdi, rcx        ; deve ser 2
>     mov rax, 60
>     syscall
> ```

**5.** Implemente um `if/elif/else` em assembly: se `RAX == 0` sai com código 1; se `RAX < 0` sai com código 2; caso contrário (`RAX > 0`) sai com código 3.
> [!success]- Resposta
> ```asm
> mov rax, 5    ; teste com valores diferentes
> cmp rax, 0
> je caso_zero
> jl caso_negativo
> mov rdi, 3     ; caso positivo
> jmp fim
> caso_zero:
> mov rdi, 1
> jmp fim
> caso_negativo:
> mov rdi, 2
> fim:
> mov rax, 60
> syscall
> ```

## Bloco 4 — Funções e a pilha

**1.** Escreva uma função `dobro` que recebe um valor em `RDI` e retorna o dobro em `RAX`, chamada a partir de `_start`.
> [!success]- Resposta
> ```asm
> section .text
>     global _start
> _start:
>     mov rdi, 21
>     call dobro
>     mov rdi, rax     ; código de saída = resultado
>     mov rax, 60
>     syscall
> dobro:
>     mov rax, rdi
>     imul rax, 2
>     ret
> ```

**2.** Escreva uma função `soma3` que recebe 3 argumentos (`RDI`, `RSI`, `RDX`) e retorna a soma dos três.
> [!success]- Resposta
> ```asm
> soma3:
>     mov rax, rdi
>     add rax, rsi
>     add rax, rdx
>     ret
> ```

**3.** Implemente uma função `fatorial` recursiva (recebe `n` em `RDI`, retorna `n!` em `RAX`). Use `push`/`pop` para preservar o `RDI` original ao longo da recursão.
> [!success]- Resposta
> ```asm
> fatorial:
>     cmp rdi, 1
>     jle caso_base
>     push rdi              ; preserva n antes da chamada recursiva
>     dec rdi
>     call fatorial          ; RAX = (n-1)!
>     pop rdi                 ; recupera n
>     imul rax, rdi           ; RAX = n * (n-1)!
>     ret
> caso_base:
>     mov rax, 1
>     ret
> ```

**4.** Escreva uma função que usa uma variável local na pilha (prólogo/epílogo completo): recebe `RDI`, guarda `RDI*2` numa variável local `[rbp-8]`, depois retorna essa variável local somada a 1.
> [!success]- Resposta
> ```asm
> minha_funcao:
>     push rbp
>     mov rbp, rsp
>     sub rsp, 16          ; reserva espaço (16 pra manter alinhamento)
>
>     mov rax, rdi
>     imul rax, 2
>     mov [rbp-8], rax    ; variável local
>
>     mov rax, [rbp-8]
>     add rax, 1
>
>     mov rsp, rbp
>     pop rbp
>     ret
> ```

**5.** Escreva uma função `eh_par` que recebe um número e retorna 1 (em RAX) se for par, 0 se for ímpar, usando `and` com máscara de bit (sem usar `div`/`mod`).
> [!success]- Resposta
> ```asm
> eh_par:
>     mov rax, rdi
>     and rax, 1       ; isola o bit menos significativo
>     xor rax, 1        ; inverte: se era 0 (par), vira 1; se era 1 (ímpar), vira 0
>     ret
> ```

## Bloco 5 — Para ir além
Depois desses, os próximos desafios naturais são: implementar um `strlen` manual (contar bytes até achar `0`), implementar uma busca linear num array, e escrever uma função que recebe uma string e a inverte no lugar. Nenhum conceito novo é necessário — é praticar combinar tudo que já apareceu aqui.

## Ver também
- [[../01_Linguagem/Funcoes_E_Convencoes_De_Chamada|Funções e convenções de chamada]]
- [[Debug_Com_GDB|Debugando com GDB]]
