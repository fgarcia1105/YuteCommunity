# Instrucciones para trabajar en el backend

## Fuentes del proyecto

Leer antes de realizar cambios:
- docs/knowledge-base/Sistema_Gestion_Comunitaria_Knowledge_Base_V1.0_CURRENT.md
- docs/planificacion/Sistema_Gestion_Comunitaria_Plan_Construccion_V1_PROPUESTA.md
- docs/decisiones/DT-01-DT-08.md
- docs/entorno/seguimiento-e1.md

Las rutas anteriores parten de la raíz del repositorio.
El Plan tiene estado APROBADO aunque su nombre conserve PROPUESTA.

La KB CURRENT es la fuente canónica del proyecto.
No inventar ni modificar reglas, invariantes, ADR, arquitectura o alcance.
Ante una ambigüedad material, documentarla y detener el componente afectado.

## Entorno de ejecución

PHP y Composer se ejecutan mediante el servicio php de Docker Compose.
Node se ejecuta mediante compose.node.yaml.
Consultar las versiones e imágenes fijadas en los archivos del repositorio.

Ejecutar desde la raíz del repositorio:

    sudo docker compose --env-file .env.docker run --rm --no-deps php php --version
    sudo docker compose --env-file .env.docker run --rm --no-deps php composer --working-dir=backend --version

El uso de sudo corresponde al equipo Debian de desarrollo de Fer.
No instalar PHP o Composer en el host por no encontrarlos en su PATH.
Laravel Boost no forma parte del entorno seleccionado; su incorporación
requiere una decisión técnica documentada.

## Trabajo y validación

Trabajar en una rama y revisar los cambios mediante pull request.
Usar los archivos lock para reproducir las dependencias.
Consultar el pipeline para conocer las comprobaciones existentes.
No declarar una prueba ejecutada sin evidencia.

No versionar secretos ni mostrar el contenido de archivos .env privados.
Ejecutar pruebas de migración o reconstrucción únicamente sobre una
base identificada y aislada para validación.

El scaffold no define los roles, permisos ni reglas del dominio.
E1 continúa abierta hasta acreditar los criterios G-E1 del Plan.
