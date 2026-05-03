<section class="nesy-hero">
  <p class="nesy-kicker">Wiki didáctica · IA Neurosimbólica · LLMs</p>
  <h1>IA Neurosimbólica + LLMs</h1>
  <p>
    Una guía para entender cómo los modelos de lenguaje pueden trabajar con
    solvers, planificadores y motores deductivos sin confundir texto plausible
    con razonamiento formal.
  </p>
  <div class="nesy-actions">
    <a class="nesy-button primary" href="guia/">Seguir la ruta guiada</a>
    <a class="nesy-button" href="guia/conceptos/">Leer conceptos base</a>
    <a class="nesy-button" href="guia/casos/">Ver sistemas concretos</a>
  </div>
</section>

!!! tip "La tesis de la wiki"
    Un LLM es útil para interpretar, traducir o proponer. Un sistema simbólico
    es útil para verificar, planificar o deducir. La IA neurosimbólica funciona
    cuando esa división de responsabilidades está diseñada con cuidado.

<div class="nesy-statline">
  <div class="nesy-stat">
    <strong>6</strong>
    <span>tipos de Kautz explicados con ejemplos y errores frecuentes</span>
  </div>
  <div class="nesy-stat">
    <strong>3</strong>
    <span>familias de sistemas: planificación, lógica y búsqueda de pruebas</span>
  </div>
  <div class="nesy-stat">
    <strong>1</strong>
    <span>pregunta crítica: ¿el solver resolvió el problema correcto?</span>
  </div>
</div>

## Lee esto como un recorrido

<div class="reading-path">
  <a class="path-step" href="guia/conceptos/">
    <strong>1. Conceptos base</strong>
    <span>LLMs, sistemas simbólicos, grounding y Sistema 1/Sistema 2.</span>
  </a>
  <a class="path-step" href="guia/taxonomia/">
    <strong>2. Taxonomía</strong>
    <span>Los seis tipos de Kautz y la trampa de AlphaGeometry2.</span>
  </a>
  <a class="path-step" href="guia/pipelines/">
    <strong>3. Pipelines</strong>
    <span>Cómo se pasa de lenguaje natural a PDDL, FOL, SMT o pruebas.</span>
  </a>
  <a class="path-step" href="guia/casos/">
    <strong>4. Sistemas reales</strong>
    <span>LLM+P, DUPLEX, Logic-LM, CEGIS, AlphaGeometry2 y NELLIE.</span>
  </a>
  <a class="path-step" href="guia/evidencia/">
    <strong>5. Evidencia</strong>
    <span>Resultados de PlanBench, Logic-LM, LLM+P y AlphaGeometry2.</span>
  </a>
  <a class="path-step" href="guia/fragilidad/">
    <strong>6. Crítica técnica</strong>
    <span>Traducción frágil, latencia y trade-off soundness/generalidad.</span>
  </a>
  <a class="path-step" href="guia/etica/">
    <strong>7. Ética</strong>
    <span>Sesgo híbrido, explainability laundering y accountability parcial.</span>
  </a>
</div>

## La idea en una figura

```mermaid
flowchart LR
    A["Lenguaje natural"] --> B["LLM: interpreta o formaliza"]
    B --> C["Representación formal"]
    C --> D["Solver / planificador / motor deductivo"]
    D --> E["Resultado verificable"]
    E --> F{"¿Fallo o inconsistencia?"}
    F -- Sí --> G["Feedback al LLM"]
    G --> B
    F -- No --> H["Respuesta, plan o prueba auditable"]
```

## Qué contiene cada zona

<div class="nesy-grid">
  <article class="nesy-card">
    <h3>Ruta guiada</h3>
    <p>Capítulos largos y didácticos. Úsala como lectura principal.</p>
    <a href="guia/">Entrar a la ruta</a>
  </article>
  <article class="nesy-card">
    <h3>Sistemas</h3>
    <p>Fichas de arquitecturas concretas para consultar rápido.</p>
    <a href="sistemas/alphageometry2/">Ver AlphaGeometry2</a>
  </article>
  <article class="nesy-card">
    <h3>Referencia</h3>
    <p>Taxonomía, técnicas, benchmarks, comparativas y páginas de apoyo.</p>
    <a href="taxonomia/kautz-overview/">Abrir referencia</a>
  </article>
</div>

## Si solo tienes diez minutos

1. Lee [Conceptos base](guia/conceptos.md).
2. Mira la tabla de [Taxonomía](guia/taxonomia.md).
3. Lee la explicación de [AlphaGeometry2](guia/casos.md#alphageometry2).
4. Revisa [Evidencia empírica](guia/evidencia.md).
5. Termina con [Fragilidad y límites](guia/fragilidad.md).

## Material de consulta rápida

| Necesitas aclarar | Página |
|---|---|
| Vocabulario técnico | [Glosario](glosario.md) |
| Papers y fuentes | [Bibliografía](bibliografia.md) |
| Cifras del merged | [Evidencia empírica](guia/evidencia.md) |
| Diferencia LLM puro vs NeSy | [LLM vs NeSy](comparativas/llm-vs-nesy.md) |
| Por qué falla la interfaz | [Fragilidad de traducción](analisis-critico/fragilidad-traduccion.md) |
| Cómo clasificar AlphaGeometry2 | [Tipo 2](taxonomia/tipo-2.md) |
