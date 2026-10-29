# Instruções Aritméticas e Lógicas

## Aritméticas básicas
```asm
add rax, rbx      ; RAX = RAX + RBX
sub rax, rbx      ; RAX = RAX - RBX
inc rax           ; RAX = RAX + 1
dec rax           ; RAX = RAX - 1
neg rax           ; RAX = -RAX (complemento de dois)
```
Repare no padrão: em x86, a maioria das instruções aritméticas segue `instrucao destino, origem`, e o **resultado sobrescreve o destino** (não existe um terceiro operando "resultado" separado, diferente de linguagens de alto nível onde `c = a + b` guarda em `c` sem mexer em `a` ou `b`).

## Multiplicação
```asm
mul rbx      ; multiplicação SEM sinal (unsigned): RDX:RAX = RAX * RBX
imul rbx     ; multiplicação COM sinal (signed)
imul rax, rbx           ; forma de 2 operandos: RAX = RAX * RBX
imul rax, rbx, 5         ; forma de 3 operandos: RAX = RBX * 5
```
Repare em algo importante: `mul`/`imul` de um operando produz um resultado **de 128 bits**, guardado em dois registradores juntos: a parte alta em `RDX`, a parte baixa em `RAX` (notação `RDX:RAX`). Isso existe porque multiplicar dois números de 64 bits pode gerar um resultado que não cabe em 64 bits.

## Divisão
```asm
div rbx      ; divisão SEM sinal: RAX = RDX:RAX / RBX,  RDX = resto
idiv rbx     ; divisão COM sinal
```
Antes de dividir, é preciso preparar `RDX:RAX` como o dividendo de 128 bits. Pra dividir um número comum de 64 bits, zera-se (ou estende o sinal de) `RDX` antes:
```asm
mov rax, 100
cqo              ; estende o sinal de RAX para RDX:RAX (sign-extend, específico para divisão com sinal)
mov rbx, 7
idiv rbx         ; RAX = 100 / 7 = 14 ;  RDX = 100 % 7 = 2
```
Esse é o motivo de, ao compilar `a / b` e `a % b` em C, o assembly gerado frequentemente calcular os dois juntos — a instrução `div`/`idiv` já devolve quociente **e** resto de graça.

## Lógicas bit a bit
```asm
and rax, rbx    ; E lógico bit a bit
or  rax, rbx    ; OU lógico bit a bit
xor rax, rbx    ; OU exclusivo bit a bit
not rax         ; inverte todos os bits (complemento de um)
```

### O truque clássico: `xor rax, rax`
Zerar um registrador com `xor rax, rax` é mais rápido (e usa menos bytes de código de máquina) do que `mov rax, 0` — qualquer valor com ele mesmo via XOR sempre dá zero. É tão comum que compiladores fazem essa otimização sozinhos.

## Deslocamento de bits (shift)
```asm
shl rax, 1      ; shift left  — desloca bits para a esquerda (equivale a multiplicar por 2)
shr rax, 1      ; shift right — desloca para a direita, SEM sinal (equivale a dividir por 2, unsigned)
sar rax, 1      ; shift right ARITMÉTICO — preserva o bit de sinal (para divisão com sinal)
```
Diferença crucial entre `shr` e `sar`: `shr` sempre preenche com 0 pela esquerda; `sar` preenche repetindo o bit de sinal — importante para números negativos em complemento de dois.

## Rotação
```asm
rol rax, 1      ; rotaciona bits para a esquerda (o bit que "sai" de um lado entra do outro)
ror rax, 1      ; rotaciona para a direita
```

## Por que aprender essas instruções "de baixo nível"
Operações bit a bit e shifts são a base de: manipulação de flags/máscaras, criptografia, compressão, otimizações (multiplicar/dividir por potências de 2 via shift é muito mais rápido que `mul`/`div`), e leitura de protocolos binários.

## Ver também
- [[../00_Fundamentos/Sistema_Binario_E_Hexadecimal|Sistema binário e hexadecimal]]
- [[Flags_E_Comparacoes|Flags e comparações]]
