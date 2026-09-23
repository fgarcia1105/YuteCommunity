---
purpose: Fuente canónica para IA, desarrollo, arquitectura, QA y gestión
  del proyecto
status: APROBADA / CURRENT
title: Sistema de Gestión Comunitaria --- Knowledge Base V1.0 CURRENT
version: 1.0
---

> **FUENTE CANÓNICA VIGENTE**
>
> Este archivo Markdown representa la Knowledge Base V1.0 aprobada del
> Sistema de Gestión Comunitaria. Debe utilizarse como contexto técnico
> y funcional antes de diseñar o implementar cambios. No se deben
> inventar requisitos ni modificar silenciosamente reglas, invariantes,
> ADR, alcance o arquitectura. Si aparece una contradicción material,
> debe detenerse la interpretación, documentarse y resolverse mediante
> el proceso de control de cambios correspondiente.

SISTEMA DE GESTIÓN COMUNITARIA

KNOWLEDGE BASE V1.0

Documento Canónico de Construcción

Fuente única de verdad para IA, desarrollo, arquitectura, QA y gestión
del proyecto

  -----------------------------------------------------------------------
  Campo                               Estado
  ----------------------------------- -----------------------------------
  Baseline                            V1.0 --- APROBADO / CONGELADO

  MVP                                 1.0 --- APROBADO / CONGELADO

  Knowledge Base                      V1.0 --- APROBADA / CURRENT

  Invariantes                         20 / 20 aprobados

  ADRs                                15 / 15 ACCEPTED

  Arquitectura                        Modular Monolith --- Laravel +
                                      PostgreSQL

  Cliente principal                   Web responsive completo

  Cliente móvil                       Flutter enfocado

  Modo operativo                      Online-first; sin operación
                                      financiera offline en MVP

  Fecha de consolidación              21 de septiembre de 2026
  -----------------------------------------------------------------------

  -----------------------------------------------------------------------
  REGLA DE GOBIERNO`<br>`{=html}Este documento es la referencia vigente
  para iniciar la construcción. Documentos anteriores que contradigan
  esta KB se consideran HISTORICAL / SUPERSEDED. Ninguna IA,
  desarrollador o responsable de proyecto debe modificar silenciosamente
  reglas, invariantes, ADR, alcance MVP o arquitectura. Los cambios
  materiales requieren Change Request y versionado.
  -----------------------------------------------------------------------

  -----------------------------------------------------------------------

Estado de revisión final: PASS --- sin contradicciones materiales
conocidas que bloqueen la planificación.

## 0. Cómo usar este documento

Este documento concentra el conocimiento aprobado necesario para que una
IA, desarrollador, arquitecto, QA, Product Owner o responsable de
proyecto pueda continuar desde el mismo punto sin reconstruir decisiones
desde conversaciones históricas.

-   Para negocio: usar las reglas y flujos como definición vigente del
    comportamiento esperado.

-   Para arquitectura: respetar Architecture Drivers, NFR, Arquitectura
    Objetivo e ADRs.

-   Para desarrollo: derivar casos de uso, modelo de dominio, contratos,
    persistencia y pruebas sin inventar requisitos.

-   Para QA: convertir invariantes, reglas y flujos E2E en criterios de
    prueba.

-   Para IA: tratar APPROVED/CURRENT como fuente normativa; marcar
    cualquier ambigüedad crítica y detenerse antes de inventar.

-   Para Project Management: construir el Plan de Construcción V1 desde
    esta KB, no desde planes anteriores.

  -----------------------------------------------------------------------
  SIGUIENTE HITO`<br>`{=html}El siguiente artefacto formal es el PLAN DE
  CONSTRUCCIÓN V1. Después se retoma ETAPA 1 --- Repositorio y Entorno.
  Esta KB no autoriza por sí sola comenzar a programar sin ordenar
  previamente la construcción.
  -----------------------------------------------------------------------

  -----------------------------------------------------------------------

## 1. Estado, gobierno y jerarquía normativa

### 1.1 Estado oficial

  Elemento                                Estado
  --------------------------------------- ----------------------------------
  Baseline V1.0                           APROBADO / CONGELADO
  MVP 1.0                                 APROBADO / CONGELADO
  KB V1.0                                 APROBADA / CURRENT
  20 invariantes V1                       APROBADOS
  15 ADR V1                               ACCEPTED
  Riesgos iniciales                       RISK-01...RISK-18 vigentes
  Go-Live                                 GO-LIVE-01...GO-LIVE-05 vigentes
  Contradicciones materiales conocidas    0
  Pendientes que bloqueen planificación   0

### 1.2 Jerarquía y resolución de conflictos

Baseline V1.0 es el contenedor normativo aprobado. Dentro de él
coexisten reglas de negocio, MVP, invariantes, ADRs y Arquitectura
Objetivo. Los artefactos inferiores ---resúmenes, planes, diseño,
código, pruebas y documentación--- no pueden modificar esos elementos
silenciosamente.

-   Si implementación y Baseline difieren, la implementación es
    incorrecta hasta que exista un cambio aprobado.

-   Si dos componentes aprobados parecen contradictorios, no se inventa
    una prioridad: se detecta, analiza y resuelve explícitamente.

-   Una propuesta no es una decisión. Una idea nueva no es
    automáticamente un requisito.

-   POST-MVP no debe infiltrarse en MVP por conveniencia técnica.

### 1.3 Clasificación de cambios

  -----------------------------------------------------------------------
  Tipo                                Tratamiento
  ----------------------------------- -----------------------------------
  Editorial                           Corrección de forma sin cambiar
                                      significado.

  Clarificación                       Hace explícito lo ya aprobado; no
                                      cambia comportamiento.

  Implementación                      Decisión técnica local dentro de
                                      límites aprobados.

  Inconsistencia                      Se corrige de forma explícita y
                                      trazable.

  Cambio de Baseline                  Requiere Change Request, impacto,
                                      aprobación y nueva versión.

  Nueva capacidad POST-MVP            Se registra sin introducirla al
                                      MVP.

  Incidente/Hotfix                    La urgencia no elimina
                                      trazabilidad, invariantes ni
                                      pruebas.
  -----------------------------------------------------------------------

## 2. Contexto, problema y visión

La comunidad administra recursos provenientes de cooperaciones,
actividades, ventas, rifas, donaciones y recuperación de préstamos. El
proceso actual depende en gran medida de libretas, pagarés, recibos
físicos y conocimiento de las personas responsables. El problema
principal no es solamente registrar préstamos: es mantener control
financiero, documental, de custodia, responsabilidades y evidencia
histórica.

-   Población aproximada: 300 personas; alrededor de 50 prestatarios.

-   Usuarios distribuidos geográficamente; no se requiere servidor local
    en oficina.

-   Una comunidad por instalación. Otra comunidad implica
    infraestructura separada usando el mismo software.

-   Dispositivos: computadora, celular y tablet.

-   Integridad financiera y trazabilidad tienen prioridad sobre
    throughput o aparente velocidad.

-   La pérdida de datos no es aceptable en operación normal.

Dominio central: Fondo → ingresos/egresos → préstamos →
pagos/recuperaciones → custodia → disponible → evidencia →
cortes/informes → auditoría.

## 3. Glosario operativo y actores

  -----------------------------------------------------------------------
  Concepto / Actor                    Definición vigente
  ----------------------------------- -----------------------------------
  Persona                             Entidad reutilizable que representa
                                      a una persona física; no equivale
                                      necesariamente a Usuario.

  Usuario                             Cuenta autenticada vinculada a una
                                      Persona cuando corresponda.

  Administrador                       Administra usuarios, configuración,
                                      reportes y auditoría; no posee
                                      autoridad financiera general.

  Encargado General                   Responsable operativo del Fondo
                                      General y autoridad financiera
                                      dentro de las reglas aprobadas.

  Responsable de Comisión             Responsable del fondo de su
                                      comisión y de sus gastos conforme a
                                      su alcance.

  Colaborador                         Usuario operativo dentro de un
                                      alcance; puede recibir efectivo,
                                      apoyar cobranza y registrar
                                      operaciones autorizadas.

  Prestatario                         Persona con préstamo; puede tener
                                      cuenta de portal cuando exista
                                      préstamo real.

  Aval                                Persona reutilizable vinculada a un
                                      préstamo específico como garante.

  Fondo                               Unidad económica con movimientos,
                                      custodia, disponibilidad, informes
                                      y alcance.

  Custodia                            Responsabilidad temporal sobre
                                      dinero o documentos; no equivale a
                                      disponibilidad del Fondo.

  Disponible                          Dinero bajo control/custodia del
                                      Fondo y utilizable conforme a
                                      reglas.

  Corte                               Snapshot histórico formal que no se
                                      reescribe silenciosamente.

  Rectificación                       Operación trazable que corrige un
                                      efecto previo sin destruir
                                      historia.

  Constancia                          Documento identificable emitido
                                      cuando un colaborador recibe
                                      efectivo; no duplica el pago.

  Recibo oficial                      Documento oficial vinculado a la
                                      operación reconocida y, cuando
                                      aplica, a la
                                      oficialización/custodia del Fondo.
  -----------------------------------------------------------------------

## 4. Modelo organizacional y autoridad

### 4.1 Roles y alcance

-   1 Administrador del sistema.

-   1 Encargado del Fondo General.

-   Responsables por comisión y uno o más colaboradores según
    organización.

-   Prestatarios con portal propio cuando corresponda.

-   La autorización siempre considera identidad + función/rol +
    alcance + permiso + vigencia + recurso.

### 4.2 Administración no equivale a autoridad financiera

El Admin puede administrar usuarios, configuración, reportes y
auditoría, pero no adquiere por ello autoridad para aprobar préstamos,
gastos o modificar efectos financieros. El Admin no obtiene acceso
automático a INE, comprobantes de domicilio, pagarés, garantías o
expedientes sensibles.

Excepción específica aprobada: el Admin tiene facultad operacional para
iniciar manualmente el nuevo ciclo anual de cooperaciones. Esta facultad
no amplía sus demás permisos financieros.

### 4.3 Periodos de responsabilidad

-   Asignaciones con persona, fondo/comisión, rol, inicio, fin planeado
    opcional, fin real y motivo.

-   Periodo típico de encargado cercano a tres años, pero no
    hardcodeado.

-   Cambio de responsable preserva cierre, entrega, historial y nueva
    gestión.

-   Una persona no puede pertenecer simultáneamente a múltiples
    comisiones como colaborador/responsable, según la regla aprobada.

## 5. Modelo financiero del Fondo

### 5.1 Separaciones obligatorias

El sistema no debe representar todo como un único "saldo". Debe
distinguir al menos:

-   dinero disponible bajo custodia/control del Fondo;

-   efectivo pendiente de entrega por colaboradores;

-   cuentas por cobrar;

-   capital prestado / pendiente / recuperado;

-   interés realizado;

-   otros ingresos;

-   gastos;

-   obligaciones y montos restringidos pendientes, como devoluciones.

Disponible ≠ patrimonio. Crecimiento ≠ disponible. Interés no cobrado ≠
utilidad actual.

### 5.2 Movimientos

-   Toda variación de un Fondo debe provenir de una operación trazable.

-   No existe edición directa de saldo.

-   Mover efectivo de caja a banco dentro del mismo Fondo no es ingreso
    ni gasto.

-   Los egresos deben indicar naturaleza económica.

-   Ingresos no relacionados con préstamos pueden incluir cooperaciones,
    actividades, ventas, rifas y donaciones.

### 5.3 Conciliación

-   Caja: esperado, contado, diferencia, responsable, fecha y
    observaciones.

-   Banco: saldo del sistema, saldo bancario verificado, fecha,
    diferencia y evidencia opcional.

-   Las diferencias generan trazabilidad/incidente; no se corrigen
    editando saldos.

## 6. Cooperaciones, actividades e ingresos comunitarios

### 6.1 Cooperaciones

-   Cooperación individual con montos variables.

-   Se permite aportación adicional.

-   Una persona puede cooperar con distintos colaboradores.

-   Advertencias por duplicados pueden permitir continuar conforme a
    configuración aprobada.

-   El nuevo ciclo anual se inicia manualmente por la facultad
    operacional específica del Admin.

-   Colaborador puede dar de alta persona, registrar cooperación e
    imprimir/emitir evidencia conforme al flujo.

### 6.2 Entrega a tesorería

-   Entrega presencial o por transferencia.

-   La entrega puede relacionar folios y personas correspondientes.

-   Si el encargado cobra directamente, el dinero puede pasar
    directamente al control del Fondo.

### 6.3 Actividades comunitarias

-   Registrar inversión, ingresos/producido, gastos, evidencia y
    aportaciones.

-   Compras sin comprobante formal pueden tener nota interna cuando esté
    permitido.

-   Las actividades no deben confundirse con préstamos.

### 6.4 Comisiones

-   Cada comisión conserva su propio fondo y su propio informe.

-   El Responsable de Comisión autoriza sus gastos dentro de su alcance.

-   El Encargado General no obtiene supervisión automática de todos los
    detalles internos de comisiones.

-   Préstamos formales Fondo General ↔ Comisión o Comisión ↔ Comisión
    son POST-MVP.

## 7. Préstamos comunitarios

### 7.1 Gobernanza y elegibilidad

-   La decisión se discute con colaboradores; el Encargado tiene
    decisión final conforme a reglas vigentes.

-   Elegibles: personas conocidas y familiares cercanos de miembros,
    conforme al proceso comunitario aprobado.

-   Máximo un préstamo no liquidado por persona en MVP. No se modela
    como invariante permanente para permitir evolución futura.

-   Monto máximo configurable para nuevos préstamos; excepciones
    requieren autorización explícita, motivo y responsable.

-   La autoridad de negocio/comunitaria decide límites y políticas; el
    Admin únicamente registra configuración salvo facultades específicas
    aprobadas.

### 7.2 Datos y documentos

-   Nombre, teléfono, correo, identificación y comprobante de domicilio
    según checklist configurable.

-   Checklist documental requerido/opcional configurable y preservado
    históricamente por solicitud/préstamo.

-   Pagaré firmado al momento de entrega conforme al proceso físico
    aprobado.

-   Garantías adicionales caso por caso; tipos abiertos/configurables.

-   Custodia de documentos físicos debe registrar recepción, ubicación,
    devolución y evidencia.

### 7.3 Estados

  -----------------------------------------------------------------------
  Transición                          Significado
  ----------------------------------- -----------------------------------
  BORRADOR → EN_REVISION              Solicitud preparada y enviada a
                                      análisis.

  EN_REVISION → AUTORIZADO            Aprobada pero todavía sin
                                      desembolso.

  EN_REVISION → RECHAZADO             Solicitud rechazada; conserva
                                      historia.

  AUTORIZADO → ACTIVO                 Sólo al entregar efectivamente el
                                      dinero.

  AUTORIZADO → CANCELADO              Cancelación antes del desembolso.

  ACTIVO → VENCIDO                    Se supera fecha de compromiso; sin
                                      penalización automática.

  ACTIVO/VENCIDO → LIQUIDADO          Obligación monetaria llega a cero.
  -----------------------------------------------------------------------

LIQUIDADO no implica cierre documental. El pagaré y garantías pueden
requerir devolución y evidencia posterior.

## 8. Reglas financieras de préstamos

### 8.1 Interés

Tasa vigente de referencia: 5% mensual, modificable por autoridad de
negocio. Cada préstamo conserva históricamente la política/tasa
aplicable al momento de desembolso.

Interés simple sobre PRINCIPAL ORIGINAL. Los pagos parciales no reducen
la base de cálculo del interés.

Ejemplo: 10,000 × 0.05 × 3 meses = 1,500 de interés.

### 8.2 Totales y liquidación

-   Total normal a vencimiento = principal original + interés del plazo
    acordado.

-   Saldo normal = total proyectado − pagos reconocidos.

-   Liquidación anticipada = principal original + interés devengado a la
    fecha − pagos reconocidos.

-   Pago el mismo día del desembolso: interés devengado 0.

-   No existe penalización financiera automática por mora en MVP.

### 8.3 Meses completos + días/30

-   Los meses completos se determinan por aniversarios mensuales desde
    la fecha real de desembolso.

-   El día del desembolso es el día ancla.

-   Si el mes destino no contiene el día ancla, se usa el último día
    válido sin desplazar permanentemente el ancla.

-   31 enero → 28/29 febrero = 1 mes completo; 31 enero → 1 marzo = 1
    mes + 1/30.

-   31 agosto → 30 septiembre = 1 mes; 31 agosto → 31 octubre = 2 meses.

-   Antes del primer aniversario: 0 meses completos + días
    transcurridos/30.

### 8.4 Redondeo

-   Aritmética decimal; Float/Double no son representación autoritativa
    de dinero.

-   Evitar redondeos intermedios innecesarios.

-   Importes monetarios oficiales se expresan a 2 decimales.

-   Regla oficial: ROUND_HALF_UP para importes positivos; 10.005 →
    10.01.

-   La precisión SQL física exacta permanece como decisión de
    implementación, siempre que respete esta regla.

### 8.5 Clasificación para reporting

El usuario registra un pago total. El sistema clasifica para reporting
CAPITAL PRIMERO y después INTERÉS. Esta clasificación es informativa y
no cambia la fórmula de obligación ni convierte el préstamo en saldo
decreciente.

## 9. Pagos, reconocimiento, custodia y PAY-01

### 9.1 Regla PAY-01

  -----------------------------------------------------------------------
  PAY-01`<br>`{=html}Efectivo entregado a un Colaborador autorizado y
  debidamente registrado reduce inmediatamente la obligación del
  Prestatario una sola vez. Al mismo tiempo crea una obligación de
  custodia/entrega del Colaborador hacia el Fondo. El dinero no es
  disponible del Fondo hasta que quede bajo su control/custodia.
  -----------------------------------------------------------------------

  -----------------------------------------------------------------------

### 9.2 Casos

  -----------------------------------------------------------------------
  Caso                    Efecto sobre deuda      Efecto sobre disponible
  ----------------------- ----------------------- -----------------------
  Encargado recibe        Reduce al registrarse   Puede quedar disponible
  efectivo                correctamente.          conforme al flujo
                                                  oficial.

  Colaborador recibe      Reduce inmediatamente   No disponible; queda
  efectivo                una sola vez.           pendiente de
                                                  entrega/custodia.

  Transferencia reportada No reduce todavía.      No disponible.

  Transferencia           Reduce con fecha        Se reconoce conforme a
  verificada              efectiva de             la cuenta/custodia
                          transferencia.          correspondiente.
  -----------------------------------------------------------------------

### 9.3 Pérdida bajo custodia

Si un Colaborador pierde efectivo después de un reconocimiento válido,
la deuda del Prestatario NO se restaura. Se registra incidente/faltante
de custodia y responsabilidad interna.

### 9.4 Portal

-   El Prestatario ve cualquier pago ya reconocido aunque la custodia
    siga pendiente.

-   Para efectivo con Colaborador: deuda reducida + constancia
    disponible + custodia pendiente.

-   La entrega posterior al Fondo no reduce nuevamente la deuda.

## 10. Sobrepagos, devoluciones y donaciones

### 10.1 Excedente

Si se recibe más de lo necesario para liquidar, el préstamo se liquida
por lo correspondiente y el excedente crea una obligación de devolución.

-   El excedente no es ingreso automático.

-   El excedente no es disponible utilizable mientras exista obligación
    de devolución.

-   Se clasifica como importe restringido / pendiente de devolución.

### 10.2 Conversión voluntaria en donación

El Prestatario puede decidir expresamente convertir total o parcialmente
el excedente en una DONACIÓN. La decisión debe ser voluntaria, expresa y
trazable. No puede inferirse por silencio, paso del tiempo o decisión
unilateral de un usuario.

-   La donación es una nueva operación de ingreso separada del pago.

-   La obligación de devolución disminuye únicamente por el importe
    expresamente donado.

-   El pago original no se reescribe.

-   Si el dinero continúa bajo custodia de un Colaborador, reconocer la
    donación no lo vuelve disponible hasta la entrega al Fondo.

## 11. Recibos, constancias y rectificaciones

### 11.1 Principios

-   Cada operación/documento relevante posee identificación/folio
    trazable conforme a reglas aplicables.

-   Un folio emitido no se reutiliza.

-   Constancia de Colaborador y recibo oficial posterior se relacionan;
    no son dos pagos.

-   PDF/documento no es la fuente autoritativa del saldo.

### 11.2 Tres conceptos distintos

  -----------------------------------------------------------------------
  Concepto                            Efecto
  ----------------------------------- -----------------------------------
  Cancelación documental              Invalida/sustituye documento; no
                                      modifica por sí sola el dinero.

  Rectificación financiera            Corrige un efecto financiero
                                      mediante operación trazable y no
                                      destructiva.

  Cancelación compuesta de negocio    Puede orquestar cancelación
                                      documental +
                                      reversión/rectificación cuando el
                                      caso de uso lo exige, por ejemplo
                                      cooperaciones.
  -----------------------------------------------------------------------

Si el pago es correcto y el recibo está mal, se conserva el pago y se
sustituye el documento. Si el pago también es incorrecto, se requiere
rectificación financiera explícita además del tratamiento documental.

## 12. Avales, garantías y custodia documental

-   Número de avales definido caso por caso.

-   Aval es Persona reutilizable; su participación se vincula al
    préstamo específico.

-   Tener préstamo pendiente o ser aval en otro crédito genera
    advertencia, no bloqueo duro.

-   Requisitos/documentos de aval configurables y preservados
    históricamente.

-   Garantías adicionales: cero o más; tipo abierto/configurable,
    descripción, persona si aplica, evidencia, recepción, custodia,
    ubicación, devolución y notas.

-   Registrar una garantía o documento en custodia no implica propiedad,
    derecho de disposición ni ejecutabilidad jurídica automática.

-   Antes de producción debe revisarse jurídicamente pagaré, avales,
    cancelaciones y garantías.

## 13. Cobranza y mora

-   Cobranza manual asistida en MVP.

-   Puede realizarla Encargado o colaboradores autorizados dentro de su
    alcance.

-   No existe número fijo de intentos antes de contactar aval; se
    documenta seguimiento.

-   Promesas pueden registrar fecha, monto, persona contactada y
    observaciones.

-   Promesa incumplida se marca; puede registrarse una nueva sin sanción
    automática.

-   Evidencia de seguimiento: descripción + documentos cuando
    corresponda.

-   Dashboard puede mostrar vencidos, promesas y ausencia de contacto
    reciente.

-   Mensajería automática queda POST-MVP.

## 14. Informes, cortes y reporting

-   No existe periodo fijo obligatorio para informes.

-   Corte formal = snapshot histórico; no se reescribe silenciosamente.

-   Correcciones posteriores se registran separadamente.

-   Informe comunitario muestra cifras consolidadas, no datos personales
    de prestatarios.

-   Informes de comisiones son independientes; no existe mega-informe
    obligatorio consolidado.

-   Misma fecha/reunión puede tener informes separados por Fondo.

-   Comparar con corte anterior y explicar variaciones mediante
    movimientos trazables.

-   Los préstamos formales interfondos son POST-MVP y no deben
    infiltrarse por el hecho de aparecer como concepto futuro en
    reportes.

## 15. Portal del Prestatario --- MVP

### 15.1 Puede consultar

-   préstamo actual y préstamos previos propios;

-   monto original, tasa, plazo, desembolso, compromiso y estado;

-   pagos reconocidos;

-   importe actual adeudado;

-   liquidación anticipada a una fecha;

-   recibos y constancias propias;

-   descarga/impresión de documentos propios autorizados.

### 15.2 No puede consultar

-   otros prestatarios; notas internas; análisis de autorización; notas
    de cobranza; expediente administrativo interno.

El backend deriva la identidad y aplica autorización a nivel de objeto.
Ocultar controles en frontend no es seguridad.

### 15.3 POST-MVP

Reporte de transferencias/carga de comprobantes, actualización autónoma
de datos, notificaciones, solicitud de liquidación, estado de devolución
de garantía/pagaré y solicitud de nuevo préstamo.

## 16. Mapa funcional de módulos

  -----------------------------------------------------------------------
  ID                      Módulo                  Responsabilidad
                                                  principal
  ----------------------- ----------------------- -----------------------
  01                      Organización e          Personas, usuarios,
                          Identidad               roles, periodos,
                                                  configuración
                                                  institucional.

  02                      Autorización y Gestión  Permisos, alcance,
                                                  vigencia y autoridad.

  03                      Fondos y Movimientos    Fondos, ingresos,
                                                  egresos, ubicaciones y
                                                  movimientos.

  04                      Custodia y Conciliación Dinero pendiente,
                                                  entregas, conciliación
                                                  e incidentes.

  05                      Actividades             Inversión, producido,
                          Comunitarias            gastos y evidencia.

  06                      Préstamos               Solicitud,
                                                  autorización,
                                                  desembolso, cálculo,
                                                  estados.

  07                      Pagos y Recibos         Reconocimiento, PAY-01,
                                                  recibos, constancias,
                                                  devoluciones.

  08                      Expedientes y Custodia  Documentos, versiones,
                          Documental              garantías, pagarés,
                                                  privacidad.

  09                      Cobranza                Seguimiento, promesas,
                                                  evidencia y vencidos.

  10                      Informes y Cortes       Snapshots, reportes y
                                                  comparación histórica.

  11                      Auditoría               Eventos relevantes,
                                                  seguridad y
                                                  trazabilidad.

  12                      Portal del Prestatario  Consulta segura de
                                                  información propia.
  -----------------------------------------------------------------------

Dashboards son transversales. Modularidad funcional no implica
microservicios.

## 17. MVP 1.0 --- alcance congelado

  -----------------------------------------------------------------------
  ID                                  Capacidad incluida
  ----------------------------------- -----------------------------------
  MVP-01                              Organización, usuarios y periodos.

  MVP-02                              Fondo General + fondos de
                                      comisiones, ubicaciones de
                                      custodia, banco/caja, movimientos,
                                      conciliación básica e incidentes;
                                      sin integración bancaria.

  MVP-03                              Flujo completo Persona → préstamo;
                                      máximo un préstamo no liquidado por
                                      persona.

  MVP-04                              Avales, garantías y custodia
                                      documental.

  MVP-05                              Pagos, custodia y recibos: PAY-01,
                                      parciales, anticipados, exceso,
                                      devolución, rectificación,
                                      idempotencia y fecha efectiva.

  MVP-06                              Actividades comunitarias básicas.

  MVP-07                              Cobranza manual asistida.

  MVP-08                              Expedientes, documentos, versiones,
                                      evidencia y permisos privados.

  MVP-09                              Informes/cortes independientes por
                                      Fondo, históricos y comparativos;
                                      sin mega-informe organizacional.

  MVP-10                              Auditoría + conciliación básica de
                                      caja/banco.

  MVP-11                              Dashboards por rol y alcance.

  MVP-12                              Portal del Prestatario para
                                      consulta y recibos.

  MVP-13                              Cliente principal Web responsive
                                      completo.

  MVP-14                              Flutter enfocado: autenticación,
                                      dashboard, consulta
                                      Persona/préstamo,
                                      recepción/consulta de pagos según
                                      permisos, recibos, cobranza de
                                      campo, evidencia, perfil y portal;
                                      sin paridad 100%.
  -----------------------------------------------------------------------

## 18. Frontera POST-MVP

1.  Préstamos formales Fondo General ↔ Comisión e intercomisiones.

2.  Múltiples préstamos simultáneos por Persona.

3.  Operaciones financieras offline.

4.  Sincronización offline-first.

5.  Integración bancaria automatizada.

6.  Cobranza automatizada.

7.  WhatsApp/SMS/push avanzados.

8.  Portal de aval.

9.  Solicitud autónoma de préstamo por Prestatario.

10. Carga autónoma de comprobante por Prestatario.

11. BI avanzado.

12. IA tomando decisiones financieras.

13. Contabilidad empresarial/formal completa.

14. Microservicios.

15. Multi-comunidad dentro de una misma instalación.

16. Paridad 100% Web/Flutter.

17. Automatización de ejecución legal de garantías.

18. Múltiples monedas salvo necesidad futura real.

## 19. Invariantes V1 --- 20 reglas que la implementación no puede violar

  -----------------------------------------------------------------------
  ID                                  Invariante
  ----------------------------------- -----------------------------------
  INV-FIN-01                          Historia financiera no destructiva;
                                      las correcciones se realizan por
                                      rectificación.

  INV-FIN-02                          Condiciones del préstamo se
                                      congelan al desembolso; la política
                                      histórica se preserva.

  INV-FIN-03                          Cada operación financiera produce
                                      efecto exactamente una vez.

  INV-FIN-04                          Cálculo financiero determinista:
                                      decimal controlado, fechas y reglas
                                      explícitas.

  INV-FIN-05                          Clasificación de reporting no
                                      altera obligación; capital-first es
                                      informativo y el interés usa
                                      principal original.

  INV-PAY-01                          Un pago reconocido reduce deuda una
                                      sola vez; custodia, entrega,
                                      conciliación o recibo posterior no
                                      vuelven a reducirla.

  INV-PAY-02                          Reconocimiento del pago y
                                      disponibilidad del Fondo son
                                      independientes.

  INV-PAY-03                          Pérdida posterior a reconocimiento
                                      válido no restaura deuda del
                                      Prestatario.

  INV-PAY-04                          Transferencia reportada no afecta
                                      deuda hasta ser verificada.

  INV-FON-01                          Toda variación del Fondo proviene
                                      de operación trazable; no se edita
                                      saldo.

  INV-FON-02                          Movimiento interno de custodia del
                                      mismo Fondo no es ingreso ni gasto.

  INV-FON-03                          Dinero pendiente de entrega por
                                      Colaborador no es disponible.

  INV-FON-04                          Disponible, cartera, patrimonio e
                                      ingreso no son equivalentes.

  INV-HIS-01                          Cortes formales son snapshots
                                      históricos inmutables.

  INV-HIS-02                          Evidencia histórica y versiones se
                                      preservan.

  INV-DOC-01                          Liquidación financiera no equivale
                                      a cierre documental.

  INV-AUT-01                          Administración técnica no equivale
                                      a autoridad financiera.

  INV-AUT-02                          Acción protegida considera
                                      identidad + función/rol + alcance +
                                      permiso + vigencia + recurso.

  INV-AUT-03                          Acceso depende de permisos/alcance,
                                      no de quién creó el registro.

  INV-AUT-04                          Admin no tiene acceso automático a
                                      documentos sensibles.
  -----------------------------------------------------------------------

## 20. Architecture Drivers y NFR

### 20.1 Integridad, consistencia y disponibilidad

-   Integridad financiera \> throughput.

-   Transacciones ACID y consistencia fuerte para efectos esenciales.

-   Idempotencia y Operation ID en operaciones críticas.

-   Resultado desconocido por timeout se resuelve por Operation
    ID/idempotencia; no mediante reintento ciego.

-   RPO ≤ 1 hora; RTO ≤ 8 horas.

-   Backups automáticos, verificables y restaurables; pruebas de
    restore.

### 20.2 Seguridad

-   Cuentas individuales; no cuentas compartidas.

-   MFA obligatorio en MVP para Admin, Encargado General y Responsables
    de Comisión.

-   Sesiones revocables; reautenticación para acciones críticas.

-   Autorización en backend y a nivel de objeto.

-   Mínimo privilegio y deny by default.

-   Secretos fuera de Git.

-   Documentos privados; sin URLs públicas permanentes.

### 20.3 UX y operación

-   Objetivo normal de interacción alrededor de ≤2s, no garantía
    absoluta.

-   Estados explícitos de loading/success/failure/unknown.

-   Responsive Web, navegadores modernos, accesibilidad básica, español
    en MVP.

-   Online-first. Sin operación financiera offline en MVP; contingencia
    manual cuando no hay conectividad.

### 20.4 Ingeniería

-   DEV / VALIDATION / PROD separados.

-   Migraciones y despliegues reproducibles/versionados.

-   Pruebas automatizadas de reglas críticas.

-   Observabilidad con errores estructurados, correlation/operation IDs,
    health checks y monitoring.

-   Jobs observables, reintentables e idempotentes cuando corresponda.

## 21. Arquitectura Objetivo V1

### 21.1 Forma general

  -----------------------------------------------------------------------
  ARQUITECTURA APROBADA`<br>`{=html}Monolito modular. Laravel como
  backend/API y autoridad de negocio/finanzas. PostgreSQL como fuente
  transaccional estructurada. Web responsive completo como cliente
  principal. Flutter como cliente móvil enfocado. Infraestructura central
  en Internet; sin servidor local obligatorio.
  -----------------------------------------------------------------------

  -----------------------------------------------------------------------

### 21.2 Capas

-   Presentation → Application → Domain → Infrastructure, aplicadas de
    forma pragmática.

-   Controllers delgados; casos de uso explícitos.

-   Reglas críticas del dominio independientes de HTTP/UI.

-   Módulos colaboran mediante contratos/casos de uso; no mediante
    mutación arbitraria de tablas ajenas.

-   Shared Kernel mínimo.

### 21.3 Datos y documentos

-   Una instancia PostgreSQL por instalación/comunidad.

-   Propiedad lógica de datos por módulos.

-   Documentos binarios fuera de PostgreSQL normalmente; en BD:
    metadata, versión, hash y referencia de storage.

-   Historial financiero no destructivo.

-   Tiempos explícitos: efectivo, registro, confirmación y vigencia
    cuando correspondan.

-   Clock controlable/testable para reglas temporales.

### 21.4 Procesamiento secundario

-   Efectos obligatorios críticos dentro de la transacción.

-   Jobs sólo después del commit para trabajo secundario.

-   Tecnología concreta de queue permanece abierta.

### 21.5 No se adopta

-   Microservicios, Kubernetes, Event Sourcing o CQRS distribuido como
    arquitectura inicial.

## 22. ADR V1 --- decisiones de arquitectura aceptadas

  -----------------------------------------------------------------------
  ADR                                 Decisión
  ----------------------------------- -----------------------------------
  ADR-001                             Monolito modular.

  ADR-002                             Laravel como backend.

  ADR-003                             PostgreSQL como fuente oficial
                                      estructurada/transaccional.

  ADR-004                             Documentos fuera de PostgreSQL
                                      normalmente.

  ADR-005                             Backend como autoridad financiera.

  ADR-006                             ACID + concurrencia + idempotencia.

  ADR-007                             Rectificación financiera no
                                      destructiva; no Event Sourcing.

  ADR-008                             Autorización contextual en backend.

  ADR-009                             Web responsive completo + Flutter
                                      enfocado.

  ADR-010                             Online-first; sin operación
                                      financiera offline.

  ADR-011                             Jobs secundarios después del
                                      commit.

  ADR-012                             DEV/VALIDATION/PROD y
                                      despliegues/migraciones
                                      versionados.

  ADR-013                             Backup/recovery integrado con RPO
                                      ≤1h y RTO ≤8h.

  ADR-014                             Separación de historia de negocio,
                                      auditoría de seguridad, logs y
                                      métricas.

  ADR-015                             Configuración histórica y
                                      separación entre autoridad de
                                      negocio y administración técnica.
  -----------------------------------------------------------------------

## 23. Seguridad, privacidad y protección de información

-   Persona y Usuario son conceptos separados.

-   Contraseñas con hash; nunca texto plano, reversible, logs o Git.

-   Recuperación de cuenta/MFA controlada; no recuperación de contraseña
    antigua.

-   Permisos sensibles separados: ver, descargar, cargar/actualizar,
    rectificar, custodiar.

-   Acceso y descarga de información sensible deben ser trazables.

-   Uploads validados más allá de extensión/nombre/content-type del
    cliente.

-   Minimización de datos en pantallas, exportaciones, logs y ambientes
    no productivos.

-   DEV usa datos sintéticos normalmente; VALIDATION no es clon
    automático de PROD.

-   No enviar PII indiscriminadamente a IA.

-   Mass assignment protegido; estados de dominio no se modifican con
    patch genérico.

-   Transporte protegido en producción; backups protegidos; restore
    privilegiado y auditado.

-   Política definitiva de retención/base legal antes de producción.

## 24. Riesgos V1

  ---------------------------------------------------------------------------------------
  ID                      Riesgo                       Control principal
  ----------------------- ---------------------------- ----------------------------------
  RISK-01                 Operación financiera crítica ACID, idempotencia, Operation ID,
                          queda parcialmente aplicada. efectos secundarios post-commit.

  RISK-02                 Confusión                    Separación explícita de estados e
                          deuda/custodia/disponible.   indicadores.

  RISK-03                 Pérdida en custodia restaura INV-PAY-03 + incidente interno.
                          deuda incorrectamente.       

  RISK-04                 Acceso indebido a datos      Autorización
                          sensibles.                   contextual/object-level, pruebas
                                                       de permisos.

  RISK-05                 Existen backups pero restore Restore probado y evidencia.
                          no funciona.                 

  RISK-06                 Cambio de política altera    Configuración versionada/vigente y
                          préstamos históricos.        freeze por préstamo.

  RISK-07                 Dependencia operacional de   Documentación, capacitación y
                          una persona.                 handoff.

  RISK-08                 Interpretación jurídica      Revisión legal previa a
                          incorrecta.                  producción.

  RISK-09                 Scope creep silencioso.      MVP congelado + CR.

  RISK-10                 Errores humanos de captura.  Validaciones, confirmaciones y
                                                       rectificación.

  RISK-11                 Operaciones retroactivas mal Fecha
                          interpretadas.               efectiva/registro/confirmación +
                                                       motivo/evidencia.

  RISK-12                 Lock-in innecesario.         Decisiones tecnológicas
                                                       justificadas por drivers.

  RISK-13                 Cliente móvil antiguo        Versionado/compatibilidad
                          incompatible.                controlada.

  RISK-14                 Crecimiento documental.      Storage privado y política de
                                                       ciclo de vida.

  RISK-15                 Cambio de responsable        Periodos y handoff históricos.
                          reescribe historia.          

  RISK-16                 Dos fuentes oficiales        Corte y fuente oficial explícitos.
                          durante Go-Live.             

  RISK-17                 Migración fabrica historia.  Clasificar datos
                                                       verificados/apertura/historia
                                                       incompleta.

  RISK-18                 IA cambia decisiones sin     KB CURRENT + protocolo IA + CR.
                          autoridad.                   
  ---------------------------------------------------------------------------------------

Las etiquetas de severidad CRÍTICO/ALTO/MEDIO, si aparecen en artefactos
previos, son orientativas mientras no exista una metodología
cuantitativa formal.

## 25. Gates de Go-Live

  -----------------------------------------------------------------------
  Gate                                Condición
  ----------------------------------- -----------------------------------
  GO-LIVE-01                          Restore probado/demostrado,
                                      coherente para PostgreSQL +
                                      documentos + configuración; RPO
                                      ≤1h, RTO ≤8h.

  GO-LIVE-02                          Reglas/invariantes financieros
                                      críticos probados en backend y
                                      persistencia, no sólo UI.

  GO-LIVE-03                          Permisos sensibles, object
                                      authorization, scopes, MFA
                                      privilegiado y documentos privados
                                      probados.

  GO-LIVE-04                          Procesos/documentos con efecto
                                      legal revisados antes de
                                      producción.

  GO-LIVE-05                          Migración/apertura reconciliada y
                                      aprobada; fuente oficial y fecha de
                                      corte claras; sin historia
                                      fabricada.
  -----------------------------------------------------------------------

Además, privacidad/retención/base legal, infraestructura productiva,
storage privado, backups, monitoring, secretos, cuentas institucionales,
contingencia, capacitación y soporte son condiciones de preparación para
producción.

## 26. Decisiones abiertas de implementación

Estos puntos NO reabren el Baseline. Deben resolverse durante el Plan de
Construcción o la etapa técnica correspondiente sin contradecir
decisiones superiores:

-   Tecnología concreta de UI Web dentro del ecosistema Laravel.

-   Implementación concreta de autenticación y MFA.

-   Mecanismo de queue/jobs.

-   Proveedor/tecnología de object storage.

-   Convención de identificadores técnicos.

-   Precisión física exacta de columnas decimal en PostgreSQL.

-   Estrategia concreta de zona horaria y Clock.

-   Proveedor Git y flujo CI/CD.

-   Versionado de API.

-   Canales de alertas/monitoring.

-   Timeout de sesión.

-   Proveedor cloud/hosting.

-   Cadencia/retención concreta de backups y pruebas de restore,
    respetando RPO/RTO.

## 27. Production blockers / readiness

-   Revisión legal de pagaré, avales, cancelaciones y garantías.

-   Política definitiva de privacidad, retención y base legal.

-   Checklist documental inicial.

-   Monto máximo y política financiera inicial configurados.

-   Configuración institucional y folios iniciales.

-   Infraestructura de producción.

-   Storage privado de producción.

-   MFA para roles privilegiados.

-   Backups automáticos que satisfagan RPO.

-   Recuperación que satisfaga RTO.

-   Restore probado.

-   Pruebas de autorización/documentos sensibles.

-   Pruebas financieras críticas.

-   Migración/apertura reconciliada.

-   Procedimiento de contingencia.

-   Capacitación y handoff operativo.

## 28. Protocolo obligatorio para IA y desarrollo

### 28.1 Antes de implementar

1.  Identificar el caso de uso y las reglas aplicables.

2.  Identificar invariantes relacionados.

3.  Identificar ADR/NFR/seguridad afectados.

4.  Confirmar si está dentro de MVP o POST-MVP.

5.  Identificar riesgos y pruebas necesarias.

6.  Si existe ambigüedad que afecte dinero, historia, permisos,
    privacidad, arquitectura o alcance: detenerse y escalar.

### 28.2 Durante la implementación

-   No diseñar CRUD primero y después intentar encajar el dominio.

-   No confiar en frontend para autorización o reglas críticas.

-   No usar SQL directo como mecanismo normal de corrección financiera.

-   No introducir dependencias o patrones por moda.

-   No convertir TODOs en sustitutos de requisitos críticos.

-   No cambiar estados mediante endpoints genéricos sin caso de uso.

-   Separar efectos obligatorios de efectos secundarios.

-   Proteger concurrencia e idempotencia donde exista dinero, folios o
    cambios de estado sensibles.

### 28.3 Después de implementar

1.  Ejecutar pruebas positivas, negativas, invariantes, autorización,
    concurrencia y fallos según aplique.

2.  Actualizar trazabilidad Regla → Caso de uso → Implementación → Test
    → Evidencia.

3.  Documentar cualquier decisión técnica relevante.

4.  No declarar PRODUCTION-READY sólo porque el código compila o el
    feature funciona en UI.

## 29. Trazabilidad maestra

La trazabilidad esperada es bidireccional: Necesidad → Regla/Decisión →
MVP → Módulo → Invariante/ADR → Riesgo → Implementación → Test →
Evidencia. La Matriz Maestra usa capacidades auxiliares C-01...C-13
únicamente para organización, no como nuevo alcance.

  Capacidad   Área
  ----------- ------------------------------
  C-01        Identidad y organización
  C-02        Autoridad
  C-03        Fondos
  C-04        Custodia
  C-05        Préstamos
  C-06        Pagos
  C-07        Documentos
  C-08        Actividades
  C-09        Cobranza
  C-10        Informes
  C-11        Auditoría
  C-12        Autoservicio del Prestatario
  C-13        Continuidad operativa

Cobertura de requisitos no equivale a code coverage. Un requisito
crítico debe tener prueba/evidencia aunque el porcentaje global de
cobertura sea alto.

## 30. Control de cambios y versionado

### 30.1 Flujo maestro

PROPOSE → CLASSIFY → IMPACT → DECIDE → VERSION → IMPLEMENT → TEST →
UPDATE TRACEABILITY → DEPLOY.

### 30.2 Change Request mínimo

-   ID, título, estado, motivo, situación actual y cambio propuesto.

-   Justificación y elementos afectados.

-   Impacto en negocio, datos, historia, seguridad, privacidad,
    arquitectura, clientes, riesgos y pruebas.

-   Decisión y responsables.

-   Migración, compatibilidad, transición y rollback cuando corresponda.

### 30.3 Versiones distintas

Versión de KB, release de aplicación, versión de API, versión de esquema
y versión de documentos de negocio son conceptos distintos y no deben
confundirse.

## 31. Documentación histórica y superseded

Todo documento anterior que contradiga KB V1.0 CURRENT debe conservarse
como HISTORICAL / SUPERSEDED, no eliminarse. Esto incluye especialmente
artefactos que contemplen servidor local, operación financiera offline,
sincronización offline-first, arquitectura distribuida previa o planes
de construcción basados en un MVP anterior.

-   No mezclar KB CURRENT con documentos SUPERSEDED para crear una
    tercera interpretación.

-   Planes de construcción anteriores no son el Plan de Construcción V1
    vigente.

-   La historia se conserva para comprender evolución, no para redefinir
    el presente.

## 32. Resultado de regresión final

  Control                                                         Resultado
  --------------------------------------------------------------- ----------------------------
  Contradicciones materiales vigentes                             0
  Decisiones de negocio sin resolver que bloqueen planificación   0
  Invariantes                                                     20/20 consistentes
  ADRs                                                            15/15 consistentes
  MVP                                                             14/14 paquetes preservados
  POST-MVP infiltrado en MVP                                      0 detectado
  Riesgos iniciales                                               18 preservados
  Go-Live gates                                                   5 preservados
  Cambios de arquitectura requeridos                              0
  Reabrir Discovery                                               NO
  Reabrir Baseline                                                NO
  Final Regression                                                PASS

## 33. Handoff para iniciar la construcción

  -----------------------------------------------------------------------
  ESTADO DE HANDOFF`<br>`{=html}El descubrimiento y la definición
  normativa están suficientemente cerrados para elaborar el Plan de
  Construcción V1. No existen decisiones de negocio pendientes conocidas
  que bloqueen la planificación.
  -----------------------------------------------------------------------

  -----------------------------------------------------------------------

### 33.1 Próxima secuencia oficial

BASELINE V1.0 APROBADO + KB V1.0 CURRENT → PLAN DE CONSTRUCCIÓN V1 →
ETAPA 1 REPOSITORIO Y ENTORNO → etapas de implementación.

### 33.2 Qué debe producir el Plan de Construcción V1

-   Orden de implementación por dependencias y riesgo.

-   Objetivo, entradas, trabajo, entregables, pruebas, riesgos,
    criterios de aceptación y gate por etapa.

-   Mapeo explícito a MVP, invariantes, ADRs y riesgos.

-   Decisiones técnicas que deben cerrarse antes de cada etapa.

-   Estrategia de migraciones, CI/CD, ambientes y datos iniciales.

-   Definition of Done y evidencia esperada.

### 33.3 Qué NO debe hacer el Plan

-   Redefinir reglas aprobadas.

-   Cambiar arquitectura sin CR.

-   Introducir POST-MVP para "dejarlo listo".

-   Inventar permisos o autoridad.

-   Reducir controles financieros por acelerar la entrega.

## 34. Prompt de arranque para otra IA o equipo

El siguiente texto puede usarse como instrucción inicial junto con este
documento:

  -----------------------------------------------------------------------
  INSTRUCCIÓN DE ARRANQUE`<br>`{=html}Usa "Sistema de Gestión Comunitaria
  --- Knowledge Base V1.0 CURRENT" como fuente normativa del proyecto. No
  modifiques silenciosamente reglas de negocio, MVP, invariantes, ADRs ni
  arquitectura. Antes de proponer implementación, identifica caso de uso,
  reglas, invariantes, ADRs, riesgos y pruebas aplicables. Si detectas
  contradicción o ambigüedad que afecte dinero, historia, seguridad,
  privacidad, autoridad, datos o alcance, detente y solicita resolución.
  No implementes capacidades POST-MVP. El siguiente objetivo es
  elaborar/seguir el Plan de Construcción V1 derivado de esta KB.
  -----------------------------------------------------------------------

  -----------------------------------------------------------------------

## 35. Changelog de Knowledge Base V1.0

-   Consolidación de fundamentos, glosario, actores y modelo
    organizacional.

-   Consolidación de modelo financiero, préstamos, pagos, custodia,
    cooperaciones y comisiones.

-   Consolidación de reglas E2E, mapa funcional, MVP y frontera
    POST-MVP.

-   Consolidación de 20 invariantes y 15 ADRs.

-   Consolidación de Architecture Drivers, NFR, Arquitectura Objetivo,
    seguridad, privacidad, riesgos y Go-Live.

-   Consolidación de trazabilidad, protocolo IA y control de cambios.

-   Cierre explícito de autoridad para ciclo anual de cooperaciones.

-   Cierre de sobrepago, devolución y conversión voluntaria a donación.

-   Cierre de ROUND_HALF_UP y regla de aniversarios mensuales + días/30.

-   Separación explícita entre cancelación documental, rectificación
    financiera y cancelación compuesta de negocio.

-   Clasificación de documentos previos incompatibles como HISTORICAL /
    SUPERSEDED.

-   Regresión final PASS y declaración KB V1.0 = APROBADA / CURRENT.

FIN DE LA FUENTE CANÓNICA V1.0 Cualquier cambio material posterior debe
gestionarse mediante Change Request y nueva versión de Knowledge Base.
