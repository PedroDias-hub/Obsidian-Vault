# Debugando com GDB

GDB permite executar seu programa **instrução por instrução**, inspecionando registradores, flags, memória e a pilha em tempo real. Para quem está aprendendo assembly, isso é ainda mais valioso do que para código de alto nível — é a forma mais direta de *ver* o que cada instrução realmente faz.

## Compilando com símbolos de debug
```bash
nasm -f elf64 -g programa.asm -o programa.o    # -g inclui informação de debug
ld programa.o -o programa
```

## Iniciando
```bash
gdb ./programa
```
Primeira coisa a fazer, sempre — usar sintaxe Intel (mais fácil de acompanhar vindo do NASM):
```
(gdb) set disassembly-flavor intel
```

## Comandos essenciais

| Comando | Atalho | O que faz |
|---|---|---|
| `break _start` | `b _start` | Coloca um breakpoint no label `_start` |
| `run` | `r` | Inicia a execução até o próximo breakpoint |
| `stepi` | `si` | Executa **uma instrução de assembly** e para |
| `nexti` | `ni` | Como `stepi`, mas não entra dentro de `call` (pula a função inteira) |
| `continue` | `c` | Continua até o próximo breakpoint |
| `info registers` | `i r` | Mostra todos os registradores e seus valores |
| `print $rax` | `p $rax` | Mostra o valor de um registrador específico |
| `x/10xb $rsp` | — | Examina memória — ver abaixo |
| `disassemble` | `disas` | Mostra o assembly da função atual |

## Examinando memória com `x`
A sintaxe é `x/NFU endereço`:
- **N**: quantas unidades mostrar
- **F**: formato (`x`=hex, `d`=decimal, `s`=string, `i`=instrução)
- **U**: tamanho da unidade (`b`=byte, `h`=halfword/2bytes, `w`=word/4bytes, `g`=giant/8bytes)

```
(gdb) x/10xb $rsp     ; mostra 10 bytes, em hex, a partir do topo da pilha
(gdb) x/4xg $rsp       ; mostra 4 qwords (8 bytes cada), em hex
(gdb) x/s msg            ; mostra a string apontada por "msg" (label do .data)
(gdb) x/5i $rip           ; mostra as próximas 5 instruções a partir do RIP atual
```

## Um roteiro de debug típico
```
(gdb) set disassembly-flavor intel
(gdb) break _start
(gdb) run
(gdb) disas                    ; ver o assembly da função atual, com uma seta "=>" na instrução atual
(gdb) stepi                    ; avança uma instrução
(gdb) info registers rax rdi rsi  ; olha só os registradores que interessam agora
(gdb) stepi
(gdb) x/4xg $rsp                ; espia o topo da pilha
```

## Vendo as flags
```
(gdb) info registers eflags
```
GDB mostra as flags ativas de forma legível, tipo `[ ZF PF ]` (indicando que Zero Flag e Parity Flag estão ligadas).

## `layout asm` e `layout regs` — modo TUI
GDB tem uma interface de texto que deixa tudo visível ao mesmo tempo:
```
(gdb) layout asm      ; mostra o assembly sendo executado, com destaque na linha atual
(gdb) layout regs      ; adiciona um painel com todos os registradores, atualizados a cada step
```
Depois disso, `stepi`/`nexti` atualizam a tela inteira automaticamente — é de longe a forma mais didática de acompanhar execução.

## Ver também
- [[Ferramentas|Ferramentas]]
- [[Exercicios|Exercícios progressivos]]
