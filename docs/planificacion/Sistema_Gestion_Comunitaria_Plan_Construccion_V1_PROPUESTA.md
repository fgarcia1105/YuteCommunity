---
title: Sistema de Gestión Comunitaria — Plan de Construcción V1
version: V1 — aprobada sobre revisión 0.2
status: APROBADO
date: 2026-09-22
normative_source: Sistema_Gestion_Comunitaria_Knowledge_Base_V1.0_CURRENT.md
source_status: Knowledge Base V1.0 APROBADA / CURRENT
purpose: Ordenar la construcción sin modificar el Baseline ni generar código
---

# Sistema de Gestión Comunitaria — Plan de Construcción V1

**Estado: APROBADO por Fer, mediante confirmación expresa «Aprobado» en esta conversación.**

Aprobación registrada el 22 de septiembre de 2026 sobre la revisión 0.2. Las decisiones técnicas abiertas siguen pendientes; ningún gate de implementación o producción se declara cumplido por esta aprobación.

Este documento deriva exclusivamente de la KB V1.0 CURRENT suministrada por el responsable del proyecto. No modifica la KB, no acredita una implementación y no constituye autorización de producción. La numeración de etapas, los identificadores PC, DT y EV, y los gates internos son elementos de organización del trabajo aprobados con este plan; no son nuevas reglas de negocio, invariantes ni ADR aceptados.

## 1. Estado de partida y límites

| Elemento | Estado de referencia |
| --- | --- |
| Baseline V1.0 / MVP 1.0 | APROBADOS / CONGELADOS |
| Knowledge Base V1.0 | APROBADA / CURRENT; consolidación del 21 de septiembre de 2026 |
| Invariantes / ADR | 20 aprobados / 15 ACCEPTED |
| Alcance / riesgos / Go-Live | 14 paquetes MVP / 18 riesgos / 5 gates |
| Revisión final de la KB | PASS; 0 contradicciones materiales conocidas y 0 pendientes que bloqueen planificación |
| Hito actual | Plan de Construcción V1 aprobado; preparación de E1.1 |
| Hito posterior | ETAPA 1 — Repositorio y Entorno |
| Implementación, infraestructura y pruebas ejecutadas | No verificadas en este trabajo documental |

Fuentes: KB §§1, 17–25, 32–33. La revisión documental permite planificar; no demuestra readiness productivo.

Se preservan Laravel como backend/API y autoridad financiera, PostgreSQL como fuente transaccional, monolito modular, Web responsive completo, Flutter enfocado, una comunidad por instalación, online-first y ausencia de operación financiera offline. Las capas y límites modulares siguen §21. No se seleccionan en este documento versiones concretas de herramientas ni proveedores.

Permanecen fuera del MVP todos los elementos de §18 y las ampliaciones del portal de §15.3: entre otros, préstamos interfondos, varios préstamos simultáneos, operación financiera offline, integración bancaria automatizada, cobranza automatizada, paridad total Web/Flutter y carga autónoma de comprobantes por prestatarios.

Si aparece una ambigüedad que afecte dinero, historia, autoridad, permisos, privacidad, arquitectura o alcance, se detiene el caso de uso afectado y se documenta para resolución conforme a §§1, 28 y 30. Las tareas independientes sólo continúan si no dependen de esa interpretación. Una elección local de implementación dentro de lo aprobado se registra sin presentarla como cambio de Baseline.

## 2. Objetivo y método

Convertir el alcance congelado en entregas pequeñas y verificables, ordenadas por dependencias y riesgo. Cada entrega conecta backend, persistencia, autorización, interfaz pertinente y evidencia de prueba. Los módulos de §16 conservan su responsabilidad; una etapa puede atravesar varios módulos.

Principios de planificación propuestos:

1. Probar primero las separaciones financieras y los límites de autoridad que condicionan el resto.
2. Desarrollar la Web junto con los casos de uso; no dejar toda la interfaz para el final.
3. Incorporar auditoría, seguridad, concurrencia, idempotencia y pruebas desde la primera función que los requiere.
4. Preparar backup/restore, revisión legal y apertura desde temprano; demostrar su cumplimiento antes de producción.
5. Implementar Flutter sobre contratos suficientemente estabilizados, manteniendo completo su alcance MVP-14.
6. Usar gates con evidencia concreta. Un porcentaje de code coverage o una pantalla funcional no sustituye la prueba del requisito.

El plan no fija fechas ni promete esfuerzo sin conocer equipo, disponibilidad, experiencia y entorno. Los entregables documentales se pueden preparar ahora; los productos de implementación descritos más adelante son trabajo futuro.

## 3. Responsabilidades de trabajo

Estos son papeles de ejecución del proyecto, no nuevos roles ni permisos de la aplicación. Una persona puede asumir varios, con la capacidad disponible.

| Papel de proyecto | Responsabilidad |
| --- | --- |
| Responsable del proyecto — Fer | Revisar/aprobar el plan, priorizar dentro del alcance, coordinar disponibilidad y confirmar quién asume cada tarea |
| Responsable técnico — por asignar | Resolver decisiones locales, revisar diseño, implementación, migraciones y evidencia técnica |
| QA / revisor — por asignar | Verificar criterios y trazabilidad; registrar resultados y defectos |
| Responsable de operación — por asignar | Preparar infraestructura, recuperación, monitoreo, soporte y simulacros |
| Autoridad de negocio correspondiente | Definir políticas/configuración que le competen y validar resultados operativos sin ampliar facultades por este plan |
| Revisión jurídica / privacidad — por coordinar | Revisar los puntos de §§23, 25 y 27 antes de producción |
| IA de apoyo | Preparar artefactos y apoyar análisis/implementación bajo §28; no aprobar políticas, asumir autoridad ni declarar gates cumplidos sin evidencia |

Aprobar este plan no convierte al responsable del proyecto en autoridad financiera de la aplicación. Las autorizaciones de negocio siguen la KB.

## 4. Secuencia y dependencias

| Etapa | Nombre | Dependencia de entrada principal | Resultado verificable |
| --- | --- | --- | --- |
| E1 | Repositorio y Entorno | Plan aprobado; inventario de equipo/entorno; DT-01 y DT-08 se resuelven en su preparación | Base reproducible para construir y validar |
| E2 | Identidad, organización y autorización | E1 | Acceso contextual, periodos, MFA y trazabilidad base |
| E3 | Fundamentos financieros y documentales | E2; decisiones monetarias, temporales y de storage | Primitivas transaccionales, cálculo y evidencia privada verificados |
| E4 | Fondos, custodia, cooperaciones y conciliación | E3 | Primer flujo completo de ingresos, entrega y evidencia |
| E5 | Préstamos, avales, garantías y desembolso | E4; cálculo validado en E3 | Flujo Persona → préstamo desembolsado con historia preservada |
| E6 | Pagos, recibos y rectificación | E5; flujo de custodia E4 | Ciclo financiero completo y PAY-01 probado |
| E7 | Actividades, cobranza, informes y Web completa | E6; extensiones no dependientes pueden adelantarse tras su gate de base | Cobertura funcional Web, dashboards y portal |
| E8 | Flutter enfocado | Contratos de E2/E6 y funciones pertinentes de E7 estabilizados | Cobertura móvil MVP-14 sin paridad total |
| E9 | Validación integral y preparación operativa | E7/E8; trabajo de recuperación iniciado en E1/E3 | Candidato con pruebas integrales y ensayo de apertura/restore |
| E10 | Go-Live y entrega operativa | E9; preparativos de §§25–27; los cinco gates deben cumplirse antes de habilitar operación real | Puesta en operación controlada y handoff |

Orden por defecto para un equipo pequeño: E1 → E2 → E3 → E4 → E5 → E6 → E7 → E8 → E9 → E10. Se pueden anticipar diseño, revisión legal, inventario de datos y documentación sin marcar funcionalidades como terminadas. Cambiar solapes requiere revisar dependencias y capacidad; no elimina gates.

E3 no construye un framework genérico: implementa únicamente fundamentos necesarios para los casos aprobados. E4 usa un flujo concreto de cooperación para comprobarlos. El cálculo de E3 se integra con préstamos en E5 y pagos en E6.

### 4.1 Preparación, implementación y cierre

Cada etapa distingue tres momentos: preparar entradas/decisiones, implementar sólo los componentes cuyas dependencias estén resueltas y demostrar el gate con evidencia. «Cerrar antes de E2» en el registro de decisiones significa antes de implementar el componente dependiente de E2; su análisis puede realizarse en la preparación de esa etapa. Una decisión pendiente no se considera resuelta por estar asignada.

Los gates no dependen de evidencia de funciones futuras. Las pruebas de componentes en E2/E3 se amplían con operaciones reales de prueba en E4–E8; las pruebas integrales de E9 no permiten postergar hasta entonces los controles críticos de cada entrega.

### 4.2 Entregas internas para etapas amplias

Estos paquetes son unidades propuestas de trabajo, no nuevas etapas oficiales ni alcance adicional. Cada uno aplica la Definition of Done de §14; el gate de etapa exige el conjunto completo.

| Etapa | Paquetes internos propuestos | Dependencia o límite |
| --- | --- | --- |
| E4 | Fondos/movimientos; cooperación y evidencia; entrega/custodia; conciliación/incidentes | La cooperación usa movimientos; la entrega usa custodia; conciliación verifica resultados trazables |
| E6 | Reconocimiento efectivo/transferencia; entrega y documentos; parciales/liquidación; exceso/devolución/donación; rectificaciones | Probar PAY-01 en cuanto exista reconocimiento; el cierre exige también todos los casos de corrección/excedente |
| E7 | Actividades; cobranza; cortes/informes; portal; dashboards y cobertura Web | Cada paquete usa contratos de E4–E6; el último revisa que ningún caso aprobado quede sin interfaz |
| E8 | Identidad/sesión; consultas/dashboard/perfil/portal; pagos/recibos; cobranza/evidencia | Comprobar desconexión e idempotencia desde el primer pago móvil; no esperar a E9 |

### 4.3 Preparativos externos y recuperación

La coordinación legal/privacidad se inicia desde E2/E3; los documentos y flujos concretos se revisan al estar disponibles en E5/E6. No se exige resolverlos para redactar este plan, pero su evidencia es obligatoria antes del uso productivo correspondiente.

El inventario de fuentes de apertura puede comenzar en E4, cuando ya existen conceptos de fondos/custodia para clasificarlas; en E5/E6 se completa con préstamos/pagos. E9 ensaya y reconcilia; E10 ejecuta la apertura real y acredita GO-LIVE-05 antes de habilitar operación financiera.

La viabilidad de cumplir RPO/RTO se evalúa al diseñar DT-12/DT-13 y el primer restore de E3. Si ese ensayo revela una limitación, se corrige antes de depender de ella en la preparación productiva. E9 demuestra los objetivos con evidencia del entorno objetivo; un restore sintético temprano no certifica producción.

## 5. Fichas de etapa

### E1 — Repositorio y Entorno

**Objetivo:** retomar la Etapa 1 oficial con un entorno reproducible y gobierno técnico mínimo.

**Entradas:** plan aprobado; información de computadora, sistema operativo, acceso y participantes. La preparación de E1 resuelve DT-01 antes de fijar estructura/UI y DT-08 antes de crear el repositorio remoto/pipeline. DT-12 puede mantenerse abierta mientras exista una ruta reproducible de validación sin comprometer el proveedor productivo.

**Trabajo:** crear/configurar repositorio y flujo de revisión; establecer estructura inicial del monolito; documentar requisitos del entorno y versiones seleccionadas posteriormente mediante fuentes oficiales; organizar DEV/VALIDATION/PROD y secretos separados; preparar migraciones, datos sintéticos, pipeline inicial, health checks y registro de evidencia. Definir estrategia de despliegue, recuperación y controles por ambiente. No introducir servidor local obligatorio para la comunidad; DEV local no altera la arquitectura productiva.

**Entregables:** repositorio inicial futuro, guía de instalación, inventario de herramientas, esquema de ambientes, pipeline y runbook inicial de migraciones/restore; decisiones registradas.

**Pruebas:** levantar desde una copia limpia; ejecutar pipeline; reconstruir esquema vacío mediante migraciones; verificar aislamiento de configuración y ausencia de secretos en el repositorio.

**Riesgos:** RISK-05, RISK-07, RISK-09, RISK-12, RISK-18.

**Gate G-E1:** instalación reproducida y evidenciada, pipeline base correcto, DEV/VALIDATION aislados para las comprobaciones pertinentes y separación de PROD documentada; DT-01/DT-08 cerradas. Las decisiones de E2 tienen responsable y punto de cierre antes de implementar su componente dependiente. Evidencia EV-01. No exige disponer ya de cuentas productivas o demostrar todavía el RPO final.

### E2 — Identidad, organización y autorización

**Objetivo:** asegurar que cada acción posterior pueda ejecutarse sólo por quien corresponda.

**Entradas:** G-E1; resolver DT-02, DT-05, DT-09 y DT-11 antes de implementar los contratos dependientes de identidad/sesión. Resolver DT-07 antes de persistir periodos o evaluar vigencias; su validación financiera continúa en E3.

**Trabajo:** separar Persona/Usuario; organización, fondos/comisiones como referencias necesarias para alcance, asignaciones, periodos y configuración institucional; autenticación, recuperación controlada, MFA privilegiado, sesiones revocables y reautenticación; autorización contextual y a nivel de objeto; historia de cambios y auditoría de seguridad separadas. Aplicar restricciones de pertenencia simultánea de §4.3 y preservar cambios de responsabilidad. Preparar interfaz Web de administración dentro de sus límites. Construir matriz de acciones/recursos únicamente desde reglas vigentes; escalar cualquier celda crítica no determinable.

**Entregables:** identidad operativa, matriz de permisos derivada, flujos de sesión, periodos e historia, pruebas negativas y paneles iniciales necesarios.

**Pruebas:** rol correcto con fondo equivocado; asignación vencida; recurso de otra persona; creador sin permiso actual; Admin intentando función financiera o acceso sensible; sesiones revocadas; recuperación y MFA; cambio de responsable sin reescribir historia.

**Riesgos:** RISK-04, RISK-10, RISK-15, RISK-18.

**Gate G-E2:** positivos y negativos de identidad, periodos y recursos existentes comprobados en backend; Admin sin privilegios implícitos; MFA para los roles exigidos y revocación verificados. Evidencia EV-02. Para operaciones financieras/documentos aún no implementados, E2 verifica la política derivada y su denegación por defecto mediante pruebas de componente; no acredita todavía sus endpoints ni descargas. E3–E8 deben añadir pruebas integradas al incorporar cada recurso.

### E3 — Fundamentos financieros y documentales

**Objetivo:** demostrar las bases de integridad, tiempo, cálculo y documentos antes de componer operaciones de negocio completas.

**Entradas:** G-E2; DT-03 a DT-07 resueltas para los componentes que se implementen; diseño inicial de DT-10 y DT-13.

**Trabajo:** casos de uso explícitos y contratos entre módulos; decimal, ROUND_HALF_UP, cálculo sobre principal original, aniversarios mensuales y días/30; Clock controlable; fechas efectivas/de registro/de confirmación/de vigencia; Operation ID, idempotencia, transacciones y concurrencia; folios no reutilizables; historia no destructiva; jobs secundarios post-commit. Storage privado, validación de cargas, metadatos, versiones, hashes, permisos separados y acceso/descarga trazables. Primer ensayo de backup/restore de datos, documentos y configuración sintéticos.

**Entregables:** fundamentos integrados mínimos, especificación técnica local de transacciones/contratos, catálogo de casos financieros límite, evidencia documental privada y runbook de recuperación inicial.

**Pruebas:** escenarios EV-03; fallo antes del commit; efecto secundario fallido después del commit; reintento tras timeout; carreras sobre una operación/folio; archivo no autorizado o inválido; recuperación coherente de una muestra sintética. Los casos monetarios se verifican con resultados esperados calculados independientemente de la implementación.

**Riesgos:** RISK-01, RISK-04, RISK-05, RISK-06, RISK-11, RISK-14.

**Gate G-E3:** cálculos deterministas y controles transaccionales/documentales probados con casos sintéticos acotados; límites de las transacciones ya implementadas documentados; ensayo inicial de restore registrado, sin presentarlo como cumplimiento productivo de RPO/RTO. Evidencia EV-03 y primera revisión de EV-10. Estas pruebas no sustituyen la atomicidad de los casos de negocio completos, que se acredita en E4–E6.

### E4 — Fondos, custodia, cooperaciones y conciliación

**Objetivo:** cerrar un primer recorrido financiero real del MVP, desde recepción hasta disponibilidad y evidencia.

**Entradas:** G-E3; referencias de organización y autoridad E2; reglas §§5–6 y 11.

**Trabajo:** Fondo General y fondos de comisiones, ubicaciones banco/caja, ingresos/egresos con naturaleza económica, movimientos internos, custodia/entrega, conciliación e incidentes. Cooperación individual, montos variables, aportaciones adicionales, varios colaboradores y advertencia configurable por duplicidad. Inicio anual manual por facultad específica del Admin. Entrega presencial/transferencia al Fondo; cobro directo del encargado conforme al flujo. Emisión de evidencia y tratamiento documental/financiero explícito, incluyendo cancelación compuesta cuando el caso de cooperación lo exige. No inventar un catálogo de transiciones de custodia: derivarlo del flujo aprobado y escalar ambigüedad material antes de implementarlo.

**Entregables:** flujo Web de cooperación/entrega; movimientos, indicadores separados, conciliaciones, incidentes, evidencia y trazabilidad.

**Pruebas:** recepción por colaborador sin disponible del Fondo; entrega única; movimiento caja/banco sin ingreso/gasto; diferencias de conciliación sin editar saldo; duplicidad de cooperación según configuración; ciclo anual sin ampliar autoridad del Admin; cancelación de documento frente a corrección del efecto financiero; aislamiento entre fondos.

**Riesgos:** RISK-01, RISK-02, RISK-04, RISK-10, RISK-11, RISK-15.

**Gate G-E4:** recorrido de cooperación → custodia → entrega → conciliación y evidencia probado, con consistencia de importes e historia; cancelación aplicable trazable y autorizada. Evidencia EV-04. PAY-01 sobre deuda de préstamo se acredita en E6, no en esta etapa.

### E5 — Préstamos, avales, garantías y desembolso

**Objetivo:** completar Persona → solicitud → revisión → autorización → desembolso, con política y expediente históricos.

**Entradas:** G-E4; cálculo E3; configuración/checklist sintéticos para validación. Valores institucionales productivos se cierran antes de E10.

**Trabajo:** elegibilidad conforme al proceso comunitario, máximo un préstamo no liquidado por persona, monto máximo configurable y excepciones autorizadas; checklist versionado requerido/opcional; avales reutilizables y advertencias sin bloqueo duro; garantías variables y custodia física; rechazo y cancelación previa al desembolso; activación sólo al entregar dinero; congelamiento de condiciones al desembolso; compromiso/vencimiento y pagaré conforme al proceso físico. Preservar devolución documental posterior a liquidación. Implementar Web de estos casos y contratos para clientes.

**Entregables:** flujo del préstamo, historial de estados/condiciones, expediente privado y custodia documental; escenarios de cálculo integrados.

**Pruebas:** dos solicitudes/desembolsos concurrentes que intenten violar el máximo; usuario sin autoridad; AUTORIZADO sin desembolso no es ACTIVO; cambio de tasa/checklist no reescribe préstamos anteriores; aval con préstamo pendiente genera advertencia; interés no usa saldo decreciente; estados inválidos rechazados por caso de uso; garantía no implica derecho automático de ejecución.

**Riesgos:** RISK-01, RISK-04, RISK-06, RISK-08, RISK-10, RISK-11.

**Gate G-E5:** flujo hasta desembolso y estados aplicables verificados, desembolso exactamente una vez, política congelada y expediente protegido. Evidencia EV-05. La integración de LIQUIDADO y devolución documental posterior se cierra en E6 con pagos reales de prueba, sin crear un endpoint genérico para forzar estados. Los documentos legales usados en validación no se declaran aprobados para uso real.

### E6 — Pagos, recibos y rectificación

**Objetivo:** demostrar el ciclo financiero completo sin confundir deuda, custodia, disponibilidad o documento.

**Entradas:** G-E5 y controles de E3/E4; contratos de reconocimiento y rectificación revisados.

**Trabajo:** efectivo con encargado/colaborador, transferencias reportadas y verificadas; fecha efectiva de transferencia; parciales y liquidación anticipada; clasificación informativa capital primero; constancia y recibo oficial vinculados; entrega posterior sin segundo pago; pérdida de custodia sin restaurar deuda. Sobrepago restringido, obligación y ejecución de devolución; conversión total/parcial en donación expresa y separada. Cancelación/sustitución documental, rectificación financiera no destructiva y casos compuestos autorizados. Liquidación financiera separada del cierre documental. Construir consulta del portal sobre pagos reconocidos sin esperar entrega al Fondo.

**Entregables:** flujos Web de pago/entrega/corrección, vista propia del prestatario y evidencias; documentación de atomicidad y resultados desconocidos.

**Pruebas:** todos los escenarios EV-06, concurrencia, reintentos y fallo parcial; combinaciones de medio de pago, custodia y permisos; devolución/donación sin reescribir pago original; efectivo aún con colaborador sigue no disponible aunque se reconozca donación.

**Riesgos:** RISK-01, RISK-02, RISK-03, RISK-04, RISK-10, RISK-11.

**Gate G-E6:** pruebas financieras pasan en backend y persistencia, no sólo UI; pago reconocido, deuda, custodia, disponible, excedente y documentos concilian con escenarios esperados. Evidencia EV-06. Sin interpretación pendiente que afecte estos efectos.

### E7 — Actividades, cobranza, informes y cobertura Web

**Objetivo:** completar la operación Web y su consulta usando efectos financieros ya probados.

**Entradas:** G-E6; fondos/egresos E4; préstamos/documentos E5.

**Trabajo:** actividades básicas con inversión, producido, gastos, aportaciones y evidencia/nota cuando corresponda; autorización de gastos de comisiones dentro de su alcance. Cobranza manual, contactos, promesas, incumplimiento y evidencia sin sanción automática. Cortes formales inmutables, comparación y correcciones separadas; informes independientes por fondo y comunitarios consolidados sin datos personales de prestatarios. Dashboards por rol/alcance. Portal completo de §15.1 con exclusiones de §15.2/15.3. Completar Web responsive en español y accesibilidad básica. Handoff/cambio de responsable con historia preservada.

**Entregables:** Web con cobertura MVP-13, actividades, cobranza, cortes e informes, dashboards y portal; matriz de pantallas/acciones asociada a permisos.

**Pruebas:** corte anterior inalterado tras rectificación; comparación explicada por movimientos; informes no filtran datos personales ni comisiones ajenas; portal no expone notas internas/otros prestatarios; préstamos previos y cálculo de liquidación a fecha; descarga autorizada; promesas sin penalización automática; operación responsive y estados loading/success/failure/unknown.

**Riesgos:** RISK-02, RISK-04, RISK-07, RISK-09, RISK-10, RISK-15.

**Gate G-E7:** matriz de cobertura Web completa, criterios funcionales/permisos verificados y snapshots preservados; no se introducen interfondos ni mega-informe obligatorio. Evidencia EV-07.

### E8 — Flutter enfocado

**Objetivo:** implementar íntegramente el alcance móvil aprobado, sin replicar toda la Web.

**Entradas:** contratos estabilizados de E2/E6/E7 según función; DT-09 y estrategia de sesión definidas; dispositivos/plataformas de validación por concretar sin ampliar alcance.

**Trabajo:** autenticación, dashboard, consulta Persona/préstamo, recepción/consulta de pagos según permisos, recibos, cobranza de campo, evidencia, perfil y portal. Mantener backend como autoridad; resolver resultado desconocido mediante Operation ID/idempotencia y estado explícito. Proteger información en el cliente y evitar que pérdida de conectividad produzca operación financiera offline o duplicados al reconectar. No agregar edición de perfil o capacidades de autoservicio no aprobadas bajo el nombre genérico de perfil.

**Entregables:** cliente Flutter enfocado, matriz MVP-14 → vista/caso de uso/prueba, evidencia de compatibilidad API y de permisos.

**Pruebas:** desconexión antes/durante/después de enviar pago; recuperación de resultado desconocido sin reintento ciego; sesión revocada/MFA; acceso a recurso ajeno; cliente incompatible; paridad del resultado financiero con Web para el mismo caso; evidencia y recibos privados.

**Riesgos:** RISK-01, RISK-04, RISK-09, RISK-13.

**Gate G-E8:** todas las capacidades explícitas de MVP-14 cubiertas y autorizadas, sin operación financiera offline ni ampliaciones del portal. Evidencia EV-08. No se posterga Flutter a POST-MVP.

### E9 — Validación integral y preparación operativa

**Objetivo:** reunir evidencia independiente de los recorridos completos y ensayar operación, recuperación y apertura.

**Entradas:** G-E7/G-E8; DT-10, DT-12 y DT-13 cerradas para el entorno objetivo; responsables y revisión legal/privacidad coordinados.

**Trabajo:** regresión de invariantes y permisos; recorridos Web/Flutter, concurrencia, fallos, temporalidad, documentos y rendimiento normal de referencia; completar observabilidad, alertas, jobs y runbooks. Ensayar restauración de PostgreSQL + documentos + configuración, medir RPO/RTO. Inventariar y clasificar datos de apertura, reconciliar ensayo de migración, definir fecha de corte/fuente oficial. Preparar capacitación, contingencia manual y soporte. Ensayar cambio de responsable y cierre/entrega histórica.

**Entregables:** candidato de release identificado, dossier de pruebas, restore medido, informe de apertura ensayada, matriz de readiness, manuales y registro de defectos.

**Pruebas:** EV-09 a EV-12; escenarios críticos de EV-02 a EV-08; errores de configuración, documento faltante y pérdida de conectividad; medición de interacciones habituales frente al objetivo aproximado de ≤2s, sin convertirlo en garantía absoluta.

**Riesgos:** los 18, con foco en RISK-05, RISK-07, RISK-08, RISK-13, RISK-16, RISK-17.

**Gate G-E9:** candidato validado con evidencia reproducible; ningún defecto conocido que vulnere un invariante o control crítico queda aceptado por conveniencia. Ensayo de apertura conciliado y restore medido. Pendientes legales/operativos, si existen, quedan explícitos como bloqueadores de E10; no se declara PRODUCTION-READY. Evidencia EV-09 a EV-12.

### E10 — Go-Live y entrega operativa

**Objetivo:** activar la fuente oficial de forma controlada y entregar operación sostenible.

**Entradas:** G-E9; GO-LIVE-01 a GO-LIVE-04 satisfechos; apertura ensayada y preparativos de §§25–27 completos. La ejecución controlada de apertura real permite acreditar GO-LIVE-05 dentro de esta etapa, antes de habilitar operación financiera a usuarios. Su aprobación correspondiente debe quedar documentada.

**Trabajo:** ejecutar apertura/migración conforme a ensayo; reconciliar valores reales; confirmar cuentas, permisos, MFA, configuración/folios, backups, monitoreo y secretos; establecer fecha de corte y fuente oficial única; capacitación, contingencia, soporte y entrega. Aplicar despliegue versionado y registrar validación posterior. Si se requiere recuperación tras operaciones reales, preservar su historia y reconciliar; no usar rollback destructivo como corrección financiera.

**Entregables:** acta de puesta en operación, evidencia de apertura real, versión desplegada, responsables/contactos operativos y handoff.

**Pruebas:** comprobaciones productivas controladas de acceso, salud, documentos, jobs y monitoreo; reconciliación de apertura; comprobación de ejecución de backups. Las pruebas sintéticas destructivas permanecen fuera de datos reales.

**Riesgos:** RISK-05, RISK-07, RISK-08, RISK-15, RISK-16, RISK-17.

**Gate G-E10:** cinco gates oficiales y readiness acreditados; fuente oficial y fecha de corte comunicadas; operación acepta la entrega. Evidencia EV-10, EV-11, EV-12. La aprobación del plan no sustituye la aprobación de Go-Live.

## 6. Matriz de cobertura MVP y módulos

Las etapas indicadas son responsables principales; autorización, seguridad y auditoría atraviesan todas. Módulos según numeración exacta de KB §16. Las capacidades C-01…C-13 de §29 se usan sólo para organización.

| Paquete | Etapas | Módulos principales | Evidencia principal |
| --- | --- | --- | --- |
| MVP-01 | E2, E7 | 01, 02, 11 | EV-02, EV-07: usuarios, periodos y handoff |
| MVP-02 | E3, E4, E6 | 03, 04, 07, 11 | EV-04, EV-06: fondos, custodia y conciliación |
| MVP-03 | E3, E5, E6 | 01, 06, 07, 08 | EV-03, EV-05, EV-06: ciclo del préstamo |
| MVP-04 | E3, E5, E6 | 06, 08 | EV-05, EV-06: avales, garantías y devolución documental |
| MVP-05 | E3, E4, E6 | 03, 04, 06, 07, 08 | EV-03, EV-06: PAY-01 y todas sus variantes |
| MVP-06 | E4, E7 | 03, 05, 08 | EV-07: actividades y gastos |
| MVP-07 | E7, E8 | 06, 08, 09 | EV-07, EV-08: cobranza manual |
| MVP-08 | E2, E3, E5, E6 | 02, 08, 11 | EV-02, EV-03, EV-05, EV-06: versiones y privacidad |
| MVP-09 | E7 | 03, 04, 06, 07, 10 | EV-07: cortes e informes |
| MVP-10 | E2–E7, E9 | 04, 11 | EV-02, EV-04, EV-09: auditoría y conciliación |
| MVP-11 | E4–E8 | 01–12 según rol/caso | EV-07, EV-08: dashboards con alcance |
| MVP-12 | E6, E7, E8 | 02, 06, 07, 08, 12 | EV-06, EV-07, EV-08: consulta propia |
| MVP-13 | E2–E7 | 01–12 | EV-07: matriz Web completa |
| MVP-14 | E8 | 01, 02, 06, 07, 08, 09, 12 y consultas autorizadas | EV-08: matriz móvil completa |

Cooperaciones e inicio anual de §6 se trazan expresamente a E4, con MVP-01/MVP-02/MVP-05 en lo pertinente. No desaparecen por no existir un paquete llamado «cooperaciones». La continuidad C-13 se trata en E1/E3/E9/E10; no se añade como paquete MVP nuevo.

## 7. Trazabilidad de invariantes

La tabla asigna comprobaciones futuras; ninguna fila significa que ya se haya ejecutado una prueba.

| Invariante KB | Etapas | Prueba/evidencia exigida |
| --- | --- | --- |
| INV-FIN-01 | E3, E4, E6, E7 | Rectificación conserva original y cortes; EV-04/06/07 |
| INV-FIN-02 | E5 | Cambio posterior de política no altera condiciones congeladas; EV-05 |
| INV-FIN-03 | E3–E6, E8 | Concurrencia/reintento/timeout producen un efecto; EV-03/06/08 |
| INV-FIN-04 | E3, E5, E6 | Decimal, ancla mensual, días/30 y Clock deterministas; EV-03/06 |
| INV-FIN-05 | E3, E6, E7 | Capital-first no cambia obligación ni base original; EV-03/06/07 |
| INV-PAY-01 | E6, E8 | Pago, entrega y recibo posterior reducen deuda sólo una vez; EV-06/08 |
| INV-PAY-02 | E6, E7 | Pago reconocido visible con custodia pendiente y sin disponible; EV-06/07 |
| INV-PAY-03 | E6 | Pérdida después del reconocimiento genera incidente sin restituir deuda; EV-06 |
| INV-PAY-04 | E6 | Transferencia reportada no reduce deuda; verificada sí conforme a fecha efectiva; EV-06 |
| INV-FON-01 | E4, E6 | Toda variación tiene operación; sin edición de saldo; EV-04/06 |
| INV-FON-02 | E4 | Caja→banco del mismo fondo no produce ingreso/gasto; EV-04 |
| INV-FON-03 | E4, E6 | Pendiente del colaborador excluido del disponible; EV-04/06 |
| INV-FON-04 | E4, E7 | Disponible, cartera, patrimonio e ingreso separados y conciliables; EV-04/07 |
| INV-HIS-01 | E7 | Rectificación posterior no modifica snapshot anterior; EV-07 |
| INV-HIS-02 | E2–E7 | Se preservan versiones, documentos y evidencia histórica; EV-02/03/05/07 |
| INV-DOC-01 | E5, E6, E7 | LIQUIDADO con devolución documental aún pendiente; EV-06/07 |
| INV-AUT-01 | E2, E4–E7 | Admin denegado en facultades financieras no otorgadas; excepción de ciclo anual acotada; EV-02/04 |
| INV-AUT-02 | E2–E8 | Identidad/rol/alcance/permiso/vigencia/recurso evaluados; EV-02/09 |
| INV-AUT-03 | E2–E8 | Crear un registro no concede acceso perpetuo; EV-02/09 |
| INV-AUT-04 | E2, E3, E5, E8 | Admin sin acceso sensible automático, incluida descarga directa; EV-02/03/08 |

## 8. Trazabilidad de ADR y NFR

| ADR KB | Etapas responsables | Evidencia de respeto |
| --- | --- | --- |
| ADR-001 | E1, E3 y siguientes | Límites del monolito modular y contratos sin mutación arbitraria de tablas ajenas |
| ADR-002 | E1 y siguientes | Laravel backend, casos de uso y controles autoritativos |
| ADR-003 | E1, E3–E6 | PostgreSQL transaccional como fuente estructurada oficial |
| ADR-004 | E3, E9 | Binarios normalmente fuera de BD; metadatos/versiones/hash y restore coherente |
| ADR-005 | E3–E8 | Clientes no pueden imponer resultado financiero ni autorización |
| ADR-006 | E3–E6, E8 | ACID, concurrencia, Operation ID e idempotencia verificados |
| ADR-007 | E4, E6, E7 | Rectificación conserva historia; sin Event Sourcing |
| ADR-008 | E2–E8 | Autorización contextual/backend y pruebas por objeto |
| ADR-009 | E2–E8 | Web completa y matriz Flutter enfocada |
| ADR-010 | E4–E8, E9 | Sin operación financiera offline; contingencia manual |
| ADR-011 | E3 y siguientes | Efectos críticos transaccionales; jobs secundarios después del commit |
| ADR-012 | E1, E9, E10 | DEV/VALIDATION/PROD separados; migraciones/releases reproducibles |
| ADR-013 | E1, E3, E9, E10 | Backup/restore integral medido, RPO ≤1h y RTO ≤8h |
| ADR-014 | E2, E3, E9 | Historia de negocio, auditoría de seguridad, logs y métricas diferenciados |
| ADR-015 | E2, E4, E5 | Configuración histórica; política de negocio separada de administración técnica |

NFR de §20: integridad y consistencia en E3–E6; MFA/sesiones/mínimo privilegio desde E2; Web responsive/español/accesibilidad y estados explícitos durante E2–E8; latencia normal de referencia evaluada en E9; observabilidad desde E1/E3 y completada en E9; recuperación desde E1/E3 con demostración final antes de E10.

## 9. Registro de decisiones de implementación

Todas las decisiones siguientes están **ABIERTAS**. Sus IDs DT son locales al plan. No son nuevos ADR aceptados. Responsable técnico prepara recomendación basada en drivers; el responsable del proyecto coordina su adopción. Si la elección cambia elementos normativos, se tramita CR. Políticas de negocio se remiten a la autoridad correspondiente.

| ID | Decisión abierta de KB §26 | Cerrar antes de | Criterio/evidencia para resolver |
| --- | --- | --- | --- |
| DT-01 | UI Web dentro del ecosistema Laravel | Preparación de E1, antes de fijar estructura/UI | Cobertura responsive completa, mantenibilidad, accesibilidad y compatibilidad con API móvil |
| DT-02 | Autenticación y MFA | E2 | Cuentas individuales, MFA privilegiado, recuperación, revocación, Web/Flutter |
| DT-03 | Queue/jobs | E3, antes de trabajos secundarios | Post-commit, reintentos observables e idempotentes donde corresponda |
| DT-04 | Object storage | E3 | Privacidad, versiones/referencias/hash, validación y recuperación; proveedor productivo confirmado antes de E9 |
| DT-05 | Identificadores técnicos | E2 | Distinguir ID técnico, Operation ID y folio de negocio; trazabilidad y no reutilización de folios |
| DT-06 | Precisión física decimal SQL | E3 | Rango documentado, exactitud, cálculo y redondeo oficial sin Float/Double autoritativo |
| DT-07 | Zona horaria y Clock | E2, antes de periodos/vigencias; validación financiera en E3 | Aniversarios, fechas efectivas/registro/confirmación/vigencia y resultados deterministas |
| DT-08 | Proveedor Git y CI/CD | Preparación de E1, antes de repositorio remoto/pipeline | Accesos, secretos, revisión, pruebas y despliegues reproducibles |
| DT-09 | Versionado de API | E2, antes de fijar contratos | Compatibilidad móvil, errores y resultados desconocidos; estrategia de clientes antiguos |
| DT-10 | Canales de alertas/monitoring | Diseño en E3; cierre antes de E9 | Fallos, jobs, health checks, backups y operación; sin ampliar mensajería al prestatario |
| DT-11 | Timeout de sesión | E2 | Sesiones revocables, riesgo y uso operativo; consistencia con reautenticación |
| DT-12 | Cloud/hosting | Antes de configurar entorno objetivo de E9 | Laravel/PostgreSQL/storage privado, conectividad, seguridad, RPO/RTO y operación sostenible |
| DT-13 | Cadencia/retención de backups y restore | Diseño en E3; cierre antes de E9 | RPO ≤1h/RTO ≤8h, protección, coherencia y prueba medida; no inferir que backup diario satisface RPO |

Formato de cada cierre: problema, opciones evaluadas, drivers, decisión, responsable, fecha, consecuencias, prueba requerida y relación con ADR aceptados. La elección de versiones concretas y herramientas auxiliares se documentará en E1 con documentación oficial vigente; no se inventa aquí un stack adicional.

## 10. Catálogo de evidencia y escenarios críticos

Los IDs EV agrupan evidencia; no reemplazan los IDs de pruebas concretas que se crearán por caso de uso.

| ID | Contenido y criterio |
| --- | --- |
| EV-01 | Reproducción del entorno y pipeline: commit/configuración, pasos, resultado y migraciones |
| EV-02 | Matriz de permisos, MFA/sesiones/recuperación y periodos: positivos/negativos por rol, recurso, fondo y vigencia |
| EV-03 | Cálculo monetario/temporal y primitivas críticas: entradas, resultado esperado independiente, resultado obtenido y fallos/concurrencia |
| EV-04 | Cooperación/fondos/custodia/conciliación: importes antes/después, operación, responsable y evidencia documental |
| EV-05 | Préstamos: estados, monto/política/checklist histórico, avales, garantías, desembolso único |
| EV-06 | Pagos y correcciones: deuda, custodia, disponible, excedente, devolución/donación y documentos antes/después |
| EV-07 | Web/reporting/portal: cobertura de funciones, snapshots, privacidad, autorización y experiencia responsive |
| EV-08 | Flutter: matriz MVP-14, compatibilidad, desconexión, resultado desconocido, identidad y permisos |
| EV-09 | Regresión integral: versión candidata, pruebas, fallos, rendimiento de referencia y trazabilidad actualizada |
| EV-10 | Backup/restore: punto recuperable, pérdida temporal medida, tiempos, coherencia BD/documentos/configuración y responsables |
| EV-11 | Migración/apertura: inventario, procedencia/calidad, conciliación, corte/fuente oficial y aprobación |
| EV-12 | Readiness/handoff: revisión legal/privacidad, configuración, capacitación, contingencia, soporte y aceptación |

### 10.1 Casos mínimos para EV-03

- 10,000 × 0.05 × 3 meses = 1,500; pago parcial no cambia principal original como base de interés.
- Mismo día de desembolso: interés devengado cero.
- 31 enero → último día de febrero: un mes; 31 enero → 1 marzo: un mes + 1/30. Cubrir febrero de año bisiesto y no bisiesto.
- 31 agosto → 30 septiembre: un mes; → 31 octubre: dos meses, conservando ancla.
- Antes del primer aniversario: días transcurridos/30.
- ROUND_HALF_UP positivo: 10.005 → 10.01; precisión suficiente y sin redondeos intermedios innecesarios.
- Cálculo repetido con igual estado y Clock produce igual resultado; clasificación capital/interés no altera obligación.

### 10.2 Casos mínimos para EV-06

- Efectivo reconocido por colaborador: deuda reducida una vez, constancia visible, custodia pendiente, sin disponible del Fondo.
- Entrega posterior: modifica custodia/disponibilidad conforme al flujo, sin nueva reducción de deuda; recibo vinculado al mismo pago.
- Pérdida posterior: incidente/faltante y responsabilidad interna, sin restaurar deuda válida.
- Transferencia reportada sin reconocimiento; verificación con fecha efectiva de transferencia y fecha de confirmación diferenciada.
- Reintento concurrente o tras timeout: una operación/efecto; consulta por Operation ID cuando el resultado es desconocido.
- Pago correcto/documento incorrecto: sustitución documental sin alterar dinero. Pago incorrecto: rectificación explícita y evidencia preservada.
- Sobrepago: liquidación por lo correspondiente y excedente restringido, no ingreso/disponible utilizable automático.
- Devolución y donación expresa parcial/total: obligación disminuye sólo por importe correspondiente; donación es ingreso separado; pago original intacto.
- Donación con dinero aún en manos de colaborador: no se vuelve disponible por esa sola decisión.
- LIQUIDADO con pagaré/garantía pendientes de devolución; cierre documental separado.

Estas listas son mínimos derivados, no agotan la regresión. No fijan permisos, políticas ni resultados no establecidos en la KB.

## 11. Estrategia de ingeniería, ambientes y datos

### 11.1 Ambientes y CI/CD

Propuesta: DEV con datos sintéticos; VALIDATION aislado para pruebas integrales y restauraciones; PROD separado para operación real. No clonar PROD automáticamente ni enviar PII indiscriminadamente a IA. Accesos, secretos y almacenamiento se separan por ambiente conforme a §§20 y 23.

Cada cambio futuro vincula caso de uso, referencias KB, pruebas y decisión local cuando aplique. El pipeline ejecutará los controles pertinentes al cambio: validación del proyecto, pruebas de dominio/persistencia, autorización, concurrencia y fallos según riesgo. La promoción reutiliza un release identificado y sus migraciones versionadas, con evidencia de validación; el mecanismo concreto depende de DT-08/DT-12.

### 11.2 Migraciones y recuperación

Migraciones versionadas y reproducibles; probar esquema vacío y actualización desde la versión anterior pertinente. Revisar impacto en datos históricos, compatibilidad de API/clientes y tiempo de ejecución. Cambios destructivos no son una vía de rectificación financiera. El procedimiento de recuperación distinguirá fallo de despliegue, fallo de migración y pérdida de datos.

Propuesta de control: probar recuperación antes de promover cambios de riesgo y conservar evidencia de la versión/datos afectados. Tras aceptar operaciones reales, no restaurar una copia antigua sin analizar/reconciliar operaciones posteriores. RPO/RTO y restauración coherente de BD, documentos y configuración siguen siendo obligatorios.

### 11.3 Datos iniciales y configuración

Separar datos sintéticos de validación de configuración institucional real. Antes de producción: usuarios individuales y asignaciones, fondos/comisiones y ubicaciones, parámetros y folios iniciales, checklist documental, monto máximo y política financiera decididos por autoridad competente. No convertir ejemplos de este plan o valores de pruebas en configuración aprobada.

### 11.4 Apertura y migración histórica

Inventariar fuentes físicas/digitales y procedencia; clasificar datos verificados, saldos/condiciones de apertura e historia incompleta. Diseñar representación de apertura dentro del modelo aprobado; si requiere un efecto no definido, escalar antes de implementarlo. No inventar recibos, pagos o fechas para rellenar huecos.

Ensayar importación y reconciliación por Fondo, préstamo y custodia según corresponda; identificar diferencias con responsable/evidencia. Fijar fecha de corte y fuente oficial. Mantener los registros anteriores como evidencia según política; evitar dos fuentes oficiales activas. Apertura real reconciliada y aprobada es GO-LIVE-05.

## 12. Registro de tratamiento de riesgos

| Riesgo KB | Etapas | Control/evidencia principal |
| --- | --- | --- |
| RISK-01 | E3–E6, E8 | Atomicidad, idempotencia, Operation ID y jobs post-commit; EV-03/06/08 |
| RISK-02 | E4, E6, E7 | Deuda/custodia/disponible separados; EV-04/06/07 |
| RISK-03 | E6 | Pérdida en custodia no restaura deuda; EV-06 |
| RISK-04 | E2–E9 | Autorización contextual, objetos, documentos y cliente; EV-02/03/09 |
| RISK-05 | E1, E3, E9, E10 | Restore real medido y coherente; EV-10 |
| RISK-06 | E3, E5 | Configuración histórica y congelamiento; EV-03/05 |
| RISK-07 | E1, E7, E9, E10 | Guías reproducibles, capacitación y handoff; EV-01/12 |
| RISK-08 | E5, E9, E10 | Revisión jurídica documentada antes de uso productivo; EV-12 |
| RISK-09 | Todas | Trazabilidad contra MVP y exclusiones, control de cambios |
| RISK-10 | E2–E8 | Validaciones, confirmaciones y rectificación trazable; EV-04/06/09 |
| RISK-11 | E3–E6, E9 | Fechas diferenciadas y evidencia de operaciones retroactivas; EV-03/06/09 |
| RISK-12 | E1, E3, E9 | Elecciones DT justificadas por drivers y operación |
| RISK-13 | E2, E8, E9 | Versionado/compatibilidad de clientes; EV-08/09 |
| RISK-14 | E3, E9 | Storage privado, ciclo de vida/retención y restore; EV-03/10/12 |
| RISK-15 | E2, E7, E9 | Periodos, cierre/entrega y nueva gestión sin reescritura; EV-02/07/09 |
| RISK-16 | E9, E10 | Corte y fuente oficial explícitos; EV-11 |
| RISK-17 | E9, E10 | Apertura reconciliada y clasificación de historia incompleta; EV-11 |
| RISK-18 | Todas | Fuente CURRENT, protocolo §28, registro de decisiones y CR |

No se agregan severidades cuantitativas no aprobadas. El riesgo se considera tratado sólo con evidencia suficiente, no por estar enumerado en esta tabla.

## 13. Gates oficiales y preparación productiva

Los gates internos G-E1…G-E10 no sustituyen los cinco GO-LIVE de la KB.

| Gate oficial | Preparación | Evidencia necesaria para E10 |
| --- | --- | --- |
| GO-LIVE-01 | E1/E3/E9 | EV-10: restauración demostrada de PostgreSQL + documentos + configuración; RPO ≤1h y RTO ≤8h |
| GO-LIVE-02 | E3–E6/E9 | EV-03/05/06/09: reglas e invariantes financieros en backend y persistencia |
| GO-LIVE-03 | E2/E3/E8/E9 | EV-02/03/08/09: permisos sensibles, objetos, scopes, MFA privilegiado y documentos privados |
| GO-LIVE-04 | Coordinación temprana; E5/E9 | EV-12: revisión legal de pagaré, avales, cancelaciones, garantías y procesos con efecto legal |
| GO-LIVE-05 | Inventario temprano; E9/E10 | EV-11: apertura/migración real reconciliada y aprobada, corte/fuente oficial definidos y sin historia fabricada |

### 13.1 Condiciones adicionales de readiness

| Condición KB §§25–27 | Preparar | Verificar antes de producción |
| --- | --- | --- |
| Privacidad, retención y base legal definitivas | Coordinación desde E2/E3 | Decisión/revisión documentada y tratamiento coherente de datos/documentos |
| Checklist documental inicial | E5 | Configuración real autorizada y versionada |
| Monto máximo y política financiera inicial | E5 | Configuración conforme a decisión de negocio; sin sustituir autoridad por Admin |
| Configuración institucional y folios | E2/E4 | Valores reales y no colisión/reutilización |
| Infraestructura, transporte protegido y cuentas institucionales | E1/E9 | Accesos, propiedad operativa, salud y aislamiento |
| Storage privado | E3/E9 | Privacidad y descarga autorizada, sin URLs públicas permanentes |
| MFA privilegiado | E2 | Admin, Encargado General y Responsables de Comisión cubiertos |
| Backups automáticos, RPO/RTO y restore | E1/E3/E9 | Evidencia GO-LIVE-01 |
| Pruebas sensibles/financieras | E2–E9 | Evidencia GO-LIVE-02/03 |
| Apertura/migración | E9/E10 | Evidencia GO-LIVE-05 |
| Monitoring, alertas, jobs y secretos | E1/E3/E9 | Configuración real, responsables y respuesta operativa probadas |
| Contingencia | E9 | Procedimiento manual ensayado; no operación financiera offline encubierta |
| Capacitación, soporte y handoff | E7/E9/E10 | Guías, responsables, contactos y evidencia de transferencia |

Estado actual de todas estas condiciones: **PENDIENTE DE VERIFICACIÓN**. El plan no las da por satisfechas.

## 14. Definition of Done y cierre de etapas

Una unidad de trabajo futura se considera terminada cuando:

1. Tiene caso de uso, alcance MVP, referencias KB y criterios verificables; cualquier ambigüedad material está resuelta.
2. Respeta invariantes/ADR/NFR aplicables y los límites de responsabilidad modular.
3. Aplica autorización en backend, privacidad e historia requeridas, con positivos/negativos pertinentes.
4. Tiene pruebas de dominio/persistencia y, donde corresponda, UI, idempotencia, concurrencia, fallos y temporalidad.
5. Las migraciones/configuraciones necesarias son reproducibles y su impacto histórico está revisado.
6. La interfaz pertinente muestra loading/success/failure/unknown y no duplica reglas financieras autoritativas.
7. Historia, auditoría, logs y métricas pertinentes están presentes sin filtrar datos sensibles.
8. La trazabilidad está actualizada y enlaza implementación futura, prueba y evidencia real.
9. Las decisiones técnicas relevantes están registradas; no hay POST-MVP infiltrado ni defecto conocido que viole un control crítico.
10. El revisor y resultado de revisión quedan registrados. Compilar o verse correctamente no basta.

Para cerrar una etapa: identificar versión/commit, entregables, pruebas, resultados, defectos y decisiones pendientes; comprobar G-E correspondiente y dejar acta breve de aceptación o bloqueo. Un defecto no crítico sólo puede diferirse documentando impacto y sin contradecir controles normativos; nunca se rebaja un invariante para pasar un gate.

### 14.1 Plantilla de unidad ejecutable

| Campo | Contenido requerido |
| --- | --- |
| ID local / etapa | Identificación de planificación, sin inventar IDs normativos |
| Caso de uso y objetivo | Actor, recurso y resultado aprobado |
| Fuente | Secciones KB, MVP, módulos, invariantes, ADR, NFR, riesgos |
| Entrada | Datos/precondiciones, dependencias y decisiones cerradas |
| Trabajo y exclusiones | Entrega concreta y frontera POST-MVP aplicable |
| Aceptación | Resultados observables positivos, negativos y límites |
| Pruebas | Escenarios, datos sintéticos, resultado esperado y fallos pertinentes |
| Evidencia | Implementación, versión, test, resultado y revisión |
| Estado | Pendiente / en curso / bloqueada / verificada, según evidencia real |

Trazabilidad completa esperada: necesidad → regla/decisión → MVP → módulo → invariante/ADR → riesgo → caso de uso → implementación → test → evidencia. Este plan cubre la asignación de trabajo/evidencia; los enlaces a código y resultados se completarán al existir. No se declara cumplida la trazabilidad de implementación antes de construir.

## 15. Calendario, recursos y revisión del plan

Antes de convertir etapas en fechas, obtener: equipo/sistema operativo disponible, capacidad semanal real, participantes y experiencia, responsables operativos, acceso a cuentas y disponibilidad para validación de negocio. No se asume la disponibilidad mencionada en conversaciones históricas.

Propuesta de estimación: descomponer la siguiente etapa usando §14.1, estimar rangos con supuestos explícitos y recalibrar después de E1 y del primer flujo E4. Incluir tiempo de validación, corrección, documentación, recuperación y capacitación. Mantener por separado esperas externas de revisión legal o infraestructura. No reducir MVP o pruebas para hacer encajar una fecha sin el proceso correspondiente.

Tras la aprobación del plan, el siguiente paquete es **E1.1 — Preparar computadora y crear repositorio inicial**. Su preparación empieza por inventariar equipo/accesos y cerrar DT-01/DT-08; los comandos y la configuración se producirán en esa etapa, no en este documento.

## 16. Revisión de consistencia del plan

| Control documental | Resultado documental |
| --- | --- |
| MVP | 14/14 paquetes asignados en §6 |
| Invariantes | 20/20 asignados en §7 |
| ADR | 15/15 asignados en §8 |
| Riesgos | 18/18 tratados en §12 |
| Gates oficiales | 5/5 preservados en §13 |
| Decisiones abiertas de implementación de KB §26 | 13/13 registradas en §9, sin declararlas resueltas |
| Etapas | 10 fichas con objetivo, entradas, trabajo, entregables, pruebas, riesgos y gate |
| Cooperaciones / ciclo anual | E4, explícitos aunque no tengan paquete propio |
| Web y Flutter | Ambos dentro del MVP; sin exigir paridad completa |
| POST-MVP | Excluido; ninguna exclusión se convierte aquí en entrega |
| Cambios a KB/Baseline/arquitectura | Ninguno propuesto |
| Código de aplicación generado | Ninguno |
| Pruebas de software / gates ejecutados | Ninguno; sólo revisión documental |
| Estado del Plan | APROBADO sobre revisión 0.2 |

La cobertura por identificador acredita presencia documental; no prueba suficiencia de una implementación. La aprobación del orden y los gates de trabajo establece este documento como plan operativo; no resuelve por anticipado decisiones técnicas abiertas ni autoriza producción.

## 17. Fuente y referencias

Única fuente normativa usada: **Sistema_Gestion_Comunitaria_Knowledge_Base_V1.0_CURRENT.md**, Knowledge Base V1.0 APROBADA / CURRENT, consolidada el 21 de septiembre de 2026 y suministrada en esta conversación.

- §§1, 28–31: jerarquía, protocolo IA, trazabilidad y control de cambios.
- §§4–15: autoridad, reglas financieras, cooperaciones, préstamos, pagos, documentos y portal.
- §§16–19: módulos, MVP, POST-MVP e invariantes.
- §§20–23: NFR, arquitectura, ADR y seguridad.
- §§24–27: riesgos, gates, decisiones abiertas y readiness.
- §§32–33: estado de handoff y contenido obligatorio del Plan de Construcción.

No se recurrió a planes históricos ni a recomendaciones externas para modificar el proyecto. Las fuentes oficiales de herramientas se consultarán al resolver decisiones de implementación y seleccionar versiones.

## 18. Historial del plan

| Revisión | Estado | Cambio |
| --- | --- | --- |
| V1 propuesta 0.1 — 2026-09-22 | Pendiente de aprobación | Primera propuesta completa de secuencia, etapas, trazabilidad, decisiones, evidencias y preparación operativa; KB intacta |
| V1 propuesta 0.2 — 2026-09-22 | Pendiente de aprobación | Revisión de orden/gates: preparación de E1, fechas desde E2, alcance de pruebas progresivo, paquetes internos y preparativos tempranos |

### 18.1 Revisión del orden y gates — propuesta 0.2

| Hallazgo de la propuesta 0.1 | Ajuste de planificación | Estado |
| --- | --- | --- |
| E1 exigía DT-01/DT-08 resueltas aunque su preparación debía resolverlas | Separación entre preparación y trabajo dependiente; sincronización de E1 y registro DT | Corregido en propuesta |
| DT-07 estaba situada en E3 aunque periodos/vigencias se implementan en E2 | Cierre antes de periodos/vigencias; validación financiera adicional en E3 | Corregido en propuesta |
| Gates de E2/E3 podían leerse como prueba integral de funciones aún inexistentes | Alcance de pruebas de componente explícito y obligación de integración E4–E8 | Aclarado |
| E5 mencionaba cierre documental posterior sin existir todavía pagos/liquidación | Gate E5 acotado hasta desembolso; integración LIQUIDADO/devolución en E6 | Aclarado |
| E4/E6/E7/E8 agrupaban demasiado trabajo para seguimiento fino | Paquetes internos verificables sin alterar las diez etapas ni reducir gates | Desglosado |
| Inventario de apertura y viabilidad de recuperación podían dejarse para E9 | Puntos de inicio y revisión temprana explícitos | Aclarado |

Resultado: se conserva la secuencia de diez etapas. No se detectaron cambios necesarios al Baseline en esta revisión del plan. Los ajustes corrigen dependencias y evidencia de la propuesta; no modifican reglas de la KB ni dan por cumplido ningún gate. Al cierre de aquella revisión, el Plan V1 permanecía pendiente de aprobación. La aprobación posterior se registra en §18.2.


### 18.2 Registro de aprobación

- Aprobador: Fer, responsable del proyecto.
- Evidencia: respuesta expresa «Aprobado» a la solicitud de aprobar la revisión 0.2 y pasar a preparar E1.1, en esta conversación.
- Fecha de registro: 22 de septiembre de 2026.
- Documento aprobado: Plan de Construcción V1, contenido de la revisión 0.2.
- Alcance: secuencia, dependencias, organización del trabajo y criterios de cierre documentados.
- Estado vigente: **APROBADO**.
- KB V1.0: permanece APROBADA / CURRENT, sin modificaciones.
- Decisiones DT-01…DT-13: permanecen ABIERTAS hasta su resolución documentada.
- Gates G-E1…G-E10 y GO-LIVE-01…GO-LIVE-05: sin evidencia de ejecución en este trabajo documental.
- Siguiente acción autorizada: preparar E1.1; obtener inventario del equipo y accesos antes de producir instrucciones específicas de entorno.

## 19. Preparación de E1.1 — inventario y decisiones iniciales

Estado: **PREPARACIÓN INICIADA; INVENTARIO PENDIENTE**. Este apartado organiza el siguiente paso dentro de E1, sin cambiar el contenido aprobado ni generar código de aplicación.

| Dato pendiente | Para qué se necesita |
| --- | --- |
| Computadora y sistema operativo con versión | Elegir instrucciones compatibles con el equipo real |
| Procesador, RAM y espacio libre aproximados | Evaluar capacidad del entorno y sus herramientas |
| Herramientas ya instaladas | Evitar instalaciones duplicadas y comprobar compatibilidad antes de cambiarlas |
| Cuenta/proveedor Git existente | Preparar DT-08 sin presuponer GitHub u otro proveedor |
| Participantes y disponibilidad semanal aproximada | Asignar trabajo y estimar sin asumir recursos históricos |

Secuencia de preparación:

1. Recibir el inventario; si algún dato se desconoce, guiar su consulta según el sistema operativo.
2. Evaluar DT-01 (UI Web) y DT-08 (Git/CI/CD) conforme a los drivers del plan y al equipo disponible, consultando documentación oficial vigente al recomendar opciones.
3. Registrar las decisiones adoptadas y su justificación sin reabrir Baseline ni añadir POST-MVP.
4. Preparar instrucciones específicas de instalación/configuración y creación del repositorio; ejecutarlas o guiarlas en el equipo correspondiente dentro del alcance autorizado.
5. Registrar evidencia de reproducción. E1.1 por sí sola no acredita todo G-E1.

No se infiere que el entorno de esta conversación sea la computadora de desarrollo de Fer. No se han creado repositorios ni instalado herramientas en su equipo.
