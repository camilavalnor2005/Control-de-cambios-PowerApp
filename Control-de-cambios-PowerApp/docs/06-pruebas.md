# Pruebas realizadas

Pruebas funcionales hechas sobre la aplicación en Power Apps. La evidencia de cada prueba está en la carpeta [capturas](../capturas/).

**Resultado:** ✅ Correcto · 🔄 Funciona en parte

## Datos de prueba

| Campo | Valor capturado |
|---|---|
| Fecha | 8/27/2026 |
| Area | BRAZING |
| Maquina | AL-040 |
| Solicitante | Camila 3022 |
| Numero de empleado | 3022649 |
| Descripcion del cambio | Cambio de herramental |
| Tipo de cambio | Modificacion de herramental |
| Prioridad | Media |
| Fecha limite | 8/28/2026 |
| Requiere aprobacion | Sí |

## Casos de prueba

| # | Prueba | Pasos | Resultado esperado | Resultado | Evidencia |
|:---:|---|---|---|:---:|---|
| P-01 | Pantalla de inicio | Abrir la aplicación | Se muestran el título, el nombre de la planta y los botones Dashboard, Registro de cambios y Nuevo cambio | ✅ | [01-inicio](../capturas/01-inicio.png) |
| P-02 | Abrir formulario | Presionar **Nuevo cambio** | Se abre la solicitud vacía y el folio indica que se genera al enviar | ✅ | [02-solicitud-nueva](../capturas/02-solicitud-nueva.png) |
| P-03 | Listas desplegables | Abrir las listas de Area, Tipo de cambio y Prioridad | Cada lista muestra sus opciones (9 tipos de cambio y 3 prioridades) | ✅ | [03-tipos-de-cambio](../capturas/03-tipos-de-cambio.png), [04-prioridad](../capturas/04-prioridad.png) |
| P-04 | Calendarios | Elegir Fecha y Fecha limite con el calendario | Las fechas se cargan en el formulario | ✅ | [05-solicitud-capturada](../capturas/05-solicitud-capturada.png) |
| P-05 | Captura completa | Llenar todos los campos con los datos de prueba | Todos los campos aceptan la información | ✅ | [05-solicitud-capturada](../capturas/05-solicitud-capturada.png) |
| P-06 | Enviar solicitud | Presionar **Enviar** | Aparece "Cambio registrado correctamente", el formulario se limpia y después aparece "Solicitud enviada correctamente" | ✅ | [06-confirmacion](../capturas/06-confirmacion.png) |
| P-07 | Registro de cambios | Presionar **Registro de cambios** | Se muestra la lista de solicitudes con folio, fecha e imagen | ✅ | [07-registro-de-cambios](../capturas/07-registro-de-cambios.png) |
| P-08 | Detalle de cambio | Presionar la flecha del folio 20 | Se muestran todos los datos de la solicitud | ✅ | [08-detalle-de-cambio](../capturas/08-detalle-de-cambio.png) |
| P-09 | Resultado de la aprobación | Revisar el detalle de una solicitud ya respondida | El estatus (Rechazado) y el comentario del gerente aparecen en la solicitud | ✅ | [08-detalle-de-cambio](../capturas/08-detalle-de-cambio.png) |
| P-10 | Solicitud pendiente | Revisar el detalle de una solicitud sin respuesta | El estatus aparece vacío | ✅ | — |
| P-11 | Navegación | Usar el botón Regresar, la flecha y la casa | Cada botón lleva a la pantalla correcta | ✅ | — |
| P-12 | Dashboard | Presionar **Dashboard** | Se abre la pantalla de indicadores; las gráficas aún no muestran los datos de la lista | 🔄 | [09-dashboard](../capturas/09-dashboard.png) |

## Pendientes detectados

- Conectar las gráficas del dashboard a la lista de SharePoint ([código](../codigo/05-dashboard.md)).
- Mostrar el folio y la máquina en la pantalla **Detalle de cambio**.
