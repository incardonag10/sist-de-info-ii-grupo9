UC-01 - Realizar cotización de seguro automotor
**Issue Jira:** SCRUM-11
**Versión:** v2 — cambio SCRUM-13. Fuente: Acta de la tercera reunión §3.1.

Actor principal: Productor Asesor de Seguros (PAS).

Precondición: El PAS dispone de la información necesaria del conductor, del vehículo y de la cobertura requerida. No se agrega autenticación porque no está especificada en las fuentes del frente.

Flujo principal:
1. El PAS inicia una nueva cotización.
2. El sistema solicita los datos necesarios para cotizar.
3. El PAS ingresa cobertura, edad del conductor, año del vehículo, zona, siniestros de los últimos 24 meses, guarda en garaje, débito automático, existencia de otra póliza y antigüedad como cliente.
4. Se ejecuta UC-02 Validar cotización (include).
5. Si las validaciones se superan, se ejecuta UC-03 Calcular cotización (include), aplicando las tarifas y condiciones comerciales vigentes al emitir la nueva cotización, sin resolver las condiciones comerciales pendientes.
6. El sistema genera el resultado y registra su fecha de emisión, versión de tarifa utilizada e importe asociado.
7. El sistema informa el resultado y su vigencia de 15 días corridos al PAS. La cotización conserva su precio durante la vigencia aunque cambie la tarifa general.

Flujo alternativo 4a - Riesgo no cotizable:
- Si la validación detecta una causa de rechazo, se ejecuta UC-04 Rechazar cotización (extend). El sistema informa el motivo al PAS y el caso termina sin generar una cotización válida.

Postcondición: La solicitud queda Cotizada con su resultado informado al PAS o Rechazada con el motivo informado.

La cotización emitida conserva sus datos, fecha, versión e importe; su situación temporal es Vigente y luego Vencida al agotarse los 15 días. El límite exacto permanece pendiente. Rechazada no equivale a Vencida: la primera no superó la validación del riesgo.

## Consulta e intento mínimo de aceptación — SCRUM-13

Interacción posterior a UC-01, sin agregar emisión de pólizas ni un include de aceptación:
1. El PAS consulta una cotización ya generada.
2. El sistema informa su situación temporal sin recalcular su precio con la tarifa actual.
3. Si el PAS acciona Aceptar cotización, el sistema verifica la vigencia en ese momento.
4. Si está vigente, permite continuar por este control temporal. En el prototipo se informa el resultado del control, sin registrar una aceptación comercial definitiva.
5. Si está vencida, bloquea la aceptación e informa el motivo y la necesidad de realizar una nueva cotización.
6. Si necesita continuar, el PAS inicia una nueva ejecución de UC-01, que utiliza la tarifa vigente. No se transforma la vencida ni se precargan datos como renovación.

El prototipo conserva únicamente resultados parciales: RF-04 y RF-05 siguen pendientes. Superar el control temporal no declara resueltos descuentos ni importe final. Los criterios CA-E4-01 a CA-E4-07 y la matriz completa están en requerimientos.md.

## Modelo textual de estados — SCRUM-13

| Situación | Condición / transición |
| --- | --- |
| Cotizada / Vigente | Resultado emitido dentro de su período de validez de 15 días corridos. Un cambio de tarifa no modifica su precio ni su versión. |
| Vencida | Al agotarse la vigencia, la cotización pasa a esta situación y no puede aceptarse. Se requiere otra cotización para continuar. |
| Rechazada | Solicitud que no superó la validación del riesgo; sin cambios respecto de E3. |

Pendiente de definición en el prototipo es una advertencia por falta de especificación del corte, no un nuevo estado comercial. No se agregan estados Renovada, Aceptada o de póliza.

[NEEDS CLARIFICATION: precisar el límite exacto de los 15 días corridos, incluyendo el cómputo del día de emisión y la hora de corte. Consulta a Marcela Duarte / Gerencia Comercial.]

[NEEDS CLARIFICATION: definir si una cotización vencida puede renovarse en un solo paso y qué datos pueden reutilizarse. Decide Marcela Duarte / Gerencia Comercial.]

| Relacion | Caso Relacionado | Tipo | Justificacion
| --- | --- | --- | --- |
| UC-01 → UC-02 | Validar cotización | include | Toda cotización debe validarse antes del cálculo; es un paso obligatorio. |
| UC-01 → UC-03 | Calcular cotización | include | Si la solicitud supera las validaciones, calcular el resultado forma parte necesaria del flujo normal. |
| UC-04 → UC-01 | Rechazar cotización | extend | Solo ocurre bajo una condición de rechazo; el flujo base de una cotización válida se completa sin esta extensión. |

# Fragmentos considerados para UC-01
| Fragmento / fuente | Qué aporta al caso de uso |
| --- | --- |
| Caso §3.1 | PAS carga datos del vehículo y conductor; la planilla devuelve un precio; el PAS comunica el resultado. |
| Cotizador B6:B14 | Define el conjunto de datos que intervienen actualmente en la cotización. |
| E1 - DFD nivel 1 | Sustenta las etapas Validar datos, Calcular cotización y generar resultado. |
| Acta §3.3 / E1-1 | Sustenta la rama de rechazo por antigüedad y la necesidad de reglas de validación. |
| Caso §1.1 / hoja Tarifas | Sustenta el uso de tarifas y condiciones comerciales definidas por Gerencia Comercial. |
| Acta de la tercera reunión §3.1 / SCRUM-13 | Fecha de emisión, versión de tarifa, vigencia, bloqueo de aceptación vencida, nueva cotización y conservación del precio. Renovación y corte exacto pendientes. |