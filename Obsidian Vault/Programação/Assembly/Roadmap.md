# Roadmap de Estudo

Uma sequência sugerida, quebrada em etapas pequenas o bastante pra não desanimar. Marque conforme for avançando — o Obsidian salva o estado das checkboxes.

## Semana 1 — Fundamentos conceituais (sem escrever código ainda)
- [ ] [[00_Fundamentos/O_que_e_Assembly|O que é Assembly]]
- [ ] [[00_Fundamentos/Arquiteturas_e_ISAs|Arquiteturas e ISAs]]
- [ ] [[00_Fundamentos/Sistema_Binario_E_Hexadecimal|Sistema binário e hexadecimal]] (revisar até estar 100% automático)
- [ ] [[00_Fundamentos/Arquitetura_Von_Neumann|Arquitetura Von Neumann]]
- [ ] [[00_Fundamentos/Registradores|Registradores]]
- [ ] [[00_Fundamentos/Memoria_E_Enderecamento|Memória e endereçamento]]

## Semana 2 — Instalar ferramentas e escrever as primeiras linhas
- [ ] [[02_Pratica/Ferramentas|Instalar NASM, GDB, objdump]]
- [ ] [[01_Linguagem/Sintaxe_Intel_vs_ATT|Sintaxe Intel vs. AT&T]]
- [ ] [[01_Linguagem/Diretivas_Do_Assembler|Diretivas do assembler]]
- [ ] [[02_Pratica/Primeiro_Programa|Rodar o Hello World de verdade]] (não só ler — montar, linkar, executar)
- [ ] [[01_Linguagem/Instrucoes_De_Movimentacao|Instruções de movimentação de dados]]

## Semana 3 — Operações e decisões
- [ ] [[01_Linguagem/Modos_De_Enderecamento|Modos de endereçamento]]
- [ ] [[01_Linguagem/Instrucoes_Aritmeticas_E_Logicas|Instruções aritméticas e lógicas]]
- [ ] [[01_Linguagem/Flags_E_Comparacoes|Flags e comparações]]
- [ ] [[01_Linguagem/Saltos_E_Estruturas_De_Controle|Saltos e estruturas de controle]]
- [ ] [[02_Pratica/Exercicios#Bloco 1 — Movimentação e aritmética básica|Exercícios — Bloco 1]]
- [ ] [[02_Pratica/Exercicios#Bloco 2 — Memória e endereçamento|Exercícios — Bloco 2]]
- [ ] [[02_Pratica/Exercicios#Bloco 3 — Saltos e estruturas de controle|Exercícios — Bloco 3]]

## Semana 4 — Pilha, funções, GDB de verdade
- [ ] [[01_Linguagem/Stack_Pilha|A pilha]]
- [ ] [[01_Linguagem/Funcoes_E_Convencoes_De_Chamada|Funções e convenções de chamada]]
- [ ] [[02_Pratica/Debug_Com_GDB|Debugando com GDB]] — usar de verdade, não só ler
- [ ] [[02_Pratica/Exercicios#Bloco 4 — Funções e a pilha|Exercícios — Bloco 4]]
- [ ] [[01_Linguagem/Chamadas_De_Sistema|Chamadas de sistema]]

## Semana 5 — Conectando com o que você já sabe (C)
- [ ] [[03_Assembly_E_C/De_C_Para_Assembly|De C para Assembly]]
- [ ] [[03_Assembly_E_C/Lendo_Assembly_Do_Compilador|Lendo o assembly gerado por um compilador]] — fazer o exercício de ler `-O0` vs `-O2`
- [ ] Pegar um programa C simples seu (de outra matéria) e tentar prever o assembly antes de gerar

## Quando estiver confortável — tópicos avançados, sem pressa
- [ ] [[04_Avancado/SIMD|SIMD e vetorização]]
- [ ] [[04_Avancado/Assembly_Inline_Em_C|Assembly inline em C]]
- [ ] [[04_Avancado/Stack_Overflow_Conceito|Como um buffer overflow acontece]]
- [ ] [[04_Avancado/ARM_x86_RISCV_Comparacao|ARM vs. x86 vs. RISC-V]]

## Sinal de que a base está sólida
Você consegue olhar uma função C pequena, prever aproximadamente o assembly que ela vira (sem decorar, só raciocinando pela lógica: onde ficam os argumentos, onde a pilha entra, onde os saltos aparecem), e conferir no GDB pra ver o quão perto chegou. Quando isso ficar natural, o resto (SIMD, outras arquiteturas, otimização) é só expansão sobre uma base que já existe.

## Ver também
- [[Assembly/README|Início]]
