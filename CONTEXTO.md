# Contexto de continuidad

- **Actualizado:** 2026-09-19.
- **Carpeta y rama:** `/Users/zonbks/sources/zonbksXS/base-config-agents`, `main` con seguimiento de `origin/main`.
- **Objetivo vigente:** implementar las mejoras de especificaciones y continuidad identificadas en la revisión anterior. Implementación terminada; cambios locales sin commit.
- **Proyecto:** plantilla documental neutral. No contiene aplicación ni comandos de compilación o pruebas de producto. Los campos de `docs/PROJECT_CONTEXT.md` se completan al adoptar la plantilla en un proyecto consumidor.
- **Restricciones:** cambio mínimo, conservación de trabajo ajeno y de la arquitectura vigente; sin acceso a Figma o Confluence sin autorización; sin dependencias nuevas ni resultados de pruebas inventados.
- **Decisión:** ampliar las cuatro plantillas SDD existentes; glosario y contratos extensos siguen siendo condicionales y deben referenciar fuentes canónicas. Motivos en `docs/DECISIONS.md`, DEC-003.
- **Avances:** fuentes y escenarios en especificaciones, contratos y compatibilidad en diseño, evaluación de patrones en plan, tareas vinculadas a AC y evidencia. La guía distingue entrega parcial de cierre satisfactorio y exige resolver dudas materiales antes de implementar.
- **Continuidad:** `AGENTS.md` exige leer y actualizar este archivo; hechos estables en `docs/PROJECT_CONTEXT.md`, historial en `WORKLOG.md`. El README explica cómo adaptar el contexto al copiar la plantilla.
- **Ejemplo:** `docs/sdd/examples/ejemplo-minimo.md` es ficticio y muestra tres criterios con verificaciones previstas; no representa funcionalidad ni pruebas ejecutadas del repositorio.
- **Manual técnico:** corregidos el retorno duplicado del diagrama de ejemplo y la propagación de fallos del bloque Bash de conteos. Los conteos no sustituyen la reconciliación del inventario.
- **Archivos relevantes:** `AGENTS.md`, `README.md`, `docs/sdd/`, `docs/instrucciones-generacion-manual-tecnico.md`, `.gitignore`, `docs/DECISIONS.md`, `CHANGELOG.md` y `WORKLOG.md`.
- **Verificaciones:** `python3 - <<'PY'` con biblioteca estándar: 16 Markdown, 10 enlaces locales y cero incidencias estructurales. Otro bloque extrajo el ejemplo Bash real, comprobó sintaxis con `bash -n` y lo ejecutó con `bash` sobre archivos temporales: 16/16 escenarios correctos (3 aceptados y 13 rechazados). `git diff --check` sin errores.
- **Exclusiones verificadas:** `git check-ignore -v docs/.DS_Store` y `git check-ignore --no-index -v .DS_Store` coinciden con la nueva regla. El `.DS_Store` de raíz sigue versionado; añadir una exclusión no lo retira del índice. No se eliminó ningún archivo.
- **Límites:** no se renderizó Mermaid porque `mmdc` no está disponible. No hay compilación ni pruebas de aplicación aplicables. La comprobación documental no demuestra comportamiento de un producto consumidor.
- **Pendientes y próximos pasos:** publicar los cambios solo si se solicita; al adoptar la plantilla, completar contexto, rutas, contratos y comandos reales. `init.ini` sigue vacío y fuera del alcance. Historial y resultados de la revisión anterior preservados en `WORKLOG.md`.
