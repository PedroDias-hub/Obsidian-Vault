# Arquitetura Von Neumann e o Ciclo Fetch-Decode-Execute

## A ideia de Von Neumann
Quase todo computador moderno segue o modelo proposto por John von Neumann em 1945: **programa e dados vivem no mesmo espaço de memória**. Isso é o que permite um programa ser carregado na memória, executado, e até modificado como dado (é literalmente o que um compilador faz: gera bytes na memória que depois viram instruções executáveis).

Componentes básicos:
- **CPU**: executa instruções. Contém a ULA (Unidade Lógica e Aritmética) e os registradores.
- **Memória (RAM)**: guarda tanto o programa (instruções) quanto os dados que ele manipula.
- **Barramento**: as "estradas" elétricas que conectam CPU, memória e periféricos.

## O ciclo fetch-decode-execute
Isso é literalmente o que a CPU fica fazendo, sem parar, bilhões de vezes por segundo:

1. **Fetch (busca)**: a CPU busca na memória a próxima instrução, no endereço apontado pelo **program counter** (chamado `RIP` em x86-64 — "Instruction Pointer").
2. **Decode (decodificação)**: a CPU interpreta os bits da instrução — que operação é essa, quais registradores/memória ela envolve.
3. **Execute (execução)**: a operação de fato acontece (soma, movimento de dado, salto, etc).
4. O `RIP` avança para a próxima instrução (ou pula para outro endereço, no caso de um salto/`jmp`), e o ciclo recomeça.

```
   ┌─────────┐     ┌──────────┐     ┌─────────┐
   │  FETCH  │ --> │  DECODE  │ --> │ EXECUTE │ --┐
   └─────────┘     └──────────┘     └─────────┘   │
        ▲                                          │
        └──────────────────────────────────────────┘
```

## Por que isso importa pra assembly
Cada linha de assembly que você escreve é, essencialmente, **uma volta desse ciclo**. Quando você entende que `mov rax, 5` significa "busca essa instrução, decodifica como 'mover valor imediato pro registrador RAX', executa colocando 5 em RAX, avança o RIP" — o assembly para de ser abstrato e vira literalmente uma narração do que o processador faz, passo a passo.

## O gargalo de Von Neumann
Vale mencionar: como programa e dados compartilham o mesmo barramento de memória, existe um limite de quantos dados e instruções conseguem "viajar" por segundo entre CPU e RAM — é o chamado **gargalo de Von Neumann**. É uma das razões pelas quais existe **cache** (memória pequena e rápida dentro/perto da CPU) — outro tópico que passa a fazer muito mais sentido depois de entender essa arquitetura.

## Ver também
- [[Registradores]]
- [[Memoria_E_Enderecamento|Memória e endereçamento]]
- [[../01_Linguagem/Saltos_E_Estruturas_De_Controle|Saltos e estruturas de controle]]
