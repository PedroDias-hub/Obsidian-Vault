# Modos de Endereçamento

"Modo de endereçamento" é a forma como uma instrução especifica **onde** está o dado que ela vai usar. Dominar isso é o que permite ler (e escrever) acesso a arrays, structs e ponteiros em assembly.

## 1. Imediato (immediate)
O valor está escrito direto na instrução — não é um endereço nem um registrador, é a constante em si:
```asm
mov rax, 5        ; 5 é um valor imediato
```

## 2. Registrador (register)
O operando é o conteúdo de um registrador:
```asm
mov rax, rbx      ; copia o CONTEÚDO de RBX
```

## 3. Direto/absoluto (direct)
O endereço de memória é um valor fixo, conhecido em tempo de montagem (geralmente um label):
```asm
mov rax, [minha_variavel]    ; lê do endereço associado ao label
```

## 4. Indireto por registrador (register indirect)
O endereço está guardado dentro de um registrador — é o equivalente assembly de "seguir um ponteiro":
```asm
mov rax, [rbx]    ; RBX guarda um endereço; lemos o que está lá
```

## 5. Base + deslocamento (base + displacement)
Endereço = valor de um registrador + uma constante somada. Muito usado para acessar **campos de uma struct** ou **variáveis locais na pilha**:
```asm
mov rax, [rbx + 8]     ; lê do endereço (RBX + 8)
mov rax, [rbp - 16]    ; comum para variável local: RBP menos um deslocamento
```

## 6. Base + índice + escala (base + index + scale)
O modo mais poderoso — usado para **acessar elementos de um array**:
```asm
mov rax, [rbx + rcx*8 + 16]
```
Aqui:
- `rbx` = endereço base do array
- `rcx` = índice do elemento (ex: `i` de um `array[i]`)
- `8` = escala — o tamanho de cada elemento em bytes (8 para um array de `long`/ponteiros, 4 para `int`, etc). Só pode ser 1, 2, 4 ou 8.
- `16` = deslocamento extra (ex: pular um cabeçalho antes do array)

### Por que isso é exatamente o que um array em C vira
Em C, `array[i]` compila (essencialmente) para essa exata fórmula: `endereço_base + i * tamanho_do_elemento`. Ver essa instrução em assembly **é literalmente ver o que `array[i]` significa por baixo dos panos** — ver [[../03_Assembly_E_C/De_C_Para_Assembly|De C para Assembly]].

## Resumindo a fórmula geral
```
[base + índice*escala + deslocamento]
```
Nem todo acesso usa todas as partes — você usa só o que precisa: `[rbx]`, `[rbx+8]`, `[rbx+rcx*4]`, etc, são todos válidos, cada um "desligando" as partes que não usa.

## Colchetes = "vá até a memória"
Vale repetir, porque é o erro mais comum de quem está começando:
```asm
mov rax, rbx       ; RAX = valor de RBX (cópia direta, sem tocar memória)
mov rax, [rbx]     ; RAX = valor QUE ESTÁ NO ENDEREÇO guardado em RBX
```

## Ver também
- [[../00_Fundamentos/Memoria_E_Enderecamento|Memória e endereçamento]]
- [[Instrucoes_De_Movimentacao|Instruções de movimentação de dados]]
- [[../03_Assembly_E_C/De_C_Para_Assembly|De C para Assembly]]
