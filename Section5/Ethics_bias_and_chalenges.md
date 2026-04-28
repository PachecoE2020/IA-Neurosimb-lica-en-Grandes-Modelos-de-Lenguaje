# 5. Cuestiones Éticas, Sesgos y Retos Futuros

La integración neurosimbólica no responde únicamente a una búsqueda de rendimiento, sino a una necesidad de mayor transparencia y responsabilidad frente a las limitaciones éticas de los modelos puramente estadísticos. Sin embargo, esta integración no elimina los problemas éticos: los redistribuye y, en ciertos casos, los complejiza.

---

## 5.1. Ética y Propagación de Sesgos en Entornos Híbridos

Los sistemas NeSy enfrentan una dualidad de sesgo con orígenes diferenciados. Los sesgos sub-simbólicos emergen de las distribuciones estadísticas en los datos de entrenamiento: la red neuronal los codifica como patrones probabilísticos opacos, difíciles de identificar y desarticular. Los sesgos simbólicos, en cambio, provienen de reglas y ontologías definidas por humanos que pueden estar pre-sesgadas desde su concepción y, al estar formalizadas, se propagan con plena certeza lógica hacia dominios de alto impacto social.

El punto crítico es que ambas dimensiones se componen en la interfaz de integración. Un hecho extraído mediante percepción neuronal sesgada se convierte en premisa del razonador simbólico, que lo trata como verdad formal. El resultado es una falsa sensación de rigor: el sistema produce árboles de prueba lógicamente válidos sobre fundamentos contaminados, lo que puede otorgarle mayor credibilidad institucional que a un modelo puramente estadístico, precisamente porque aparenta ser explicable. Marcos como LNN abordan este problema mediante salvaguardas matemáticas que detectan contradicciones antes de que se propaguen, pero la calidad de los datos y la neutralidad de las reglas siguen siendo responsabilidades externas al formalismo técnico.

---

## 5.2. Responsabilidad (Accountability) y Transparencia

En dominios de alto riesgo como la medicina o el derecho, la opacidad de la caja negra neural es inaceptable. La integración NeSy transforma la transparencia de una interpretación post-hoc a una propiedad nativa de la arquitectura: cada decisión puede rastrearse a través de las fórmulas lógicas que la produjeron, vinculando el resultado a los hechos concretos de la base de conocimiento que activaron las reglas.

Sin embargo, esta explicabilidad es parcial por construcción. Los árboles de prueba son trazables en su dimensión simbólica, pero sus premisas provienen de la red neuronal, que permanece relativamente opaca. Esto genera una brecha en la accountability causal: cuando el sistema comete un error, no siempre es posible determinar si la falla residió en la percepción, en las reglas o en la arquitectura de integración. Para mitigar este problema, arquitecturas recientes como DUPLEX restringen el componente neural a la extracción de información estructurada, delegando la validación lógica a planificadores simbólicos, e incorporan ciclos de autocorrección cuando se detectan inconsistencias.

En síntesis, la integración neurosimbólica representa un avance real hacia una IA auditable y responsable. Sin embargo, la equidad de los datos, la neutralidad de las reglas y la delimitación ética de los dominios de aplicación permanecen como obligaciones institucionales que ninguna arquitectura puede sustituir.
