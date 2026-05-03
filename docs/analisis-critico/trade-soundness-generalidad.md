# Trade-off: soundness vs generalidad

!!! tip "TL;DR"
    Cuanto más formal y verificable es un sistema, más estrecho suele ser su
    dominio. AlphaGeometry2 es muy sound pero solo resuelve geometría; NELLIE es
    más general pero introduce ruido semántico.

## Mapa conceptual

| Sistema | Soundness | Generalidad |
|---|---|---|
| AlphaGeometry2 | Alta | Baja |
| Logic-LM | Media-alta | Media |
| NELLIE | Media | Alta |
| LLM puro | Baja | Alta |

## La intuición

Los lenguajes formales reducen ambigüedad, pero obligan a definir de antemano
el dominio. Cuanto más abierto es el lenguaje, más ruido entra en la inferencia.

## Ver también

- [AlphaGeometry2](../sistemas/alphageometry2.md)
- [NELLIE](../sistemas/nellie.md)
- [AlphaGeometry2 vs NELLIE](../comparativas/alphageometry2-vs-nellie.md)
