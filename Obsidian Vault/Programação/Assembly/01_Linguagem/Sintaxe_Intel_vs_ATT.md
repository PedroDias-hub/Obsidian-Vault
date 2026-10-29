# Sintaxe Intel vs. AT&T

A mesma instrução de máquina pode ser **escrita** de duas formas bem diferentes, dependendo da convenção. Isso é puramente cosmético — não muda o que o processador executa — mas é importante saber ler as duas, porque você vai encontrar as duas por aí (o Linux, por padrão, mostra AT&T em ferramentas como `objdump` e `gdb`, enquanto NASM e a documentação da Intel usam sintaxe Intel).

## As diferenças principais

| | Intel | AT&T |
|---|---|---|
| Ordem dos operandos | `destino, origem` | `origem, destino` |
| Prefixo de registrador | nenhum | `%` (ex: `%rax`) |
| Prefixo de valor imediato | nenhum | `$` (ex: `$5`) |
| Acesso à memória | `[rax + 4]` | `4(%rax)` |
| Sufixo de tamanho | tamanho explícito quando ambíguo (`mov dword [rax], 5`) | sufixo na instrução: `b`(byte) `w`(word) `l`(long/dword) `q`(quad) |

## Exemplo lado a lado
Mesma instrução — "mova o valor 5 para RAX":
```
Intel:   mov rax, 5
AT&T:    movq $5, %rax
```

Outra — "some o valor no endereço RBX+8 com RAX, guarde em RAX":
```
Intel:   add rax, [rbx + 8]
AT&T:    addq 8(%rbx), %rax
```

## Qual usar?
Este vault usa **sintaxe Intel** (a do NASM) por ser mais legível para quem está começando — a ordem "destino primeiro" combina com como a gente já lê `x = 5` em outras linguagens. Mas ao usar `objdump -d` ou `gdb` no Linux, o padrão costuma ser AT&T — dá pra forçar sintaxe Intel em ambos:
```bash
objdump -d -M intel arquivo.o
```
No GDB:
```
(gdb) set disassembly-flavor intel
```

## Ver também
- [[../02_Pratica/Ferramentas|Ferramentas]]
- [[Instrucoes_De_Movimentacao|Instruções de movimentação de dados]]
