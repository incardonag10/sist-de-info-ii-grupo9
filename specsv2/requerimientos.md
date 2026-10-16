| ID | Issue | Requerimiento | Nivel / Tipo | Origen | Verificación |
| --- | --- | --- | --- | --- | --- |
| RF-01 | SCRUM-6 | El sistema debe registrar para cada cotización la cobertura, edad del conductor habitual, año del vehículo, zona de radicación, siniestros de los últimos 24 meses, guarda en garaje, débito automático, existencia de otra póliza vigente y antigüedad como cliente. | Usuario / Funcional | Caso §3.1; Cotizador B6:B14 | Al intentar calcular una cotización, todos esos datos están disponibles para la validación y el cálculo. |
| RF-02 | SCRUM-7 | El sistema debe rechazar la cotización de vehículos con más de 20 años de antigüedad, independientemente de la cobertura seleccionada. | Negocio / Funcional | Acta §3.3; hallazgo E11 | Se cotiza un vehículo de más de 20 años con RC, TC y TR: las tres pruebas son rechazadas. |
| RF-03 | SCRUM-8 | El sistema debe calcular la cotización utilizando las tarifas y condiciones comerciales vigentes definidas por la Gerencia Comercial. | Sistema / Funcional | Caso §1.1 y §3.1; hoja Tarifas | Al modificar una tarifa vigente y volver a cotizar el mismo riesgo, el cálculo utiliza la tarifa actualizada. |
| RF-04 | SCRUM-9 | El sistema debe informar al PAS el resultado de la cotización, indicando el importe final a pagar o el motivo de rechazo. [NEEDS CLARIFICATION: deben definirse los impuestos, tasas y gastos que integran el importe final. Deciden Gerencia Comercial y Gerencia Técnica.] | Usuario / Funcional | Caso §3.1; Acta §3.4; hallazgo E1-2 | Una cotización válida muestra un importe final y una rechazada muestra el motivo. La composición exacta del importe queda pendiente hasta la decisión. |
| RF-05 | SCRUM-10 | El sistema debe aplicar los descuentos comerciales correspondientes a la cotización. [NEEDS CLARIFICATION: Héctor Vidal indica que los descuentos están topeados y no pueden acumularse todos; Julián Ponce afirma que se suman. Decide Gerencia Comercial.] | Usuario/Funcional | Caso §3.1; Acta §3.4; hallazgo E1-2 | Pendiente: luego de definirse la regla, se combinan las condiciones de descuento y se comprueba que el porcentaje aplicado coincida con la política aprobada. |

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
