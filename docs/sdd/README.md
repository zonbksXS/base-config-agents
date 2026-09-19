# Desarrollo dirigido por especificaciones

Usa este flujo para cambios no triviales, con múltiples componentes, contratos nuevos o decisiones relevantes. Los ajustes pequeños pueden documentarse directamente en el plan de trabajo si el contexto es suficiente. El [ejemplo mínimo](examples/ejemplo-minimo.md) es ficticio y muestra cómo enlazar los documentos sin exigir su tamaño ni sus detalles en cada cambio.

## Flujo

1. `spec.md`: define problema, alcance y criterios de aceptación.
2. `design.md`: describe la solución técnica y sus decisiones.
3. `plan.md`: ordena la implementación y la validación.
4. `tasks.md`: registra tareas concretas y su estado.

## Reglas

- Copia las plantillas a una carpeta propia del cambio, por ejemplo `docs/sdd/<identificador>/`.
- Antes de implementar, verifica las fuentes del comportamiento existente y separa hechos confirmados (con fuente), decisiones, inferencias o supuestos y preguntas abiertas. Resuelve con quien corresponda las preguntas que cambien materialmente comportamiento, seguridad, datos o compatibilidad; no las conviertas silenciosamente en decisiones.
- Antes de iniciar la implementación, deja claros el alcance, los AC y los contratos aplicables, y resuelve las dudas materiales con las autorizaciones ya existentes. Define requisitos y criterios observables y verificables. Incluye precondiciones, reglas, estados, errores y contratos cuando apliquen. Un requisito de calidad aplicable también lleva `REQ` y `AC`, con medida y umbral confirmados; no inventes umbrales ni contratos.
- Enlaza `REQ` → `AC` → diseño/componente → tarea → comprobación prevista → resultado real. Un criterio pendiente debe seguir figurando como pendiente; registra comandos o inspecciones ejecutados, fecha, resultado y limitaciones sin declarar éxitos supuestos.
- Actualiza la decisión acordada antes de desviar la implementación; si no se puede, registra la divergencia explícitamente. Al terminar una sesión o entregar un avance parcial, registra el estado real y las limitaciones. Declara el cambio completado y verificado solo si todos los AC aplicables están satisfechos con evidencia real, no quedan bloqueos y la documentación refleja el comportamiento entregado. Un AC fallido o sin ejecutar sigue pendiente aunque su limitación esté documentada.
- El estado de cada documento es distinto del estado de cada tarea (`pendiente`, `en curso`, `bloqueada`, `completada`). `borrador` indica contenido aún sujeto a definición; `acordado`, contrato listo para implementar con dudas materiales resueltas; `revisado`, contenido contrastado con el resultado real. Estos estados describen madurez documental, no equivalen a cambio completado ni crean aprobaciones adicionales.
- Si un contrato o vocabulario compartido necesita detalle extenso, enlaza desde `spec.md` o `design.md` a un documento canónico de contratos o glosario. Créalo solo si aporta una responsabilidad distinta y una necesidad presente; evita duplicar definiciones.
- No incluyas reglas de conducta de agentes; esas pertenecen a `AGENTS.md`.
