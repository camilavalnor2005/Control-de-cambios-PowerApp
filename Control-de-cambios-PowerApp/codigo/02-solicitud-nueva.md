# Pantalla Solicitud nueva (`scrNuevoCambio`)

![Solicitud capturada](../capturas/05-solicitud-capturada.png)

## Descripción

Formulario (`Form2`) para registrar una solicitud de cambio en la lista de SharePoint. El botón **Enviar** guarda la solicitud, inicia el flujo de aprobación y muestra un mensaje de confirmación.

## Código Power Apps

### Formulario `Form2`

```powerfx
// DataSource
'Control de cambios'

// DefaultMode
FormMode.New
```

**Form2 → OnSuccess** (se ejecuta cuando la solicitud se guardó bien)

```powerfx
Notify(
    "Cambio registrado correctamente",
    NotificationType.Success
);
NewForm(Form2)
```

### Etiqueta del folio → Text

```powerfx
"Folio: se genera al enviar"
```

### Listas desplegables → Items

```powerfx
// Area
Choices([@'Control de cambios'].Area)

// Tipo de cambio
Choices([@'Control de cambios'].'Tipo de cambio')

// Prioridad
Choices([@'Control de cambios'].Prioridad)
```

### Botón "Enviar" → OnSelect

Este código se ejecuta al presionar el botón **Enviar**. Su función es:

- Guardar la solicitud capturada en el formulario.
- Iniciar el flujo de aprobación en Power Automate.
- Mostrar un mensaje de confirmación al usuario.

```powerfx
SubmitForm(Form2);

'PowerAppV2->Startandwaitforanapproval,Condition,Sendanemai...'
.Run(Form2.LastSubmit.ID);

Notify(
    "Solicitud enviada correctamente",
    NotificationType.Success
)
```

### Flecha de regreso → OnSelect

```powerfx
ResetForm(Form2);
Navigate(scrHome, ScreenTransition.Fade)
```

## Explicación

**SubmitForm(Form2)**
Guarda la información capturada en el formulario.

**Run(Form2.LastSubmit.ID)**
Ejecuta el flujo de Power Automate utilizando el ID del registro recién creado.

**Notify()**
Muestra una notificación indicando que la solicitud fue enviada correctamente.

**OnSuccess**
Se ejecuta solo cuando SharePoint confirma que la solicitud se guardó. Muestra el mensaje "Cambio registrado correctamente" y deja el formulario limpio con `NewForm(Form2)`.

**Choices()**
Toma las opciones directamente de las columnas de la lista de SharePoint. Si se agrega una nueva área o un nuevo tipo de cambio en la lista, aparece en la app sin modificar el código.

**ResetForm(Form2)**
Borra lo que se haya capturado si el usuario sale de la pantalla sin enviar.

## Mejora sugerida

Si el guardado falla (por ejemplo, porque falta un dato obligatorio), el código actual de todos modos inicia el flujo y muestra "Solicitud enviada correctamente". Para evitarlo, el flujo se puede llamar desde `OnSuccess`, que solo se ejecuta cuando la solicitud sí se guardó:

```powerfx
// Botón "Enviar" → OnSelect
SubmitForm(Form2)

// Form2 → OnSuccess
'PowerAppV2->Startandwaitforanapproval,Condition,Sendanemai...'
.Run(Form2.LastSubmit.ID);
Notify(
    "Solicitud enviada correctamente",
    NotificationType.Success
);
NewForm(Form2)

// Form2 → OnFailure
Notify(
    "No se pudo guardar la solicitud. Revisa los campos e intenta de nuevo.",
    NotificationType.Error
)
```
