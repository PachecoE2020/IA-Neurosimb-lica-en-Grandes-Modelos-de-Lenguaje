# Tipo 5: NeuroSYMBOLIC

**Abreviación:** `NeuroSYMBOLIC`  
**Direccionalidad:** reglas simbólicas durante entrenamiento  
**Escalabilidad a LLMs:** abierta

!!! tip "TL;DR"
    Las reglas lógicas se integran en la arquitectura o función de pérdida. La
    red aprende a respetar restricciones, pero no obtiene garantías formales en
    runtime.

## Definición

Marcos como Logic Tensor Networks, Logical Neural Networks y Semantic Loss
relajan reglas lógicas hacia funciones diferenciables que penalizan violaciones
durante el entrenamiento.

## Fortalezas

- Inyecta conocimiento de dominio.
- Reduce contradicciones en ciertos entornos.
- No requiere solver externo en inferencia.

## Limitaciones

- Coste alto de *weighted model counting*.
- No demostrado a escala de LLM frontera.
- Aproxima lógica, no la ejecuta como garantía determinista.

## Ver también

- [Tipo 3](tipo-3.md)
- [Latencia y coste](../analisis-critico/latencia.md)
- [Bibliografía](../bibliografia.md)
