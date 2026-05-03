# IMO Geometry

**Tarea:** problemas de geometría de olimpiada  
**Métrica:** problemas resueltos con prueba verificable  
**Sistema destacado:** [AlphaGeometry2](../sistemas/alphageometry2.md)

!!! tip "TL;DR"
    AlphaGeometry2 alcanza 84% en problemas IMO Geometry 2000-2024, frente al
    54% de AlphaGeometry original. La prueba final es verificada por DDAR.

## Qué mide

Mide capacidad de producir pruebas geométricas, no solo respuestas finales. Eso
exige construcciones auxiliares y cierre deductivo.

## Resultados de referencia

| Sistema | Resultado |
|---|---:|
| AlphaGeometry | 54% |
| AlphaGeometry2 | 84% (42/50) |

## Por qué es relevante

IMO Geometry no mide conversación ni plausibilidad textual. Mide la capacidad de
producir una prueba geométrica verificable. Por eso es un benchmark especialmente
adecuado para defender la tesis neurosimbólica: el modelo neuronal propone
construcciones auxiliares, pero la validez final depende del motor deductivo
DDAR [15], [21].

!!! note "Relación con la taxonomía"
    Este resultado no convierte a AlphaGeometry2 en Tipo 4. Al contrario:
    refuerza su lectura como Tipo 2 `Symbolic[Neuro]`, porque el control de la
    prueba permanece en DDAR.

## Ver también

- [AlphaGeometry2](../sistemas/alphageometry2.md)
- [Construcciones auxiliares](../tecnicas/auxiliary-constructions.md)
- [AlphaGeometry2 vs NELLIE](../comparativas/alphageometry2-vs-nellie.md)
