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

En el merged se usa PlanBench como evidencia contra una lectura demasiado
optimista de chain-of-thought. El punto no es que GPT-4 nunca pueda resolver
planes pequeños, sino que su rendimiento cae cuando aumenta el horizonte, se
renombran acciones o se exige validez formal.

## Resultado citado

| Configuración | Resultado aproximado citado en el merged |
|---|---:|
| GPT-4 + chain-of-thought en Blocksworld | ~35% |
| Planificador clásico sobre PDDL correcto | ~97-100% |

La comparación es importante porque cambia el criterio de éxito: no se evalúa
si el texto parece razonable, sino si el plan satisface precondiciones, efectos
y meta.

## Por qué importa

Si renombrar acciones o aumentar el horizonte destruye el rendimiento del LLM,
eso sugiere reconocimiento superficial de patrones más que planificación
composicional robusta.

## Ver también

- [LLM+P](../sistemas/llm-p.md)
- [PDDL](../tecnicas/pddl.md)
- [Fallas de LLMs](../fallas-llm/overview.md)
