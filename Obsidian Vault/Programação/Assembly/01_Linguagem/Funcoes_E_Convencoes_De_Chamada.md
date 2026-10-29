# Funções e Convenções de Chamada

## `call` e `ret`
Duas instruções fazem o trabalho pesado de "chamar uma função" em assembly:

```asm
call minha_funcao
```
Isso faz **duas coisas**:
1. Empilha (`push`) o endereço da instrução seguinte ao `call` — o **endereço de retorno**.
2. Salta (`jmp`) para `minha_funcao`.

```asm
ret
```
Faz o inverso: desempilha (`pop`) o endereço de retorno guardado, e salta pra lá — voltando exatamente para depois de onde o `call` foi feito.

```
chamador:
    call minha_funcao     ; push do endereço da linha seguinte; jmp pra minha_funcao
    mov rax, 1              ; ← call vai voltar exatamente pra cá

minha_funcao:
    ; ... faz algo ...
    ret                    ; pop do endereço; jmp de volta pra "mov rax, 1"
```

Isso é o que torna `call`/`ret` diferentes de um `jmp` comum: eles automaticamente lembram **de onde vieram**, usando a pilha — ver [[Stack_Pilha|A pilha]].

## Convenção de chamada — por que ela precisa existir
Quando uma função chama outra, ambas precisam concordar em coisas como: "em que registrador está o primeiro argumento?", "quem garante que RBX não vai ser destruído?", "onde fica o valor de retorno?". Isso é a **calling convention** — um contrato que todo código (inclusive gerado por compiladores diferentes, ou até linguagens diferentes) segue, permitindo que funções compiladas separadamente consigam se chamar.

## A convenção do Linux x86-64: System V AMD64 ABI
É a que você vai usar ao programar em NASM no Linux (ou ler assembly gerado por gcc lá).

### Argumentos inteiros/ponteiros — nos registradores, nesta ordem:
```
1º argumento → RDI
2º argumento → RSI
3º argumento → RDX
4º argumento → RCX
5º argumento → R8
6º argumento → R9
(a partir do 7º argumento, vai pra pilha)
```

### Valor de retorno
```
RAX  (ou RDX:RAX se o retorno for maior que 64 bits)
```

### Registradores "caller-saved" vs "callee-saved"
Isso resolve o problema: "se minha função usa RBX, e a função que eu chamo também usa RBX, como evito que um sobrescreva o valor do outro sem avisar?"

- **Caller-saved** (`RAX`, `RCX`, `RDX`, `RSI`, `RDI`, `R8`–`R11`): se você (quem chama) tem algo importante nesses registradores, **é sua responsabilidade salvar antes de chamar outra função** — ela pode sobrescrever livremente.
- **Callee-saved** (`RBX`, `RBP`, `R12`–`R15`, e o próprio `RSP`): se a função que você está escrevendo usa esses registradores, **é responsabilidade dela salvar o valor original (com `push`) no início e restaurar (com `pop`) no fim**, antes de retornar.

```asm
minha_funcao:
    push rbx           ; RBX é callee-saved: salvo o valor de quem chamou
    ; ... uso RBX livremente aqui dentro ...
    pop rbx             ; restauro antes de sair
    ret
```

## Exemplo completo: uma função `soma(a, b)`
C equivalente:
```c
int soma(int a, int b) {
    return a + b;
}
```
Assembly (System V AMD64):
```asm
soma:
    ; RDI = a (1º argumento), RSI = b (2º argumento)
    mov eax, edi        ; RAX = a
    add eax, esi          ; RAX = a + b
    ret                    ; retorno em EAX
```
Repare: nem precisou tocar a pilha explicitamente — para uma função simples assim, os argumentos já chegam em registradores, e o retorno já sai em `RAX`, então nem prólogo/epílogo completo é estritamente necessário.

## Alinhamento da pilha — um detalhe que gera bugs sutis
A ABI exige que, **no momento de um `call`**, `RSP` esteja alinhado a 16 bytes. Isso importa principalmente quando você mistura seu assembly com chamadas a funções de biblioteca (como `printf`) — desalinhar a pilha pode causar crashes (especialmente em instruções SIMD que exigem alinhamento). Na prática: sempre que empilhar valores manualmente antes de um `call`, contar em múltiplos de 16 bytes.

## Ver também
- [[Stack_Pilha|A pilha]]
- [[Chamadas_De_Sistema|Chamadas de sistema]]
- [[../03_Assembly_E_C/De_C_Para_Assembly|De C para Assembly]]
