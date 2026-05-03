# Tipo 4: Neuro → Symbolic

**Abreviación:** `Neuro → Symbolic`  
**Direccionalidad:** LLM formaliza; solver razona  
**Escalabilidad a LLMs:** paradigma dominante

!!! tip "TL;DR"
    El LLM traduce lenguaje natural a un lenguaje formal como PDDL, FOL o
    SMT-LIB. El solver ejecuta el razonamiento. Es útil, pero sufre fragilidad
    de traducción.

## Definición

El componente neuronal actúa como analizador semántico. Produce una
representación formal que después procesa un motor determinista.

```mermaid
flowchart LR
    A[Lenguaje natural] --> B[LLM formaliza]
    B --> C[PDDL / FOL / SMT]
    C --> D[Solver]
    D --> E[Resultado verificado]
```

## Sistemas en este tipo

| Sistema | Lenguaje formal | Solver |
|---|---|---|
| [LLM+P](../sistemas/llm-p.md) | PDDL | Fast Downward |
| [DUPLEX](../sistemas/duplex.md) | PDDL vía esquema | Fast Downward |
| [Logic-LM](../sistemas/logic-lm.md) | FOL, SAT, CSP, LP | Prover9, Z3, Pyke |

## Limitación crítica

!!! warning "Soundness no transitiva"
    El solver puede ser correcto, pero el pipeline completo no lo es si el LLM
    traduce mal la intención del usuario.

## Ver también

- [Fragilidad de traducción](../analisis-critico/fragilidad-traduccion.md)
- [Schema-guided IE](../tecnicas/schema-guided-ie.md)
- [LLM+P](../sistemas/llm-p.md)
