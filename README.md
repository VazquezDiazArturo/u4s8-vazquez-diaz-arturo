# U4S8 — Vazquez Diaz Arturo

## Demo en vivo (producción)
https://u4s8-vazquez-diaz-arturo.onrender.com

## Qué hace este proyecto
Aplicación web desarrollada con Django y MySQL para la gestión integral de un catálogo de servicios. El sistema cuenta con autenticación nativa de usuarios, operaciones CRUD completas (alta, edición con formularios precargados, confirmación previa de borrado y listado), validación personalizada de reglas de negocio en formularios, búsqueda por coincidencias parciales insensible a mayúsculas y paginación fija en el listado.

Todo el acceso a los datos está blindado por usuario: las vistas filtran siempre mediante `request.user` para garantizar aislamiento estricto de la información, protegiendo al sistema contra vulnerabilidades de referencia directa a objetos (IDOR).

## Stack técnico
Django + MySQL (Aiven) + Tailwind CSS + Render

## Cómo se prueba el aislamiento por usuario
Se registran dos cuentas independientes (`usuario_a` y `usuario_b`). Al iniciar sesión como `usuario_b` e intentar acceder manualmente a través de la URL al recurso `/servicios/<id_de_usuario_a>/editar/`, el sistema rechaza la petición respondiendo con un error `404 Not Found` gracias al filtro estricto `get_object_or_404(Servicio, pk=pk, propietario=request.user)`.

## Historial de unidades
- Unidad 1: portafolio estático con HTML5 + Tailwind CSS
- Unidad 2: modelo Servicio conectado y migrado a MySQL en Aiven, deploy dinámico en Render
- Unidad 3: CRUD completo con ModelForms, autenticación nativa y sesiones seguras
- Unidad 4: paginación, búsqueda simple, auditoría de accesibilidad/UX, Release v1.0 y defensa final