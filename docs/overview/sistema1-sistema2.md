# Sistema 1 / Sistema 2

!!! tip "TL;DR"
    La metáfora dual-process ayuda a explicar NeSy: LLM como Sistema 1
    rápido/intuitivo; solver como Sistema 2 lento/deliberativo. Es útil para
    enseñar, pero no debe tomarse como equivalencia cognitiva literal.

## El marco original

Kahneman distingue entre un Sistema 1 rápido, asociativo e intuitivo, y un
Sistema 2 más lento, deliberativo y costoso. La literatura NeSy usa esta
metáfora para explicar por qué combinar LLMs y solvers tiene sentido.

## Mapeo a NeSy

| Rasgo | LLM | Solver simbólico |
|---|---|---|
| Velocidad | Alta | Variable, a menudo costosa |
| Naturaleza | Probabilística | Formal / determinista |
| Fortaleza | Lenguaje natural, patrones | Pruebas, planes, restricciones |
| Riesgo | Alucinación | Fragilidad ante input malformado |

## Crítica honesta

La metáfora no es perfecta. Un LLM puede hacer tareas que parecen deliberativas
para humanos, y un solver no es literalmente un Sistema 2 psicológico. Aun así,
la metáfora ayuda a comunicar la separación de responsabilidades.

## Ver también

- [DUPLEX](../sistemas/duplex.md)
- [¿Qué es NeSy?](que-es-nesy.md)
- [Matriz funcional](../comparativas/matriz-funcional.md)
