# Sistema Binário e Hexadecimal

Sem fluência aqui, assembly vira decoreba sem sentido. Vale garantir que isso está sólido antes de seguir.

## Por que binário
Um transistor (a unidade mais básica de um processador) só tem dois estados estáveis: ligado ou desligado. Isso naturalmente mapeia para o sistema **binário** (base 2): cada dígito (**bit**) é 0 ou 1.

## Conversão binário → decimal
Cada posição vale uma potência de 2, da direita pra esquerda ($2^0, 2^1, 2^2, ...$):

```
1  0  1  1
8  4  2  1   ← valor de cada posição
```
$1{\cdot}8 + 0{\cdot}4 + 1{\cdot}2 + 1{\cdot}1 = 11$

Então `1011` em binário = `11` em decimal.

## Conversão decimal → binário
Divisões sucessivas por 2, guardando os restos:
```
13 ÷ 2 = 6  resto 1
 6 ÷ 2 = 3  resto 0
 3 ÷ 2 = 1  resto 1
 1 ÷ 2 = 0  resto 1
```
Lendo os restos de baixo pra cima: `13` = `1101`

## Agrupamentos: bit, byte, word, dword, qword
Assembly usa esses termos o tempo todo:

| Nome | Tamanho | Nome em x86 |
|---|---|---|
| bit | 1 bit | — |
| **byte** | 8 bits | `byte` |
| **word** | 16 bits (2 bytes) | `word` |
| **dword** | 32 bits (4 bytes) — "double word" | `dword` |
| **qword** | 64 bits (8 bytes) — "quad word" | `qword` |

Isso importa porque, em assembly, você frequentemente precisa dizer explicitamente *quantos bytes* uma instrução deve tratar — ex: `mov dword [rax], 5` vs `mov byte [rax], 5`.

## Por que hexadecimal existe
Binário fica ilegível rápido — um número de 32 bits vira uma sequência de 32 dígitos. Hexadecimal (**base 16**) resolve isso porque **cada dígito hexadecimal representa exatamente 4 bits**, então converter entre eles é trivial (diferente de decimal, que não bate certinho com potências de 2).

Dígitos hexadecimais: `0 1 2 3 4 5 6 7 8 9 A B C D E F` (A=10, B=11, ..., F=15)

| Binário (4 bits) | Hex |
|---|---|
| 0000 | 0 |
| 0101 | 5 |
| 1010 | A |
| 1111 | F |

Um byte inteiro (8 bits) sempre cabe em **exatamente 2 dígitos hex**. Por isso endereços de memória e valores de registrador quase sempre aparecem em hex, prefixados com `0x`:
```
0x1A3F   (equivale a 4 grupos de 4 bits: 0001 1010 0011 1111)
```

## Conversão rápida binário ↔ hex
Separe o binário em grupos de 4 bits (da direita pra esquerda) e converta cada grupo:
```
1010 1111 0011
 A    F    3
→ 0xAF3
```

## Números negativos: complemento de dois
Assembly (e praticamente todo hardware) representa inteiros negativos usando **complemento de dois**: para negar um número, inverte-se todos os bits e soma-se 1.

Exemplo com 8 bits, representando -5:
```
 5 em binário:       0000 0101
inverter os bits:    1111 1010
somar 1:             1111 1011   ← isso é -5 em complemento de dois
```

Por que assim, e não só um "bit de sinal"? Porque complemento de dois permite que a **mesma instrução de soma** funcione tanto para números positivos quanto negativos, sem lógica especial — o hardware fica mais simples e rápido. Isso também explica por que o intervalo de um `int` de 8 bits é assimétrico: de $-128$ a $127$ (não $-127$ a $127$), porque o zero "come" um dos slots positivos.

## Ver também
- [[Registradores]]
- [[../01_Linguagem/Instrucoes_Aritmeticas_E_Logicas|Instruções aritméticas e lógicas]]
