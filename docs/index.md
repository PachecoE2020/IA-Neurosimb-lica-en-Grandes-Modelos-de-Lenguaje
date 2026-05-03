# IA Neurosimbólica + LLMs

Una wiki sobre cómo combinar Grandes Modelos de Lenguaje con sistemas de
razonamiento formal: taxonomía, sistemas concretos, benchmarks, cuellos de
botella y riesgos éticos.

!!! tip "TL;DR"
    Los LLMs son buenos interpretando lenguaje natural, pero frágiles al razonar
    formalmente. Los sistemas simbólicos son verificables, pero necesitan
    entradas formales. La IA neurosimbólica los combina: el componente neuronal
    traduce o propone; el componente simbólico verifica, planifica o deduce.

## Por dónde empezar

- Si nunca has oído hablar de NeSy: [¿Qué es la IA neurosimbólica?](overview/que-es-nesy.md)
- Si quieres el mapa conceptual: [Taxonomía de Kautz](taxonomia/kautz-overview.md)
- Si buscas sistemas concretos: [LLM+P](sistemas/llm-p.md), [Logic-LM](sistemas/logic-lm.md), [AlphaGeometry2](sistemas/alphageometry2.md)
- Si te interesan los límites: [Fragilidad de traducción](analisis-critico/fragilidad-traduccion.md)
- Si te preocupa la dimensión social: [Explainability laundering](etica/explainability-laundering.md)

## La idea en 30 segundos

```mermaid
flowchart LR
    A[Lenguaje natural] --> B[LLM / modelo neuronal]
    B --> C[Representación formal<br/>PDDL · FOL · SMT]
    C --> D[Solver / planificador<br/>Z3 · Fast Downward · DDAR]
    D --> E[Resultado verificable]
    E --> F[Verbalización o prueba auditable]
```

## Estructura de la wiki

| Bloque | Qué contiene |
|---|---|
| [Visión general](overview/que-es-nesy.md) | Motivación, *symbol grounding* y marco dual-process. |
| [Taxonomía](taxonomia/kautz-overview.md) | Los seis tipos de Kautz y su mapeo a LLMs. |
| [Sistemas](sistemas/llm-p.md) | LLM+P, DUPLEX, Logic-LM, CEGIS, AlphaGeometry2 y NELLIE. |
| [Técnicas](tecnicas/self-refinement.md) | PDDL, SMT, self-refinement, schema-guided IE y construcciones auxiliares. |
| [Análisis crítico](analisis-critico/latencia.md) | Latencia, fragilidad de traducción y trade-off soundness/generalidad. |
| [Ética](etica/doble-sesgo.md) | Sesgo híbrido, accountability y legitimación por explicabilidad. |

## Ver también

- [Glosario](glosario.md)
- [Bibliografía](bibliografia.md)
- [Matriz funcional](comparativas/matriz-funcional.md)
- [PlanBench](benchmarks/planbench.md)
