# Undefined Behavior

Estudar exemplos:

- acesso fora dos limites;
- use-after-free;
- double free;
- dereferência de `nullptr`;
- signed overflow;
- data race;
- lifetime inválido;
- strict aliasing;
- iterator invalidation.

## Regra

Comportamento indefinido não é simplesmente "deu erro"; o compilador pode assumir que ele nunca acontece.
