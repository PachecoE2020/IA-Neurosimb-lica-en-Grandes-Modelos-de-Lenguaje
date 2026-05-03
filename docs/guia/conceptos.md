# 1. Conceptos base

La IA neurosimbólica nace de una tensión sencilla: los modelos neuronales son
flexibles, pero no verificables; los sistemas simbólicos son verificables, pero
son rígidos. La pregunta central no es cuál de los dos paradigmas gana, sino
cómo repartir el trabajo para que el sistema completo sea más fiable.

Esta formulación sigue el marco del documento merged y se apoya en los surveys
de Wang et al. [1], Bhuyan et al. [2] y Sarker et al. [5]. La metáfora
Sistema 1/Sistema 2 se toma de Kahneman [6], pero se usa aquí como analogía de
diseño, no como afirmación cognitiva fuerte sobre los LLMs.

!!! info "Idea clave"
    En una arquitectura NeSy-LLM bien diseñada, el componente neuronal no debe
    cargar con todo el razonamiento. Su papel típico es interpretar lenguaje
    natural, extraer información o proponer hipótesis. El componente simbólico
    se encarga de validar, buscar, deducir o planificar.

## Dos formas de inteligencia artificial

| Paradigma | Qué hace bien | Dónde falla |
|---|---|---|
| Conexionista | Aprende patrones desde datos, tolera ruido, interpreta lenguaje natural. | No garantiza verdad, consistencia ni trazabilidad formal. |
| Simbólico | Aplica reglas explícitas, produce pruebas, permite verificación. | Necesita entradas formales limpias y conocimiento escrito a mano. |

Un LLM pertenece al lado conexionista. Convierte texto en vectores, procesa
relaciones estadísticas y vuelve a generar texto. Puede producir una explicación
convincente, pero esa explicación no es una prueba formal. Un solver simbólico,
en cambio, no "entiende" lenguaje natural, pero sí puede comprobar si una
fórmula, un plan o una prueba satisface reglas estrictas.

## El problema del grounding

El *symbol grounding* pregunta cómo se conectan los símbolos con aquello que
significan. Un sistema formal puede manipular `Doctor(Ana)` y
`Professional(Ana)`, pero la lógica por sí sola no sabe qué es Ana ni qué es ser
profesional. Un LLM puede usar esas palabras de forma fluida, pero tampoco tiene
un anclaje causal directo con el mundo.

En los sistemas NeSy-LLM, el grounding aparece en la interfaz:

```mermaid
flowchart LR
    A["Texto del usuario"] --> B["Interpretación neuronal"]
    B --> C["Símbolos formales"]
    C --> D["Razonamiento simbólico"]
    D --> E["Respuesta o prueba"]
```

El paso delicado es `B -> C`. Si el LLM traduce mal el texto, el solver puede
razonar perfectamente sobre un problema equivocado.

## Sistema 1 y Sistema 2

La metáfora de Kahneman ayuda a entender el reparto:

- **Sistema 1:** rápido, intuitivo, asociativo. En esta wiki corresponde al LLM
  o al componente neuronal.
- **Sistema 2:** lento, deliberativo, estructurado. Corresponde al solver,
  planificador o motor deductivo.

La arquitectura NeSy no dice que el Sistema 1 sea inútil. Dice que es peligroso
usarlo como único juez en tareas que requieren garantías. El LLM puede proponer;
el solver debe comprobar.

## Ejemplo mínimo

Problema en lenguaje natural:

> Todos los médicos son profesionales. Ana es médica. ¿Ana es profesional?

Un LLM puede contestar "sí" porque el patrón textual es común. Un pipeline NeSy
lo haría de forma más auditable:

1. El LLM formaliza:

```text
forall x: Doctor(x) -> Professional(x)
Doctor(Ana)
query Professional(Ana)
```

2. Un solver lógico verifica si la conclusión se sigue de las premisas.
3. El sistema verbaliza el resultado.

La diferencia no está en que la respuesta sea más larga, sino en que existe un
mecanismo externo que puede comprobar la inferencia.

## Lo que NeSy intenta evitar

| Modo de fallo del LLM | Qué aporta lo simbólico |
|---|---|
| Alucinación factual | Verificación contra reglas o base de conocimiento. |
| Contradicción lógica | Consistencia formal. |
| Plan plausible pero imposible | Validación de precondiciones y efectos. |
| Cálculo incorrecto | Ejecución o solver externo. |
| Explicación opaca | Árbol de prueba o traza auditable. |

## Evidencia mínima

El merged no defiende NeSy solo como intuición filosófica. Lo conecta con
resultados empíricos:

| Fenómeno | Evidencia resumida |
|---|---|
| Planificación frágil | En PlanBench/Blocksworld, GPT-4 con chain-of-thought ronda ~35% de éxito, frente a ~97-100% de planificadores clásicos sobre PDDL correcto [16]. |
| Deducción formal limitada | En FOLIO, GPT-4 con CoT queda alrededor de ~70-78% según configuración; Logic-LM mejora al usar solvers externos, pero no alcanza la fiabilidad de una formalización manual correcta [9]. |
| Geometría formal | AlphaGeometry2 resuelve 84% de IMO Geometry 2000-2024, con pruebas verificadas por DDAR [15]. |

Estos números no significan que todos los LLMs fallen siempre ni que todo solver
sea perfecto. Significan algo más preciso: cuando la tarea exige garantías
formales, la arquitectura debe separar generación flexible y verificación.

## Errores frecuentes

!!! warning "NeSy no significa siempre lo mismo"
    No todo sistema que mezcla un LLM con una herramienta es automáticamente
    neurosimbólico fuerte. La pregunta importante es si hay representación
    formal, verificación y separación clara de responsabilidades.

!!! warning "Chain-of-thought no es prueba"
    Una cadena de razonamiento generada por un LLM puede ser útil como pista,
    pero no tiene garantías formales. Puede sonar lógica y seguir siendo falsa.

!!! warning "El solver no salva una mala formalización"
    Si el LLM traduce mal la tarea, el solver resolverá otra tarea. Ese es el
    punto crítico de la mayoría de pipelines modernos.

## Próximo capítulo

Ahora que la motivación está clara, sigue con [Taxonomía de Kautz](taxonomia.md)
para aprender a clasificar arquitecturas sin mezclar roles funcionales con tipos
taxonómicos.
