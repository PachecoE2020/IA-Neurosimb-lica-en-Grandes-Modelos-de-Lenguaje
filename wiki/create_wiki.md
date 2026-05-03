# Wiki Blueprint: IA Neurosimbólica y LLMs

> **Audiencia objetivo:** estudiantes de máster e investigadores en IA, profesores, tribunal de seminario.
> **Stack recomendado:** MkDocs + Material theme (razones al final).
> **Idioma principal:** español; términos técnico∫s en inglés cuando sea convención.

---

## 1. Filosofía de diseño

Una wiki **no es un PDF roto en pedazos**. Es una estructura hipertextual donde cada página:

1. Resuelve **una pregunta concreta** del lector (qué es X, cómo funciona Y, cómo se compara Z con W).
2. Es **autocontenida**: se puede leer fuera de orden y aún tener sentido.
3. Termina con **enlaces a las 3-5 páginas relacionadas más relevantes**.
4. Tiene **un diagrama o tabla por página** como mínimo, idealmente arriba (escaneabilidad).
5. Cita inline las refs relevantes (no al final con números) — el lector hace clic y va.

Decisiones de organización:

- **Páginas-concepto** (qué es X): cortas, definicionales, con ejemplo mínimo.
- **Páginas-sistema** (cómo funciona Y): pipeline + diagrama + ejemplo trabajado + benchmarks + límites.
- **Páginas-comparativa** (X vs Y): tabla + cuándo usar cada una.
- **Páginas-tema-transversal**: latencia, fragilidad de traducción, ética. Cruzan múltiples sistemas.

---

## 2. Mapa de la wiki

```
docs/
├── index.md                        # Landing page
├── overview/
│   ├── que-es-nesy.md               # Concept: ¿Qué es la IA neurosimbólica?
│   ├── symbol-grounding.md          # Concept: el problema de Harnad
│   ├── sistema1-sistema2.md         # Concept: marco dual-process Kahneman
│   └── por-que-importa-en-llms.md   # Motivación específica para LLMs
│
├── taxonomia/
│   ├── kautz-overview.md            # Visión general taxonomía Kautz
│   ├── tipo-1.md                    # Symbolic Neuro Symbolic
│   ├── tipo-2.md                    # Symbolic[Neuro]
│   ├── tipo-3.md                    # Neuro ∪ Symbolic
│   ├── tipo-4.md                    # Neuro → Symbolic
│   ├── tipo-5.md                    # NeuroSYMBOLIC
│   ├── tipo-6.md                    # Neuro[Symbolic]
│   └── taxonomias-alternativas.md   # Hitzler, van Harmelen, Bhuyan
│
├── fallas-llm/
│   ├── overview.md                  # Las 5 fallas estructurales
│   ├── alucinaciones.md
│   ├── razonamiento-multipaso.md
│   ├── deduccion-formal.md
│   ├── generalizacion-composicional.md
│   └── opacidad.md
│
├── ventajas-simbolicas/
│   ├── overview.md                  # 4 propiedades core
│   ├── determinismo.md
│   ├── verificacion-formal.md
│   ├── busqueda-combinatoria.md
│   └── auditabilidad.md
│
├── sistemas/
│   ├── llm-p.md                     # Sistema: LLM+P
│   ├── duplex.md                    # Sistema: DUPLEX
│   ├── llm-modulo.md                # Sistema: LLM-Modulo
│   ├── logic-lm.md                  # Sistema: Logic-LM
│   ├── cegis.md                     # Sistema: CEGIS+LLM
│   ├── alphageometry2.md            # Sistema: AlphaGeometry2
│   ├── nellie.md                    # Sistema: NELLIE
│   ├── deepproblog.md               # Sistema: DeepProbLog (referencia Tipo 3)
│   ├── pal.md                       # Sistema: PAL
│   └── linc.md                      # Sistema: LINC
│
├── tecnicas/
│   ├── pddl.md                      # Lenguaje formal: PDDL
│   ├── smt-solvers.md               # Lenguaje formal: SMT-LIB / Z3
│   ├── first-order-logic.md         # Lenguaje formal: FOL / Prover9
│   ├── self-refinement.md           # Patrón: bucle de auto-refinamiento
│   ├── schema-guided-ie.md          # Patrón: extracción guiada por esquema
│   ├── constrained-decoding.md      # Patrón: decodificación restringida
│   ├── cegis-pattern.md             # Patrón: counterexample-guided
│   ├── backward-chaining.md         # Patrón: backward chaining
│   └── auxiliary-constructions.md   # Patrón: construcciones auxiliares
│
├── benchmarks/
│   ├── overview.md                  # Mapa de benchmarks NeSy-LLM
│   ├── proofwriter.md
│   ├── folio.md
│   ├── planbench.md
│   ├── travelplanner.md
│   ├── imo-geometry.md
│   ├── entailmentbank.md
│   └── ar-lsat.md
│
├── analisis-critico/
│   ├── latencia.md                  # Cuello de botella: tiempo
│   ├── fragilidad-traduccion.md     # Cuello de botella: traducción
│   ├── trade-soundness-generalidad.md
│   └── coste-computacional.md
│
├── etica/
│   ├── doble-sesgo.md                       # Sesgo sub-simbólico vs simbólico
│   ├── explainability-laundering.md         # Caso: triaje médico
│   ├── accountability.md                    # Brecha de atribución
│   └── implicaciones-regulatorias.md        # AI Act, alto riesgo
│
├── comparativas/
│   ├── llm-vs-nesy.md                       # CoT puro vs sistemas NeSy
│   ├── llmp-vs-duplex-vs-modulo.md          # Tres sistemas de planificación
│   ├── logic-lm-vs-cegis.md                 # Densidad del feedback
│   ├── alphageometry2-vs-nellie.md          # Forward vs backward chaining
│   └── matriz-funcional.md                  # Matriz rol-neuronal × control-simbólico
│
├── glosario.md
├── bibliografia.md
└── sobre.md                                  # Acerca del proyecto, autor, agradecimientos
```

**Total:** ~60 páginas. Cada una entre 300-1500 palabras. El documento original se redistribuye sin perder contenido pero ganando navegabilidad.

---

## 3. Especificación detallada por página

A continuación, contenido preciso para cada página. Estructura uniforme:

- **Tipo:** concepto / sistema / patrón / comparativa / tema-transversal
- **Pregunta que responde:** una sola, en lenguaje natural
- **Bloque inicial:** TL;DR de 2-3 líneas (decisión de UX clave: el lector debe saber en 10 segundos si la página le sirve)
- **Estructura:** secciones internas H2
- **Elementos visuales:** qué diagrama / tabla / imagen va dónde
- **Cross-links:** enlaces salientes obligatorios

---

### 3.1. `index.md` — Landing page

**Tipo:** entrada
**Pregunta:** ¿qué encontraré aquí?

**Estructura:**

```markdown
# IA Neurosimbólica + LLMs

Una wiki sobre cómo combinar Grandes Modelos de Lenguaje con sistemas de
razonamiento formal — taxonomía, sistemas concretos, benchmarks y críticas.

## Por dónde empezar

- 🆕 **Si nunca has oído hablar de NeSy** → [¿Qué es la IA neurosimbólica?](overview/que-es-nesy.md)
- 🧭 **Si quieres el mapa conceptual completo** → [Taxonomía de Kautz](taxonomia/kautz-overview.md)
- 🔧 **Si buscas un sistema concreto** → [Catálogo de sistemas](sistemas/)
- 📊 **Si te interesan los números** → [Benchmarks](benchmarks/overview.md)
- ⚠️ **Si quieres saber por qué falla** → [Análisis crítico](analisis-critico/fragilidad-traduccion.md)
- ⚖️ **Si te preocupa la ética** → [Explainability laundering](etica/explainability-laundering.md)

## La idea en 30 segundos

Los LLMs son buenos interpretando lenguaje natural pero malos razonando
formalmente. Los sistemas simbólicos son buenos razonando formalmente pero
malos con lenguaje natural. La IA neurosimbólica los combina, **dejando que
cada uno haga lo que sabe hacer**: el LLM traduce o propone, el sistema
simbólico verifica.

[Diagrama hero animado: NL → LLM → representación formal → solver → resultado]
```

**Elementos visuales:**

- Hero diagram (Mermaid o SVG estática) del pipeline genérico.
- 3 cards: "Aprende", "Compara", "Critica" → cada una linkea a hub correspondiente.

**Cross-links salientes:** todos los hubs principales.

---

### 3.2. `overview/que-es-nesy.md`

**Tipo:** concepto
**Pregunta:** ¿qué es la IA neurosimbólica y por qué existe?

**TL;DR:** *La IA neurosimbólica acopla redes neuronales (Sistema 1: rápido, intuitivo) con motores de razonamiento simbólico (Sistema 2: lento, deliberativo). Existe porque los LLMs alucinan al razonar formalmente y los solvers simbólicos no entienden lenguaje natural — combinarlos resuelve ambos problemas.*

**Secciones:**

1. **El problema que resuelve.** Dicotomía conexionista vs simbólico (1-2 párrafos, no más). Ejemplo: GPT-4 calcula mal sumas largas; un solver SMT no entiende "suma estos dos números" en español. NeSy hace que el LLM extraiga `add(3,5)` y el solver lo resuelva.
2. **La hipótesis central.** El LLM no es un razonador end-to-end; es una **interfaz semántica**. Cita LLM-Modulo [Kambhampati 2024].
3. **Tres roles funcionales del componente neuronal.** Formalizador / proponente / heurística. Tabla pequeña. Linkea a la matriz funcional.
4. **Lo que NeSy NO es.** No es un ensemble. No es chain-of-thought. No es RAG. (Distinguir explícitamente — son confusiones frecuentes.)

**Visuales:** un solo diagrama con dos cajas (LLM | Solver) y flechas etiquetadas.

**Cross-links salientes:**

- → `overview/symbol-grounding.md` (por qué LLM puro falla)
- → `overview/sistema1-sistema2.md` (marco cognitivo)
- → `taxonomia/kautz-overview.md` (cómo se clasifica)
- → `sistemas/llm-p.md` (primer sistema concreto)

---

### 3.3. `overview/symbol-grounding.md`

**Tipo:** concepto
**Pregunta:** ¿por qué un LLM no puede razonar formalmente solo?

**TL;DR:** *El problema del symbol grounding (Harnad, 1990) dice que un sistema que solo manipula símbolos no adquiere semántica intrínseca. En LLMs, esto se traduce en que los embeddings capturan estadística, no causalidad: el modelo puede producir una demostración correcta sin "entender" los axiomas.*

**Secciones:**

1. **Harnad 1990 en una página.** Formulación original (~150 palabras), por qué importa.
2. **Cómo aparece en LLMs.** Los embeddings son representaciones distribuidas; pueden capturar regularidades estadísticas asombrosas pero no anclan semántica al mundo.
3. **Evidencia empírica.** PlanBench: GPT-4 cae catastróficamente cuando los nombres de acciones se ofuscan (renombras `pickup` como `xyzzy`). Si el modelo "entendiera" la acción, el renombrado no debería importar. → linkea a `benchmarks/planbench.md`.
4. **La salida NeSy.** El solver simbólico opera sobre símbolos cuya semántica está definida por reglas — no necesita grounding causal porque opera en el dominio formal. El LLM se restringe a la traducción, donde su "sabe" probabilístico es útil.

**Visuales:** ejemplo con dos columnas: el mismo problema con vocabulario natural vs vocabulario ofuscado, mostrando la caída de rendimiento.

**Cross-links salientes:**

- → `overview/que-es-nesy.md`
- → `fallas-llm/overview.md`
- → `benchmarks/planbench.md`

---

### 3.4. `overview/sistema1-sistema2.md`

**Tipo:** concepto
**Pregunta:** ¿qué tiene que ver Kahneman con la IA neurosimbólica?

**TL;DR:** *El marco dual-process de Kahneman (Sistema 1 rápido/intuitivo vs Sistema 2 lento/deliberativo) es la metáfora cognitiva dominante en NeSy. LLM = Sistema 1, solver = Sistema 2. Útil pedagógicamente; imperfecta técnicamente.*

**Secciones:**

1. **El marco original.** Resumen de *Thinking, Fast and Slow* (un párrafo).
2. **El mapeo a NeSy.** LLM como Sistema 1 (asociativo, propenso a errores), solver como Sistema 2 (deliberativo, costoso). DUPLEX adopta este marco explícitamente.
3. **Crítica honesta.** La metáfora se rompe en varios puntos:
   - El cerebro humano no tiene una transición discreta como LLM→PDDL→Z3.
   - Los LLMs hacen "fast thinking" sobre tareas que son Sistema 2 para humanos (matemáticas).
   - Sistema 1/Sistema 2 es un modelo psicológico contestado, no un hecho neuroanatómico.
4. **Por qué se usa de todas formas.** Útil para comunicar la idea de "diferentes computaciones para diferentes tareas". No tomar literalmente.

**Visuales:** tabla 2x4 (Sistema 1 / Sistema 2 × velocidad / esfuerzo / fiabilidad / coste), con LLM y solver mapeados.

**Cross-links:** → `sistemas/duplex.md`

---

### 3.5. `taxonomia/kautz-overview.md`

**Tipo:** hub de taxonomía
**Pregunta:** ¿cómo se clasifican las arquitecturas NeSy?

**TL;DR:** *Henry Kautz (AAAI 2020) propuso seis tipos según direccionalidad del flujo y acoplamiento. Es la taxonomía estándar en literatura LLM-NeSy. No es la única — coexiste con Hitzler, van Harmelen, Bhuyan.*

**Estructura:**

1. **Origen.** Conferencia AAAI 2020, *The Third AI Summer*. Embebed YouTube (`<iframe>` permitido en MkDocs).
2. **Los seis tipos en una tabla.** Fila por tipo, columnas: nombre, abreviación, ejemplo canónico, escalabilidad a LLM. Cada fila linkea a su página dedicada.
3. **Cómo navegar la taxonomía.** Diagrama que muestra los tipos en un eje "acoplamiento" (1 superficial → 6 fundido). Marca cuáles son alcanzables hoy con LLMs y cuáles son horizonte teórico.
4. **Limitaciones de Kautz.** La frontera Tipo 5 / Tipo 6 está mal definida. Tipo 1 es una lectura post-hoc cuando se aplica a LLMs. → linkea a `taxonomias-alternativas.md`.

**Visuales:**

- Tabla resumen con 6 filas.
- Diagrama de Figura 1.1 del original (taxonomy.png).
- Embed de la conferencia AAAI 2020 (45 min).

**Cross-links:** los 6 tipos + `taxonomias-alternativas.md`.

---

### 3.6. Páginas `taxonomia/tipo-N.md` (6 páginas)

**Plantilla común para cada Tipo:**

```markdown
# Tipo N: <Nombre>

**Abreviación:** ...
**Direccionalidad:** ...
**Escalabilidad a LLMs:** ✅ común | ⚠️ limitado | ❌ horizonte teórico

> TL;DR de 2 líneas

## Definición formal

(2-3 párrafos)

## Pipeline conceptual

[Diagrama Mermaid mostrando flujo NL → ... → output]

## Ejemplo canónico

(sistema concreto, descripción mínima, link a su página)

## Sistemas que pertenecen a este tipo

- [Sistema A](../sistemas/A.md) — descripción de una línea
- [Sistema B](../sistemas/B.md) — descripción de una línea

## Fortalezas

(3-5 bullets)

## Limitaciones

(3-5 bullets)

## Comparación con tipos adyacentes

(¿en qué se diferencia del Tipo N-1 y N+1? 1 párrafo cada uno)

## Lecturas adicionales

(2-3 refs externas)
```

**Contenido específico por tipo:**

- **Tipo 1:** ejemplo canónico = traducción automática neuronal (lectura original Kautz). Lectura LLM-céntrica = LLMs vanilla. Sistemas: ninguno NeSy verdadero — esta es la *baseline* contra la que se compara.
- **Tipo 2:** ejemplo canónico = AlphaGo. Sistemas en wiki: AlphaGeometry2. Énfasis: solver gobierna, neural es subrutina.
- **Tipo 3:** ejemplo canónico = DeepProbLog. Énfasis: gradiente fluye a través del solver. Limitación crítica: difícil de escalar a LLMs.
- **Tipo 4:** ejemplo canónico = Logic-LM, LLM+P, DUPLEX. Es el tipo dominante. Página más larga de las 6.
- **Tipo 5:** ejemplo canónico = LTNs, Semantic Loss. Énfasis: integración en *training time*. Estado: no demostrado a escala LLM.
- **Tipo 6:** ejemplo canónico = LNNs (clasificación contestada). Énfasis: razonamiento simbólico nativo en cómputo tensorial. Estado: horizonte teórico.

---

### 3.7. `taxonomia/taxonomias-alternativas.md`

**Tipo:** concepto / referencia
**Pregunta:** ¿hay otras formas de clasificar sistemas NeSy?

**Estructura:**

1. **Por qué importa.** Defenderse en tribunal: *"¿por qué Kautz y no Hitzler?"*
2. **Hitzler et al. (boxology).** Notación gráfica con cajas y flechas. Cuándo usarla.
3. **van Harmelen & ten Teije.** Énfasis en dirección del flujo de información.
4. **Bhuyan et al. survey [2].** Eje training-time vs inference-time.
5. **Cuándo usar cuál.** Tabla con criterios de elección.

**Visuales:** tabla comparativa de las 4 taxonomías.

---

### 3.8. Páginas `sistemas/*.md` (10 páginas)

**Plantilla común para cada sistema:**

```markdown
# <Nombre del sistema>

**Año:** ...
**Tipo Kautz:** ...
**Componente simbólico:** Z3 / Fast Downward / DDAR / etc.
**Paper:** [link arxiv]

> TL;DR de 2-3 líneas: qué problema resuelve, cómo, qué métrica reporta.

## Problema que resuelve

(1-2 párrafos)

## Arquitectura

[Diagrama Mermaid del pipeline]

(Descripción paso a paso, 4-7 pasos)

## Ejemplo trabajado

(Input NL → output simbólico → resultado del solver → verbalización final)

## Resultados empíricos

| Benchmark | Métrica | Baseline | Este sistema |
|---|---|---|---|
| ... | ... | ... | ... |

## Fortalezas

(3-5 bullets)

## Limitaciones

(3-5 bullets)

## Comparación con sistemas relacionados

(2-3 párrafos linkeando a otros sistemas)

## Implementación

(¿hay código público? GitHub link, dependencias clave, dificultad de reproducir)

## Referencias

(las 3-5 más relevantes)
```

**Páginas específicas:**

#### `sistemas/llm-p.md`

- **Año:** 2023
- **Pipeline:** NL → LLM (con dominio PDDL fijo + 1 ejemplo few-shot) → problem.pddl → Fast Downward → plan → LLM → NL
- **Resultados:** 7 dominios IPC; ~80-100% éxito vs ~10-30% LLM-as-planner.
- **Limitación clave:** asume que el dominio PDDL ya existe. Frágil en escenarios abiertos.
- **Cross-links:** → DUPLEX (mejora directa), → LLM-Modulo (generalización), → PDDL (lenguaje formal).

#### `sistemas/duplex.md`

- **Año:** 2026 (Hua et al., Midea Group)
- **Pipeline:** Fast System (LLM ligero + JSON Schema) → mapper determinista → PDDL → planner → [Slow System en caso de fallo]
- **Innovación clave:** schema-guided IE con mapper determinista — elimina alucinaciones sintácticas.
- **Resultados:** 12 dominios; supera baselines end-to-end e híbridos.
- **Cross-links:** → LLM+P (predecesor), → schema-guided-ie (técnica), → sistema1-sistema2 (marco).

#### `sistemas/llm-modulo.md`

- **Año:** 2024 (Kambhampati et al., ICML)
- **Pipeline:** LLM como generador de candidatos → conjunto de verificadores externos → re-prompt dirigido si falla cualquier verificador
- **Innovación:** verificadores múltiples e independientes; back-prompting bidireccional.
- **Resultados:** TravelPlanner: 0.6% (GPT-4 vanilla) → 20% (GPT-4-Turbo + Modulo) → 65% (o1-preview + Modulo).
- **Cross-links:** todos los sistemas de planificación.

#### `sistemas/logic-lm.md`

- **Año:** 2023 (Pan et al., EMNLP Findings)
- **Pipeline:** Problem Formulator (LLM) → Symbolic Reasoner (Z3/Prover9/Pyke/python-constraint) → Result Interpreter (LLM); con bucle Self-Refiner.
- **Resultados:** Tabla detallada de 5 benchmarks. ProofWriter +11.22pp, FOLIO +3.92pp, LogicalDeduction +16.30pp, AR-LSAT +9.71pp, PrOntoQA -5.19pp (interesante: por qué cae).
- **Auto-refinement contribuye:** +4.86% (GPT-3.5) a +7.82% (GPT-4).
- **Cross-links:** → CEGIS (comparación de feedback), → self-refinement (técnica).

#### `sistemas/cegis.md`

- **Año:** 2023 (Jha et al., MILCOM)
- **Pipeline:** LLM propone candidato → Z3 verifica → si falla, contraejemplo concreto → re-prompt → repetir.
- **Innovación clave:** densidad de la señal de feedback. Contraejemplo concreto > mensaje de error genérico.
- **Cross-links:** → cegis-pattern, → smt-solvers, → logic-lm (comparación).

#### `sistemas/alphageometry2.md`

- **Año:** 2025 (Chervonyi et al., DeepMind)
- **Tipo:** Symbolic[Neuro] (Tipo 2)
- **Componentes:** DDAR (motor simbólico, C++) + Gemini fine-tuneado (~150M-3.3B parámetros) como heurística + SKEST (algoritmo de búsqueda con knowledge sharing).
- **Hay DOS LLMs:** auto-formalizador (NL→DSL) + proposer de construcciones auxiliares.
- **Resultados:** 84% IMO 2000-2024 (42/50), vs 54% AG1, vs ~0% para o1/Gemini Thinking puros. Plata en IMO 2024.
- **Importante:** página debe explicar la confusión común "¿es realmente un LLM?". Sí, técnicamente lo es; el rol arquitectónico es lo que difiere.
- **Cross-links:** → tipo-2, → auxiliary-constructions, → imo-geometry (benchmark).

#### `sistemas/nellie.md`

- **Año:** 2022 (Weir, Clark, Van Durme)
- **Pipeline:** backward chaining estilo Prolog donde átomos = frases NL; unificación = NLI semántico.
- **Innovación:** retrieval/generación de reglas + unificación via NLI.
- **Cross-links:** → backward-chaining (técnica), → entailmentbank (benchmark).

#### `sistemas/deepproblog.md`

- **Año:** 2018 (Manhaeve et al., NeurIPS)
- **Por qué está aquí:** ejemplo canónico de Tipo 3, aunque no escala a LLMs.
- **Importancia:** precedente histórico, base teórica de la diferenciación a través de inferencia probabilística.

#### `sistemas/pal.md`

- **Año:** 2022 (Gao et al.)
- **Pipeline:** LLM genera código Python ejecutable → intérprete Python ejecuta → resultado.
- **Por qué importa:** caso especial donde el "solver" es el intérprete de Python. Más simple que SMT pero efectivo.

#### `sistemas/linc.md`

- **Año:** 2023 (Olausson et al., EMNLP)
- **Pipeline:** LLM como semantic parser NL→FOL → theorem prover externo.
- **Resultados:** +26pp sobre CoT en ProofWriter con GPT-4. StarCoder+ con LINC supera a GPT-4-CoT.

---

### 3.9. Páginas `tecnicas/*.md` (9 páginas)

**Plantilla común:**

```markdown
# <Nombre de la técnica>

**Familia:** patrón / lenguaje formal / mecanismo de control
**Usado por:** [lista de sistemas]

> TL;DR de 2 líneas

## Idea fundamental

## Cómo funciona

(diagrama + explicación)

## Variantes

## Limitaciones

## Sistemas que la usan

(lista con cross-links)
```

**Páginas específicas:**

- **`pddl.md`:** Sintaxis básica `(:objects ...)`, `(:init ...)`, `(:goal ...)`, definición de acciones con preconditions/effects. Ejemplo Blocksworld minimal.
- **`smt-solvers.md`:** Z3 en su modo SMT-LIB. Ejemplo simple. Diferencia con SAT puro.
- **`first-order-logic.md`:** Sintaxis FOL, Prover9. Cuantificadores, predicados, aridades.
- **`self-refinement.md`:** Patrón de bucle: solver error → reprompt → reformular. Pseudocódigo. Riesgos: no convergencia, oscilación.
- **`schema-guided-ie.md`:** JSON Schema + LLM relleno de campos. Pseudocódigo. Por qué reduce alucinaciones sintácticas.
- **`constrained-decoding.md`:** Outlines, GBNF, structured outputs. Cómo gramática regular o CFG restringe la generación token a token.
- **`cegis-pattern.md`:** El loop genérico (no específico al uso con LLMs). Origen Solar-Lezama. Comparación con randomized search.
- **`backward-chaining.md`:** SLD-resolution, Prolog. Cómo NELLIE lo extiende a NL.
- **`auxiliary-constructions.md`:** Por qué muchos teoremas de geometría requieren construcciones auxiliares (no derivables por cierre deductivo del enunciado). Cómo AlphaGeometry2 las propone.

---

### 3.10. Páginas `benchmarks/*.md` (7 páginas)

**Plantilla:**

```markdown
# <Nombre del benchmark>

**Año:** ...
**Tarea:** ...
**Tamaño:** N instancias
**Métrica principal:** ...

> TL;DR

## Qué mide

## Ejemplo de instancia

(input completo + output esperado)

## Resultados de referencia

| Sistema | Modelo base | Resultado |
|---|---|---|
| LLM puro (CoT) | GPT-4 | X% |
| Sistema NeSy | ... | Y% |
| ... | ... | ... |

## Limitaciones del benchmark

## Sistemas evaluados sobre este benchmark

(lista con cross-links)
```

**Específicos:**

- **proofwriter.md:** Razonamiento deductivo multi-hop. ~5K instancias. CoT GPT-4 ~68%, Logic-LM ~79%, LINC ~84%.
- **folio.md:** NL→FOL. ~1.4K instancias. Más realista que ProofWriter. CoT GPT-4 ~70.6%, Logic-LM ~74.5%.
- **planbench.md:** Suite de 8 tasks sobre Blocksworld y Logistics. 600+285 instancias. Diseñado por Valmeekam et al. para exponer fallos de planificación de LLMs.
- **travelplanner.md:** Benchmark agentic con restricciones reales. GPT-4 vanilla 0.6% éxito; LLM-Modulo eleva a 20-65%.
- **imo-geometry.md:** 50 problemas IMO 2000-2024. AG2 84%. o1/Gemini Thinking ~0%.
- **entailmentbank.md:** Razonamiento composicional sobre ciencia de primaria. Evalúa NELLIE.
- **ar-lsat.md:** Razonamiento legal. Difícil. CoT GPT-4 ~33%, Logic-LM ~43%.

---

### 3.11. Páginas `analisis-critico/*.md` (4 páginas)

#### `latencia.md`

**TL;DR:** Los pipelines NeSy hacen N llamadas al solver más M llamadas al LLM. Acumulan latencia que descarta su uso en tiempo real.

**Tabla central:** la del seminario (LLM puro / Logic-LM / LLM+P / DUPLEX / Modulo / AG2) con orden de magnitud.

**Linkea a:** todos los sistemas + `coste-computacional.md`.

#### `fragilidad-traduccion.md`

**TL;DR:** Si el LLM traduce mal el problema, el solver resuelve un problema distinto. Es el modo de falla universal de NeSy-LLM.

**Estructura:**

1. **El problema en una frase.**
2. **Diagrama de los dos caminos** (el SVG existente).
3. **Cuatro categorías de error de traducción:** sintácticos / semánticos / predicados alucinados / omisión de premisas. Ejemplo de cada uno.
4. **Mitigaciones existentes:** Self-Refinement (parcial), schema-guided IE (sintáctico), constrained decoding (sintáctico), CEGIS (con feedback denso).
5. **Lo que ninguna mitigación resuelve:** error semántico que produce PDDL bien formado pero equivocado.

**Cross-links:** → todas las técnicas mitigantes + `etica/explainability-laundering.md` (porque ese error semántico es el vector ético).

#### `trade-soundness-generalidad.md`

**TL;DR:** Sistemas más sound cubren menos dominio. AG2 (sound) solo geometría euclidiana; NELLIE (general) introduce ruido NLI. No hay almuerzo gratis.

**Visuales:** scatterplot conceptual con sistemas en eje soundness × generalidad.

#### `coste-computacional.md`

Profundización del coste por componente: training-time (Tipo 5) vs inference-time (Tipos 2,3,4). Por qué Semantic Loss no escala a LLMs.

---

### 3.12. Páginas `etica/*.md` (4 páginas)

#### `doble-sesgo.md`

**TL;DR:** En NeSy hay dos vectores de sesgo: el sub-simbólico (datos del LLM) y el simbólico (reglas humanas). Ambos se componen en la interfaz.

#### `explainability-laundering.md`

**Esta es la página más importante de la sección de ética.**

**Estructura:**

1. **Definición.** El árbol de prueba simbólico legitima predicados sesgados extraídos por el LLM.
2. **Caso trabajado: triaje médico.** El ejemplo del seminario, expandido con detalles concretos. Cómo `cumpleAdherencia(P)=false` puede correlar con código postal o lenguaje del clínico.
3. **Por qué es peor que el LLM puro.** Un score opaco se cuestiona; un árbol de prueba se respeta.
4. **Otros dominios de riesgo:** sentencing algorítmico, aprobación de créditos, elegibilidad migratoria.
5. **Mitigaciones parciales.** Auditoría independiente sobre los predicados extraídos, no solo sobre la cadena de prueba.
6. **Lo que NO mitiga.** Schema-guided IE garantiza forma correcta, no neutralidad de los hechos.

**Cita externa clave:** Obermeyer et al., *Science* 2019, sobre sesgo en algoritmos médicos.

#### `accountability.md`

Brecha de atribución: cuando el sistema falla, ¿fue percepción, regla, o integración? Implicaciones bajo AI Act.

#### `implicaciones-regulatorias.md`

AI Act europeo: sistemas de alto riesgo. Por qué NeSy es mejor que LLM puro pero peor que sistema simbólico clásico para cumplimiento.

---

### 3.13. Páginas `comparativas/*.md` (5 páginas)

Cada una es una tabla con prosa explicativa.

- **`llm-vs-nesy.md`:** la tabla de delta de rendimiento sobre 4-5 benchmarks.
- **`llmp-vs-duplex-vs-modulo.md`:** progresión de robustez en planificación.
- **`logic-lm-vs-cegis.md`:** densidad del feedback. Tabla del seminario.
- **`alphageometry2-vs-nellie.md`:** forward vs backward, sound vs general.
- **`matriz-funcional.md`:** la matriz 2x2 (rol del componente neuronal × régimen de control).

---

### 3.14. Páginas auxiliares

#### `glosario.md`

Diccionario con ~30-40 términos: NeSy, LLM, PDDL, SMT, FOL, CoT, RAG, ICL, *self-refinement*, *grounding*, *embedding*, *autoregresivo*, *DDAR*, *SKEST*, *backward chaining*, *forward chaining*, *boxology*, *symbol grounding problem*, *Sistema 1/2*, *fast downward*, *Z3*, *Prover9*, *DeepProbLog*, *Logic Tensor Networks*, *Semantic Loss*, *Weighted Model Counting*, *constrained decoding*, *schema-guided IE*, *explainability laundering*, *ablation*, *few-shot*, *in-context learning*, *fine-tuning*.

Cada término: 1-2 frases + link a su página detallada si existe.

#### `bibliografia.md`

Las 26 referencias del seminario, formateadas con DOI/arXiv link, ordenadas alfabéticamente (no por orden de aparición — en una wiki el lector busca por autor).

#### `sobre.md`

Autoría, fuente del seminario, agradecimientos a la advisora (Lorena González Manzano), licencia.

---

## 4. Stack técnico recomendado: MkDocs + Material

### 4.1. Por qué MkDocs Material

Comparé tres opciones realistas:

| Stack                       | Pro                                                                                                                                                | Contra                                                      | Veredicto                       |
| --------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------- | ------------------------------- |
| **MkDocs + Material** | Mermaid nativo, MathJax, búsqueda integrada, dark mode, deploy GitHub Pages en 1 comando, configuración YAML simple, comunidad académica activa | Solo MD, no MDX                                             | ✅**Elección**           |
| **Docusaurus**        | MDX (componentes React inline), versioning, blog                                                                                                   | Overkill para wiki estática, más config, menos académico | ❌                              |
| **VitePress**         | Rápido, Vue-based, bonito                                                                                                                         | Menos mature, menos plugins matemáticos                    | ⚠️ Alternativa si conoces Vue |

### 4.2. Configuración mínima

`mkdocs.yml`:

```yaml
site_name: IA Neurosimbólica + LLMs
site_description: Wiki de seminario sobre integración NeSy con Grandes Modelos de Lenguaje
site_author: Iabin Arteaga
site_url: https://<usuario>.github.io/nesy-llm-wiki/

theme:
  name: material
  language: es
  features:
    - navigation.tabs
    - navigation.sections
    - navigation.expand
    - navigation.top
    - navigation.indexes
    - search.suggest
    - search.highlight
    - content.code.copy
    - content.code.annotate
    - toc.follow
  palette:
    - media: "(prefers-color-scheme: light)"
      scheme: default
      primary: indigo
      accent: deep purple
      toggle:
        icon: material/brightness-7
        name: Cambiar a modo oscuro
    - media: "(prefers-color-scheme: dark)"
      scheme: slate
      primary: indigo
      accent: deep purple
      toggle:
        icon: material/brightness-4
        name: Cambiar a modo claro

plugins:
  - search:
      lang: es
  - tags
  - glightbox  # zoom on images

markdown_extensions:
  - admonition
  - pymdownx.details
  - pymdownx.superfences:
      custom_fences:
        - name: mermaid
          class: mermaid
          format: !!python/name:pymdownx.superfences.fence_code_format
  - pymdownx.tabbed:
      alternate_style: true
  - pymdownx.arithmatex:
      generic: true
  - footnotes
  - tables
  - attr_list
  - md_in_html
  - toc:
      permalink: true

extra_javascript:
  - https://polyfill.io/v3/polyfill.min.js?features=es6
  - https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js
  - https://unpkg.com/mermaid@10/dist/mermaid.min.js

nav:
  - Inicio: index.md
  - Visión general:
      - overview/que-es-nesy.md
      - overview/symbol-grounding.md
      - overview/sistema1-sistema2.md
      - overview/por-que-importa-en-llms.md
  - Taxonomía:
      - taxonomia/kautz-overview.md
      - Tipo 1: taxonomia/tipo-1.md
      - Tipo 2: taxonomia/tipo-2.md
      - Tipo 3: taxonomia/tipo-3.md
      - Tipo 4: taxonomia/tipo-4.md
      - Tipo 5: taxonomia/tipo-5.md
      - Tipo 6: taxonomia/tipo-6.md
      - taxonomia/taxonomias-alternativas.md
  - Fallas de los LLMs:
      - fallas-llm/overview.md
      - fallas-llm/alucinaciones.md
      - fallas-llm/razonamiento-multipaso.md
      - fallas-llm/deduccion-formal.md
      - fallas-llm/generalizacion-composicional.md
      - fallas-llm/opacidad.md
  - Ventajas simbólicas:
      - ventajas-simbolicas/overview.md
      - ventajas-simbolicas/determinismo.md
      - ventajas-simbolicas/verificacion-formal.md
      - ventajas-simbolicas/busqueda-combinatoria.md
      - ventajas-simbolicas/auditabilidad.md
  - Sistemas:
      - sistemas/llm-p.md
      - sistemas/duplex.md
      - sistemas/llm-modulo.md
      - sistemas/logic-lm.md
      - sistemas/cegis.md
      - sistemas/alphageometry2.md
      - sistemas/nellie.md
      - sistemas/deepproblog.md
      - sistemas/pal.md
      - sistemas/linc.md
  - Técnicas y patrones:
      - tecnicas/pddl.md
      - tecnicas/smt-solvers.md
      - tecnicas/first-order-logic.md
      - tecnicas/self-refinement.md
      - tecnicas/schema-guided-ie.md
      - tecnicas/constrained-decoding.md
      - tecnicas/cegis-pattern.md
      - tecnicas/backward-chaining.md
      - tecnicas/auxiliary-constructions.md
  - Benchmarks:
      - benchmarks/overview.md
      - benchmarks/proofwriter.md
      - benchmarks/folio.md
      - benchmarks/planbench.md
      - benchmarks/travelplanner.md
      - benchmarks/imo-geometry.md
      - benchmarks/entailmentbank.md
      - benchmarks/ar-lsat.md
  - Análisis crítico:
      - analisis-critico/latencia.md
      - analisis-critico/fragilidad-traduccion.md
      - analisis-critico/trade-soundness-generalidad.md
      - analisis-critico/coste-computacional.md
  - Ética:
      - etica/doble-sesgo.md
      - etica/explainability-laundering.md
      - etica/accountability.md
      - etica/implicaciones-regulatorias.md
  - Comparativas:
      - comparativas/llm-vs-nesy.md
      - comparativas/llmp-vs-duplex-vs-modulo.md
      - comparativas/logic-lm-vs-cegis.md
      - comparativas/alphageometry2-vs-nellie.md
      - comparativas/matriz-funcional.md
  - Glosario: glosario.md
  - Bibliografía: bibliografia.md
  - Sobre: sobre.md
```

### 4.3. Convenciones de estilo

Usar **admonitions** de Material para destacar:

- `!!! tip "TL;DR"` — el resumen al inicio de cada página.
- `!!! warning "Limitación crítica"` — para los modos de falla.
- `!!! example "Ejemplo trabajado"` — para casos concretos.
- `!!! quote "Cita clave"` — para citas literales (cortas) de papers.
- `!!! note "Para profundizar"` — para references externas.

**Bloques de código:** anotaciones `# (1)` que MkDocs renderiza como notas al pie.

**Imágenes:** todas en `docs/assets/`. Usar `![alt](../../assets/foo.svg){ width="600" }` para control de tamaño.

**Diagramas:** preferir Mermaid sobre SVG estática siempre que sea posible (editable, accesible, ligero).

### 4.4. Deploy en GitHub Pages

```bash
# Setup inicial
pip install mkdocs-material mkdocs-glightbox

# Local preview
mkdocs serve  # → http://localhost:8000

# Deploy
mkdocs gh-deploy --force
# → publica en https://<usuario>.github.io/<repo>/
```

CI con GitHub Actions (`.github/workflows/docs.yml`):

```yaml
name: Deploy MkDocs
on:
  push:
    branches: [main]
permissions:
  contents: write
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-python@v5
        with:
          python-version: '3.12'
      - run: pip install mkdocs-material mkdocs-glightbox
      - run: mkdocs gh-deploy --force
```

### 4.5. Mejoras opcionales pero altamente recomendadas

1. **Plugin `mkdocs-bibtex`:** permite citar `[@kautz2022]` con un `.bib` central. Convierte la bibliografía en algo automantenible.
2. **Plugin `mkdocs-table-reader`:** tablas grandes desde CSV externo. Útil para los benchmarks.
3. **Plugin `mkdocs-redirects`:** si renombras páginas más adelante, mantienes URLs viejas funcionando.
4. **Plugin `mkdocs-git-revision-date-localized`:** muestra "última actualización" en cada página. Profesional.
5. **Tags:** Material soporta tags por página. Útil para filtros tipo "todas las páginas Tipo 4" o "todas las que mencionan Z3".

---

## 5. Plan de migración del seminario actual

### Orden de trabajo recomendado (10-15 horas)

**Fase 1: Esqueleto técnico (1-2h)**

- Setup MkDocs + Material localmente.
- Crear todas las carpetas y archivos `.md` vacíos con su título.
- Configurar `mkdocs.yml` con la nav completa.
- Verificar que `mkdocs serve` levanta sin errores.

**Fase 2: Migración de contenido del seminario actual (4-5h)**

- Copiar literalmente las secciones existentes a sus páginas correspondientes.
- Solo limpiar: añadir TL;DR al inicio, ajustar headings (H1 → título, H2 → secciones).
- No re-escribir todavía.

**Fase 3: Páginas que faltan (3-4h)**

- Páginas de tipos Kautz individuales (las 6).
- Páginas de técnicas (las 9).
- Páginas de benchmarks (las 7).
- Glosario.

**Fase 4: Cross-linking (2h)**

- Añadir bloque "Ver también" al final de cada página con 3-5 enlaces.
- Hacer pasada de búsqueda: cada vez que se mencione "Logic-LM" en cualquier página, verificar que linkea a `sistemas/logic-lm.md`.

**Fase 5: Pulido visual (2h)**

- Añadir admonitions donde corresponda.
- Convertir SVG estática a Mermaid donde se pueda.
- Verificar mobile responsiveness.

---

## 6. Riesgos y consejos

1. **No re-escribir todo desde cero.** El contenido del seminario actual es bueno; el problema es la organización, no la prosa. Cortar y pegar 70%, escribir nuevo 30%.
2. **No sobreingeniería.** Material es bonito por defecto. Resistir la tentación de personalizar CSS hasta que funcione básicamente.
3. **Mantener una página = una idea.** Si una página supera 1500 palabras, dividirla.
4. **Cross-links son el 80% del valor.** Una wiki con poca interconexión es solo un libro mal paginado.
5. **Antes de publicar:** correr `mkdocs build --strict` — falla si hay enlaces rotos. Esencial.
6. **Para el tribunal:** la wiki se puede defender en sí misma como artefacto adicional al PDF. Mostrar en pantalla durante la presentación es legítimo y diferencia.

---

## 7. Estimación de magnitud final

- **Páginas:** ~60.
- **Palabras totales:** ~25,000-30,000 (vs 8,000 del MD actual — el aumento viene de TL;DRs, ejemplos trabajados expandidos, cross-references, secciones de "ver también").
- **Diagramas Mermaid:** ~25-30.
- **Tablas:** ~40-50.
- **Tiempo total realista:** 15-20 horas para una versión completa, pulida y desplegada.
