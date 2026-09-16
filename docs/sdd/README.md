# Desarrollo dirigido por especificaciones

Usa este flujo para cambios no triviales, con múltiples componentes, contratos nuevos o decisiones relevantes. Los ajustes pequeños pueden documentarse directamente en el plan de trabajo si el contexto es suficiente.

## Flujo

1. `spec.md`: define problema, alcance y criterios de aceptación.
2. `design.md`: describe la solución técnica y sus decisiones.
3. `plan.md`: ordena la implementación y la validación.
4. `tasks.md`: registra tareas concretas y su estado.

## Reglas

- Copia las plantillas a una carpeta propia del cambio, por ejemplo `docs/sdd/<identificador>/`.
- Distingue hechos confirmados, decisiones, supuestos y preguntas abiertas.
- Mantén trazabilidad entre requisitos, diseño, tareas y pruebas.
- Actualiza los documentos cuando cambie una decisión relevante.
- No incluyas reglas de conducta de agentes; esas pertenecen a `AGENTS.md`.
