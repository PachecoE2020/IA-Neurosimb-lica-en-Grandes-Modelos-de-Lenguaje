# Tipo 3: Neuro ∪ Symbolic

**Abreviación:** `Neuro ∪ Symbolic`  
**Direccionalidad:** acoplamiento bidireccional  
**Escalabilidad a LLMs:** limitada

!!! tip "TL;DR"
    El componente neuronal y el simbólico interactúan de forma diferenciable:
    el motor lógico no solo verifica, también puede producir señal de aprendizaje.
    Es potente, pero difícil de escalar a LLMs.

## Definición

El modelo neuronal produce probabilidades sobre hechos; el razonador simbólico
usa esos hechos y devuelve una señal que puede afectar al entrenamiento. Un
ejemplo clásico es DeepProbLog.

## Pipeline conceptual

```mermaid
flowchart LR
    A[Red neuronal] --> B[Probabilidades sobre hechos]
    B --> C[Razonador lógico-probabilístico]
    C --> D[Prueba / pérdida]
    D --> A
```

## Limitaciones

- Retropropagar a través de inferencia discreta es costoso.
- Los ejemplos publicados suelen usar redes pequeñas.
- No es el patrón dominante para LLMs frontera.

## Ver también

- [Tipo 5](tipo-5.md)
- [Coste computacional](../analisis-critico/latencia.md)
- [Bibliografía](../bibliografia.md)
