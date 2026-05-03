# Doble sesgo en sistemas NeSy

!!! tip "TL;DR"
    En NeSy hay dos fuentes de sesgo: el componente neuronal puede extraer
    premisas sesgadas; el componente simbólico puede contener reglas u
    ontologías sesgadas. Juntas producen decisiones con apariencia de rigor.

## Dos vectores

| Vector | Origen | Riesgo |
|---|---|---|
| Sub-simbólico | Datos de entrenamiento, embeddings | Premisas sesgadas |
| Simbólico | Reglas, ontologías humanas | Sesgo formalizado |

## Por qué preocupa

El solver puede generar una prueba perfectamente válida a partir de premisas
contaminadas. La explicación formal puede aumentar la credibilidad de una
decisión injusta.

## Ver también

- [Explainability laundering](explainability-laundering.md)
- [Accountability](accountability.md)
- [Fragilidad de traducción](../analisis-critico/fragilidad-traduccion.md)
