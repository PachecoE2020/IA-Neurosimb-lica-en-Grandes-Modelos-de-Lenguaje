# Taxonomía de Kautz

!!! tip "TL;DR"
    Kautz organiza los sistemas neurosimbólicos en seis tipos según cómo se
    acoplan lo neuronal y lo simbólico. Para LLMs, los tipos más relevantes hoy
    son Tipo 2, Tipo 4 y, en entrenamiento, Tipo 5.

## Los seis tipos

| Tipo | Abreviación | Idea | Ejemplo en esta wiki |
|---|---|---|---|
| [1](tipo-1.md) | `Symbolic Neuro Symbolic` | Entrada/salida simbólica con procesamiento neuronal | LLM vanilla |
| [2](tipo-2.md) | `Symbolic[Neuro]` | Solver gobierna, red como subrutina | AlphaGeometry2 |
| [3](tipo-3.md) | `Neuro ∪ Symbolic` | Acoplamiento bidireccional diferenciable | DeepProbLog |
| [4](tipo-4.md) | `Neuro → Symbolic` | LLM formaliza, solver razona | LLM+P, Logic-LM |
| [5](tipo-5.md) | `NeuroSYMBOLIC` | Reglas en pérdida o arquitectura | Semantic Loss, LTN |
| [6](tipo-6.md) | `Neuro[Symbolic]` | Fusión intrínseca | Horizonte teórico |

![Taxonomía de Kautz](../assets/taxonomy.png){ width="620" }

## Cómo leerla en LLMs

La taxonomía original no fue diseñada exclusivamente para LLMs. Por eso conviene
separar dos cosas:

- **Taxonomía formal:** ubicación de una arquitectura según Kautz.
- **Rol funcional:** si el modelo neuronal formaliza, repara, propone o guía.

!!! warning "Confusión frecuente"
    AlphaGeometry2 no es un pipeline `Neuro → Symbolic`: su motor DDAR conserva
    el control de la búsqueda. Por eso encaja en Tipo 2.

## Ver también

- [Tipo 2](tipo-2.md)
- [Tipo 4](tipo-4.md)
- [AlphaGeometry2](../sistemas/alphageometry2.md)
- [Matriz funcional](../comparativas/matriz-funcional.md)
