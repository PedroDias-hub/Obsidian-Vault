# Como um Buffer Overflow Acontece (Conceito)

Esta nota é conceitual — o objetivo é entender **por que** esse tipo de vulnerabilidade existe, como consequência direta de como a pilha funciona (ver [[../01_Linguagem/Stack_Pilha|A pilha]]), e quais defesas existem hoje. Não é um tutorial de exploração — é a base pra entender por que certas práticas de programação são exigidas em código C/C++, e por que linguagens modernas (Rust, Java, Python) eliminam essa classe inteira de bug por design.

## Relembrando o layout da pilha
Dentro de uma função, variáveis locais e o **endereço de retorno** (colocado lá pelo `call`) convivem na mesma região de memória — a pilha:
```
Endereços altos
┌─────────────────────┐
│  endereço de retorno  │  ← pra onde o `ret` vai saltar
├─────────────────────┤
│  RBP salvo             │
├─────────────────────┤
│  variável local (buffer)│  ← ex: um array/string local
└─────────────────────┘
Endereços baixos
```

## O problema
Em C, escrever além do tamanho de um array/buffer **não gera erro automaticamente** — a linguagem não verifica limites em tempo de execução (diferente de Java, Python, etc). Se uma função copia dados para um `buffer` local **sem checar o tamanho**, e a quantidade de dados excede o espaço reservado, a escrita continua "vazando" para a memória vizinha — que, no layout acima, é exatamente o `RBP` salvo e, principalmente, **o endereço de retorno**.

## Consequência
Se um atacante controla o conteúdo que estoura o buffer, ele pode controlar os bytes que sobrescrevem o endereço de retorno. Quando a função executa `ret`, em vez de voltar para onde deveria, o processador salta para o endereço (agora malicioso) que foi escrito ali — potencialmente desviando a execução do programa inteiro para código que o atacante controla.

Essa é a essência de um **buffer overflow de pilha** (stack buffer overflow), historicamente uma das classes de vulnerabilidade mais exploradas em software.

## Por que isso não é "culpa do assembly"
`ret` fazendo exatamente o que sempre fez (pop do endereço, salta pra lá) não é um bug — é o comportamento correto e documentado. O problema real é **código de mais alto nível (C) que confia em dados externos sem validar tamanho**. Assembly só expõe, sem esconder nada, a superfície onde isso pode dar errado.

## Defesas modernas (por que isso é bem mais difícil hoje)
- **Stack canaries**: o compilador insere um valor aleatório conhecido entre as variáveis locais e o endereço de retorno; antes do `ret`, o programa checa se esse valor ainda está intacto — se um overflow o alterou, o programa aborta em vez de continuar (proteção `-fstack-protector` no gcc, ligada por padrão hoje).
- **ASLR** (Address Space Layout Randomization): endereços de pilha, heap e bibliotecas mudam a cada execução, dificultando prever endereços válidos para redirecionar a execução.
- **NX bit / DEP** (No-eXecute / Data Execution Prevention): marca a região da pilha como **não-executável** — mesmo que um atacante consiga colocar código malicioso lá, o processador se recusa a executar instruções vindas dessa região.
- **Funções seguras**: preferir `strncpy`/`snprintf` (com limite explícito de tamanho) em vez de `strcpy`/`sprintf` (sem limite).
- **Linguagens memory-safe**: Rust, Java, Go, Python, etc., verificam limites de array em tempo de execução por padrão — essa classe de bug não existe nelas (ao custo de uma checagem extra, geralmente barata).

## Por que vale entender isso mesmo sem estudar segurança ofensiva
- Explica por que compiladores C modernos gritam warnings sobre `strcpy`, `gets`, `sprintf`.
- É a motivação real por trás de boa parte do design de linguagens modernas.
- Aparece constantemente em CVEs de software real — entender a causa raiz ajuda a ler relatórios de vulnerabilidade com propriedade.

## Ver também
- [[../01_Linguagem/Stack_Pilha|A pilha]]
- [[../01_Linguagem/Funcoes_E_Convencoes_De_Chamada|Funções e convenções de chamada]]
