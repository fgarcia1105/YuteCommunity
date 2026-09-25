# Seguimiento de E1 — Repositorio y Entorno

Fecha: 2026-09-25
Estado: EN CURSO; G-E1 NO CERRADO.

Este registro documenta ejecución. No modifica la KB ni el Plan aprobado.

## Evidencia disponible

- Equipo: Debian 12 amd64, 4 vCPU, 7.7 GiB RAM.
- Responsable de ejecución: Fer; disponibilidad aproximada de 2 h semanales.
- Repositorio: fgarcia1105/YuteCommunity.
- Preparación integrada en main: commit 591ab5d.
- PHP 8.4.25 y Composer 2.10.3 comprobados en el contenedor PHP.
- PostgreSQL 17.11: servicio DEV healthy y consulta PDO SELECT 1 correcta.
- Laravel 13.33.0: versión y requisitos de plataforma comprobados.
- Compilación Web completada; manifest.json generado.
- CI del commit 33eadce: resultado verde confirmado por Fer.
- Main actualizado y árbol limpio después de integrar la preparación.
- .env.docker, backend/.env y backend/vendor/autoload.php:
  exclusión de Git comprobada.

La evidencia procede de salidas de terminal y confirmaciones de Fer
en la conversación. No constituye validación productiva.

## Pendientes para G-E1

- Completar el registro de cierre de DT-01 y DT-08 con evidencia.
- Integrar y verificar Livewire conforme a DT-01.
- Documentar instalación, versiones y comandos reproducibles.
- Preparar validación PostgreSQL aislada de DEV.
- Demostrar migraciones desde esquema vacío en VALIDATION.
- Documentar separación de DEV, VALIDATION y PROD.
- Preparar runbook inicial de migraciones y recuperación.
- Completar EV-01 con reproducción desde copia limpia y enlaces a CI.
- Asignar responsables y puntos de cierre de decisiones dependientes de E2.
- Revisar G-E1 y registrar su aceptación o sus bloqueadores.

La prueba HTTP inicial con SQLite no acredita migraciones,
restricciones ni comportamiento transaccional de PostgreSQL.
