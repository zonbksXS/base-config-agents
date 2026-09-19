# Changelog

Los cambios relevantes de este proyecto se documentan en este archivo.

El formato sigue las categorías de Keep a Changelog y el versionado se definirá cuando el proyecto adopte una estrategia de versiones.

## [Sin publicar]

### Agregado

- Regla de continuidad entre sesiones en `CONTEXTO.md`, diferenciada del contexto estable y del historial.
- Ejemplo SDD ficticio con trazabilidad desde requisitos hasta comprobaciones previstas.
- Exclusión de metadatos locales de macOS mediante `.gitignore`.

- Evaluación obligatoria de patrones de diseño antes de implementar, con adopción condicionada a un beneficio concreto y sin sobreingeniería.

- Definición arquitectónica neutral con hexagonal por defecto, alternativa Clean y registros de adaptaciones y propuestas.
- Ubicación semántica obligatoria y espacios propios para DTO, entidades y modelos de persistencia.

- Estructura base neutral para trabajar con agentes IA.
- Reglas operativas, trazabilidad y plantillas SDD.
- Estándar neutral de estilo de código y revisión técnica.

### Cambiado

- Plantillas SDD con fuentes, escenarios, contratos, requisitos de calidad aplicables, criterios de inicio y cierre, y evidencia de validación por criterio de aceptación.
- Índice y uso inicial de la plantilla para incluir continuidad, ejemplo SDD y guía de manual técnico.

- Separación explícita de namespaces para DTO entre capas, entidades de base de datos y DTO de respuesta al frontend, con mapeos en los límites.

### Corregido

- El bloque de comprobación de cobertura del manual propaga fallos de lectura, secciones ausentes y diferencias de conteo.
- El ejemplo de secuencia del manual devuelve un único resultado por rama.

### Eliminado
