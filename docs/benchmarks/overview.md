# Benchmarks

!!! tip "TL;DR"
    Los benchmarks muestran dónde los LLMs fallan y dónde los sistemas NeSy
    aportan valor: planificación, lógica formal, geometría olímpica y
    razonamiento composicional.

## Mapa rápido

| Benchmark | Qué mide | Sistemas relevantes |
|---|---|---|
| [PlanBench](planbench.md) | Planificación en dominios clásicos | LLM+P, DUPLEX |
| FOLIO / ProofWriter | Deducción formal | Logic-LM, LINC |
| [IMO Geometry](imo-geometry.md) | Pruebas geométricas olímpicas | AlphaGeometry2 |
| EntailmentBank | Árboles de explicación científica | NELLIE |

## Resultados usados en la wiki

| Benchmark | Resultado citado | Lectura correcta |
|---|---|---|
| PlanBench / Blocksworld | GPT-4 + CoT ~35% frente a ~97-100% de planificadores clásicos sobre PDDL correcto [16]. | Los LLMs producen planes plausibles, pero no garantizan validez. |
| FOLIO | GPT-4 + CoT ~70.6%; Logic-LM + GPT-4 ~78.9% [9]. | El solver externo mejora consistencia, pero la formalización sigue siendo cuello de botella. |
| ProofWriter | GPT-4 + CoT ~76%; Logic-LM + GPT-4 ~83% [9]. | El patrón se repite: mejora parcial, no garantía absoluta. |
| IMO Geometry 2000-2024 | AlphaGeometry2 resuelve 84% (42/50), frente a 54% del sistema original [15], [21]. | La combinación DDAR + heurística neuronal es especialmente fuerte en dominio cerrado. |

Estas cifras se centralizan en la [página de evidencia](../guia/evidencia.md)
para evitar que la wiki se convierta en una lista de números sin contexto.

## Ver también

- [LLM vs NeSy](../comparativas/llm-vs-nesy.md)
- [Fragilidad de traducción](../analisis-critico/fragilidad-traduccion.md)
