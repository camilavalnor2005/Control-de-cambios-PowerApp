# Pantalla Dashboard (`srcDeshboard`)

![Dashboard](../capturas/09-dashboard.png)

## Descripción

Pantalla de indicadores con tres títulos (**Total de cambios**, **Pendientes** y **Cerrados**), una gráfica de columnas y una gráfica circular.

**Estado actual:** la pantalla y las gráficas ya están creadas, pero todavía no leen los datos de la lista de SharePoint (por eso muestran 0). Las fórmulas de esta página sirven para conectarlas.

## Código Power Apps

### Indicadores → Text

```powerfx
// Total de cambios
CountRows('Control de cambios')

// Pendientes (el gerente aún no responde)
CountIf('Control de cambios', IsBlank(Estatus.Value))

// Cerrados (aprobados o rechazados)
CountIf(
    'Control de cambios',
    Estatus.Value = "Aprobado" || Estatus.Value = "Rechazado"
)
```

### Gráfica de columnas → Items (cambios por área)

```powerfx
AddColumns(
    GroupBy(
        AddColumns('Control de cambios', NombreArea, Area.Value),
        NombreArea,
        Registros
    ),
    Total,
    CountRows(Registros)
)
```

En las propiedades de la gráfica se elige **NombreArea** como etiqueta y **Total** como serie.

### Gráfica circular → Items (solicitudes por estatus)

```powerfx
Table(
    { Estado: "Pendientes", Total: CountIf('Control de cambios', IsBlank(Estatus.Value)) },
    { Estado: "Aprobados",  Total: CountIf('Control de cambios', Estatus.Value = "Aprobado") },
    { Estado: "Rechazados", Total: CountIf('Control de cambios', Estatus.Value = "Rechazado") }
)
```

En las propiedades de la gráfica se elige **Estado** como etiqueta y **Total** como valor.

### Ícono de casa → OnSelect

```powerfx
Navigate(scrHome, ScreenTransition.Fade)
```

## Explicación

**CountRows()**
Cuenta cuántas solicitudes hay en la lista.

**CountIf()**
Cuenta solo las solicitudes que cumplen una condición; por ejemplo, las que tienen el estatus vacío (pendientes).

**AddColumns() y GroupBy()**
Agrupan las solicitudes por área y agregan una columna **Total** con cuántas solicitudes tiene cada una. El resultado es la tabla que dibuja la gráfica de columnas.

**Table()**
Arma una tabla pequeña con los totales de pendientes, aprobados y rechazados para la gráfica circular.

**Nota:** si en la lista la columna **Estatus** es de tipo texto en lugar de opción, se escribe `Estatus` en vez de `Estatus.Value`.
