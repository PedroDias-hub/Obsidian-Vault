# Assembly Inline Dentro de C

Às vezes você quer usar uma instrução assembly específica **dentro** de um programa C — geralmente para acessar algo que C não expõe diretamente (uma instrução de CPU específica, um registrador especial) ou para otimizar um trecho crítico manualmente.

## Sintaxe básica (GCC, estilo GNU)
```c
asm("nop");    // executa a instrução NOP (não faz nada), sem envolver variáveis C
```

## Passando dados entre C e o assembly inline
```c
int a = 10, resultado;

asm("mov %1, %%eax;"
    "add $5, %%eax;"
    "mov %%eax, %0;"
    : "=r" (resultado)   // saída: resultado recebe o que sair em qualquer registrador
    : "r" (a)               // entrada: a é colocado em algum registrador
    : "%eax"                 // "clobber list": avisa o compilador que EAX foi alterado
);
// resultado agora vale 15
```
Repare que essa sintaxe usa **AT&T** (`%eax` com `%`, `$5` para imediato) mesmo que o resto do seu código C não tenha nada a ver com isso — é a convenção do GCC para assembly inline.

## Os três "campos" depois dos dois pontos
```c
asm( "instruções"
   : lista de saídas
   : lista de entradas
   : registradores modificados ("clobbered")
);
```
- **Saídas**: variáveis C que recebem valores de volta do assembly.
- **Entradas**: variáveis C cujos valores entram no assembly.
- **Clobber list**: registradores (ou `"memory"`, `"cc"` para flags) que o trecho de assembly mexe, além do declarado nas saídas — isso avisa o compilador para não assumir que esses registradores mantiveram seus valores.

## Por que isso é perigoso se mal usado
Assembly inline **quebra o modelo mental do compilador** — ele não "vê dentro" do que você escreveu, só confia no que você declarou nos três campos. Esquecer de listar um registrador modificado na clobber list é uma fonte clássica de bugs extremamente difíceis de rastrear (o compilador reusa um registrador achando que está livre, mas seu assembly mudou ele).

## Quando isso é usado de verdade
- Acessar instruções de CPU muito específicas sem esperar o compilador "descobrir" sozinho (ex: `rdtsc` para ler o contador de ciclos da CPU, ou instruções de criptografia dedicadas como `AES-NI`).
- Código de sistema operacional / kernel, onde é preciso manipular registradores de controle que C não modela (registradores de segmento, interrupções).
- Otimizações extremas e muito específicas, quando o compilador comprovadamente não gera o código ideal sozinho (raro hoje em dia — compiladores modernos costumam ser melhores que humanos nisso).

## Alternativa mais segura: intrínsecos (intrinsics)
Para a maioria dos casos (principalmente SIMD), existe uma alternativa mais segura que o assembly inline cru: **funções intrínsecas**, que parecem funções C normais mas o compilador as traduz direto para a instrução assembly correspondente, mantendo type-checking e sem quebrar as garantias do compilador:
```c
#include <immintrin.h>
__m128 a = _mm_load_ps(array1);   // vira uma instrução SSE, mas com sintaxe de função C
```
Na prática, hoje em dia, **intrínsecos são preferidos a assembly inline** sempre que existem para o que você precisa — só se recorre a assembly inline cru quando nem intrínseco cobre o caso.

## Ver também
- [[../01_Linguagem/Sintaxe_Intel_vs_ATT|Sintaxe Intel vs. AT&T]]
- [[SIMD|SIMD e vetorização]]
