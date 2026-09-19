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

## 2026-09-19 — Analizar mejoras y suficiencia de especificaciones

- **Objetivo:** identificar mejoras verificables y archivos adicionales útiles para especificaciones sin implementar cambios en los estándares.
- **Alcance:** reglas, arquitectura, contexto, README, cuatro plantillas SDD y guía de manual técnico. Revisión SDD especializada de solo lectura; consolidación en `CONTEXTO.md` y este registro.
- **Hallazgos:** ampliar escenarios, reglas y requisitos de calidad en la especificación; conectar tareas con criterios y evidencia; incorporar al plan la evaluación de patrones ya exigida; definir preparación y cierre de especificaciones. Aclarar continuidad en las reglas versionadas y el índice de documentos. La guía contiene comparaciones que pueden ocultar un fallo previo y un retorno adicional tras una rama que declara finalizar el flujo.
- **Propuestas:** ampliar documentos existentes antes de crear otros; glosario, detalle de contratos y ejemplo SDD resuelto solo cuando aporten valor. Ninguna propuesta se convirtió en regla vigente.
- **Patrón de diseño:** no aplica; análisis documental.
- **Comprobaciones:** `git status --short --branch`, `rg --files --hidden -g '!.git/**' -g '!**/.DS_Store'` y `git ls-files --stage` confirmaron el inventario. `python3 - <<'PY'` con `pathlib` y `re` verificó 15 Markdown y 5 enlaces locales: sin archivos vacíos, espacios finales, marcas de conflicto ni cercas abiertas. El mismo bloque extrajo las cinco comparaciones del manual y las ejecutó con `bash -c`: conteos simulados `endpoints=1`, `descriptions=0` y los demás iguales a 1 terminaron con código 0, reproduciendo el fallo de propagación.
- **Pendientes:** aplicar las propuestas si se solicita. No se ejecutaron compilación, pruebas de aplicación ni renderizado Mermaid; la comprobación estructural no los sustituye. Se conservaron los archivos `.DS_Store` existentes.

## 2026-09-19 — Implementar mejoras de especificaciones y continuidad

- **Objetivo:** aplicar las mejoras autorizadas manteniendo la neutralidad y el alcance documental.
- **Cambios:** ampliadas guía y cuatro plantillas SDD; añadido ejemplo ficticio con tres criterios; continuidad integrada en `AGENTS.md` y README; agregado `.gitignore` para macOS; corregidos propagación de errores y retorno del ejemplo del manual; actualizados DEC-003, changelog y contexto. El glosario y los contratos extensos se crean únicamente cuando exista necesidad; no se generaron plantillas vacías adicionales.
- **Patrón de diseño:** no aplica; edición documental. El bloque Bash conserva una sola ruta de comprobación y usa un subshell para limitar las opciones de error.
- **Comprobaciones:** `python3 - <<'PY'` con `pathlib` y `re`: 16 Markdown y 10 enlaces locales, sin archivos vacíos, espacios finales, marcas de conflicto ni cercas abiertas. Un segundo bloque con `subprocess` y `tempfile` extrajo el ejemplo Bash del manual, ejecutó `bash -n` y comprobó 16 escenarios ejecutando `bash`: tres documentos válidos aceptados y trece rechazos esperados (secciones ausentes o duplicadas, archivo vacío/inexistente y ausencia de operaciones). Los archivos temporales se eliminaron automáticamente.
- **Revisión:** trazabilidad manual de los tres AC del ejemplo hacia requisito, componente, tarea y resultado esperado; evidencia ficticia marcada pendiente. `git diff --check` terminó sin errores. `git check-ignore -v docs/.DS_Store` y `git check-ignore --no-index -v .DS_Store` confirmaron la regla de exclusión.
- **Limitaciones:** `command -v mmdc` no encontró renderizador; no se renderizó Mermaid. Compilación y pruebas de aplicación no aplican. El `.DS_Store` de raíz continúa versionado; los archivos existentes y los registros previos fueron conservados.
- **Pendientes:** sin implementación pendiente dentro del alcance. Cambios locales sin commit; configuración de proyectos consumidores y publicación quedan para solicitudes posteriores.
