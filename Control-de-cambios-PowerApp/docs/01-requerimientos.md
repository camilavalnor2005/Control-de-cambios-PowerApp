# Requerimientos del sistema

Requerimientos definidos en la Fase 1 del proyecto y su avance en la versión actual de la aplicación.

**Avance:** ✅ Cubierto · 🔄 Cubierto en parte · ⏳ Pendiente

## Requerimientos funcionales

### 1. Gestión de usuarios

| Requerimiento | Avance | Cómo se cubre |
|---|:---:|---|
| Registrar y administrar usuarios autorizados (solicitantes, responsables, aprobadores y administrador) | ⏳ | — |
| Crear, editar y desactivar perfiles de usuario | ⏳ | — |
| Gestionar roles y permisos según el flujo de control de cambios | ⏳ | — |
| Autenticación mediante credenciales corporativas | ✅ | La app se abre con la cuenta de Microsoft 365 de la empresa. |

### 2. Gestión de cambios

| Requerimiento | Avance | Cómo se cubre |
|---|:---:|---|
| Registrar solicitudes de cambio | ✅ | Pantalla **Solicitud nueva**. |
| Modificar y actualizar registros de cambios | ⏳ | El detalle es de solo lectura. |
| Clasificar cambios por categoría, área o tipo | ✅ | Campos **Área** y **Tipo de cambio**. |
| Asignar responsables y fechas compromiso | 🔄 | Se captura la **Fecha límite**; falta asignar un responsable. |

### 3. Seguimiento de cambios

| Requerimiento | Avance | Cómo se cubre |
|---|:---:|---|
| Registrar historial de modificaciones y comentarios | 🔄 | Se guardan los **Comentarios de aprobación** de cada solicitud. |
| Dar seguimiento al estatus del cambio | ✅ | Campo **Estatus** en la pantalla **Detalle de cambio**. |
| Clasificar cambios por prioridad e impacto | 🔄 | Se clasifica por **Prioridad** (Baja, Media, Alta); falta el campo de impacto. |
| Almacenar evidencia y documentación relacionada | ✅ | Campo **Agregar imagen**. |

### 4. Aprobaciones

| Requerimiento | Avance | Cómo se cubre |
|---|:---:|---|
| Gestionar flujo de aprobación digital | ✅ | Flujo de Power Automate con aprobación en Teams. |
| Registrar autorizaciones y rechazos | ✅ | El flujo guarda **Aprobado** o **Rechazado** en la solicitud. |
| Generar evidencias de aprobación | ✅ | La decisión y los comentarios del gerente quedan guardados en la solicitud. |
| Controlar estados del proceso | ✅ | Estatus vacío (pendiente), Aprobado o Rechazado. |

### 5. Notificaciones

| Requerimiento | Avance | Cómo se cubre |
|---|:---:|---|
| Enviar correos automáticos sobre nuevos cambios | ✅ | El gerente recibe la solicitud de aprobación en Teams y por correo. |
| Enviar recordatorios de aprobación y vencimientos | ⏳ | — |
| Notificar cambios de estado | ✅ | El flujo envía un correo con el resultado. |

### 6. Control y monitoreo

| Requerimiento | Avance | Cómo se cubre |
|---|:---:|---|
| Registrar avances y cierre de cambios | ⏳ | — |
| Capturar observaciones y acciones correctivas | ⏳ | — |

### 7. Reportes y análisis

| Requerimiento | Avance | Cómo se cubre |
|---|:---:|---|
| Generar reportes de cambios registrados | 🔄 | Pantalla **Registro de cambios** con búsqueda por folio o área. |
| Mostrar estadísticas por área, responsable y estatus | 🔄 | Pantalla **Dashboard** creada; falta conectar las gráficas a los datos. |
| Visualizar indicadores mediante dashboards | 🔄 | Indicadores de total, pendientes y cerrados (en desarrollo). |

### 8. Integración

| Requerimiento | Avance | Cómo se cubre |
|---|:---:|---|
| Exportar información a Excel y PDF | 🔄 | La lista de SharePoint se puede exportar a Excel; falta la exportación a PDF. |
| Integración con SharePoint y Microsoft 365 | ✅ | Datos en SharePoint, aprobaciones en Teams y correos con Outlook. |

## Requerimientos no funcionales

| Requerimiento | Cómo se atiende |
|---|---|
| **Rendimiento:** respuesta menor a 3 segundos y varios usuarios al mismo tiempo | La app consulta directamente la lista de SharePoint y Power Apps permite que varios usuarios la usen a la vez. |
| **Seguridad:** acceso por roles y protección de la información | El acceso requiere la cuenta corporativa y los permisos se controlan desde Microsoft 365 (app y lista de SharePoint). |
| **Disponibilidad:** mínimo 99.5 % y recuperación ante fallos | La solución funciona sobre los servicios en la nube de Microsoft 365. |
| **Usabilidad:** interfaz intuitiva y compatible con móvil y computadora | Botones grandes, listas desplegables y calendarios. Se puede abrir desde el navegador o desde la app de Power Apps. |
| **Escalabilidad:** agregar tipos de cambio y usuarios sin afectar el desempeño | Las áreas, tipos de cambio y prioridades se toman de la lista de SharePoint, así que se pueden agregar opciones sin modificar la app. |
| **Mantenibilidad:** código y flujos documentados | Este repositorio documenta las pantallas, el código y el flujo. |
| **Compatibilidad:** Edge, Chrome, Firefox y Safari en Windows, macOS y Linux | Power Apps funciona en navegadores modernos. |
| **Confiabilidad:** integridad y trazabilidad de los cambios | Cada solicitud tiene un folio único y su estatus queda registrado. |
