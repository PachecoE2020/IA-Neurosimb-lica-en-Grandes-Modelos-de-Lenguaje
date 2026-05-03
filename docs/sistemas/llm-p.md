# LLM+P

**Año:** 2023  
**Tipo Kautz:** Tipo 4 (`Neuro → Symbolic`)  
**Componente simbólico:** Fast Downward  
**Paper:** Liu et al., arXiv:2304.11477

!!! tip "TL;DR"
    LLM+P usa el LLM para traducir una descripción en lenguaje natural a un
    problema PDDL. Fast Downward genera el plan. El LLM no planifica: formaliza
    y verbaliza.

## Problema que resuelve

Los usuarios describen objetivos en lenguaje natural; los planificadores
clásicos necesitan PDDL. LLM+P conecta ambos mundos.

## Arquitectura

```mermaid
flowchart LR
    A[Descripción NL] --> B[LLM + dominio PDDL + ejemplo]
    B --> C[problem.pddl]
    C --> D[Fast Downward]
    D --> E[Plan simbólico]
    E --> F[LLM verbaliza]
```

## Pasos

1. Se asume que el dominio PDDL ya existe.
2. El LLM completa objetos, estado inicial y meta.
3. Fast Downward busca un plan.
4. El LLM traduce el plan a lenguaje natural.

## Fortalezas

- Reutiliza planificadores maduros.
- Evita que el LLM planifique de extremo a extremo.
- Produce planes validables.

## Limitaciones

- Requiere dominio PDDL predefinido.
- Frágil ante predicados inventados u omisiones.
- No resuelve entornos abiertos sin ingeniería adicional.

## Ver también

- [DUPLEX](duplex.md)
- [PDDL](../tecnicas/pddl.md)
- [Fragilidad de traducción](../analisis-critico/fragilidad-traduccion.md)
