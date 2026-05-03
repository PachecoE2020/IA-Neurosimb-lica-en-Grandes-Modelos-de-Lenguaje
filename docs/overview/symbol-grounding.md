# El problema del *symbol grounding*

!!! tip "TL;DR"
    El *symbol grounding problem* pregunta cómo adquieren significado los
    símbolos. En LLMs, las palabras se anclan a patrones estadísticos, no a una
    semántica causal o formal. Por eso pueden generar pasos plausibles pero
    lógicamente inválidos.

## Harnad en una página

Stevan Harnad formuló el problema en 1990: un sistema que solo manipula símbolos
según reglas sintácticas no adquiere automáticamente semántica intrínseca. Puede
operar sobre tokens, pero eso no implica que esos tokens estén anclados al mundo
o a una teoría formal.

## Cómo aparece en LLMs

Los LLMs proyectan texto a espacios vectoriales continuos. Esos *embeddings*
capturan relaciones estadísticas ricas, pero no garantizan que una respuesta
respete axiomas, precondiciones o restricciones de un dominio.

!!! warning "Falla típica"
    Un LLM puede producir una demostración matemática porque ha visto textos
    parecidos, no porque su arquitectura esté obligada a preservar los axiomas.

## La salida neurosimbólica

NeSy reduce el daño asignando funciones distintas:

- El LLM interpreta lenguaje natural.
- El sistema simbólico opera sobre símbolos con semántica definida.
- Los errores del LLM se intentan detectar con validadores, solvers o bucles de
  reparación.

## Ver también

- [Fallas estructurales de los LLMs](../fallas-llm/overview.md)
- [Fragilidad de traducción](../analisis-critico/fragilidad-traduccion.md)
- [PlanBench](../benchmarks/planbench.md)
