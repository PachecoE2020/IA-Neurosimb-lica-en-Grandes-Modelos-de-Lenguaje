# 7. Ética y accountability

La IA neurosimbólica suele presentarse como más transparente que los LLMs puros.
Eso es cierto en parte: una prueba, un plan o una traza lógica son más
auditables que una respuesta generada sin estructura. Pero la transparencia
simbólica no resuelve automáticamente los problemas éticos. A veces los hace más
difíciles de ver.

## Doble origen del sesgo

En un sistema híbrido hay dos fuentes de sesgo:

| Fuente | De dónde viene | Cómo se propaga |
|---|---|---|
| Sesgo neuronal | Datos de entrenamiento, embeddings, extracción de información. | El LLM convierte patrones sesgados en hechos o premisas. |
| Sesgo simbólico | Ontologías, reglas, categorías humanas. | El solver aplica reglas sesgadas con certeza lógica. |

El problema aparece cuando un hecho extraído por el componente neuronal entra al
motor simbólico. Desde ese momento, el solver lo trata como premisa formal.

## Explainability laundering

*Explainability laundering* significa que una explicación formal puede lavar o
legitimar una decisión problemática. El sistema muestra un árbol de prueba y eso
produce confianza, aunque las premisas sean defectuosas.

Ejemplo abstracto:

1. El LLM clasifica erróneamente a una persona dentro de una categoría.
2. Esa categoría se convierte en predicado formal.
3. El sistema simbólico aplica reglas correctamente.
4. La conclusión parece objetiva porque tiene una traza lógica.

La lógica no arregla una premisa injusta. Solo la propaga de forma consistente.

El merged ilustra este riesgo con un ejemplo inspirado en sesgo médico:
Obermeyer et al. muestran que algoritmos sanitarios pueden codificar sesgos
raciales cuando usan proxies aparentemente neutrales, como costes de salud, en
lugar de necesidad médica real [26]. En un sistema NeSy, un componente neuronal
podría extraer un predicado sesgado y el razonador simbólico aplicarlo con
perfecta consistencia formal. La traza sería auditable, pero la premisa seguiría
siendo injusta.

## Accountability parcial

Los sistemas NeSy mejoran la trazabilidad del componente simbólico:

- se puede ver qué regla se activó;
- se puede inspeccionar qué premisa se usó;
- se puede reproducir la inferencia;
- se puede validar un plan o una prueba.

Pero queda una zona opaca:

- por qué el LLM extrajo esa premisa;
- por qué omitió otra;
- por qué interpretó una frase de cierta manera;
- qué sesgos estaban presentes en sus pesos o datos.

Por eso la accountability es parcial. Se sabe cómo razonó el solver, pero no
siempre se sabe por qué el sistema llegó a esas premisas.

## Buenas prácticas

| Riesgo | Buena práctica |
|---|---|
| Premisas sesgadas | Registrar fuente, confianza y método de extracción. |
| Reglas injustas | Auditar ontologías con expertos del dominio. |
| Falsa certeza | Presentar conclusiones condicionadas por premisas. |
| Opacidad neuronal | Separar claramente extracción, validación e inferencia. |
| Dominio crítico | Mantener revisión humana y trazas reproducibles. |

## Qué decir en la conclusión del trabajo

Una conclusión fuerte no debería decir simplemente:

> NeSy resuelve la opacidad de los LLMs.

Sería más preciso decir:

> NeSy desplaza parte de la opacidad hacia interfaces más auditables. Mejora la
> trazabilidad del razonamiento, pero no garantiza justicia, verdad ni
> corrección end-to-end si las premisas, reglas u ontologías son defectuosas.

## Cierre de la ruta

Has recorrido la idea completa:

1. Los LLMs son flexibles pero no verificables.
2. Los sistemas simbólicos son verificables pero rígidos.
3. La taxonomía de Kautz permite clasificar formas de integración.
4. Los pipelines modernos separan traducción neuronal y razonamiento simbólico.
5. Los sistemas reales mejoran fiabilidad, pero siguen siendo frágiles.
6. La evidencia empírica apoya mejoras reales, pero condicionadas por dominio,
   formalización y presupuesto de cómputo.
7. La explicabilidad simbólica no elimina sesgos ni responsabilidad humana.

Para repasar visualmente, vuelve a la [Matriz funcional](../comparativas/matriz-funcional.md)
o revisa el [Glosario](../glosario.md).
