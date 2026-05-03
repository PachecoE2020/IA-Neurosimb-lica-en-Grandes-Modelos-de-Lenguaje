# Explainability laundering

!!! tip "TL;DR"
    Una cadena de prueba simbólica puede legitimar premisas sesgadas extraídas
    por un LLM. El sistema parece explicable, pero la explicación limpia una
    entrada contaminada.

## Definición

*Explainability laundering* ocurre cuando la parte simbólica produce una traza
auditable que da apariencia de rigor a hechos obtenidos por un componente
neuronal opaco o sesgado.

## Caso típico

```mermaid
flowchart LR
    A[Historia clínica] --> B[LLM extrae predicados]
    B --> C[Predicado sesgado]
    C --> D[Reglas clínicas]
    D --> E[Decisión explicable pero injusta]
```

## Por qué es peor que un LLM puro

Un score opaco suele generar sospecha. Un árbol de prueba puede parecer
objetivo, aunque sus premisas no lo sean.

## Mitigación

Auditar no solo la regla final, sino también los predicados extraídos y su
correlación con variables protegidas.

## Ver también

- [Doble sesgo](doble-sesgo.md)
- [Accountability](accountability.md)
- [Fragilidad de traducción](../analisis-critico/fragilidad-traduccion.md)
