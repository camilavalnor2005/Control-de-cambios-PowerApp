# Código de la aplicación

Fórmulas de Power Fx de la aplicación, organizadas por pantalla. Cada archivo sigue el mismo formato: **descripción**, **código** y **explicación**.

| Archivo | Pantalla |
|---|---|
| [01-inicio.md](01-inicio.md) | Inicio (`scrHome`) |
| [02-solicitud-nueva.md](02-solicitud-nueva.md) | Solicitud nueva (`scrNuevoCambio`) |
| [03-registro-de-cambios.md](03-registro-de-cambios.md) | Registro de cambios (`srcVerCambios`) |
| [04-detalle-de-cambio.md](04-detalle-de-cambio.md) | Detalle de cambio (`scrDetalleCambio`) |
| [05-dashboard.md](05-dashboard.md) | Dashboard (`srcDeshboard`) |

El flujo de Power Automate se documenta en [docs/04-flujo-de-aprobacion.md](../docs/04-flujo-de-aprobacion.md).

## Nombres usados en el código

| Elemento | Nombre |
|---|---|
| Pantalla de inicio | `scrHome` |
| Pantalla de solicitud nueva | `scrNuevoCambio` |
| Pantalla de registro de cambios | `srcVerCambios` |
| Pantalla de detalle | `scrDetalleCambio` |
| Pantalla de dashboard | `srcDeshboard` |
| Formulario de solicitud nueva | `Form2` |
| Galería del registro de cambios | `galCambios` |
| Buscador del registro de cambios | `txtBuscar` |
| Formulario del detalle | `frmDetalle` |
| Lista de SharePoint | `'Control de cambios'` |
| Flujo de aprobación | `'PowerAppV2->Startandwaitforanapproval,Condition,Sendanemai...'` |

## Notas

- Los nombres de columnas son los de la lista de SharePoint (por ejemplo `'Tipo de cambio'` o `'Fecha limite'`). Cuando un nombre tiene espacios, va entre comillas simples.
- En las columnas de tipo **Opción** se usa `.Value` para leer el texto (por ejemplo `Estatus.Value`).
- El nombre del flujo se muestra recortado con `...`; en la app aparece completo.
