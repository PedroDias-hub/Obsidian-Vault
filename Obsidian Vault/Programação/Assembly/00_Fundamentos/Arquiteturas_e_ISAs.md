# Arquiteturas e ISAs

## ISA — Instruction Set Architecture
É o "contrato" entre o software e o hardware: a lista completa de instruções que um processador entende, os registradores disponíveis, como a memória é endereçada, etc. Duas CPUs diferentes que implementam a mesma ISA (ex: um Intel e um AMD, ambos x86-64) rodam exatamente o mesmo código de máquina, mesmo sendo hardware fisicamente diferente por dentro.

## As principais famílias

### x86 / x86-64
- Criada pela Intel nos anos 80 (o "86" vem do 8086), hoje dominante em PCs e servidores (Intel, AMD).
- **x86-64** (também chamado **AMD64**, criado pela AMD) é a versão de 64 bits — o padrão atual.
- É uma arquitetura **CISC** (Complex Instruction Set Computer): instruções variadas, de tamanho variável, muitas fazem várias coisas de uma vez (ex: uma instrução pode ler da memória, operar e escrever de volta).
- Esse vault foca em x86-64.

### ARM
- Domina celulares, tablets, e cada vez mais notebooks e servidores (Apple Silicon M1/M2/M3, muitos servidores em nuvem).
- Arquitetura **RISC** (Reduced Instruction Set Computer): instruções mais simples, tamanho fixo, geralmente uma instrução faz uma coisa só. Isso favorece eficiência energética — por isso domina em dispositivos móveis.

### RISC-V
- ISA **aberta e livre** (sem royalties), crescendo rápido em pesquisa, embarcados e até em processadores comerciais recentes.
- Também RISC, com filosofia de design bem limpa — muita gente usa pra *aprender* conceitos de arquitetura de computadores justamente por ser mais enxuta que x86.

### MIPS
- Historicamente muito usada em ensino de arquitetura de computadores (didática, RISC clássica) e em alguns embarcados/roteadores antigos.

## CISC vs. RISC — a diferença que mais importa pra aprender
| | CISC (x86) | RISC (ARM, RISC-V, MIPS) |
|---|---|---|
| Tamanho das instruções | Variável (1 a 15 bytes) | Fixo (geralmente 4 bytes) |
| Complexidade por instrução | Alta — uma instrução pode fazer muito | Baixa — cada instrução faz pouco |
| Quantidade de instruções | Centenas | Dezenas a poucas centenas |
| Acesso à memória | Muitas instruções podem ler/escrever memória direto | Só instruções `load`/`store` tocam memória; o resto opera só em registradores ("load-store architecture") |

Essa distinção explica, por exemplo, por que em ARM você vê muito mais instruções `ldr`/`str` explícitas, enquanto em x86 uma instrução como `add [rax], 5` já lê e escreve na memória sozinha.

## Por que este vault escolhe x86-64
- É quase certamente a arquitetura do seu computador (a menos que seja um Mac com Apple Silicon ou algo ARM).
- É a mais documentada e com mais material didático em português e inglês.
- Depois de entender x86-64 de verdade, migrar mentalmente pra ARM ou RISC-V é muito mais fácil — os *conceitos* (registradores, pilha, flags, saltos) são universais; muda a sintaxe e o "sabor".

## Ver também
- [[O_que_e_Assembly|O que é Assembly]]
- [[../04_Avancado/ARM_x86_RISCV_Comparacao|ARM vs. x86 vs. RISC-V (comparação detalhada)]]
- [[../README|Início]]
