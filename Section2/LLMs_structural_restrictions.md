# Restricciones Estructurales de los LLMs y el Rescate Simbólico

## 2.1 Fallas estructurales de los modelos conexionistas

A pesar de la muy demostrada capacidad de los modelos conexionistas más aclamados de la actualidad (LLMs) de generar texto coherente y resolver tareas usando aproximación estadística, los mismos presentan dificultades importantes en cuanto a la generalización composicional, además de ser ineficientes con el uso de datos y de naturaleza opaca \[7\].

Su funcionamiento es el de una caja negra compuesta de nodos donde el conocimiento se encuentra distribuido en entre pesos numéricos complejos, lo que hace su comprensión una labor casi imposible \[10\]. Esta opacidad combinado con la carencia de inferencia verifiable provoca limitaciones en cuanto al uso de estas tecnologias en dominios críticos como pueden ser la medicina o el derecho.

Otra imperfección de estos son las alucinaciones (contenido generado sintácticamente correcto pero factualmente incorrecto).  Este fenómeno surge de la codificación con pérdida de información, además de la distorsión de memoria que ocurre al generalizar el conocimiento en lo que se diluye entre las sinapsis de las neuronas y el fenómeno de "Grounding" mencionado anteriormente.

En cuanto a tareas más elaboradas como pueden ser el razonamiento multi-paso o la planeación, pese a no tener una capacidad nula, estos modelos fallan sistemáticamente al intentar aplica rigor lógico a secuencias largas, pueden darse casos de alucinaciones en pasos o acciones concretas, los cuales terminan acarreando errores que terminan por generar soluciones inconsistentes a largo plazo o violar precondiciones \[10\]. Este mismo error puede ser observado al realizar calculos lógicos y aritméticos, especialmente con números grandes o cálculos complejos.

La naturaleza no determinista del conexionismo a su vez provoca fallas en la deducción formal. Los LLMs modernos a menudo se contradicen a sí mismos y fallan en tareas simples de deducción formal, como aplicar correctamente el modus ponens, el modus tollens o mantener la consistencia ante la negación \[4\]. Dichos modelos a su vez tienen una gran fragilidad sintáctica, cualquier error en el prompt o la omisión de un solo predicado por parte del LLM hace que todo el proceso falle, ya que el modelo no comprende la semántica precisa del lenguaje formal que genera \[5\].

Finalmente otra de las limitaciones de estos modelos es la dificultad para la generalización composicional. Pese a que en ocasiones logran "comprender" piezas o tareas, no siempre pueden directamente extrapolarlas y aplicarlas correctamente en secuencias no conocidas, demostrando esto que sus capacidades son de reconocimiento de patrones, no de entendimiento de las acciones o procesos como tal.

&nbsp;

## Ventajas de la arquitectura simbólica

A diferencia de los modelos completamente conexionistas, los cuales on probabilisticos, los sistemas simbólicos operan bajo reglas lógicas estrictas las cuales garantizan resultados consistentes.

Los motores de razonamiento simbólico, como las Redes Neuronales Lógicas (LNN), permiten realizar inferencias deterministas y reproducirles, dicha convergencia es demostrable en un número finito de pasos. En problemas como los de planificación robótica, se hace empleo de lenguajes formales como PDDL con el fin de conservar de manera explícita la trazabilidad del proceso de decisión y reducir la variabilidad no controlada que aparece en los modelos de aprendizaje estadístico puro.

Otra ventaja de la arquitectura NeSy es la posible implementacion de mecanismos de verificación formal los cuales otorgan garantías de seguridad matemáticamente verificables. Para esto los planificadores clásicos facilitan dicha validación, ya que permiten que mecanismos verificadores externos comprueben matemáticamente que las precondiciones de cada acción, los efectos de las transiciones y las metas del sistema se cumplan correctamente antes y durante la ejecución del plan.

Otra alternativa es que al incorporar solucionadores SMT (Satisfiability Modulo Theories) o intérpretes de código, como ocurre en enfoques como PAL, el resultado final deja de depender únicamente de la generación probabilística del modelo y pasa a estar respaldado por un mecanismo de ejecución o verificación formal. De esta manera, las respuestas pueden obtenerse con precisión y corrección por construcción, reduciendo de forma importante los errores lógicos o aritméticos que suelen aparecer en los LLMs mencionados en la sección anterior \[3\].

Para la resolución de problemas combinatorios complejos y la búsqueda de la ruta de ejecución mas eficiente los motores simbólicos destacan especialmente. Herramientas como el Fast Downward usan algoritmos de búsqueda los cuales permiten computar la secuencia de acciones optima para alcanzar el objetivo, una labor que suele ser difícil para los modelos conexionistas. Sistemas como **AlphaGeometry** muestran que un motor simbólico puede inferir propiedades de manera fiable mediante reglas formales de deducción, llegando incluso a superar a expertos humanos en la resolución de problemas de olimpiadas matemáticas, y haciéndolo sin introducir errores de cálculo \[5\].

Podemos interpretar el la arquitectura simbólica como un sistema que razona de una manera más lenta, deliberativa y lógica, como un paso a paso, lo que proporciona una estructura que los humanos podemos auditar. Cada desición esta respaldada por un arbol de pruebas interpretable por humanos además, en marcos como las LNN cada elemento de la red tiene una correspondencia 1 a 1 con fórmulas lógicas, lo que permite examinar la cadena de inferencias calculada para cualquier consulta.

### Referencias

\[1\] R. Riegel et al., “Logical Neural Networks,” arXiv preprint arXiv:2006.13155, 2020.

\[2\] N. Weir, P. Clark, and B. Van Durme, “NELLIE: A Neuro-Symbolic Inference Engine for Grounded, Compositional, and Explainable Reasoning,” arXiv preprint arXiv:2209.07662, 2022.

\[3\] L. Gao et al., “PAL: Program-aided Language Models,” arXiv preprint arXiv:2211.10435, 2022.

\[4\] D. Calanzone, S. Teso, and A. Vergari, “Logically Consistent Language Models via Neuro-Symbolic Integration,” arXiv preprint arXiv:2409.13724, 2024.

\[5\] Y. Chervonyi et al., “Gold-medalist Performance in Solving Olympiad Geometry with AlphaGeometry2,” Google DeepMind, 2025.

\[6\] A. Patil and A. Jadon, “Advancing Reasoning in Large Language Models: Promising Methods and Approaches,” arXiv preprint arXiv:2502.03671, 2025.

\[7\] K. Hua, Y. Gu, D. Wang, and X. Ma, “DUPLEX: Agentic Dual-System Planning via LLM-Driven Information Extraction,” arXiv preprint arXiv:2603.23909, 2026.

\[8\] L. Luo, Y.-F. Li, G. Haffari, and S. Pan, “Reasoning on Graphs: Faithful and Interpretable Large Language Model Reasoning,” 2024.

\[9\] S. K. Jha et al., “Counterexample Guided Inductive Synthesis Using Large Language Models and Satisfiability Solving,” 2023.

\[10\] W. Wang, Y. Yang, and F. Wu, “Towards Data-And Knowledge-Driven AI: A Survey on Neuro-Symbolic Computing,” IEEE Transactions on Pattern Analysis and Machine Intelligence, vol. 47, no. 1, 2024.

\[11\] B. P. Bhuyan, A. Ramdane-Cherif, R. Tomar, and T. P. Singh, “Neuro-symbolic artificial intelligence: a survey,” Neural Computing and Applications, vol. 36, pp. 12809–12844, 2024.

\[12\] T. H. Trinh, Y. Wu, Q. V. Le, H. He, and T. Luong, “Solving olympiad geometry without human demonstrations,” Nature, vol. 625, no. 7995, 2024.

&nbsp;
