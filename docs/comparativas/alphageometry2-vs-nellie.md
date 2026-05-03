# AlphaGeometry2 vs NELLIE

!!! tip "TL;DR"
    AlphaGeometry2 es más sound y especializado: geometría formal con DDAR.
    NELLIE es más general: razonamiento sobre lenguaje natural con unificación
    semántica, pero menos verificable.

## Comparación

| Aspecto | AlphaGeometry2 | NELLIE |
|---|---|---|
| Dominio | Geometría olímpica | Ciencia / lenguaje natural |
| Búsqueda | Forward chaining + construcciones | Backward chaining |
| Verificación | DDAR | NLI + árbol de prueba |
| Soundness | Alta | Media |
| Generalidad | Baja | Alta |

## Lección

No hay integración gratis: cuanto más formal es el sistema, más estrecho suele
ser el dominio.

## Ver también

- [AlphaGeometry2](../sistemas/alphageometry2.md)
- [NELLIE](../sistemas/nellie.md)
- [Soundness vs generalidad](../analisis-critico/trade-soundness-generalidad.md)
