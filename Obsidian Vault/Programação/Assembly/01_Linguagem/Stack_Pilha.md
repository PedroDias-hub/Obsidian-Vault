# A Pilha (Stack)

Se tivesse que escolher **um** conceito de assembly pra entender muito bem, seria este. A pilha é o que torna funções, recursão e variáveis locais possíveis.

## O que é, fisicamente
A pilha é só uma região de memória RAM (ver [[../00_Fundamentos/Memoria_E_Enderecamento|Memória e endereçamento]]) — não tem nada de especial fisicamente. O que a torna "a pilha" é a **convenção** de uso: um registrador dedicado, `RSP` (Stack Pointer), sempre aponta para o topo dela, e duas instruções (`push`/`pop`) manipulam esse topo de forma organizada.

## Ela cresce para baixo
Isso surpreende muita gente: em x86, a pilha cresce em direção a **endereços menores**. "Empilhar" (`push`) **diminui** `RSP`; "desempilhar" (`pop`) **aumenta** `RSP`.

```
Endereços altos
┌─────────────┐
│             │  ← início da pilha (RSP aqui antes de qualquer push)
│             │
│   (vazio)    │
│             │
├─────────────┤ ← RSP aponta aqui depois de alguns push's
│  valor 3     │
│  valor 2     │
│  valor 1     │
└─────────────┘
Endereços baixos
```

## `push` e `pop`
```asm
push rax    ; RSP -= 8 ; depois guarda RAX no endereço [RSP]
pop  rbx    ; lê o valor em [RSP] para RBX ; depois RSP += 8
```
(Os `8` bytes são porque em x86-64 a pilha trabalha em unidades de 8 bytes/qword por padrão.)

`push`/`pop` seguem estritamente a ordem **LIFO** (Last In, First Out — o último que entrou é o primeiro que sai):
```asm
push rax    ; empilha A
push rbx    ; empilha B
pop  rcx    ; RCX recebe B (o último que entrou)
pop  rdx    ; RDX recebe A
```

## Para que a pilha serve, na prática
1. **Guardar endereço de retorno de uma função** (feito automaticamente por `call`/`ret`).
2. **Guardar variáveis locais** de uma função.
3. **Preservar valores de registradores** antes de uma função usá-los para outra coisa, para poder restaurar depois.
4. **Passar argumentos** para funções (em algumas convenções de chamada, ou quando há mais argumentos do que registradores disponíveis).

## `RBP` — o "âncora" do frame da função (stack frame)
Uma convenção extremamente comum: no início de uma função, guardar o `RSP` atual em `RBP`, para ter um ponto de referência **fixo** durante toda a função (já que `RSP` fica se mexendo com cada `push`/`pop` dentro dela):

```asm
minha_funcao:
    push rbp          ; salva o RBP da função anterior (quem chamou)
    mov rbp, rsp        ; RBP = topo atual → agora é o "ponto zero" desta função
    sub rsp, 32          ; reserva 32 bytes na pilha para variáveis locais

    ; ... corpo da função, usando [rbp - 8], [rbp - 16], etc para variáveis locais ...

    mov rsp, rbp        ; desfaz o "sub rsp, 32" de uma vez
    pop rbp              ; restaura o RBP da função anterior
    ret                   ; volta pra quem chamou
```
Esse bloco `push rbp` / `mov rbp, rsp` é tão padronizado que tem nome: **function prologue** (prólogo). O bloco final (`mov rsp, rbp` / `pop rbp` / `ret`) é o **function epilogue** (epílogo). Existe até uma instrução que faz o prólogo/epílogo parcial de uma vez: `enter`/`leave` — hoje raramente usadas por compiladores, mas equivalentes.

## Por que variáveis locais usam `[rbp - N]`
Depois do prólogo, `RBP` fica fixo durante toda a função. Variáveis locais recebem posições **abaixo** dele (por isso o sinal de menos — lembra que a pilha cresce para baixo):
```asm
mov qword [rbp - 8], 10    ; variável local "a" = 10
mov qword [rbp - 16], 20   ; variável local "b" = 20
```

## Ver também
- [[Funcoes_E_Convencoes_De_Chamada|Funções e convenções de chamada]]
- [[../00_Fundamentos/Memoria_E_Enderecamento|Memória e endereçamento]]
- [[../04_Avancado/Stack_Overflow_Conceito|Como um buffer overflow acontece]]
