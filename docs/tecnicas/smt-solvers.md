# SMT solvers y Z3

**Familia:** solver formal  
**Usado por:** [Logic-LM](../sistemas/logic-lm.md), [CEGIS](../sistemas/cegis.md)

!!! tip "TL;DR"
    Un solver SMT decide satisfacibilidad bajo teorías como enteros, arrays o
    bit-vectors. En NeSy sirve para verificar candidatos y producir modelos o
    contraejemplos.

## SAT vs SMT

SAT razona sobre proposiciones booleanas. SMT extiende SAT con teorías
matemáticas: aritmética, igualdad, funciones, arrays, etc.

## Ejemplo conceptual

```text
assert x > 0
assert y = x + 1
query y > 1
```

El solver puede decidir si la conclusión se sigue o producir un modelo que la
refuta.

## Ver también

- [CEGIS](../sistemas/cegis.md)
- [Logic-LM](../sistemas/logic-lm.md)
- [Logic-LM vs CEGIS](../comparativas/logic-lm-vs-cegis.md)
