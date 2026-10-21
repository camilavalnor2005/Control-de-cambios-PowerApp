# Pantalla Detalle de cambio (`scrDetalleCambio`)

![Detalle de cambio](../capturas/08-detalle-de-cambio.png)

## Descripción

Formulario de solo lectura (`frmDetalle`) que muestra todos los datos de la solicitud elegida en el registro de cambios, incluidos el **Estatus** y los **Comentarios de aprobacion** que guarda el flujo de Power Automate.

## Código Power Apps

### Formulario `frmDetalle`

```powerfx
// DataSource
'Control de cambios'

// Item
galCambios.Selected

// DefaultMode
FormMode.View
```

### Botón "Regresar" y flecha de regreso → OnSelect

```powerfx
Back()
```

## Explicación

**Item: galCambios.Selected**
El formulario muestra la solicitud que el usuario tocó en la galería de la pantalla anterior.

**FormMode.View**
Muestra los datos sin permitir modificarlos, para que el detalle sirva solo como consulta.

**Back()**
Regresa a la pantalla anterior, en este caso el registro de cambios.

## Mejoras sugeridas

**Mostrar el folio en el encabezado.** Cambiar la propiedad *Text* del título por:

```powerfx
"DETALLE DE CAMBIO · Folio " & galCambios.Selected.ID
```

**Mostrar la máquina.** El campo **Maquina** se captura en la solicitud, pero no aparece en el detalle. Se puede agregar desde la opción *Editar campos* del formulario.
