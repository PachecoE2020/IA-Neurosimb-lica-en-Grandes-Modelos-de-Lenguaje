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
traducción del LLM.

<svg width="100%" viewBox="0 0 689.45 340" role="img" xmlns="http://www.w3.org/2000/svg">
	<title>Caminos de éxito y fallo en la traducción neurosimbólica</title>
	<desc>Diagrama bifurcado que muestra el camino de éxito (traducción válida lleva a plan correcto) y el camino de fallo (predicado inventado lleva a error irreparable o bucle infinito).</desc>
	<defs>
		<marker id="arrow" viewBox="0 0 10 10" refX="8" refY="5" markerWidth="6" markerHeight="6" orient="auto-start-reverse">
			<path d="M2 1L8 5L2 9" fill="none" stroke="context-stroke" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
		</marker>
	</defs>

	<!-- INPUT -->
	<g>
		<rect x="240" y="20" width="200" height="48" rx="8" stroke-width="0.5" style="fill:rgb(68, 68, 65);stroke:rgb(180, 178, 169);"/>
		<text x="340" y="40" text-anchor="middle" dominant-baseline="central" style="fill:rgb(211, 209, 199);font-size:14px;font-weight:500;">Lenguaje natural</text>
		<text x="340" y="58" text-anchor="middle" dominant-baseline="central" style="fill:rgb(180, 178, 169);font-size:12px;">Entrada del usuario</text>
	</g>

	<!-- Arrow down to LLM -->
	<line x1="340" y1="68" x2="340" y2="100" marker-end="url(#arrow)" style="stroke:rgb(156, 154, 146);stroke-width:1.5px;"/>

	<!-- LLM TRANSLATION -->
	<g>
		<rect x="220" y="100" width="240" height="48" rx="8" stroke-width="1" style="fill:rgb(99, 56, 6);stroke:rgb(239, 159, 39);"/>
		<text x="340" y="120" text-anchor="middle" dominant-baseline="central" style="fill:rgb(250, 199, 117);font-size:14px;font-weight:500;">LLM — Traducción</text>
		<text x="340" y="138" text-anchor="middle" dominant-baseline="central" style="fill:rgb(239, 159, 39);font-size:12px;">Genera FOL / PDDL / SMT</text>
	</g>

	<!-- Fork arrow left (success) -->
	<path d="M280 148 L160 180" fill="none" stroke="rgba(222, 220, 209, 0.4)" stroke-width="1" marker-end="url(#arrow)"/>
	<text x="188" y="168" text-anchor="middle" style="fill:rgb(194, 192, 182);font-size:12px;">✓ Válida</text>

	<!-- Fork arrow right (failure) -->
	<path d="M400 148 L520 180" fill="none" stroke="rgba(222, 220, 209, 0.4)" stroke-width="1" marker-end="url(#arrow)"/>
	<text x="492" y="168" text-anchor="middle" style="fill:rgb(194, 192, 182);font-size:12px;">✗ Inválida</text>

	<!-- SUCCESS PATH -->
	<g>
		<rect x="60" y="180" width="200" height="48" rx="8" stroke-width="0.5" style="fill:rgb(8, 80, 65);stroke:rgb(93, 202, 165);"/>
		<text x="160" y="200" text-anchor="middle" dominant-baseline="central" style="fill:rgb(159, 225, 203);font-size:14px;font-weight:500;">Solver simbólico</text>
		<text x="160" y="218" text-anchor="middle" dominant-baseline="central" style="fill:rgb(93, 202, 165);font-size:12px;">Z3 / Fast Downward</text>
	</g>
	<line x1="160" y1="228" x2="160" y2="268" marker-end="url(#arrow)" style="stroke:rgb(156, 154, 146);stroke-width:1.5px;"/>
	<g>
		<rect x="60" y="268" width="200" height="44" rx="8" stroke-width="0.5" style="fill:rgb(8, 80, 65);stroke:rgb(93, 202, 165);"/>
		<text x="160" y="286" text-anchor="middle" dominant-baseline="central" style="fill:rgb(159, 225, 203);font-size:14px;font-weight:500;">Plan / prueba válida</text>
		<text x="160" y="302" text-anchor="middle" dominant-baseline="central" style="fill:rgb(93, 202, 165);font-size:12px;">Respuesta correcta</text>
	</g>

	<!-- FAILURE PATH -->
	<g>
		<rect x="420" y="180" width="200" height="48" rx="8" stroke-width="0.5" style="fill:rgb(113, 43, 19);stroke:rgb(240, 153, 123);"/>
		<text x="520" y="200" text-anchor="middle" dominant-baseline="central" style="fill:rgb(245, 196, 179);font-size:14px;font-weight:500;">Solver rechaza input</text>
		<text x="520" y="218" text-anchor="middle" dominant-baseline="central" style="fill:rgb(240, 153, 123);font-size:12px;">Predicado inventado / sintaxis</text>
	</g>

	<!-- Failure: loop back or dead end -->
	<path d="M520 228 L520 290 L460 290" fill="none" stroke="rgba(222, 220, 209, 0.3)" stroke-width="1" stroke-dasharray="5 4" marker-end="url(#arrow)"/>
	<g>
		<rect x="420" y="268" width="200" height="44" rx="8" stroke-width="0.5" style="fill:rgb(113, 43, 19);stroke:rgb(240, 153, 123);"/>
		<text x="520" y="286" text-anchor="middle" dominant-baseline="central" style="fill:rgb(245, 196, 179);font-size:14px;font-weight:500;">Error / bucle sin fin</text>
		<text x="520" y="302" text-anchor="middle" dominant-baseline="central" style="fill:rgb(240, 153, 123);font-size:12px;">Self-Refinement no converge</text>
	</g>

	<!-- Dashed loop arrow back to LLM -->
	<path d="M620 204 L650 204 L650 124 L462 124" fill="none" stroke="rgba(222, 220, 209, 0.3)" stroke-width="1" stroke-dasharray="4 4" marker-end="url(#arrow)"/>
	<text x="655" y="168" text-anchor="start" style="fill:rgb(194, 192, 182);font-size:12px;">loop</text>
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