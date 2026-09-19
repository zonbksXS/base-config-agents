# Registro de decisiones

Registra aquí decisiones duraderas que afecten arquitectura, contratos, seguridad, datos, operación o proceso. No conviertas preferencias temporales en reglas permanentes.

## Plantilla

### DEC-000 — Título

- **Fecha:** AAAA-MM-DD
- **Estado:** propuesta | aceptada | reemplazada | descartada
- **Contexto:** hechos y restricciones que motivan la decisión.
- **Decisión:** alternativa elegida.
- **Consecuencias:** beneficios, costos, riesgos y límites.
- **Reemplaza a:** no aplica o identificador anterior.

## Decisiones

### DEC-001 — Mantener una base tecnológica neutral

- **Fecha:** 2026-09-06
- **Estado:** aceptada
- **Contexto:** la tecnología, arquitectura y los perfiles especializados se definirán progresivamente.
- **Decisión:** la estructura inicial no prescribe stack, proveedor, arquitectura ni herramientas.
- **Consecuencias:** cada proyecto deberá completar su contexto y agregar únicamente las reglas específicas que necesite.
- **Reemplaza a:** no aplica.

### DEC-002 — Arquitectura configurable y ubicación semántica obligatoria

- **Fecha:** 2026-09-08
- **Estado:** aceptada
- **Contexto:** se solicita explicitar ingeniería de software y arquitectura sin anclar la plantilla a una tecnología.
- **Decisión:** usar `ARCHITECTURE.md` como definición vigente, hexagonal por defecto y Clean como alternativa elegida explícitamente; separar espacios de DTO, entidades y persistencia y distinguir adaptaciones aceptadas de propuestas.
- **Consecuencias:** cada proyecto concreta sus rutas y límites sin imponer stack ni crear capas vacías. Los proyectos existentes requieren diagnóstico y decisión antes de migrar.
- **Reemplaza a:** DEC-001 únicamente en la ausencia de arquitectura predeterminada; se conserva la neutralidad tecnológica.

### DEC-003 — Especificaciones verificables y continuidad sin duplicación

- **Fecha:** 2026-09-19
- **Estado:** aceptada
- **Contexto:** la revisión detectó vacíos de trazabilidad y continuidad; se autorizó implementar las mejoras manteniendo una base proporcional y neutral.
- **Decisión:** ampliar las cuatro plantillas SDD existentes para enlazar requisitos, criterios, diseño, tareas y resultados reales. Conservar hechos estables en `docs/PROJECT_CONTEXT.md`, continuidad en `CONTEXTO.md` e historial en `WORKLOG.md`. Crear glosarios o documentos adicionales de contratos solo ante una necesidad real y sin duplicar fuentes canónicas.
- **Consecuencias:** las comprobaciones previstas se distinguen de las ejecutadas; los pendientes no se presentan como cumplimiento. Los cambios pequeños conservan el flujo breve y no se agregan herramientas ni aprobaciones a las ya concedidas.
- **Reemplaza a:** no aplica.
