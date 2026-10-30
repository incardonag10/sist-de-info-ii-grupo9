| ID | Issue | Requerimiento | Nivel / Tipo | Origen | Verificación |
| --- | --- | --- | --- | --- | --- |
| RF-01 v2 | SCRUM-6; cambio SCRUM-13 | El sistema debe registrar para cada cotización la cobertura, edad del conductor habitual, año del vehículo, zona de radicación, siniestros de los últimos 24 meses, guarda en garaje, débito automático, existencia de otra póliza vigente y antigüedad como cliente y, al emitirla, su fecha de emisión y versión de tarifa utilizada. | Usuario / Funcional | Caso §3.1; Cotizador B6:B14; Acta de la tercera reunión §3.1 | CA-E4-01: los nueve datos, la fecha de emisión y la versión de tarifa quedan asociados al resultado. |
| RF-02 | SCRUM-7 | El sistema debe rechazar la cotización de vehículos con más de 20 años de antigüedad, independientemente de la cobertura seleccionada. | Negocio / Funcional | Acta §3.3; hallazgo E1-1 | Se cotiza un vehículo de más de 20 años con RC, TC y TR: las tres pruebas son rechazadas. |
| RF-03 v2 | SCRUM-8; cambio SCRUM-13 | El sistema debe calcular cada nueva cotización utilizando las tarifas y condiciones comerciales vigentes definidas por la Gerencia Comercial en el momento de su emisión, sin resolver las condiciones comerciales pendientes de definición. | Sistema / Funcional | Caso §1.1 y §3.1; hoja Tarifas; Acta de la tercera reunión §3.1 | CA-E4-05: una nueva cotización utiliza la tarifa vigente al emitirla; consultar la anterior no provoca su recálculo. |
| RF-04 | SCRUM-9 | El sistema debe informar al PAS el resultado de la cotización, indicando el importe final a pagar o el motivo de rechazo. [NEEDS CLARIFICATION: deben definirse los impuestos, tasas y gastos que integran el importe final. Deciden Gerencia Comercial y Gerencia Técnica.] | Usuario / Funcional | Caso §3.1; Acta §3.4; hallazgo E1-2 | Una cotización válida muestra un importe final y una rechazada muestra el motivo. La composición exacta del importe queda pendiente hasta la decisión. |
| RF-05 | SCRUM-10 | El sistema debe aplicar los descuentos comerciales correspondientes a la cotización. [NEEDS CLARIFICATION: Héctor Vidal indica que los descuentos están topeados y no pueden acumularse todos; Julián Ponce afirma que se suman. Decide Gerencia Comercial.] | Usuario/Funcional | Caso §3.1; Acta §3.4; hallazgo E1-2 | Pendiente: luego de definirse la regla, se combinan las condiciones de descuento y se comprueba que el porcentaje aplicado coincida con la política aprobada. |
| RF-06 v1 | SCRUM-14 | El sistema debe determinar la vigencia de cada cotización durante los 15 días corridos establecidos desde su fecha de emisión. | Sistema / Funcional | Acta de la tercera reunión §3.1 | CA-E4-02; el límite exacto queda pendiente según la observación temporal. |
| RF-07 v1 | SCRUM-15 | El sistema debe impedir la aceptación de una cotización vencida. | Negocio / Funcional | Acta de la tercera reunión §3.1 | CA-E4-03: el intento queda bloqueado con el motivo de vencimiento. |
| RF-08 v1 | SCRUM-16 | Cuando se necesite continuar a partir de una cotización vencida, el sistema debe requerir la realización de una nueva cotización con la tarifa vigente al emitirla. | Sistema / Funcional | Acta de la tercera reunión §3.1 | CA-E4-05: se registra una cotización nueva, sin transformar ni sobrescribir la vencida. |
| RF-09 v1 | SCRUM-17 | El sistema debe conservar el precio emitido de una cotización hasta su vencimiento aunque cambie la tarifa general durante su vigencia. | Negocio / Funcional | Acta de la tercera reunión §3.1 | CA-E4-04: la cotización conserva su importe y versión originales. |

## E4 — SCRUM-13: registro del cambio

Fuente del cambio: Acta de la tercera reunión, §3.1 Validez de las cotizaciones, según el fragmento aportado por el grupo. El acta completa no está versionada en este repositorio.

### 4.1 — Devoluciones previas

E2: **Aprobada sin correcciones**. No hubo modificaciones que aplicar por esa entrega. No se realizan correcciones de E3 no expresamente informadas. La página E3 corresponde a SCRUM-12, incorporada mediante PR #2; UC-01 conserva SCRUM-11.

### Versionado e impacto

RF-01 y RF-03 pasan a v2 sin cambiar sus identificadores ni sus issues originales. RF-06 a RF-09 nacen en v1. Los RF anteriores sin versión explícita conservan su redacción vigente. Todos los cambios de esta sección corresponden a SCRUM-13.

| Elemento revisado | Impacto por SCRUM-13 |
| --- | --- |
| RF-01 | Agrega fecha de emisión y versión de tarifa, sin eliminar los nueve datos. |
| RF-02 | Sin cambios: rechazo por más de 20 años en RC, TC y TR. |
| RF-03 | Precisa la tarifa vigente al emitir una nueva cotización. La conservación posterior se especifica en RF-09. |
| RF-04 | Sin cambios: importe final, impuestos, tasas y gastos siguen pendientes. |
| RF-05 | Sin cambios: acumulación y tope de descuentos siguen pendientes. |
| UC-01 | Registra metadatos de emisión y documenta la consulta de vigencia y el intento mínimo de aceptación. |
| DFD nivel 1 | No está versionado. Impacto conceptual: incorporar fecha y versión al resultado y consultar su vigencia. No se reconstruye el diagrama sin su fuente. |
| Estados | La postcondición de UC-01 es el único modelo previo disponible. Se documenta Cotizada/Vigente → Vencida, sin agregar estados de póliza. |
| Criterios E3 | No hay archivo separado: se preservan las verificaciones anteriores y se agregan los criterios E4 siguientes. |
| index.html | Conserva resultados independientes en memoria, agrega fecha, versión, consulta temporal, aceptación mínima y nueva cotización. |

### Observaciones y decisiones pendientes

[NEEDS CLARIFICATION: precisar el límite exacto de los 15 días corridos, incluyendo el cómputo del día de emisión y la hora de corte. No se define una fecha/hora exacta de vencimiento hasta su confirmación. Consulta a Marcela Duarte / Gerencia Comercial.]

[NEEDS CLARIFICATION: definir si una cotización vencida puede renovarse en un solo paso y qué datos pueden reutilizarse. Decide Marcela Duarte / Gerencia Comercial.]

Se conservan además los pendientes de RF-04 y RF-05. No se agregan excepciones de aceptación del riesgo ni reglas de descuentos.

### Criterios de aceptación E4

| ID | Dado | Cuando | Entonces | RF |
| --- | --- | --- | --- | --- |
| CA-E4-01 | Una solicitud con los nueve datos válidos y una tarifa de referencia T1 | Se genera la cotización de prueba el 01/11/2026 | Se conservan juntos los nueve datos, fecha, versión T1 e importe calculado. | RF-01 v2 |
| CA-E4-02 | Una cotización del 01/11/2026 | Se consulta el 10/11/2026 y se acciona Aceptar cotización | Se informa Vigente y se permite continuar por el control temporal, sin emitir póliza ni declarar resuelto el precio final. | RF-06, RF-07 |
| CA-E4-03 | Una cotización del 01/11/2026 | Se intenta aceptarla el 17/11/2026 | Se informa Vencida y se bloquea la aceptación, indicando que se requiere una nueva cotización. | RF-06, RF-07, RF-08 |
| CA-E4-04 | Una cotización vigente del 01/11 con T1 e importe P1 | Se activa una tarifa de prueba T2 el 05/11 y se consulta la anterior el 10/11 | La anterior conserva T1 y P1. Consultar o aceptar no recalcula. | RF-09 |
| CA-E4-05 | Una cotización del 01/11 vencida al 17/11 y una tarifa vigente de prueba T2 | El PAS inicia y completa una nueva cotización el 17/11 | Se genera otra referencia con fecha 17/11 y tarifa T2. La anterior conserva sus datos. No se precargan datos como una renovación. | RF-03 v2, RF-08 |
| CA-E4-06 | Una solicitud de vehículo con más de 20 años | Se calcula con RC, TC y TR | Se rechaza en las tres pruebas, sin habilitar aceptación. | RF-02 |
| CA-E4-07 | Una cotización del 01/11 | Se consulta el 16/11, día cuyo corte exacto no está definido | El prototipo informa Pendiente de definición, no declara Vigente ni Vencida y no autoriza continuidad por su cuenta. Este comportamiento es una limitación del prototipo, no una regla comercial nueva. | RF-06 parcial |

Las fechas 10/11 y 17/11 evitan el límite exacto. Con fechas sin hora, el prototipo solo clasifica los casos inequívocos: diferencia de fechas de 0 a 14 días como vigente, de 16 o más como vencida; la diferencia de 15 días queda indeterminada. Una fecha de consulta anterior a la emisión es un escenario de prueba inválido. Esto no fija el instante comercial de vencimiento.

### Alcance de la página v2

El resultado sigue siendo la prima parcial previa a descuentos. Los controles de fecha y tarifas son herramientas de prueba: sus cambios no constituyen decisiones comerciales. REF-v4.2 identifica técnicamente los valores de referencia tomados del Excel, no una versión comercial de tarifa confirmada por Gerencia Comercial. Se permite sustituir ese identificador y las primas base para probar T1/T2; se impide reutilizar un identificador con valores distintos dentro de la sesión.

Cada resultado calculable se conserva con su fecha, versión, prima y datos, sin recalcularlo al consultar. La acción Aceptar cotización verifica únicamente la continuidad temporal: una vigente puede continuar y una vencida queda bloqueada. No registra una aceptación comercial definitiva ni emite pólizas. El límite ambiguo permanece sin resolver. Las solicitudes rechazadas o sin factor tarifario confirmado no habilitan esa acción.

Las cotizaciones de prueba se conservan únicamente mientras la página permanece abierta; recargar elimina la sesión. No se implementa ni se afirma un archivo histórico persistente. Nueva cotización inicia un formulario vacío; no existe renovación en un paso ni reutilización automática. No se alteran los factores tarifarios, descuentos ni validaciones del riesgo de E3.

### Hallazgo E4-1 contra el oráculo

Inspección de la copia disponible de Cotizador Pampa v4.2.xlsx: hojas Cotizador y Tarifas (oculta), celdas y fórmulas. El Excel no está versionado en el repositorio.

| # | Qué se observó | Dónde | Resultado | Decisor |
| --- | --- | --- | --- | --- |
| E4-1 | No registra fecha de emisión ni versión de tarifa por cotización, no controla los 15 días ni conserva explícitamente cotizaciones históricas con importe fijado. A3 identifica la versión general del archivo, no la tarifa de un registro histórico. | Cotizador!A3, B6:B14, B17:B26; hoja Tarifas. TODAY() se usa para antigüedad del vehículo, no vencimiento. | Brecha con la tercera reunión §3.1. Las fórmulas consultan directamente Tarifas: el oráculo no implementa SCRUM-13. | Marcela Duarte / Gerencia Comercial. |

Anexo A pendiente de capturas reales: (1) Cotizador completo con encabezado, entradas y resultado; (2) barra de fórmula de B17 con la referencia a Tarifas; (3) en una copia de prueba, tarifa e importe antes/después de un cambio. Las capturas deben acompañar la inspección estructural; una imagen aislada no demuestra ausencia de historial. No se presentan capturas como realizadas ni se modifica el Excel original.

### Validación del prototipo — SCRUM-13

Se aprobaron 29 comprobaciones funcionales automatizadas sobre el DOM, sin incorporar una suite ni dependencias al repositorio. Se verificaron los escenarios E4, el corte pendiente, datos inválidos, rechazo por antigüedad en las tres coberturas, conservación de resultados, tarifa actualizada para una nueva cotización y limpieza al recargar. Caso de referencia: TC, conductor 30, vehículo 2021, CABA, cero siniestros y garaje, fecha 01/11/2026 → prima parcial 41.400; cambiando solo la base TC de 32.000 a 40.000 en una tarifa de prueba nueva → 51.750 para una nueva cotización. La anterior conserva 41.400. No se aplicaron descuentos ni componentes pendientes. La revisión visual en navegador y las capturas reales de Anexo A siguen pendientes; estas comprobaciones no se presentan como pruebas visuales.

### Matriz de trazabilidad vigente

La columna Commit identifica antecedentes comprobados y el cambio E4 por su mensaje; los hashes E4 se obtienen del historial de e4-cambio una vez creados, sin inventar un hash autorreferencial en el archivo.

| Fuente | Issue Jira | Requerimiento | Modelo / UC | Criterio | Commit |
| --- | --- | --- | --- | --- | --- |
| Caso §3.1; Cotizador B6:B14; tercera reunión §3.1 | SCRUM-6; cambio SCRUM-13 | RF-01 v2 | UC-01, registro | CA-E4-01 y nueve datos obligatorios | Antecedente 029a32f; revisión: SCRUM-13: documenta vigencia y trazabilidad E4. |
| Acta §3.3; E1-1 | SCRUM-7 | RF-02 | UC-02 / UC-04 referenciados por UC-01 | CA-E4-06 | 04f138a, d1a66fb; sin modificación funcional E4. |
| Caso §1.1 y §3.1; tercera reunión §3.1 | SCRUM-8; cambio SCRUM-13 | RF-03 v2 | UC-03 referenciado por UC-01 | CA-E4-05; actualización de tarifa para nueva cotización | Antecedente 864ad45; revisión: SCRUM-13: documenta vigencia y trazabilidad E4. |
| Caso §3.1; Acta §3.4; E1-2 | SCRUM-9 | RF-04 | UC-01, resultado | Motivo de rechazo; importe final pendiente de definición | 864ad45; sin modificación funcional E4. |
| Caso §3.1; Acta §3.4; E2-1 | SCRUM-10 | RF-05 | Cálculo referido por UC-01 | Pendiente de decisión comercial; no se afirma implementado | 3249747; sin modificación E4. |
| Tercera reunión §3.1 | SCRUM-14; cambio SCRUM-13 | RF-06 v1 | Cotizada/Vigente → Vencida | CA-E4-02, CA-E4-03; CA-E4-07 sin resolver corte | SCRUM-14: vincula RF-06 a su issue propio; SCRUM-13: agrega control de vigencia a la página E4. |
| Tercera reunión §3.1 | SCRUM-15; cambio SCRUM-13 | RF-07 v1 | Control posterior a UC-01 | CA-E4-02 y CA-E4-03 | SCRUM-15: vincula RF-07 a su issue propio; SCRUM-13: agrega control de vigencia a la página E4. |
| Tercera reunión §3.1 | SCRUM-16; cambio SCRUM-13 | RF-08 v1 | Nueva ejecución de UC-01 | CA-E4-05 | SCRUM-16: vincula RF-08 a su issue propio; SCRUM-13: agrega control de vigencia a la página E4. |
| Tercera reunión §3.1 | SCRUM-17; cambio SCRUM-13 | RF-09 v1 | Conservación de Cotizada/Vigente | CA-E4-04 | SCRUM-17: vincula RF-09 a su issue propio; SCRUM-13: agrega control de vigencia a la página E4. |

UC-01 conserva SCRUM-11 y el antecedente 5a95b3a; su revisión se traza al commit documental SCRUM-13. La página parte de e596e5b (SCRUM-12, PR #2) y su revisión al commit de página SCRUM-13. No hay DFD versionado que pueda enlazarse a un commit de modificación.

Hallazgo nuevo contra el oráculo
E2-1 - Acumulación de descuentos

| Qué se observó | Dónde | Resultado | Decisor
| --- | --- | --- | --- |
| E2-1 | El Cotizador v4.2 suma en B24 los descuentos por débito automático, multipóliza y antigüedad >5 años. Los valores configurados son 5%, 10% y 5%; si se cumplen las tres condiciones, la fórmula suma 20%. | Cotizador Pampa v4.2.xlsx: Cotizador!B24 y Tarifas!B39:B41 | Pendiente de decisión: coincide con Julián Ponce (“se suman”) y contradice a Héctor Vidal (“están topeados”). | Gerencia Comercial / Marcela Duarte |

#Fragmentos que no son requerimientos

| Fragmento | Texto resumido | Categoria | Justificacion |
| --- | --- | --- | --- |
| Caso §2 / situación actual | SIGA no cubre cotización; los PAS usan una planilla Excel descargable. | Dato de contexto | Describe cómo funciona hoy. Justifica el problema, pero no especifica por sí sola una función del sistema nuevo. |
| Alberto Pampín | “Sistema rápido, moderno y fácil de usar”. | RNF | Son cualidades sin una métrica concreta; no deben convertirse en RF funcionales. |
| Alberto Pampín | “Antes de que se jubile Héctor”. | Objetivo/meta de negocio | Es un plazo/objetivo del proyecto, no una función del sistema. |
| Julián Ponce | Necesita emitir desde su computadora en el momento. | Dato de contexto / fuera del frente | Es relevante para el frente Emisión de pólizas, no para el alcance funcional de Cotización trabajado por G9. |