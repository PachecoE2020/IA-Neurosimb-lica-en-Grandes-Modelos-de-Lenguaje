## 4. Análisis Crítico: Cuellos de Botella y Fragilidad del Sistema

A pesar del prometedor potencial de las arquitecturas NeSy-LLM, su integración
en sistemas reales enfrenta limitaciones técnicas severas. Esta sección examina
los dos cuellos de botella más críticos: la latencia computacional y la fragilidad
inherente al proceso de traducción neurosimbólica.

---

### 4.1. Latencia y Cuellos de Botella Computacionales

Los pipelines NeSy-LLM no generan respuestas en una sola pasada de inferencia.
Requieren llamadas repetidas a solvers lógicos externos —como Z3 o Fast Downward—
en cada nodo del árbol de búsqueda o planificación. El coste se multiplica en cada
iteración del bucle de *Self-Refinement*, donde los errores del solver se reinyectan
como nuevos prompts al LLM [7, 8]. El resultado es una latencia acumulativa
inaceptable para aplicaciones en tiempo real.

La tabla siguiente resume el impacto de latencia según el tipo de sistema y la
estrategia de integración:

| Sistema | Estrategia de integración | Número de llamadas al solver | Viabilidad en tiempo real |
|---|---|---|---|
| LLM puro (CoT) | Ninguna | 0 | ✓ Alta |
| Logic-LM [8] | Inferencia + Self-Refinement | 1–N (iterativo) | ✗ Baja |
| LLM+P [7] | Planificador clásico offline | 1 (batch) | ~ Media (offline) |
| DUPLEX [3] | IE + PDDL + planificador | 1–2 | ~ Media |
| AlphaGeometry2 [4] | DDAR + búsqueda de prueba | N (árbol profundo) | ✗ Muy baja |

Este patrón de ejecución confina los sistemas NeSy-LLM, en la práctica, a tareas
de procesamiento por lotes o generación de pruebas matemáticas donde la latencia
no es un factor crítico. La introducción de técnicas de caché simbólico o compilación
parcial de problemas PDDL es un área de investigación activa, aunque no resuelve
el problema de fondo en dominios dinámicos.

---

### 4.2. Extrema Fragilidad de Traducción

El cuello de botella más profundo de los sistemas NeSy-LLM no es la velocidad,
sino la fiabilidad de la interfaz de traducción. Al convertir lenguaje natural a
representaciones formales —FOL, PDDL, SMT— el LLM puede generar fórmulas
sintácticamente inválidas, predicados inventados (*hallucinated predicates*) o
inconsistencias semánticas que el solver no puede resolver [1, 8].

La consecuencia es estructural: **una traducción inicial incorrecta destruye por
completo el flujo de inferencia simbólica subsecuente**. Los solvers operan sobre
representaciones formalmente correctas; si el input es malformado, el sistema no
puede producir ningún resultado útil, con independencia de la calidad de los
pasos posteriores.

El diagrama siguiente ilustra ambos caminos posibles a partir de la etapa de
traducción del LL

<svg width="100%" viewBox="0 0 680 340" role="img">
  <title>Caminos de éxito y fallo en la traducción neurosimbólica</title>
  <defs>
    <marker id="arrow" viewBox="0 0 10 10" refX="8" refY="5"
      markerWidth="6" markerHeight="6" orient="auto-start-reverse">
      <path d="M2 1L8 5L2 9" fill="none" stroke="context-stroke"
        stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
    </marker>
  </defs>

  <!-- INPUT -->
  <rect x="240" y="20" width="200" height="48" rx="8"
    fill="#D3D1C7" stroke="#5F5E5A" stroke-width="0.5"/>
  <text font-size="14" font-weight="500" x="340" y="40"
    text-anchor="middle" dominant-baseline="central">Lenguaje natural</text>
  <text font-size="12" x="340" y="58"
    text-anchor="middle" dominant-baseline="central">Entrada del usuario</text>

  <line x1="340" y1="68" x2="340" y2="100"
    stroke="#5F5E5A" stroke-width="1.5" marker-end="url(#arrow)"/>

  <!-- LLM -->
  <rect x="220" y="100" width="240" height="48" rx="8"
    fill="#FAC775" stroke="#BA7517" stroke-width="1"/>
  <text font-size="14" font-weight="500" x="340" y="120"
    text-anchor="middle" dominant-baseline="central">LLM — Traducción</text>
  <text font-size="12" x="340" y="138"
    text-anchor="middle" dominant-baseline="central">Genera FOL / PDDL / SMT</text>

  <!-- Fork izquierda (éxito) -->
  <path d="M280 148 L160 180" fill="none"
    stroke="#5F5E5A" stroke-width="1" marker-end="url(#arrow)"/>
  <text font-size="12" x="196" y="162" text-anchor="middle">✓ Válida</text>

  <!-- Fork derecha (fallo) -->
  <path d="M400 148 L520 180" fill="none"
    stroke="#5F5E5A" stroke-width="1" marker-end="url(#arrow)"/>
  <text font-size="12" x="484" y="162" text-anchor="middle">✗ Inválida</text>

  <!-- ÉXITO -->
  <rect x="60" y="180" width="200" height="48" rx="8"
    fill="#9FE1CB" stroke="#0F6E56" stroke-width="0.5"/>
  <text font-size="14" font-weight="500" x="160" y="200"
    text-anchor="middle" dominant-baseline="central">Solver simbólico</text>
  <text font-size="12" x="160" y="218"
    text-anchor="middle" dominant-baseline="central">Z3 / Fast Downward</text>

  <line x1="160" y1="228" x2="160" y2="268"
    stroke="#5F5E5A" stroke-width="1.5" marker-end="url(#arrow)"/>

  <rect x="60" y="268" width="200" height="44" rx="8"
    fill="#9FE1CB" stroke="#0F6E56" stroke-width="0.5"/>
  <text font-size="14" font-weight="500" x="160" y="286"
    text-anchor="middle" dominant-baseline="central">Plan / prueba válida</text>
  <text font-size="12" x="160" y="302"
    text-anchor="middle" dominant-baseline="central">Respuesta correcta</text>

  <!-- FALLO -->
  <rect x="420" y="180" width="200" height="48" rx="8"
    fill="#F5C4B3" stroke="#993C1D" stroke-width="0.5"/>
  <text font-size="14" font-weight="500" x="520" y="200"
    text-anchor="middle" dominant-baseline="central">Solver rechaza input</text>
  <text font-size="12" x="520" y="218"
    text-anchor="middle" dominant-baseline="central">Predicado inventado / sintaxis</text>

  <path d="M520 228 L520 290 L460 290" fill="none"
    stroke="#993C1D" stroke-width="1" stroke-dasharray="5 4"
    marker-end="url(#arrow)"/>

  <rect x="420" y="268" width="200" height="44" rx="8"
    fill="#F5C4B3" stroke="#993C1D" stroke-width="0.5"/>
  <text font-size="14" font-weight="500" x="520" y="286"
    text-anchor="middle" dominant-baseline="central">Error / bucle sin fin</text>
  <text font-size="12" x="520" y="302"
    text-anchor="middle" dominant-baseline="central">Self-Refinement no converge</text>

  <!-- Loop de vuelta al LLM -->
  <path d="M620 204 L648 204 L648 124 L462 124" fill="none"
    stroke="#993C1D" stroke-width="1" stroke-dasharray="4 4"
    marker-end="url(#arrow)"/>
  <text font-size="11" x="649" y="168" text-anchor="start">loop</text>
</svg>

El mecanismo de *Self-Refinement* —presente en Logic-LM [8] y CEGIS [2]—
mitiga parcialmente este problema reinyectando los mensajes de error del solver
como nuevos prompts al LLM. Sin embargo, este bucle presenta sus propias
limitaciones: el modelo puede no converger, o corregir el error superficial
introduciendo nuevas inconsistencias semánticas más profundas. En todos los casos,
la robustez del sistema depende de prompts de traducción ultra-específicos con
numerosos ejemplos *few-shot*, lo que dificulta la generalización a dominios nuevos.

En conjunto, mientras el componente neuronal siga siendo propenso a alucinaciones
estructurales, la integración con componentes simbólicos deterministas no puede
garantizar la fiabilidad *end-to-end* del pipeline [1].

---

### Referencias

[1] A. Patil and A. Jadon, "Advancing Reasoning in Large Language Models:
Promising Methods and Approaches," *arXiv*:2502.03671, May 2025.
doi: [10.48550/arXiv.2502.03671](https://doi.org/10.48550/arXiv.2502.03671)

[2] S. K. Jha et al., "Counterexample Guided Inductive Synthesis Using Large
Language Models and Satisfiability Solving," in *MILCOM 2023*, pp. 944–949.
doi: [10.1109/MILCOM58377.2023.10356332](https://doi.org/10.1109/MILCOM58377.2023.10356332)

[3] K. Hua et al., "DUPLEX: Agentic Dual-System Planning via LLM-Driven
Information Extraction," *arXiv*:2603.23909, Mar. 2026.
doi: [10.48550/arXiv.2603.23909](https://doi.org/10.48550/arXiv.2603.23909)

[4] Y. Chervonyi et al., "Gold-medalist Performance in Solving Olympiad Geometry
with AlphaGeometry2," *arXiv*:2502.03544, Dec. 2025.
doi: [10.48550/arXiv.2502.03544](https://doi.org/10.48550/arXiv.2502.03544)

[7] B. Liu et al., "LLM+P: Empowering Large Language Models with Optimal
Planning Proficiency," *arXiv*:2304.11477, 2023.
doi: [10.48550/arXiv.2304.11477](https://doi.org/10.48550/arXiv.2304.11477)

[8] L. Pan et al., "Logic-LM: Empowering Large Language Models with Symbolic
Solvers for Faithful Logical Reasoning," in *Findings of ACL: EMNLP 2023*,
pp. 3806–3824.
doi: [10.18653/v1/2023.findings-emnlp.248](https://doi.org/10.18653/v1/2023.findings-emnlp.248)