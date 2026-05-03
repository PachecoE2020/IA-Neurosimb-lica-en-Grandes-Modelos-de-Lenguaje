# Fallas estructurales de los LLMs

!!! tip "TL;DR"
    Los LLMs producen lenguaje plausible, pero no garantizan verdad, consistencia
    ni cumplimiento de restricciones. Sus fallas críticas aparecen en
    planificación, deducción formal, generalización composicional y auditabilidad.

## Cinco fallas centrales

| Falla | Qué significa | Mitigación NeSy |
|---|---|---|
| Opacidad | El conocimiento está distribuido en pesos | Trazas simbólicas |
| Alucinación | Texto correcto en forma, falso en contenido | Verificación externa |
| Multi-paso | Errores locales se acumulan | Solver / planificador |
| Deducción formal | Fallos en reglas como modus ponens | FOL / theorem prover |
| Composicionalidad | No recombina reglas de forma robusta | Lenguajes formales |

## Ejemplo: planificación

En benchmarks como PlanBench, los LLMs con *Chain-of-Thought* pueden producir
planes plausibles pero inválidos. Un planificador clásico, si recibe PDDL
correcto, verifica precondiciones y efectos de cada acción.

## Ver también

- [PlanBench](../benchmarks/planbench.md)
- [LLM vs NeSy](../comparativas/llm-vs-nesy.md)
- [Ventajas simbólicas](../ventajas-simbolicas/overview.md)
