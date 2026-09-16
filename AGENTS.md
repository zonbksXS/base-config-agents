# Instrucciones para agentes IA

## Propósito

Estas reglas aplican a todo el repositorio. Un archivo `AGENTS.md` ubicado en un directorio más específico puede agregar o precisar reglas para ese alcance, sin contradecir restricciones de nivel superior.

## Principios de trabajo

- Comprende el objetivo y verifica las premisas antes de modificar archivos.
- Realiza el cambio mínimo suficiente para cumplir la solicitud.
- Lee directamente el código, las pruebas, la configuración y la documentación relacionados.
- Reutiliza patrones y utilidades existentes antes de crear otros.
- Corrige la causa raíz y elimina la ruta reemplazada cuando la compatibilidad no sea un requisito.
- Conserva cambios ajenos y evita modificaciones no relacionadas.
- No inventes requisitos, contratos, comandos, resultados ni decisiones técnicas.
- No expongas secretos, credenciales, tokens, datos personales ni cargas sensibles.

## Plan mínimo antes de editar

Antes de implementar cualquier tarea o solución, evalúa si un patrón de diseño aporta una ventaja concreta frente a la solución directa, según los criterios de `CODING_STYLE.md`. La evaluación es obligatoria; adoptar un patrón no lo es. Para tareas sin diseño de código, indica que no aplica.

Declara de forma breve:

- **Resultado:** comportamiento o artefacto exacto que se entregará.
- **Fuera de alcance:** cambios que no se realizarán.
- **Archivos:** conjunto mínimo previsto.
- **Comprobación:** evidencia que demostrará el resultado.
- **Patrón de diseño:** patrón elegido y beneficio concreto, o motivo breve para mantener una solución directa o indicar que no aplica.

Si el plan crece materialmente, detén la implementación, reduce el alcance o solicita confirmación.

## Cambios que requieren confirmación

Solicita autorización antes de:

- Cambiar una API pública, un esquema persistente o un formato de comunicación.
- Agregar dependencias, servicios, infraestructura o herramientas nuevas.
- Eliminar datos, descartar trabajo existente o reescribir historial Git.
- Ampliar el trabajo a componentes no relacionados.
- Mantener dos implementaciones activas para el mismo comportamiento.

La exploración de solo lectura y las verificaciones no destructivas están permitidas.

## Implementación

- Cumple el estándar general definido en `CODING_STYLE.md` y las convenciones específicas del área modificada.
- Cumple la arquitectura vigente y la ubicación semántica obligatoria de [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md). Lee su definición, mapa y adaptaciones antes de implementar; las propuestas pendientes no son reglas vigentes.
- Respeta el estilo y los límites ya presentes; no migres una arquitectura existente sin una decisión aceptada.
- Mantén separadas las reglas de negocio de los detalles de infraestructura y verifica la dirección de dependencias.
- Actualiza contratos, configuración y documentación solo cuando el cambio lo requiera.
- No dejes código de depuración, archivos temporales, copias de respaldo ni rutas obsoletas.
- Usa comentarios para explicar decisiones no evidentes, no para repetir el código.

## Pruebas y validación

- Ejecuta primero las pruebas existentes más específicas del comportamiento modificado.
- Amplía una prueba relevante antes de crear infraestructura de pruebas nueva.
- Agrega pruebas cuando cambie comportamiento observable, exista riesgo de regresión o el usuario lo solicite.
- Ejecuta compilación, análisis estático o formato cuando estén definidos por el proyecto y sean pertinentes.
- Informa únicamente comandos realmente ejecutados y sus resultados.
- Declara con claridad cualquier validación pendiente o imposible de ejecutar.

## Documentación y trazabilidad

- Usa `docs/PROJECT_CONTEXT.md` como contexto confirmado del proyecto.
- Registra decisiones duraderas en `docs/DECISIONS.md`.
- Usa `docs/sdd/` para cambios que necesiten especificación y diseño previos.
- Actualiza `CHANGELOG.md` con cambios relevantes para usuarios o integraciones.
- Actualiza `WORKLOG.md` con acciones, archivos y verificaciones reales.
- Nunca registres secretos ni datos sensibles en estos documentos.

## Entrega

Antes de finalizar:

- Verifica que el resultado solicitado esté completo.
- Revisa que cada archivo modificado sea necesario.
- Confirma que no existan cambios no relacionados.
- Resume cambios, comprobaciones, limitaciones y pendientes.
