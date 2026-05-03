# Ventajas de la arquitectura simbólica

!!! tip "TL;DR"
    Los sistemas simbólicos aportan reglas explícitas, verificabilidad y trazas
    auditables. NeSy los usa para compensar la naturaleza probabilística de los
    LLMs.

## Propiedades clave

- **Determinismo:** mismas premisas, misma inferencia.
- **Verificación formal:** precondiciones, efectos y metas pueden comprobarse.
- **Búsqueda combinatoria:** planificadores y solvers exploran espacios enormes.
- **Auditabilidad:** las pruebas y planes pueden inspeccionarse paso a paso.

## Lo que no resuelve automáticamente

!!! warning "Basura entra, basura sale"
    Un solver correcto puede razonar perfectamente sobre premisas equivocadas.
    La calidad de la interfaz neuronal-simbólica sigue siendo el punto crítico.

## Ver también

- [Fragilidad de traducción](../analisis-critico/fragilidad-traduccion.md)
- [PDDL](../tecnicas/pddl.md)
- [SMT / Z3](../tecnicas/smt-solvers.md)
