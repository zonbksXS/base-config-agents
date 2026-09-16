# Arquitectura del proyecto

## Propósito y autoridad

Este archivo define la arquitectura vigente, sus límites y la ubicación semántica del código. Es independiente del lenguaje, framework, proveedor y mecanismo de persistencia. El stack confirmado se registra en [PROJECT_CONTEXT.md](PROJECT_CONTEXT.md); las decisiones y sus motivos, en [DECISIONS.md](DECISIONS.md).

Las adaptaciones tecnológicas concretan estas reglas sin invertir dependencias ni mezclar responsabilidades. Una propuesta no modifica la arquitectura vigente hasta que sea aceptada y este documento se actualice.

## Definición vigente

| Aspecto | Definición |
| --- | --- |
| Estilo predeterminado | Hexagonal: dominio y casos de uso aislados mediante puertos y adaptadores. |
| Alternativa admitida | Clean Architecture, cuando el proyecto registre explícitamente su elección. No se mantienen ambos estilos como implementaciones paralelas. |
| Alcance | Código nuevo de proyectos que adopten esta plantilla. En proyectos existentes, registrar primero su arquitectura real y acordar cualquier migración. |
| Módulos y límites de negocio | Por definir según requisitos confirmados. |
| Mapa de rutas físicas | Por definir al conocer la estructura real del proyecto. |
| Adaptaciones vigentes | Ninguna. |

Para seleccionar Clean u otro estilo, actualizar esta definición y registrar la decisión aceptada. La elección de estilo no determina tecnologías ni obliga a crear carpetas, interfaces o capas vacías.

## Límites y dependencias

- **Dominio:** entidades, objetos de valor, invariantes y políticas de negocio. No depende de transporte, persistencia, interfaz de usuario ni frameworks de infraestructura.
- **Aplicación:** casos de uso y coordinación del dominio. Declara los puertos que necesita para comunicarse con el exterior y sus contratos de entrada y salida.
- **Adaptadores de entrada:** traducen acciones externas a invocaciones de casos de uso. No contienen reglas de negocio.
- **Adaptadores de salida:** implementan puertos para persistencia, servicios externos u otros mecanismos técnicos.
- **Composición:** conecta implementaciones y configura el ciclo de vida de dependencias en el borde del sistema.

Las dependencias de código apuntan hacia el interior: adaptadores → aplicación → dominio. Un puerto pertenece a la capa interior que lo necesita; su implementación pertenece al adaptador. El dominio no importa aplicación ni adaptadores. El flujo de ejecución puede ir hacia el exterior a través de un puerto sin invertir esta regla de dependencias.

En Clean, los mismos límites se expresan como entidades, casos de uso, adaptadores de interfaz y mecanismos externos. Documentar la correspondencia concreta al elegirla; no duplicar capas únicamente para conservar ambos vocabularios.

## Ubicación semántica obligatoria

Cada clase, tipo, función o módulo debe ubicarse según su responsabilidad y propietario, no solo por su sufijo o conveniencia de importación. Organizar primero por capacidad de negocio cuando corresponda y, dentro de ella, por límites arquitectónicos y espacios semánticos.

Un espacio propio comprende una ubicación explícita en el repositorio y un namespace, paquete o módulo diferenciado, según los mecanismos del lenguaje. Separar únicamente carpetas no basta cuando los tipos siguen expuestos en un mismo espacio de nombres genérico. Los nombres siguientes son orientativos; la separación de responsabilidades es obligatoria. Cada DTO y entidad debe tener su archivo o unidad de definición propia, conforme al lenguaje, dentro de su espacio correspondiente; no declararlos dentro de controladores, casos de uso, servicios o utilidades.

| Elemento | Espacio y responsabilidad |
| --- | --- |
| Entidades de dominio | `domain/entities` del módulo propietario; identidad e invariantes del negocio. |
| Objetos de valor | `domain/value-objects`; valores e invariantes sin identidad propia. |
| Casos de uso | `application/use-cases`; coordinación de una operación de negocio. |
| Puertos | `application/ports` o el espacio de la capa interior que los necesita; contratos independientes de implementaciones externas. |
| DTO de transferencia entre capas | `application/dtos` o el espacio de contratos de la capa propietaria; intercambio interno de datos, separado de persistencia y de respuestas al frontend. |
| DTO de respuesta al frontend | `adapters/<entrada>/dtos/responses`; contrato público de salida de una funcionalidad, con los campos destinados al consumidor. |
| DTO de transporte o integración | `adapters/<adaptador>/dtos`; solicitudes, respuestas o mensajes del protocolo correspondiente. |
| Modelos o entidades de persistencia | `adapters/persistence/models` o `entities`; representación de tablas de base de datos o estructuras equivalentes de almacenamiento, separada de las entidades de dominio y los DTO. |
| Mapeadores | Espacio `mappers` del adaptador o límite que conoce ambos modelos; no hacer que el dominio conozca tipos externos. |
| Constantes | Espacio `constants` del módulo y capa propietarios cuando sean compartidas en ese alcance; las exclusivas de un tipo permanecen privadas en él. |
| Herramientas y utilidades | Espacio `tools` o `utilities` del módulo y capa que las necesitan, con responsabilidad específica; scripts de desarrollo fuera del código de negocio. |
| Configuración y composición | Borde externo del sistema; valores variables por entorno no se disfrazan de constantes de negocio. |
| Pruebas | Estructura que refleje el módulo, límite y comportamiento que verifican, según las convenciones existentes. |

Reglas de aplicación:

- No mezclar DTO, entidades de dominio y modelos persistentes en un contenedor genérico `models` ni reutilizar una misma definición para esos roles.
- No usar `tools`, `utils`, `helpers`, `common` o `shared` como depósitos de código sin propietario. Una regla de negocio permanece en dominio aunque sea reutilizable.
- Compartir un elemento entre módulos solo cuando existan consumidores reales y una responsabilidad común estable; mantener sus dependencias dentro de los límites permitidos.
- No crear un catálogo global de constantes que acople módulos. Ubicar cada constante junto a su concepto propietario y evitar secretos en código.
- Crear solamente los espacios necesarios para elementos existentes. Los DTO de transferencia interna y los DTO de respuesta al frontend son contratos de responsabilidades distintas y deben permanecer separados aunque sus campos coincidan.

## Separación de contratos y espacios de nombres

Mantener siempre espacios de nombres distintos para estas tres categorías, cuando existan en el proyecto:

| Categoría | Ejemplo de namespace lógico | Uso permitido |
| --- | --- | --- |
| DTO de transferencia entre capas | `<modulo>.application.dtos` | Transportar datos entre límites internos respetando la dirección de dependencias. |
| Entidades de base de datos | `<modulo>.adapters.persistence.entities` | Representar tablas y relaciones persistidas dentro del adaptador de persistencia. |
| DTO de respuesta al frontend | `<modulo>.adapters.input.dtos.responses` | Exponer el resultado de una funcionalidad mediante un contrato explícito para el frontend. |

Estos nombres son ejemplos neutrales: usar namespaces, paquetes o módulos según el lenguaje. Las entidades de dominio mantienen además su espacio propio; una entidad de base de datos no equivale a una entidad de dominio.

- No compartir una misma clase, alias o reexportación para representar categorías distintas ni agruparlas bajo un único namespace `Dtos` o `Models`.
- No retornar directamente entidades de base de datos ni DTO internos al frontend. Construir el DTO de respuesta con un mapeo explícito en el adaptador de entrada, seleccionando únicamente los campos del contrato público.
- Mapear las entidades persistentes a los tipos del contrato interior en el adaptador de persistencia. Los casos de uso no deben importar entidades de base de datos ni DTO de respuesta al frontend.
- Conservar esta separación aunque inicialmente coincidan todos los campos; permite evolucionar persistencia, transferencia interna y respuesta pública de forma independiente.

## Mapa concreto del proyecto

Completar antes de implementar en un proyecto consumidor. Las rutas de la tabla anterior son ejemplos, no una estructura tecnológica obligatoria.

| Módulo o capacidad | Responsabilidad | Capa o límite | Ruta real | Dependencias permitidas |
| --- | --- | --- | --- | --- |
| Por definir | Por definir | Por definir | Por definir | Por definir |

## Adaptaciones aceptadas

Registrar aquí únicamente cambios aceptados respecto de la base. Actualizar también la definición vigente y el mapa afectados, para conservar una sola descripción activa.

| ID de decisión | Regla adaptada | Alcance y definición vigente | Motivo | Verificación |
| --- | --- | --- | --- | --- |
| Ninguna | No aplica | No aplica | No aplica | No aplica |

## Posibles modificaciones

Estas propuestas no autorizan cambios de código ni sustituyen las reglas vigentes. Al aceptar una, trasladarla al registro de adaptaciones y enlazar su decisión; al descartarla, conservar su resolución en el registro de decisiones.

| Propuesta | Necesidad o condición de adopción | Impacto y riesgos | Estado | Decisión relacionada |
| --- | --- | --- | --- | --- |
| Ninguna | No aplica | No aplica | No aplica | No aplica |

## Verificación en cada cambio

- Identificar el módulo, responsabilidad, espacio semántico y dependencias de cada elemento agregado o modificado.
- Comprobar namespaces, paquetes o módulos separados para DTO entre capas, entidades de base de datos y DTO de respuesta al frontend; verificar sus mapeos y que no se filtran tipos externos hacia el interior ni entidades persistentes hacia el frontend.
- Revisar imports o referencias reales; una estructura de carpetas correcta por sí sola no demuestra aislamiento.
- Probar invariantes del dominio y casos de uso sin servicios externos; verificar contratos de adaptadores con las pruebas pertinentes existentes.
- Usar los mecanismos de análisis arquitectónico ya disponibles. Si no existen, revisar las dependencias directamente y registrar la evidencia sin introducir herramientas nuevas.
- Registrar excepciones aceptadas y declarar propuestas o migraciones pendientes sin presentarlas como implementadas.
