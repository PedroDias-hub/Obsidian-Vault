# Ferramentas: NASM, GDB, objdump, ld

## NASM (Netwide Assembler)
O assembler que traduz seu arquivo `.asm` em código de máquina. Instalação (Linux):
```bash
sudo apt install nasm      # Debian/Ubuntu
```
Uso básico:
```bash
nasm -f elf64 programa.asm -o programa.o
```
- `-f elf64`: formato de saída — ELF de 64 bits (o formato de objeto do Linux). No Windows seria `-f win64`; no macOS, `-f macho64`.
- Gera um **arquivo objeto** (`.o`) — código de máquina, mas ainda não é um executável completo.

## `ld` — o linker
Um arquivo objeto sozinho não roda — falta "linkar" (juntar) com outras peças (bibliotecas, resolver endereços finais) e gerar o executável de fato:
```bash
ld programa.o -o programa
```
Depois disso, `./programa` já roda.

Quando o código usa funções da libc (como `printf`), o link fica um pouco diferente — geralmente é mais simples deixar o `gcc` cuidar disso:
```bash
gcc programa.o -o programa -no-pie
```
(`-no-pie` desliga uma proteção — Position Independent Executable — que às vezes complica exemplos didáticos simples com endereços fixos.)

## objdump — desmontando um binário
Transforma código de máquina de volta em assembly legível (desmontagem/disassembly) — essencial pra **ler** o que um binário já compilado faz:
```bash
objdump -d programa          # desmonta a seção de código, sintaxe AT&T (padrão)
objdump -d -M intel programa  # mesma coisa, sintaxe Intel (mais fácil de ler pra quem estuda com NASM)
```

## GDB — GNU Debugger
Permite rodar um programa passo a passo, ver registradores, memória, pilha, em tempo real. Ver [[Debug_Com_GDB|Debugando com GDB]] para um guia completo.
```bash
gdb ./programa
```

## Resumo do fluxo completo
```bash
nasm -f elf64 programa.asm -o programa.o    # assembly → objeto
ld programa.o -o programa                     # objeto → executável
./programa                                       # roda
objdump -d -M intel programa                    # inspeciona o binário gerado
gdb ./programa                                    # debuga passo a passo
```

## Editor recomendado
Qualquer editor de texto serve, mas VS Code com a extensão "x86 and x86_64 Assembly" dá highlight de sintaxe decente para NASM.

## Ver também
- [[Primeiro_Programa|Seu primeiro programa]]
- [[Debug_Com_GDB|Debugando com GDB]]
