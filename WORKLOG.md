# Registro de trabajo

Este documento conserva evidencia operativa. No reemplaza al `CHANGELOG.md`: aquí se registran acciones y comprobaciones; allí, cambios relevantes del producto o plantilla.

## Formato de entrada

### AAAA-MM-DD — Título breve

- **Objetivo:** resultado solicitado.
- **Alcance:** componentes o archivos afectados.
- **Cambios:** acciones completadas.
- **Comprobaciones:** comandos ejecutados y resultados reales.
- **Pendientes:** limitaciones o trabajo no realizado.

## 2026-09-06 — Crear estructura estándar inicial

- **Objetivo:** establecer una base neutral para proyectos asistidos por agentes IA.
- **Alcance:** gobierno de agentes, contexto, decisiones, trazabilidad y plantillas SDD.
- **Cambios:** se crearon los documentos iniciales del repositorio.
- **Comprobaciones:** se confirmó que los 12 archivos esperados existen y no están vacíos; no se detectaron marcadores de trabajo pendiente. `git diff --check` no aplica porque la carpeta aún no es un repositorio Git.
- **Pendientes:** definir tecnología, arquitectura, comandos, perfiles y políticas específicas según futuras indicaciones.

## 2026-09-06 — Agregar estándar de estilo de código

- **Objetivo:** definir reglas generales de codificación aplicables a distintos lenguajes y frameworks.
- **Alcance:** estilo de código, referencias operativas y trazabilidad.
- **Cambios:** se agregó `CODING_STYLE.md` y se enlazó desde `README.md` y `AGENTS.md`.
- **Comprobaciones:** `CODING_STYLE.md` existe y no está vacío; sus referencias desde `README.md` y `AGENTS.md` están presentes; los Markdown no tienen espacios finales ni marcadores de trabajo pendiente. `git diff --check` no aplica porque la carpeta aún no es un repositorio Git.
- **Pendientes:** crear adaptaciones por tecnología cuando se defina el stack de cada proyecto.

## 2026-09-08 — Definir arquitectura neutral y ubicación semántica

- **Objetivo:** explicitar arquitectura e ingeniería de software sin fijar tecnología.
- **Alcance:** `docs/ARCHITECTURE.md`, `AGENTS.md`, `CODING_STYLE.md`, `README.md`, `docs/sdd/templates/design.md`, `docs/DECISIONS.md`, `CHANGELOG.md` y `WORKLOG.md`.
- **Cambios:** se definió hexagonal por defecto con Clean como alternativa explícita, dirección de dependencias, espacios propios para DTO y entidades y ubicación de constantes y utilidades por responsabilidad. Se separaron adaptaciones aceptadas de propuestas y se conectó la definición con las reglas y el diseño SDD.
- **Comprobaciones:** `python3 - <<'PY'` (validación documental mediante `pathlib` y `re`) terminó correctamente: 13 Markdown no vacíos y sin espacios finales, 5 enlaces locales válidos, secciones y referencias arquitectónicas presentes. Revisión directa de los documentos afectados para comprobar neutralidad tecnológica y separación entre reglas vigentes y propuestas. `git status --short` confirmó que la carpeta no es un repositorio Git; no se pudo usar un diff Git.
- **Pendientes:** cada proyecto consumidor debe definir módulos y rutas reales. No hay compilación ni pruebas de aplicación aplicables a esta plantilla documental. No se generó un grafo ni se instalaron herramientas.

## 2026-09-08 — Separar namespaces de contratos y persistencia

- **Objetivo:** distinguir obligatoriamente DTO entre capas, entidades de base de datos y DTO de respuesta al frontend.
- **Alcance:** `docs/ARCHITECTURE.md`, `CODING_STYLE.md`, `CHANGELOG.md` y `WORKLOG.md`.
- **Cambios:** se precisaron namespaces, paquetes o módulos separados, incluso con campos idénticos; se documentaron mapeos en adaptadores y la prohibición de exponer entidades persistentes o DTO internos como respuestas públicas. Se reemplazó la regla previa que podía permitir compartir DTO entre esos límites.
- **Comprobaciones:** `python3 - <<'PY'` con `pathlib` y `re`: 13 Markdown no vacíos y sin espacios finales, 5 enlaces locales válidos, sección nueva presente y excepción anterior retirada. Revisión de coherencia entre arquitectura y estilo.
- **Pendientes:** validación de código no aplicable; cambio exclusivamente documental.

## 2026-09-08 — Evaluar patrones de diseño sin sobreingeniería

- **Objetivo:** evaluar patrones antes de implementar y adoptarlos solo cuando aporten valor concreto.
- **Alcance:** `AGENTS.md`, `CODING_STYLE.md`, `CHANGELOG.md` y `WORKLOG.md`.
- **Cambios:** evaluación obligatoria en el plan previo, comparación con la solución directa y criterios de beneficio frente a complejidad; se permite descartar patrones o indicar que no aplican sin crear documentación adicional.
- **Patrón de diseño:** no aplica; ajuste de instrucciones documentales sin diseño de código.
- **Comprobaciones:** `python3 - <<'PY'` con `pathlib` y `re` terminó correctamente: 13 Markdown no vacíos y sin espacios finales, 5 enlaces locales válidos y reglas de evaluación presentes. Revisión directa de compatibilidad con las restricciones existentes sobre abstracciones y alcance.
- **Pendientes:** compilación y pruebas de aplicación no aplican al cambio documental.
