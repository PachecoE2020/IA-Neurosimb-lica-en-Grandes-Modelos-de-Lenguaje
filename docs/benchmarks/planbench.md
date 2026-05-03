# PlanBench

**Tarea:** planificación clásica con LLMs  
**Dominio destacado:** Blocksworld  
**Métrica:** éxito del plan / validez

!!! tip "TL;DR"
    PlanBench muestra que los LLMs pueden producir planes plausibles pero
    inválidos. Los planificadores clásicos siguen siendo mucho más fiables
    cuando reciben especificaciones formales correctas.

## Qué mide

Evalúa si un modelo puede generar planes que satisfagan precondiciones y metas
en dominios de planificación.

## Por qué importa

Si renombrar acciones o aumentar el horizonte destruye el rendimiento del LLM,
eso sugiere reconocimiento superficial de patrones más que planificación
composicional robusta.

## Ver también

- [LLM+P](../sistemas/llm-p.md)
- [PDDL](../tecnicas/pddl.md)
- [Fallas de LLMs](../fallas-llm/overview.md)
