# Tipo 1: Symbolic Neuro Symbolic

**Abreviación:** `Symbolic Neuro Symbolic`  
**Direccionalidad:** símbolos → red neuronal → símbolos  
**Escalabilidad a LLMs:** común como baseline

!!! tip "TL;DR"
    Es la forma nativa de un LLM: recibe texto, procesa en embeddings y devuelve
    texto. Parece razonar, pero no contiene un solver formal interno.

## Definición

El sistema recibe una entrada simbólica discreta, la transforma en
representaciones continuas y decodifica una salida simbólica. En LLMs, esto es
texto → embeddings → texto.

## Pipeline

```mermaid
flowchart LR
    A[Texto] --> B[Transformer]
    B --> C[Embeddings / pesos]
    C --> D[Texto]
```

## Fortalezas

- Flexible ante lenguaje natural.
- Escalable con datos y parámetros.
- Excelente para generación y adaptación contextual.

## Limitaciones

- Sin garantías formales.
- Propenso a alucinaciones.
- Difícil de auditar.

## Ver también

- [Fallas de LLMs](../fallas-llm/overview.md)
- [Tipo 4](tipo-4.md)
- [LLM vs NeSy](../comparativas/llm-vs-nesy.md)
