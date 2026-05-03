# 5. Evidencia empírica y claims verificables

Esta página conecta la lectura pedagógica con la evidencia académica. Su función
es dejar claro qué afirmaciones están apoyadas por resultados concretos, qué
afirmaciones son interpretativas y dónde están los límites de cada claim.

!!! warning "Lectura correcta de las cifras"
    Las cifras dependen del benchmark, modelo base, configuración de prompting,
    hardware y presupuesto de búsqueda. Deben leerse como evidencia comparativa,
    no como constantes universales.

## Tabla de resultados clave

| Claim | Evidencia citada | Interpretación |
|---|---|---|
| Los LLMs puros fallan en planificación de horizonte medio. | En Blocksworld/PlanBench, GPT-4 con chain-of-thought ronda ~35% de éxito, frente a ~97-100% de planificadores clásicos sobre PDDL correcto [16]. | El LLM produce planes plausibles, pero no garantiza satisfacibilidad ni respeto de precondiciones. |
| LLM+P mejora sobre planificación end-to-end. | En dominios IPC evaluados por LLM+P, el pipeline LLM + Fast Downward supera claramente a baselines vanilla, a menudo acercándose a 80-100% según dominio [8]. | La mejora viene de delegar la búsqueda al planificador, no de que el LLM planifique formalmente. |
| Logic-LM mejora razonamiento lógico frente a CoT puro. | En FOLIO, GPT-4 + CoT ronda ~70.6%, mientras Logic-LM con GPT-4 alcanza ~78.9%; en ProofWriter pasa aproximadamente de ~76% a ~83% [9]. | Los solvers externos corrigen parte de la inconsistencia, aunque no eliminan errores de formalización. |
| El self-refinement aporta, pero no garantiza convergencia. | Logic-LM reporta mejoras de varios puntos por bucles de reparación, alrededor de ~5-8 puntos según ablation [9], [20]. | El feedback del solver es útil, pero puede ser pobre o introducir nuevas inconsistencias. |
| AlphaGeometry2 es un caso fuerte de generación neuronal + verificación simbólica. | AlphaGeometry2 resuelve 84% de los problemas IMO Geometry 2000-2024 (42/50), frente al 54% de AlphaGeometry original [15], [21]. | El modelo neuronal propone construcciones; DDAR valida la prueba. Por eso es Tipo 2. |
| NeSy mejora trazabilidad, no justicia automática. | El caso de sesgo médico de Obermeyer et al. advierte que premisas sesgadas pueden recibir legitimación formal [26]. | Una inferencia simbólica puede ser válida y aun así descansar sobre datos injustos. |

## Qué claims son taxonómicos

| Claim | Estado |
|---|---|
| LLM vanilla como Tipo 1 bajo lectura LLM-céntrica de Kautz. | Interpretación usada en esta wiki, con matiz de que la formulación original de Kautz no estaba pensada solo para LLMs. |
| LLM+P, Logic-LM y DUPLEX como Tipo 4. | Claim taxonómico fuerte: el LLM formaliza y el solver razona. |
| AlphaGeometry2 como Tipo 2. | Claim taxonómico fuerte: DDAR gobierna la búsqueda y el modelo neuronal funciona como subrutina heurística. |
| CEGIS como híbrido funcional. | La wiki lo trata con cuidado: es generación neuronal + verificación SMT, pero no se fuerza a una etiqueta Kautz única. |
| NELLIE como búsqueda de pruebas menos rígida. | Claim funcional: combina backward chaining con recuperación/generación/unificación semántica, por lo que su encaje taxonómico es menos limpio. |

## Qué claims son críticos

| Claim crítico | Fundamento |
|---|---|
| La interfaz neuronal-simbólica es el eslabón débil. | En LLM+P, Logic-LM y DUPLEX, el solver solo razona sobre la formalización recibida. Si esa formalización es incorrecta, la salida puede ser inútil o engañosa [8], [9], [14], [16]. |
| La latencia limita aplicaciones reactivas. | Los pipelines revisados requieren 1-N llamadas a solver/LLM y tiempos aproximados de segundos a minutos, especialmente en self-refinement y búsqueda de pruebas. |
| La soundness se compra con pérdida de generalidad. | Z3, Fast Downward y DDAR ofrecen garantías fuertes dentro de lenguajes estrechos; NELLIE y LLMs puros cubren más lenguaje natural, pero con menos garantías. |

## Tabla de latencia orientativa

| Sistema | Estrategia | Llamadas al solver | Latencia aproximada | Viabilidad en tiempo real |
|---|---|---:|---|---|
| LLM puro + CoT | Sin solver externo | 0 | ~1-10 s | Alta |
| Logic-LM | Solver + self-refinement | 1-N | ~10-60 s | Baja |
| LLM+P | Planificador offline | 1 | ~5-30 s + planner | Media/offline |
| DUPLEX | IE + PDDL + planner + Slow System | 1-3 | ~10-90 s | Media |
| AlphaGeometry2 | DDAR + búsqueda con construcciones | N | minutos a horas | Muy baja |

## Función dentro de la wiki

Esta página complementa la ruta conceptual con evidencia empírica y cautelas de
interpretación:

1. Sitúa la tesis: LLM para traducir/proponer; solver para verificar.
2. Relaciona la taxonomía con sistemas concretos: Tipo 4 para pipelines, Tipo 2 para AlphaGeometry2.
3. Resume resultados que justifican la motivación neurosimbólica.
4. Mantiene la cautela crítica: la formalización y el grounding siguen siendo el
   punto frágil.

## Próximo capítulo

Después de revisar la evidencia, continúa con [Fragilidad y límites](fragilidad.md).
