# Assembly — Do Zero ao Entendimento Real

Bem-vindo(a) ao seu vault de Assembly. A proposta aqui não é decorar instruções — é entender, camada por camada, **o que o computador realmente faz** quando um programa roda. Assembly é a linguagem mais próxima do hardware que ainda é "legível" por humanos, e uma vez que ela faz sentido, praticamente tudo em Ciência da Computação (compiladores, sistemas operacionais, segurança, performance) fica mais claro — porque tudo isso, no fundo, vira isto.

Este vault usa **x86-64** (a arquitetura do seu próprio computador, quase certamente) com sintaxe **NASM/Intel**, por ser a mais didática e a mais usada em material de estudo hoje. ARM e RISC-V aparecem por comparação lá na frente, quando a base já estiver sólida.

## Como navegar
Siga a ordem — assembly é uma daquelas áreas em que pular etapas custa caro depois.

### 00 — Fundamentos (o "porquê" antes do "como")
1. [[00_Fundamentos/O_que_e_Assembly|O que é Assembly]]
2. [[00_Fundamentos/Arquiteturas_e_ISAs|Arquiteturas e ISAs (x86, ARM, RISC-V)]]
3. [[00_Fundamentos/Sistema_Binario_E_Hexadecimal|Sistema binário e hexadecimal]]
4. [[00_Fundamentos/Arquitetura_Von_Neumann|Arquitetura Von Neumann e o ciclo fetch-decode-execute]]
5. [[00_Fundamentos/Registradores|Registradores]]
6. [[00_Fundamentos/Memoria_E_Enderecamento|Memória e endereçamento]]

### 01 — A linguagem em si
7. [[01_Linguagem/Sintaxe_Intel_vs_ATT|Sintaxe Intel vs. AT&T]]
8. [[01_Linguagem/Diretivas_Do_Assembler|Diretivas do assembler (seções, .data, .text)]]
9. [[01_Linguagem/Instrucoes_De_Movimentacao|Instruções de movimentação de dados]]
10. [[01_Linguagem/Modos_De_Enderecamento|Modos de endereçamento]]
11. [[01_Linguagem/Instrucoes_Aritmeticas_E_Logicas|Instruções aritméticas e lógicas]]
12. [[01_Linguagem/Flags_E_Comparacoes|Flags e comparações]]
13. [[01_Linguagem/Saltos_E_Estruturas_De_Controle|Saltos e estruturas de controle (if/while em assembly)]]
14. [[01_Linguagem/Stack_Pilha|A pilha (stack)]]
15. [[01_Linguagem/Funcoes_E_Convencoes_De_Chamada|Funções e convenções de chamada]]
16. [[01_Linguagem/Chamadas_De_Sistema|Chamadas de sistema (syscalls)]]

### 02 — Prática (mão na massa)
17. [[02_Pratica/Ferramentas|Ferramentas: NASM, GDB, objdump, ld]]
18. [[02_Pratica/Primeiro_Programa|Seu primeiro programa: Hello World]]
19. [[02_Pratica/Debug_Com_GDB|Debugando com GDB]]
20. [[02_Pratica/Exercicios|Exercícios progressivos]]

### 03 — Assembly e C (a ponte)
21. [[03_Assembly_E_C/De_C_Para_Assembly|De C para Assembly: como um `for` vira instruções]]
22. [[03_Assembly_E_C/Lendo_Assembly_Do_Compilador|Lendo o assembly gerado por um compilador]]

### 04 — Tópicos avançados
23. [[04_Avancado/SIMD|SIMD e vetorização]]
24. [[04_Avancado/Assembly_Inline_Em_C|Assembly inline dentro de C]]
25. [[04_Avancado/Stack_Overflow_Conceito|Como um buffer overflow acontece (conceito)]]
26. [[04_Avancado/ARM_x86_RISCV_Comparacao|ARM vs. x86 vs. RISC-V]]

## O roadmap com prazos sugeridos
Ver [[Roadmap|Roadmap]] para uma sequência de estudo com checkboxes.

## Um conselho antes de começar
Assembly não perdoa "mais ou menos entendi". A boa notícia é que o universo de conceitos é pequeno — um punhado de registradores, um punhado de instruções, e a pilha. A sensação de "uau, é só isso?" costuma vir rápido depois que trava no começo. Vá com calma nas primeiras notas, teste cada exemplo de verdade no seu terminal, e não tenha pressa de chegar no avançado.
