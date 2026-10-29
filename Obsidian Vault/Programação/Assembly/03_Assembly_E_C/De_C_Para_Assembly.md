# De C para Assembly: Como Cada Construção Vira Instruções

Já vimos peças isoladas (`if`, `while`, arrays, funções). Esta nota junta tudo, mostrando construções de C completas ao lado do assembly que um compilador razoável geraria (levemente simplificado para clareza didática — um compilador real otimiza mais).

## Variáveis simples
```c
int a = 5;
int b = a + 3;
```
```asm
mov dword [rbp-4], 5           ; a
mov eax, [rbp-4]
add eax, 3
mov dword [rbp-8], eax          ; b
```

## Structs viram deslocamentos fixos
```c
struct Ponto { int x; int y; };
struct Ponto p;
p.x = 10;
p.y = 20;
```
Como `x` e `y` são ambos `int` (4 bytes), `y` fica no deslocamento 4 a partir do início da struct:
```asm
mov dword [rbp-8], 10      ; p.x   (offset 0)
mov dword [rbp-4], 20      ; p.y   (offset 4)
```
Isso explica por que a **ordem dos campos numa struct importa** para o tamanho final (padding/alinhamento) — cada campo é só um deslocamento fixo calculado em tempo de compilação.

## Arrays
```c
int arr[5];
arr[2] = 99;
```
```asm
mov dword [rbp - 20 + 2*4], 99    ; endereço base do array + índice*tamanho
```
(Na prática o compilador já resolve `2*4=8` em tempo de compilação, viraria `[rbp-12]` direto — mas conceitualmente é sempre `base + índice*escala`, como vimos em [[../01_Linguagem/Modos_De_Enderecamento|Modos de endereçamento]].)

## Ponteiros
```c
int x = 10;
int *p = &x;
*p = 20;
```
```asm
mov dword [rbp-4], 10      ; x
lea rax, [rbp-4]              ; p = &x  (endereço, não valor — por isso "lea")
mov [rbp-16], rax             ; guarda o ponteiro p
mov rax, [rbp-16]              ; lê o ponteiro p
mov dword [rax], 20              ; *p = 20  (escreve no endereço apontado)
```
Essa é a tradução mais literal possível do conceito de ponteiro: **um ponteiro é só um endereço guardado como um valor comum**, e "desreferenciar" (`*p`) é simplesmente usar esse valor como endereço — exatamente o modo de endereçamento indireto por registrador.

## `if`/`else`, `while`, `for`
Já cobertos em detalhe em [[../01_Linguagem/Saltos_E_Estruturas_De_Controle|Saltos e estruturas de controle]] — vale revisar aquela nota lado a lado com esta.

## Chamada de função com múltiplos argumentos
```c
int resultado = soma(a, b, c);
```
```asm
mov edi, [a]     ; 1º argumento
mov esi, [b]       ; 2º argumento
mov edx, [c]         ; 3º argumento
call soma
mov [resultado], eax   ; valor de retorno vem em EAX
```

## `switch` — geralmente vira uma jump table
```c
switch (x) {
    case 0: ... break;
    case 1: ... break;
    case 2: ... break;
}
```
Para valores de `case` sequenciais, compiladores costumam gerar uma **tabela de saltos** (array de endereços) em vez de comparações em cadeia — o índice `x` é usado direto como índice no array de endereços, saltando pro lugar certo em tempo O(1), sem testar `cmp` um por um:
```asm
cmp eax, 2          ; garante que está dentro do range válido
ja default_case
lea rcx, [tabela]
jmp [rcx + rax*8]     ; salta direto pro endereço da tabela

tabela:
    dq caso0
    dq caso1
    dq caso2
```
Isso só compensa quando os valores dos `case` são densos/sequenciais — `case` esparsos (`0, 100, 50000`) geralmente viram comparações em cadeia, como um `if/elif` comum.

## Por que ver isso importa
Depois de acompanhar essas traduções, ideias que antes eram "regras da linguagem C" (por que ponteiro e array são parecidos, por que structs desalinhadas desperdiçam memória, por que recursão profunda estoura a pilha) deixam de ser regras memorizadas e passam a ser **consequências óbvias** de como a memória e a pilha realmente funcionam.

## Ver também
- [[Lendo_Assembly_Do_Compilador|Lendo o assembly gerado por um compilador]]
- [[../01_Linguagem/Modos_De_Enderecamento|Modos de endereçamento]]
- [[../01_Linguagem/Stack_Pilha|A pilha]]
