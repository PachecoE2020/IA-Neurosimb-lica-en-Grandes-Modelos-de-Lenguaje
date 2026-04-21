# Restricciones Estructurales de los LLMs y el Rescate Simbólico
## 2.1 Fallas estructurales de los modelos conexionistas

A pesar de la muy demostrada capacidad de los modelos conexionistas más aclamados de la actualidad (LLMs) de generar texto coherente y resolver tareas usando aproximación estadística, los mismos presentan dificultades importantes en cuanto a la generalización composicional, además de ser ineficientes con el uso de datos y de naturaleza opaca. (Wang et al.)

Su funcionamiento es el de una caja negra compuesta de nodos donde el conocimiento se encuentra distribuido en entre pesos numéricos complejos, lo que hace su comprensión una labor casi imposible. (Towards_Data-And_Knowledge-Driven_AI_A_Survey_on_Neuro-Symbolic_Computing.pdf) Esta opacidad combinado con la carencia de inferencia verifiable provoca limitaciones en cuanto al uso de estas tecnologias en dominios críticos como pueden ser la medicina o el derecho.

Otra imperfección de estos son las alucinaciones (contenido generado sintácticamente correcto pero factualmente incorrecto).  Este fenómeno surge de la codificación con pérdida de información, además de la distorsión de memoria que ocurre al generalizar el conocimiento en lo que se diluye entre las sinapsis de las neuronas y el fenómeno de "Grounding" mencionado anteriormente.

En cuanto a tareas más elaboradas como pueden ser el razonamiento multi-paso o la planeación, pese a no tener una capacidad nula, estos modelos fallan sistemáticamente al intentar aplica rigor lógico a secuencias largas, pueden darse casos de alucinaciones en pasos o acciones concretas, los cuales terminan acarreando errores que terminan por generar soluciones inconsistentes a largo plazo o violar precondiciones. (DUPLEX: Agentic Dual-System Planning via LLM-Driven Information Extraction). Este mismo error puede ser observado al realizar calculos lógicos y aritméticos, especialmente con números grandes o cálculos complejos.

La naturaleza no determinista del conexionismo a su vez provoca fallas en la deducción formal. Los LLMs modernos a menudo se contradicen a sí mismos y fallan en tareas simples de deducción formal, como aplicar correctamente el modus ponens, el modus tollens o mantener la consistencia ante la negación (Logically Consistent Language Models via Neuro-Symbolic Integration). Dichos modelos a su vez tienen una gran fragilidad sintáctica, cualquier error en el prompt o la omisión de un solo predicado por parte del LLM hace que todo el proceso falle, ya que el modelo no comprende la semántica precisa del lenguaje formal que genera. (Gold-medalist Performance in Solving Olympiad Geometry with AlphaGeometry2)

Finalmente otra de las limitaciones de estos modelos es la dificultad para la generalización composicional. Pese a que en ocasiones logran "comprender" piezas o tareas, no siempre pueden directamente extrapolarlas y aplicarlas correctamente en secuencias no conocidas, demostrando esto que sus capacidades son de reconocimiento de patrones, no de entendimiento de las acciones o procesos como tal.



## 2.2 Ventajas de la arquitectura simbólica

WIP




