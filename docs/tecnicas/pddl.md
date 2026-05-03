# PDDL

**Familia:** lenguaje formal de planificación  
**Usado por:** [LLM+P](../sistemas/llm-p.md), [DUPLEX](../sistemas/duplex.md)

!!! tip "TL;DR"
    PDDL representa objetos, estado inicial, metas y acciones con precondiciones
    y efectos. Permite que un planificador verifique si una secuencia de acciones
    es ejecutable.

## Estructura mínima

```lisp
(:objects robot box room1 room2)
(:init (robot_at room1) (box_at box room1))
(:goal (box_at box room2))
```

## Por qué importa en NeSy

El LLM traduce la intención humana a PDDL; el planificador calcula el plan. La
calidad de esta traducción determina si el solver resuelve el problema correcto.

## Ver también

- [LLM+P](../sistemas/llm-p.md)
- [DUPLEX](../sistemas/duplex.md)
- [Fragilidad de traducción](../analisis-critico/fragilidad-traduccion.md)
