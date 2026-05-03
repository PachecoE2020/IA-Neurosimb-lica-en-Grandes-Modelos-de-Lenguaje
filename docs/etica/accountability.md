# Accountability

!!! tip "TL;DR"
    Cuando un sistema NeSy falla, no siempre está claro si el error vino del
    LLM, de las reglas simbólicas, del solver o de la interfaz. Esa brecha
    complica la responsabilidad.

## Brecha de atribución

| Fuente de error | Ejemplo |
|---|---|
| Percepción neuronal | Entidad mal extraída |
| Formalización | Cuantificador equivocado |
| Reglas | Ontología sesgada |
| Integración | Feedback mal usado |

## Qué exige una auditoría seria

- Logs de extracción neuronal.
- Validación de predicados.
- Trazas del solver.
- Registro de iteraciones de self-refinement.

## Ver también

- [Doble sesgo](doble-sesgo.md)
- [Explainability laundering](explainability-laundering.md)
- [Ventajas simbólicas](../ventajas-simbolicas/overview.md)
