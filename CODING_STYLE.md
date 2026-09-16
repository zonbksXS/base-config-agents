# Estándar de estilo de código

## Propósito

Este documento define criterios generales para producir código legible, seguro, comprobable y fácil de mantener. Aplica a todo el repositorio salvo que una guía específica del lenguaje o un archivo más cercano establezca una regla más precisa.

Las herramientas automáticas configuradas por el proyecto —formateador, linter, compilador y analizadores— son la fuente de verdad para las reglas mecanizables.

## Principios generales

- Prioriza claridad y corrección por sobre brevedad o ingenio.
- Mantén cada cambio limitado al comportamiento solicitado.
- Sigue los patrones existentes cuando sean seguros y consistentes.
- Evita duplicación real, pero no agregues abstracciones sin una segunda necesidad concreta.
- Separa responsabilidades y mantén explícitas las dependencias.
- Aplica responsabilidad única, alta cohesión, bajo acoplamiento e inversión de dependencias; usa los principios SOLID donde correspondan sin crear interfaces o jerarquías sin necesidad real.
- Cumple la ubicación semántica y los límites definidos en [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md), independientemente de la tecnología.
- Elimina código reemplazado, comentarios obsoletos y rutas sin uso.
- No optimices sin una necesidad medida o un requisito verificable.

## Patrones de diseño sin sobreingeniería

- Antes de implementar, identifica el problema real y evalúa si un patrón de diseño conocido ayuda a resolverlo. La posibilidad de aplicarlo no justifica por sí sola su adopción.
- Compara el patrón pertinente con la solución directa más simple; no recorras un catálogo completo ni diseñes para necesidades hipotéticas.
- Reutiliza primero los patrones existentes que sean adecuados y respeta la arquitectura y la dirección de dependencias vigentes.
- Adopta un patrón solo si aporta un beneficio concreto en claridad, desacoplamiento, eliminación de duplicación real o facilidad de prueba, y ese beneficio compensa las clases, interfaces e indirecciones añadidas.
- No agregues capas, jerarquías, fábricas, adaptadores ni configuración únicamente para cumplir un patrón o anticipar extensiones futuras. Las abstracciones nuevas requieren una segunda necesidad real en la tarea o un requisito explícito.
- Si la solución directa satisface el requisito con menor complejidad y sin perjudicar los límites existentes, elígela. No aplicar un patrón es una decisión válida.
- Expresa brevemente la decisión en el plan previo. Registra en `docs/DECISIONS.md` únicamente decisiones duraderas; esta evaluación no exige documentos adicionales para cada tarea.

## Formato

- Usa el formateador oficial o configurado para el lenguaje.
- Respeta la codificación UTF-8 y los finales de línea definidos por el repositorio.
- Evita espacios finales, líneas innecesariamente largas y bloques difíciles de recorrer.
- Mantén una instrucción por línea cuando mejore la lectura.
- No alinees manualmente con espacios si el formateador deshará esa alineación.
- Conserva el estilo del archivo cuando todavía no exista una configuración automática.

## Nombres

- Usa nombres descriptivos y coherentes con el dominio.
- Nombra funciones y métodos con verbos que expresen su acción.
- Nombra tipos, módulos y componentes por su responsabilidad.
- Nombra booleanos como condiciones afirmativas cuando sea posible.
- Evita abreviaturas ambiguas, nombres genéricos y diferencias basadas solo en números.
- Mantén un solo término para cada concepto del dominio.
- Respeta las convenciones idiomáticas del lenguaje para mayúsculas y separadores.

## Funciones y módulos

- Da a cada función, clase o módulo una responsabilidad principal reconocible.
- Mantén las funciones pequeñas cuando la extracción produzca una unidad con significado propio.
- Reduce anidamientos mediante validaciones tempranas cuando mejoren la claridad.
- Haz explícitas las entradas, salidas y dependencias relevantes.
- Evita estado global mutable y efectos laterales ocultos.
- No combines reglas de negocio con transporte, persistencia o presentación respetando los límites de la arquitectura vigente.

## Tipos, contratos y datos

- Usa el sistema de tipos disponible y evita eludirlo sin justificación.
- Valida datos en los límites del sistema: entrada del usuario, red, archivos y servicios externos.
- Mantén DTO de transferencia entre capas, entidades de base de datos y DTO de respuesta al frontend en namespaces, paquetes o módulos distintos, aunque sus campos coincidan. Las entidades de dominio conservan también su espacio propio. Aplica los mapeos y límites de la arquitectura; no expongas entidades persistentes ni DTO internos como respuestas públicas.
- Mantén los contratos compatibles salvo que exista autorización explícita para modificarlos.
- Representa estados inválidos de forma difícil de construir cuando el lenguaje lo permita.
- No uses valores mágicos; asigna nombres a constantes con significado.

## Manejo de errores

- Gestiona los errores en el nivel que pueda aportar contexto o tomar una decisión.
- No ignores excepciones, rechazos ni códigos de error silenciosamente.
- Conserva la causa original al envolver o transformar un error.
- Entrega mensajes útiles sin revelar detalles internos o datos sensibles.
- Distingue errores esperados de fallos inesperados.
- Evita usar excepciones como flujo normal cuando el lenguaje ofrezca una alternativa clara.

## Seguridad y privacidad

- Nunca incorpores secretos, tokens, claves o credenciales al código fuente.
- No registres contraseñas, tokens, datos personales ni cargas sensibles.
- Trata toda entrada externa como no confiable y valida antes de usarla.
- Usa consultas parametrizadas y APIs seguras para construir comandos o contenido.
- Aplica el mínimo privilegio en permisos y accesos.
- Usa generadores criptográficamente seguros para valores relacionados con seguridad.
- No implementes criptografía propia ni desactives validaciones de seguridad para resolver errores.

## Comentarios y documentación

- Prefiere código que exprese claramente qué hace.
- Usa comentarios para explicar por qué existe una decisión no evidente, una restricción o un riesgo.
- No repitas el código en lenguaje natural ni conserves código comentado.
- Documenta APIs públicas, contratos y comportamientos sorprendentes según las convenciones del lenguaje.
- Actualiza o elimina comentarios cuando cambie el comportamiento.

## Pruebas

- Escribe pruebas deterministas, independientes y legibles.
- Relaciona cada prueba con un criterio de aceptación o riesgo de regresión.
- Sigue el patrón organizar, actuar y comprobar, o el equivalente del proyecto.
- Prueba comportamiento observable y evita acoplarte innecesariamente a detalles internos.
- Incluye casos exitosos, errores relevantes y límites solicitados.
- No ocultes fallos con reintentos arbitrarios, esperas fijas o aserciones débiles.
- No dependas de servicios reales en pruebas unitarias.

## Concurrencia y asincronía

- Mantén visible el ciclo de vida de tareas, recursos y cancelaciones.
- Propaga cancelación y errores cuando el entorno lo permita.
- Evita bloqueos síncronos dentro de flujos asíncronos.
- Protege el estado compartido y documenta las garantías de concurrencia.
- No agregues paralelismo sin beneficio demostrado y una estrategia de control de fallos.

## Logs y observabilidad

- Usa el mecanismo de logging establecido por el proyecto, no salidas de depuración directas.
- Registra eventos accionables con contexto suficiente y datos estructurados cuando sea posible.
- Usa el nivel correcto y evita ruido repetitivo.
- Incluye identificadores de correlación existentes sin exponer información sensible.
- No uses logs como sustituto del manejo de errores.

## Dependencias

- Reutiliza las dependencias existentes antes de incorporar otra.
- Agrega una dependencia solo con una necesidad actual y aprobación cuando corresponda.
- Evalúa mantenimiento, licencia, seguridad, tamaño e impacto operativo.
- Fija y actualiza versiones mediante el mecanismo estándar del ecosistema.
- Elimina dependencias que queden sin uso como resultado del cambio.

## Revisión antes de entregar

- El código cumple el formateador, linter, compilador y analizadores configurados.
- Las pruebas pertinentes pasan y sus resultados fueron registrados.
- Los nombres y límites reflejan el dominio y las responsabilidades.
- Los errores se manejan sin ocultar fallos ni filtrar datos sensibles.
- No quedan depuración, código muerto, archivos temporales o cambios no relacionados.
- La documentación y los contratos afectados están actualizados.

## Adaptaciones por tecnología

Las reglas específicas de un lenguaje o framework deben documentarse en archivos separados o en un `AGENTS.md` más cercano. Cada adaptación debe indicar:

- versión y alcance;
- formateador, linter y analizadores;
- convenciones idiomáticas;
- estructura de módulos y dependencias;
- estrategia de pruebas;
- comandos exactos de validación.
