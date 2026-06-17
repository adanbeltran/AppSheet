# 1. Conceptos Básicos de AppSheet

[Volver al README](./README.md) · [Abrir la plantilla Excel](./plantilla_appsheet_panaderia.xlsx) · [Continuar con el contexto](./2_Contexto_del_taller.md)

## 1. Vigencia de la guía

AppSheet es una plataforma no-code ofrecida como servicio en la nube. Sus funciones y su editor se actualizan de forma continua; por ello, esta guía no hace referencia a un número fijo de versión. La navegación fue verificada el **17 de junio de 2026** con el editor mejorado, que se encuentra habilitado de manera predeterminada.

La navegación vigente se organiza principalmente así:

| Sección actual | Uso principal | Equivalencia del editor heredado |
|---|---|---|
| `Data` | Tablas, columnas, segmentos de datos y estructura de la fuente. | `Data` |
| `App` | Vistas, navegación y presentación de la aplicación. | `UX` |
| `Actions` | Botones y operaciones ejecutadas por el usuario. | `Behavior > Actions` |
| `Automation` | Bots, eventos, procesos y tareas automáticas. | `Automation` |
| `Security` | Inicio de sesión, usuarios y filtros de seguridad. | `Security` |
| `Settings` | Tema, localización, rendimiento, trabajo sin conexión y sincronización. | Configuraciones distribuidas en varias secciones |
| `Manage` | Versiones, supervisión, comprobación de despliegue y publicación. | `Manage` |

## 2. ¿Qué es AppSheet?

AppSheet permite construir aplicaciones web y móviles a partir de fuentes de datos como Google Sheets, Microsoft Excel, AppSheet databases y bases de datos compatibles. La aplicación se conecta a la fuente; los datos no quedan incorporados permanentemente dentro del diseño de la app. Cuando el usuario registra o modifica información, los cambios se guardan en la fuente conectada.

La vista previa del editor es una **aplicación activa**. Los registros creados o modificados durante una prueba se almacenan en la fuente de datos; por ello, el taller utiliza únicamente datos de prueba.

## 3. Uso del archivo Excel

La plantilla del taller está en formato `.xlsx`. Existen dos rutas recomendadas:

### Ruta A. Convertir a Google Sheets

Es la opción más sencilla para un entorno académico basado en Google Workspace:

1. Subir el archivo a Google Drive.
2. Abrirlo con Google Sheets.
3. Guardarlo como hoja de cálculo de Google.
4. Crear la app desde `Google Sheets`.

La conversión debe revisarse para confirmar que las hojas, los encabezados y los datos de prueba se conservaron.

### Ruta B. Conservar el formato Excel

AppSheet admite archivos `.xlsx` alojados en fuentes compatibles, como OneDrive o SharePoint. No admite archivos `.xls` ni `.xlsm`. Esta ruta conserva el libro como Excel, pero requiere que la cuenta tenga acceso a la fuente de Microsoft correspondiente.

## 4. Modelo de datos del taller

La aplicación utiliza tres clases de tablas:

### 4.1. Tablas maestras

Contienen información relativamente estable y reutilizable:

- `Proveedores`
- `Materias_Primas`
- `Productos_Terminados`

No se debe repetir toda la información de una materia prima o de un proveedor en cada transacción. Las tablas transaccionales almacenan únicamente la referencia al registro maestro.

### 4.2. Tablas transaccionales

Representan eventos del negocio:

- `Ingresos_MP`
- `Ordenes_Produccion`
- `Ventas`

Cada fila registra un hecho ocurrido en una fecha determinada.

### 4.3. Tablas de detalle o asociación

Permiten representar relaciones uno-a-muchos o muchos-a-muchos:

- `Recetas`
- `Consumos_MP_OP`
- `Detalle_Ventas`

Una venta puede contener varios productos; una orden puede consumir varias materias primas; y un producto puede requerir varias materias primas.

## 5. Columnas esenciales

### 5.1. Key

Una columna marcada como `Key` identifica cada fila de manera única y estable. No debe depender de un nombre, una posición de fila o un consecutivo que pueda cambiar.

Configuración recomendada:

```appsheet
Initial value: UNIQUEID()
```

El valor debe generarse al crear la fila y no modificarse después.

### 5.2. Label

La columna `Label` define el texto legible con el que AppSheet presenta un registro referenciado. Por ejemplo, la llave de un proveedor puede ser un código técnico, mientras que `nombre_proveedor` funciona como etiqueta visible.

### 5.3. Ref

Una columna `Ref` almacena la llave de una fila ubicada en otra tabla. Esta configuración crea relaciones, listas de selección y navegación entre registros.

Ejemplo:

```text
Ingresos_MP[id_proveedor] → Proveedores[id_proveedor]
```

### 5.4. IsPartOf

`IsPartOf` fortalece una relación padre–hijo. Permite agregar filas hijas dentro del formulario o detalle del registro padre y aplicar un comportamiento conjunto.

Se recomienda en:

```text
Detalle_Ventas[id_venta] → Ventas
Consumos_MP_OP[id_orden_produccion] → Ordenes_Produccion
```

### 5.5. Initial value y App formula

- **Initial value:** se evalúa al crear la fila. El usuario puede modificar el valor cuando la columna sea editable.
- **App formula:** se recalcula a partir de otras columnas y normalmente no debe ser editada manualmente.
- **Virtual column:** existe en el modelo de AppSheet, pero no como columna física en la hoja. Es útil para cálculos derivados, aunque un número excesivo de columnas virtuales puede afectar el rendimiento.

## 6. Expresiones utilizadas

### Generación de identificadores

```appsheet
UNIQUEID()
```

### Desreferenciación

Obtiene un campo del registro seleccionado:

```appsheet
[id_producto].[precio_venta]
```

### Subtotal de una línea

```appsheet
[cantidad] * [precio_unitario]
```

### Total de una venta

```appsheet
SUM(
  SELECT(
    Detalle_Ventas[subtotal],
    [id_venta] = [_THISROW].[id_venta]
  )
)
```

### Inventario estimado de materia prima

```appsheet
[stock_inicial]
+
SUM(
  SELECT(
    Ingresos_MP[cantidad],
    [id_materia_prima] = [_THISROW].[id_materia_prima]
  )
)
-
SUM(
  SELECT(
    Consumos_MP_OP[cantidad_consumida],
    [id_materia_prima] = [_THISROW].[id_materia_prima]
  )
)
```

### Inventario estimado de producto terminado

```appsheet
[stock_inicial]
+
SUM(
  SELECT(
    Ordenes_Produccion[cantidad_producida],
    AND(
      [id_producto] = [_THISROW].[id_producto],
      [estado_orden] = "Cerrada"
    )
  )
)
-
SUM(
  SELECT(
    Detalle_Ventas[cantidad],
    [id_producto] = [_THISROW].[id_producto]
  )
)
```

## 7. Validaciones

`Valid_If` restringe los valores que puede guardar el usuario.

Cantidad positiva:

```appsheet
[_THIS] > 0
```

Cantidad no negativa:

```appsheet
[_THIS] >= 0
```

Fecha de vencimiento válida:

```appsheet
OR(
  ISBLANK([_THIS]),
  [_THIS] >= [fecha_ingreso]
)
```

Las validaciones mejoran la calidad de los datos, pero no sustituyen el diseño correcto de llaves, relaciones y permisos.

## 8. Vistas y navegación

AppSheet puede generar vistas automáticamente. En el editor actual se administran en `App > Views`.

Tipos utilizados en el taller:

- `Table`: consulta tabular y auditoría de registros.
- `Deck`: presentación resumida de registros.
- `Detail`: detalle de una fila y sus registros relacionados.
- `Form`: captura y edición.
- `Chart`: representación gráfica.
- `Dashboard`: composición de varias vistas.

Las vistas de uso frecuente deben ubicarse en la navegación primaria. Las vistas administrativas o poco frecuentes pueden ubicarse en el menú.

## 9. Acciones y automatización

Una **acción** se ejecuta por intervención del usuario: abrir una vista, modificar datos, agregar una fila relacionada o acceder a un enlace.

Un **bot** de Automation se activa por un evento, ejecuta un proceso y contiene uno o más pasos. La primera versión del taller no requiere automatizaciones complejas. Las alertas por correo o la generación de documentos se consideran ampliaciones posteriores.

## 10. Seguridad

Para un piloto con datos reales, se debe:

1. Activar `Security > Require sign-in`.
2. Compartir la aplicación solo con usuarios autorizados.
3. Revisar los permisos de la fuente de datos.
4. Usar filtros de seguridad cuando cada usuario deba recibir solo una parte de los registros.
5. Evitar tratar `Show_If`, slices o vistas ocultas como controles de seguridad.

Los filtros de seguridad reducen los datos sincronizados, pero la protección también debe aplicarse en la fuente.

## 11. Sincronización y despliegue

La configuración de trabajo sin conexión y sincronización se encuentra en `Settings`. Antes de publicar:

1. Guardar la app.
2. Corregir errores y revisar advertencias.
3. Ejecutar `Manage > Deploy > Deployment Check`.
4. Verificar compatibilidad con el plan de licenciamiento.
5. Compartir la app únicamente con los usuarios del piloto.

## 12. Buenas prácticas

- Mantener una sola fila de encabezados por hoja.
- Evitar celdas combinadas, subtítulos y filas vacías dentro de las tablas operativas.
- Usar llaves técnicas y estables.
- No utilizar `ROWNUMBER` como llave.
- Conservar los mismos nombres técnicos de columnas durante el taller.
- No editar manualmente valores calculados.
- No agregar columnas a la fuente sin regenerar el esquema.
- Evitar datos personales reales durante las pruebas.
- Guardar cambios con frecuencia y revisar el panel de errores.

## 13. Fuentes oficiales consultadas

- [Explorar el editor de AppSheet](https://support.google.com/appsheet/answer/12290157?hl=en)
- [Resumen de mejoras del editor](https://support.google.com/appsheet/answer/12490168?hl=en)
- [Crear una app a partir de datos existentes](https://support.google.com/appsheet/answer/12008053?hl=en)
- [Usar Excel en Office 365 y SharePoint](https://support.google.com/appsheet/answer/10106311?hl=en)
- [Regenerar el esquema de una tabla](https://support.google.com/appsheet/answer/10106675?hl=en)
- [Diseño de aplicaciones](https://support.google.com/appsheet/answer/10099795?hl=en)
- [Seguridad](https://support.google.com/appsheet/answer/10105078?hl=en)
- [Despliegue](https://support.google.com/appsheet/answer/10104495?hl=en)
- [Notas de la versión de AppSheet](https://discuss.google.dev/c/appsheet/appsheet-release-notes/123)
