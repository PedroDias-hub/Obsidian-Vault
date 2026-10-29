# Lendo o Assembly Gerado por um Compilador

## Pedindo pro gcc mostrar o assembly
```bash
gcc -S -O0 -masm=intel programa.c -o programa.s
```
- `-S`: para depois de gerar assembly, sem montar/linkar.
- `-O0`: sem otimização — o assembly fica mais parecido "linha a linha" com o C original, ideal pra aprender.
- `-masm=intel`: sintaxe Intel em vez de AT&T.

Depois de entender o `-O0`, vale comparar com `-O2` (otimizado) no mesmo código — a diferença costuma ser reveladora.

## Usando um binário já compilado
```bash
objdump -d -M intel programa > saida.txt
```
ou, interativamente, dentro do GDB:
```
(gdb) disas main
```

## O que esperar ver e não travar
- **Prólogo/epílogo em toda função** (`push rbp` / `mov rbp,rsp` ... `pop rbp` / `ret`) — ver [[../01_Linguagem/Stack_Pilha|A pilha]].
- **Nomes de registradores "estranhos"** tipo `eax` em vez de `rax` — o compilador usa o tamanho certo pro tipo da variável C (`int` = 32 bits = `eax`; `long`/ponteiro = 64 bits = `rax`).
- **Endereços tipo `[rbp-0x4]`** — variáveis locais na pilha, como vimos em [[../03_Assembly_E_C/De_C_Para_Assembly|De C para Assembly]].
- **Chamadas a funções da libc** (`call printf@plt`, por exemplo) — o `@plt` indica que é resolvido via *Procedure Linkage Table*, mecanismo de link dinâmico (a função só é localizada de fato quando o programa roda, não em tempo de compilação).

## O efeito da otimização (`-O0` vs `-O2`)
Com `-O0`, o compilador é "preguiçoso de propósito" — gera código quase ingênuo, fácil de mapear de volta pro C original. Com `-O2` ou `-O3`, ele começa a:
- Manter variáveis em registradores em vez de ir na pilha toda hora.
- Eliminar código morto (variáveis nunca lidas).
- Desenrolar loops (loop unrolling) — repetir o corpo do loop várias vezes ao invés de saltar de volta, evitando o custo do salto.
- Usar instruções SIMD automaticamente quando possível — ver [[../04_Avancado/SIMD|SIMD e vetorização]].
- Reordenar instruções para melhor aproveitar o pipeline da CPU.

Isso é também por que debugar um programa compilado com otimização costuma ser mais confuso — o assembly "não bate" linha a linha com o C fonte, porque literalmente não é mais uma tradução direta.

## Um exercício de leitura
Pegue uma função C bem simples que você já escreveu (um `for` somando um array, por exemplo), gere o assembly com `-O0`, e tente narrar em português, linha por linha, o que cada instrução faz — comparando com [[../01_Linguagem/Saltos_E_Estruturas_De_Controle|Saltos e estruturas de controle]] e [[../03_Assembly_E_C/De_C_Para_Assembly|De C para Assembly]] sempre que travar. Depois repita com `-O2` no mesmo código e veja o que mudou.

## Ver também
- [[De_C_Para_Assembly|De C para Assembly]]
- [[../02_Pratica/Debug_Com_GDB|Debugando com GDB]]
