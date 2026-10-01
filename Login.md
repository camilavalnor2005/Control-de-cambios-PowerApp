Descripción
Este código se ejecuta al presionar el botón "Enviar" dentro de la aplicación de Control de Cambios.

Su función es:

Guardar la solicitud capturada en el formulario.
Iniciar el flujo de aprobación en Power Automate.
Mostrar un mensaje de confirmación al usuario.
Código Power Apps
SubmitForm(Form2);

'PowerAppV2->Startandwaitforanapproval,Condition,Sendanemai...'
.Run(Form2.LastSubmit.ID);

Notify(
    "Solicitud enviada correctamente",
    NotificationType.Success
)
Explicación
SubmitForm(Form2)
Guarda la información capturada en el formulario.

Run(Form2.LastSubmit.ID)
Ejecuta el flujo de Power Automate utilizando el ID del registro recién creado.

Notify()
Muestra una notificación indicando que la solicitud fue enviada correctamente.
