# 6. Fragilidad y límites

La integración neurosimbólica mejora la fiabilidad, pero no elimina el problema
de raíz. Muchas veces solo desplaza el punto frágil: el razonamiento simbólico
puede ser correcto, mientras que la traducción que lo alimenta puede ser mala.

!!! warning "Pregunta central"
    No basta con preguntar si el solver resolvió el problema. Hay que preguntar
    si el problema formal era realmente el problema que el usuario quería
    resolver.

## Tres cuellos de botella

### 1. Fragilidad de traducción

El LLM convierte lenguaje natural en símbolos. Puede fallar de cuatro formas:

| Error | Ejemplo | Resultado |
|---|---|---|
| Sintaxis inválida | Paréntesis roto en PDDL. | El parser falla. |
| Predicado inventado | `AtBox` cuando el dominio solo acepta `box_at`. | El solver rechaza. |
| Omisión | Falta una precondición importante. | El plan puede ser inválido en el mundo real. |
| Desviación semántica | Formaliza una meta parecida, no la meta real. | El solver da una respuesta rigurosa pero equivocada. |

La sintaxis se detecta con facilidad. La desviación semántica es mucho más
grave porque puede pasar desapercibida.

### 2. Latencia

Los sistemas NeSy-LLM suelen hacer varias llamadas:

1. llamada al LLM para formalizar;
2. validación sintáctica;
3. llamada al solver;
4. posible reparación;
5. nueva llamada al LLM;
6. nueva llamada al solver.

En tareas offline, como demostrar geometría olímpica, esto es aceptable. En
robótica reactiva o sistemas de control en tiempo real, puede ser problemático.

El merged resume esta limitación con una tabla aproximada: LLM puro con CoT
puede tardar ~1-10 s; Logic-LM con self-refinement ~10-60 s; DUPLEX ~10-90 s;
AlphaGeometry2 puede ir de minutos a horas por problema difícil [8], [9], [14],
[15]. Estas cifras no son universales, pero sí capturan el patrón: la
verificación externa mejora fiabilidad a costa de llamadas, búsqueda y latencia.

### 3. Soundness frente a generalidad

Cuanto más formal es el sistema, más garantías ofrece, pero más estrecho es el
dominio.

| Sistema | Soundness | Generalidad |
|---|---|---|
| Z3 sobre SMT bien formalizado | Muy alta | Baja a media |
| Fast Downward sobre PDDL | Alta | Media |
| DDAR en geometría | Muy alta | Baja |
| NELLIE con lenguaje natural | Media | Alta |
| LLM puro | Baja | Muy alta |

Este trade-off es inevitable. No hay una arquitectura que sea universal,
rápida, flexible, interpretable y formalmente sound a la vez.

## Mitigaciones

| Problema | Mitigación | Limitación |
|---|---|---|
| Sintaxis rota | Parsers, gramáticas, JSON Schema. | No detectan intención equivocada. |
| Predicados inventados | Vocabulario cerrado y tipos. | Requiere diseño por dominio. |
| Omisión de premisas | Preguntas aclaratorias, validadores, tests. | Puede aumentar interacción. |
| Mala solución candidata | CEGIS y contraejemplos. | Necesita especificación formal. |
| Búsqueda explosiva | Heurísticas neuronales, caché, límites. | Puede perder completitud práctica. |

!!! note "Qué sí y qué no corrigen estas mitigaciones"
    Parsers, JSON Schema y vocabularios cerrados corrigen errores sintácticos.
    No demuestran que la formalización capture la intención real del usuario.
    Esta diferencia es una de las tesis críticas del merged.

## Checklist crítico

Antes de confiar en un sistema NeSy-LLM, revisa:

- ¿El dominio formal está escrito a mano o generado por el LLM?
- ¿Existe un vocabulario cerrado de predicados y tipos?
- ¿Se valida la sintaxis antes del solver?
- ¿Se valida que la formalización capture la intención del usuario?
- ¿El sistema guarda una traza auditable?
- ¿Hay límite de iteraciones en el self-refinement?
- ¿Qué pasa si el solver no encuentra solución?
- ¿El resultado se presenta como certeza total o como salida condicionada por premisas?

## El peligro de la falsa seguridad

Una salida con símbolos, pruebas y tablas puede parecer más rigurosa que una
respuesta normal de un LLM. Pero si las premisas vienen de una extracción
neuronal sesgada o incompleta, la prueba puede legitimar un error.

```mermaid
flowchart LR
    A["Dato mal extraído"] --> B["Premisa formal"]
    B --> C["Solver razona correctamente"]
    C --> D["Conclusión aparentemente rigurosa"]
```

La parte simbólica puede hacer que el error parezca más serio, no menos.

## Próximo capítulo

Sigue con [Ética y accountability](etica.md), donde esta falsa seguridad se
analiza como problema de sesgo, transparencia y responsabilidad.
