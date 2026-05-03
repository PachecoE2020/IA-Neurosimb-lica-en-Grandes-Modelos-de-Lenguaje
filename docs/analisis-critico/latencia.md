# Latencia y coste computacional

!!! tip "TL;DR"
    NeSy añade llamadas a solvers, validadores y a veces múltiples rondas de
    LLM. No todos los sistemas son igual de lentos: LLM+P suele ser una pasada;
    Logic-LM, CEGIS y AlphaGeometry2 pueden iterar muchas veces.

## Tabla rápida

| Sistema | Patrón | Riesgo de latencia |
|---|---|---|
| LLM+P | 1 llamada al planificador | Medio |
| DUPLEX | extracción + posible reparación | Medio |
| Logic-LM | 1-N rondas | Alto |
| CEGIS | N candidatos | Alto |
| AlphaGeometry2 | búsqueda profunda | Muy alto |

## Lectura correcta

El cuello de botella no es uniforme. Depende de si el sistema es:

- pipeline de una pasada;
- bucle de reparación;
- búsqueda profunda guiada por heurísticas.

## Ver también

- [Self-refinement](../tecnicas/self-refinement.md)
- [Logic-LM](../sistemas/logic-lm.md)
- [AlphaGeometry2](../sistemas/alphageometry2.md)
