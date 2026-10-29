# Saltos e Estruturas de Controle

Assembly não tem `if`, `while` ou `for`. Tudo isso é construído com **saltos** (mudar o `RIP` para outro endereço) combinados com comparações — ver [[Flags_E_Comparacoes|Flags e comparações]] antes desta nota, se ainda não leu.

## `jmp` — salto incondicional
```asm
jmp destino    ; sempre pula para o label "destino", sem checar nada
```

## Saltos condicionais
Executam **só se** a condição (baseada nas flags do `cmp`/`test` anterior) for verdadeira:

| Instrução | Salta se | Baseado em |
|---|---|---|
| `je` / `jz` | igual / zero | `ZF=1` |
| `jne` / `jnz` | diferente / não-zero | `ZF=0` |
| `jg` | maior (com sinal) | `ZF=0` e `SF=OF` |
| `jge` | maior ou igual (com sinal) | `SF=OF` |
| `jl` | menor (com sinal) | `SF≠OF` |
| `jle` | menor ou igual (com sinal) | `ZF=1` ou `SF≠OF` |
| `ja` | maior (sem sinal) | `CF=0` e `ZF=0` |
| `jae` | maior ou igual (sem sinal) | `CF=0` |
| `jb` | menor (sem sinal) | `CF=1` |
| `jbe` | menor ou igual (sem sinal) | `CF=1` ou `ZF=1` |

(Não precisa decorar a coluna "baseado em" — o assembler cuida disso; o que importa é saber usar `g`/`l` para com sinal e `a`/`b` para sem sinal.)

## Traduzindo um `if` para assembly
C:
```c
if (a > b) {
    x = 1;
} else {
    x = 2;
}
```
Assembly (a mesma ideia sempre aparece: comparar, saltar, "senão caia direto"):
```asm
    mov rax, [a]
    mov rbx, [b]
    cmp rax, rbx
    jle senao          ; se NÃO (a > b), pula pro else

    mov qword [x], 1   ; corpo do "if"
    jmp fim

senao:
    mov qword [x], 2   ; corpo do "else"

fim:
```
Repare no padrão: a condição do `if` é **invertida** no assembly (`jle` em vez de checar `jg`) — porque é mais natural "pular o bloco do if quando a condição é falsa" do que o contrário.

## Traduzindo um `while` para assembly
C:
```c
while (i < 10) {
    i = i + 1;
}
```
Assembly:
```asm
    mov rcx, 0          ; i = 0

loop_inicio:
    cmp rcx, 10
    jge loop_fim         ; se i >= 10, sai do loop

    inc rcx               ; i = i + 1
    jmp loop_inicio       ; volta pro início

loop_fim:
```

## Traduzindo um `for` para assembly
C:
```c
for (int i = 0; i < 5; i++) {
    soma += i;
}
```
Assembly — é o mesmo esqueleto do `while`, só reorganizando onde cada parte do `for` (inicialização, condição, incremento) entra:
```asm
    mov rcx, 0          ; inicialização: i = 0
    mov rax, 0           ; soma = 0

for_inicio:
    cmp rcx, 5
    jge for_fim           ; condição: i < 5 ?

    add rax, rcx           ; corpo: soma += i

    inc rcx                 ; incremento: i++
    jmp for_inicio

for_fim:
```

## A instrução `loop` (atalho para contadores)
x86 tem uma instrução dedicada que usa `RCX` como contador automático:
```asm
    mov rcx, 5      ; RCX = quantidade de repetições

repete:
    ; corpo do loop

    loop repete      ; decrementa RCX automaticamente; salta se RCX != 0
```
Na prática, compiladores modernos raramente geram `loop` (é mais lenta que um `dec`+`jnz` manual em CPUs atuais), mas é bom conhecer — aparece bastante em material didático.

## Ver também
- [[Flags_E_Comparacoes|Flags e comparações]]
- [[../03_Assembly_E_C/De_C_Para_Assembly|De C para Assembly]]
- [[Stack_Pilha|A pilha]]
