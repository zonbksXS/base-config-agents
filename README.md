# Base de configuración para agentes IA

Plantilla neutral para iniciar proyectos de software asistidos por agentes de inteligencia artificial. Define reglas de trabajo, trazabilidad y documentos mínimos sin imponer lenguaje, framework o proveedor. Usa arquitectura hexagonal por defecto, con Clean como alternativa explícita y adaptaciones documentadas.

## Objetivo

- Mantener instrucciones claras y versionadas para agentes y personas.
- Limitar cada cambio al alcance solicitado.
- Registrar decisiones, cambios y verificaciones reales.
- Permitir que las reglas evolucionen junto con el proyecto.

## Archivos incluidos

| Archivo | Propósito |
| --- | --- |
| `AGENTS.md` | Reglas operativas para cualquier agente que trabaje en el proyecto. |
| [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md) | Arquitectura vigente, ubicación semántica, adaptaciones aceptadas y posibles modificaciones. |
| `CODING_STYLE.md` | Criterios generales para escribir y revisar código mantenible. |
| `CHANGELOG.md` | Historial de cambios relevantes del producto o de la plantilla. |
| `WORKLOG.md` | Evidencia cronológica del trabajo realizado y sus verificaciones. |
| `docs/PROJECT_CONTEXT.md` | Contexto, alcance, usuarios y restricciones confirmadas. |
| `docs/DECISIONS.md` | Registro breve de decisiones técnicas o de proceso. |
| `docs/sdd/README.md` | Flujo de desarrollo dirigido por especificaciones. |
| `docs/sdd/templates/` | Plantillas neutrales de especificación, diseño, plan y tareas. |

## Uso inicial

1. Copiar estos archivos a la raíz del proyecto.
2. Completar `docs/PROJECT_CONTEXT.md` únicamente con información confirmada.
3. Ajustar `AGENTS.md` y `CODING_STYLE.md` con los comandos y convenciones reales del repositorio.
4. Completar `docs/ARCHITECTURE.md`: elegir el estilo, mapear módulos y rutas reales y registrar adaptaciones aceptadas. En proyectos existentes, documentar primero la arquitectura real.
5. Para un cambio no trivial, crear su documentación desde `docs/sdd/templates/`.
6. Mantener `CHANGELOG.md` y `WORKLOG.md` durante la ejecución.

## Principio de adaptación

Esta base es deliberadamente mínima. Las adaptaciones de arquitectura y las reglas específicas de seguridad, pruebas, despliegue o perfiles de agentes se incorporarán cuando exista una necesidad real y verificable.
