UC-01 - Realizar cotización de seguro automotor
**Issue Jira:** SCRUM-11

Actor principal: Productor Asesor de Seguros (PAS).

Precondición: El PAS dispone de la información necesaria del conductor, del vehículo y de la cobertura requerida. No se agrega autenticación porque no está especificada en las fuentes del frente.

Flujo principal:
1. El PAS inicia una nueva cotización.
2. El sistema solicita los datos necesarios para cotizar.
3. El PAS ingresa cobertura, edad del conductor, año del vehículo, zona, siniestros de los últimos 24 meses, guarda en garaje, débito automático, existencia de otra póliza y antigüedad como cliente.
4. Se ejecuta UC-02 Validar cotización (include).
5. Si las validaciones se superan, se ejecuta UC-03 Calcular cotización (include), aplicando las tarifas y condiciones comerciales vigentes.
6. El sistema genera el resultado de la cotización.
7. El sistema informa el resultado al PAS.

Flujo alternativo 4a - Riesgo no cotizable:
- Si la validación detecta una causa de rechazo, se ejecuta UC-04 Rechazar cotización (extend). El sistema informa el motivo al PAS y el caso termina sin generar una cotización válida.

Postcondición: La solicitud queda Cotizada con su resultado informado al PAS o Rechazada con el motivo informado.

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
