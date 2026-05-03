# LLM puro vs sistemas NeSy

!!! tip "TL;DR"
    Un LLM puro maximiza flexibilidad, pero no ofrece garantías. Un sistema NeSy
    sacrifica parte de esa flexibilidad para ganar verificación, trazabilidad y
    control de restricciones.

## Comparación rápida

| Criterio | LLM puro | NeSy |
|---|---|---|
| Lenguaje natural | Excelente | Excelente si usa LLM |
| Razonamiento formal | Frágil | Fuerte si la traducción es correcta |
| Trazabilidad | Baja | Media-alta |
| Latencia | Baja | Media-alta |
| Dominio abierto | Alto | Depende del esquema |

## Regla práctica

Usa LLM puro para tareas abiertas y de bajo riesgo. Usa NeSy cuando importan
precondiciones, consistencia, pruebas o auditabilidad.

## Ver también

- [Fallas de LLMs](../fallas-llm/overview.md)
- [Fragilidad de traducción](../analisis-critico/fragilidad-traduccion.md)
- [Tipo 4](../taxonomia/tipo-4.md)
