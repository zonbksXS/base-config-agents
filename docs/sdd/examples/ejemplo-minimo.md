# Ejemplo mínimo SDD: nombre obligatorio

Ejemplo ficticio y didáctico; no describe código, fuentes ni pruebas de este repositorio. Todas las premisas siguientes se consideran acordadas **solo dentro del ejemplo**. En un proyecto real habría que verificarlas antes de implementar.

## Especificación (`spec.md`)

- **Estado documental:** acordado dentro del ejemplo ficticio.
- **Objetivo:** impedir el envío de un formulario con nombre vacío y permitirlo con nombre válido.
- **Fuera de alcance:** almacenamiento, red y otros campos.
- **Actor y precondición:** persona con el formulario abierto que puede escribir «nombre» y pulsar «Enviar».
- **Regla:** se considera vacío `""` o una cadena compuesta solo por espacios; cualquier cadena con al menos un carácter distinto de espacio es válida. No se transforma el valor.
- **Mensaje acordado:** `Ingresa tu nombre.` para ambos casos vacíos.
- **REQ-001:** el formulario impide el envío con nombre vacío y muestra el mensaje acordado; permite el envío con nombre válido.
- **AC-001 / REQ-001:** dado `""`, al pulsar «Enviar», muestra `Ingresa tu nombre.`, no envía y permanece abierto.
- **AC-002 / REQ-001:** dado `"   "`, al pulsar «Enviar», muestra el mismo mensaje, no envía y permanece abierto.
- **AC-003 / REQ-001:** dado `"Ana"`, al pulsar «Enviar», no muestra el aviso y realiza el envío.
- **Contrato y compatibilidad:** entrada local `nombre` como cadena; no cambian API, datos persistidos ni formato externo en este ejemplo.
- **Preguntas bloqueantes:** ninguna dentro del ejemplo ficticio.

## Diseño (`design.md`)

- **REQ-001 / AC-001–AC-003 → componente:** validación del formulario ficticio antes de enviar.
- **Flujo:** comprueba si `nombre` tiene algún carácter distinto de espacio; si no, muestra el mensaje y conserva el formulario; si sí, continúa el envío.
- **Contratos y migración:** el contrato local descrito arriba es canónico para el ejemplo; sin migración.

## Plan (`plan.md`)

- **Patrón de diseño:** solución directa; una única validación no justifica una abstracción.
- **Archivo previsto:** formulario ficticio; la ruta real se identificaría en el proyecto correspondiente.
- **Comprobación prevista:**

| AC | Entrada y acción | Resultado esperado |
| --- | --- | --- |
| AC-001 | `""` y pulsar «Enviar» | Aviso exacto, sin envío, formulario abierto |
| AC-002 | `"   "` y pulsar «Enviar» | Aviso exacto, sin envío, formulario abierto |
| AC-003 | `"Ana"` y pulsar «Enviar» | Sin aviso, envío realizado |

## Tareas y validación (`tasks.md`)

| ID | Estado | REQ / AC | Componente | Tarea | Evidencia |
| --- | --- | --- | --- | --- | --- |
| T-001 | pendiente | REQ-001 / AC-001–AC-003 | Formulario ficticio | Validar el nombre y comprobar los tres casos | Pendiente |

- **AC-001–AC-003:** sin ejecución. Fecha, revisión, comando o inspección, resultados y limitaciones se anotarán solo tras la verificación real. El cambio ficticio no está declarado completado.
