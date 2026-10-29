# Memória e Endereçamento

## Memória como um array gigante de bytes
A forma mais simples de pensar na RAM: é um array enorme, onde cada posição (**endereço**) guarda exatamente **1 byte**. Um endereço de memória em x86-64 tem 64 bits — na prática, hoje em dia, só os 48 bits mais baixos são realmente usados (endereçando até 256 TB), mas o registrador reservado pra endereço é de 64 bits.

```
Endereço:  0x1000  0x1001  0x1002  0x1003  ...
Conteúdo:  [ 0x4A ][ 0xF1 ][ 0x00 ][ 0x3B ] ...
```

Para guardar um valor maior que 1 byte (um `int` de 4 bytes, por exemplo), ele ocupa **vários endereços consecutivos**.

## Little-endian vs. big-endian
x86-64 é **little-endian**: o byte menos significativo é guardado no endereço mais baixo.

Exemplo: guardar o valor `0x12345678` (4 bytes) a partir do endereço `0x1000`:
```
Endereço:   0x1000  0x1001  0x1002  0x1003
Little-endian:  78      56      34      12
```

Isso costuma confundir muita gente ao olhar memória crua num debugger (os bytes parecem "invertidos"). É só lembrar: **o byte de menor peso fica no endereço mais baixo**.

## Segmentos de memória de um programa
Quando um programa roda, a memória que ele usa é organizada em regiões com propósitos diferentes:

```
Endereços altos
┌─────────────────────┐
│        Stack         │  ← cresce para baixo, variáveis locais, endereços de retorno
│          ↓            │
│                       │
│          ↑            │
│         Heap          │  ← cresce para cima, alocação dinâmica (malloc)
├─────────────────────┤
│   .bss (variáveis     │  ← globais/estáticas não inicializadas (zeradas)
│   globais não init.)  │
├─────────────────────┤
│   .data (variáveis    │  ← globais/estáticas inicializadas
│   globais inicial.)   │
├─────────────────────┤
│   .text (código)      │  ← as instruções de máquina do programa
└─────────────────────┘
Endereços baixos
```

Essas seções (`.text`, `.data`, `.bss`) aparecem literalmente no código assembly como diretivas — ver [[../01_Linguagem/Diretivas_Do_Assembler|Diretivas do assembler]].

## Memória virtual (uma pincelada)
O endereço que seu programa "vê" (ex: `0x1000`) **não é** o endereço físico real na RAM. O sistema operacional, com ajuda de hardware (a MMU — Memory Management Unit), traduz endereços virtuais para físicos. Isso é o que permite:
- Cada processo achar que tem a memória "só pra ele", começando do zero.
- O SO isolar processos (um programa não consegue ler memória de outro por engano/malícia).
- Usar mais memória do que fisicamente existe (swap/paginação).

Para quem está começando, o importante é saber que **os endereços que você vê em assembly são virtuais** — isso não muda como você escreve código, mas explica por que endereços "parecem" arbitrários e por que dois programas podem "ter" o mesmo endereço sem conflito.

## Acessando memória a partir de um registrador
Em NASM, colchetes `[...]` significam "o conteúdo do endereço", não o endereço em si:
```asm
mov rax, [rbx]      ; RAX recebe o VALOR guardado no endereço apontado por RBX
mov rax, rbx         ; RAX recebe o próprio valor de RBX (cópia direta, sem acessar memória)
```
Essa diferença é uma das primeiras coisas que trava iniciantes — vale grudar essa distinção antes de seguir para [[../01_Linguagem/Modos_De_Enderecamento|Modos de endereçamento]], que aprofunda isso.

## Ver também
- [[Registradores]]
- [[../01_Linguagem/Modos_De_Enderecamento|Modos de endereçamento]]
- [[../01_Linguagem/Stack_Pilha|A pilha]]
