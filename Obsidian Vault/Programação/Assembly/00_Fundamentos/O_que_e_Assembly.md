# O que é Assembly

## A ideia central
Um processador só entende **números binários** — sequências de 0s e 1s chamadas de **código de máquina**. Cada instrução que a CPU executa (somar dois números, mover um valor de um lugar pra outro, pular para outra parte do programa) corresponde a um padrão específico de bits.

Escrever código de máquina diretamente é possível, mas humanamente inviável — ninguém decora que `10110000 01100001` significa "coloque o valor 97 no registrador AL". Assembly resolve isso dando um **nome legível** para cada instrução de máquina:

```
mov al, 97
```

Isso é exatamente a mesma instrução, só que escrita de um jeito que um humano consegue ler e escrever. Essa correspondência é o que define Assembly: **cada linha de assembly corresponde (quase sempre) a exatamente uma instrução de máquina.** Isso é bem diferente de uma linguagem como Python ou Java, onde uma linha pode virar dezenas de instruções de máquina.

## Assembly não é "uma linguagem"
Isso é importante: não existe *"a"* linguagem Assembly, universal. Cada família de processador (x86, ARM, RISC-V, MIPS...) tem seu próprio **conjunto de instruções** (ISA — Instruction Set Architecture), e portanto seu próprio "dialeto" de assembly. Um programa em assembly x86 não roda numa CPU ARM, porque as instruções de máquina são literalmente diferentes bits.

Aprender assembly x86-64 (o foco deste vault) te dá a base conceitual pra entender qualquer outro — os conceitos (registradores, pilha, saltos) se repetem, só a sintaxe e o conjunto exato de instruções mudam.

## O que é um "assembler"?
É o programa que traduz o texto assembly (`mov al, 97`) para os bytes reais de código de máquina que o processador executa. É o irmão mais simples de um compilador — enquanto um compilador (gcc, javac) faz transformações complexas, o assembler faz uma tradução quase 1-para-1.

Assemblers comuns para x86: **NASM**, **GAS** (GNU Assembler), **MASM** (Windows). Este vault usa NASM.

## Onde o Assembly se encaixa
```
Código fonte (C, Java, Python...)
        ↓  compilador
Assembly
        ↓  assembler
Código de máquina (binário)
        ↓  CPU executa
```

Quando você compila um programa em C com `gcc`, o compilador na verdade gera assembly como etapa intermediária (você pode até pedir pra ver: `gcc -S arquivo.c`), e só depois o assembler transforma isso em binário executável.

## Por que aprender, na prática
- **Entender o que o computador realmente faz** — deixa de ser uma "caixa preta".
- **Debugar em baixo nível** — ler um `objdump -d` ou o assembly gerado num debugger deixa de ser hieróglifo.
- **Entender performance** — por que um `for` é mais rápido que outro, cache, branch prediction, tudo isso vira concreto.
- **Segurança/engenharia reversa** — análise de malware, CTFs, exploração de vulnerabilidades passam por aqui.
- **Sistemas embarcados e SO** — onde não tem intérprete nem runtime, só o metal.

## Ver também
- [[Arquiteturas_e_ISAs|Arquiteturas e ISAs]]
- [[Registradores]]
- [[../README|Início]]
