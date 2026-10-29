# Instruções de Movimentação de Dados

A instrução mais usada em qualquer programa assembly é, disparado, `mov`. Vale entender ela profundamente antes de seguir.

## `mov` — a instrução fundamental
```asm
mov destino, origem
```
Copia o valor de `origem` para `destino`. **Importante: não é uma "movimentação" no sentido de remover de um lugar — é uma cópia.** O valor original em `origem` continua lá.

### As quatro combinações possíveis
```asm
mov rax, rbx          ; registrador ← registrador
mov rax, 5             ; registrador ← valor imediato (constante)
mov rax, [rbx]         ; registrador ← memória (lê o que está no endereço em RBX)
mov [rbx], rax         ; memória ← registrador (escreve RAX no endereço em RBX)
```

### O que **não** existe
```asm
mov [rax], [rbx]   ; ❌ ILEGAL — não dá pra mover memória para memória direto
```
Motivo: a CPU só tem "canos" de dados suficientes para uma operação de memória por vez nessas instruções simples. Pra copiar memória→memória, você passa por um registrador:
```asm
mov rcx, [rbx]   ; lê da memória para um registrador
mov [rax], rcx   ; escreve o registrador na memória
```

## Tamanho importa
Quando o tamanho não é óbvio pelo registrador usado, é preciso ser explícito:
```asm
mov byte [rax], 5     ; escreve só 1 byte no endereço
mov dword [rax], 5    ; escreve 4 bytes
mov qword [rax], 5    ; escreve 8 bytes
```

## `lea` — Load Effective Address
Parecido com `mov [algo]`, mas em vez de ler o *conteúdo* do endereço, `lea` calcula e guarda **o próprio endereço** (ou um cálculo aritmético):
```asm
lea rax, [rbx + 8]    ; RAX = RBX + 8  (um cálculo, NÃO acessa memória)
mov rax, [rbx + 8]    ; RAX = valor guardado no endereço RBX+8 (ACESSA memória)
```
`lea` é frequentemente usado como um "add rápido" mesmo sem intenção de endereçar memória, porque a CPU tem uma unidade dedicada pra esses cálculos, tornando `lea` muito eficiente para certas contas.

## `movzx` e `movsx` — mover com extensão
Ao mover um valor pequeno (ex: 1 byte) para um registrador maior (ex: 64 bits), é preciso decidir o que preencher no resto dos bits:
- **`movzx`** (zero-extend): preenche com zeros — usado para valores **sem sinal** (unsigned).
- **`movsx`** (sign-extend): replica o bit de sinal — usado para valores **com sinal** (signed), preservando se era positivo ou negativo.

```asm
movzx rax, byte [valor_unsigned]   ; estende com zeros
movsx rax, byte [valor_signed]     ; estende preservando o sinal
```

## `xchg` — troca (swap)
```asm
xchg rax, rbx    ; troca os valores de RAX e RBX entre si
```

## Ver também
- [[../00_Fundamentos/Registradores|Registradores]]
- [[Modos_De_Enderecamento|Modos de endereçamento]]
- [[Instrucoes_Aritmeticas_E_Logicas|Instruções aritméticas e lógicas]]
