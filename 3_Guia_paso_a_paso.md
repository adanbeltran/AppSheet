# 3. Guía paso a paso

[Volver al README](./README.md) · [Abrir la plantilla Excel](./plantilla_appsheet_panaderia.xlsx) · [Revisar conceptos](./1_Conceptos_Basicos_de_AppSheet.md)

## 0. Antes de comenzar

1. Extraiga todos los archivos del paquete en una misma carpeta.
2. Abra [plantilla_appsheet_panaderia.xlsx](./plantilla_appsheet_panaderia.xlsx).
3. Revise las hojas `README`, `Modelo_Datos`, `Guia_AppSheet`, `Listas` y `Fuentes`.
4. No cambie los nombres de las hojas operativas ni de sus columnas durante la primera construcción.
5. Trabaje con una copia del archivo y únicamente con datos de prueba.

## 1. Preparar la fuente de datos

### Opción A. Google Sheets — recomendada para el taller

1. Crear una Carpeta en GoogleDrive con el nombre de TallerPanaderia
   <img width="1147" height="520" alt="image" src="https://github.com/user-attachments/assets/006edf62-4890-4276-83a5-29c08f5c9f4d" />

2. Subir el archivo plantilla_appsheet_panaderia en la carpeta creada

<img width="998" height="478" alt="image" src="https://github.com/user-attachments/assets/810ea499-907e-45fc-a81b-2e2438b2b5a3" />

3. Ábralo con Google Sheets.
<img width="822" height="542" alt="image" src="https://github.com/user-attachments/assets/c4f6568f-e8dc-401d-a618-d0be2777f162" />

   
7. Use `Archivo > Guardar como Hojas de cálculo de Google`.

<img width="1506" height="691" alt="image" src="https://github.com/user-attachments/assets/d193cc6d-4feb-435a-b86c-13ccaa967070" />

9. Confirme que cada hoja mantenga la primera fila como encabezado.
10. Revise que no existan celdas combinadas ni filas de título dentro de las hojas operativas.


## 2. Crear la aplicación

1. Inicie sesión en AppSheet. https://www.appsheet.com/Home/Apps
   
2. En `My Apps`, seleccione `Create > App > Start with existing data`.
<img width="718" height="408" alt="image" src="https://github.com/user-attachments/assets/8d93267e-9021-4d9f-868a-e7efa63e3ee9" />

   
3. Escriba  `Panaderia_App_Prueba`.
<img width="587" height="271" alt="image" src="https://github.com/user-attachments/assets/9e82c1f4-2dc9-4980-b9d3-7d056775f3e7" />


4. Seleccione `Choose your data`.
5. Elija la fuente:  `Google Sheets`, 
  
6. Seleccione el archivo.
<img width="943" height="582" alt="image" src="https://github.com/user-attachments/assets/28d315a7-5917-446b-bdf4-bd145e0e438e" />

   
7. Espere a que se genere la app.
8. Cuando aparezca la pantalla inicial, seleccione `Customize with AppSheet`.
<img width="768" height="758" alt="image" src="https://github.com/user-attachments/assets/4b669252-bf78-492e-a22a-86be68c2d9b8" />

   

## 3. Agregar las tablas

En el editor actual:

1. Abra `Data`.
2. Use el botón `+` del panel de datos para agregar hojas que no se hayan incorporado.
<img width="1257" height="563" alt="image" src="https://github.com/user-attachments/assets/44bdeb67-e9a4-4b4e-bcfc-046685e0b791" />


3. Agregue estas tablas operativas:

```text
Proveedores
Materias_Primas
Productos_Terminados
Recetas
Ingresos_MP
Ordenes_Produccion
Consumos_MP_OP
Ventas
Detalle_Ventas
```

4. No agregue como tablas operativas `README`, `Modelo_Datos`, `Guia_AppSheet`, `Fuentes`, `Listas` o `Dashboard`, salvo que el diseño requiera consultar alguna de ellas dentro de la app.
5. Para cada tabla, confirme que los usuarios puedan realizar las operaciones necesarias: `Adds`, `Updates` y, solo cuando corresponda, `Deletes`.
<img width="585" height="372" alt="image" src="https://github.com/user-attachments/assets/a49914c8-2f97-4d9f-80eb-073be908dcf9" />


<img width="552" height="697" alt="image" src="https://github.com/user-attachments/assets/569168dd-7c8e-4731-9a91-534a9667afb6" />



## 4. Configurar llaves

En `Data`, seleccione una tabla y luego la columna identificadora. Marque `Key` y configure `Initial value` con:

```appsheet
UNIQUEID()
```

<img width="1492" height="605" alt="image" src="https://github.com/user-attachments/assets/65ee90e2-b3d1-4255-b580-748c86dac4e1" />


| Tabla | Key |
|---|---|
| `Proveedores` | `id_proveedor` |
| `Materias_Primas` | `id_materia_prima` |
| `Productos_Terminados` | `id_producto` |
| `Recetas` | `id_receta` |
| `Ingresos_MP` | `id_ingreso_mp` |
| `Ordenes_Produccion` | `id_orden_produccion` |
| `Consumos_MP_OP` | `id_consumo_mp` |
| `Ventas` | `id_venta` |
| `Detalle_Ventas` | `id_detalle_venta` |

Configuración adicional recomendada para las llaves:

- `Show?`: desactivado.
- `Editable?`: desactivado.
- `Required?`: activado.
- Tipo: `Text`.

Si agrego la Tabla Lista, se debe eliminar del modelo

<img width="408" height="320" alt="image" src="https://github.com/user-attachments/assets/34275653-7ff2-41af-8b2c-b6ee9fd4da44" />


No use nombres, números de documento, consecutivos de fila ni `ROWNUMBER` como llave.

## 5. Configurar etiquetas

Marque como `Label`:

| Tabla | Label |
|---|---|
| `Proveedores` | `nombre_proveedor` |
| `Materias_Primas` | `nombre_materia_prima` |
| `Productos_Terminados` | `nombre_producto` |


<img width="957" height="738" alt="image" src="https://github.com/user-attachments/assets/e6b98c4c-1df6-4eae-96ab-f4313aac9961" />


Para órdenes y ventas puede conservarse el identificador o crear posteriormente una columna virtual descriptiva.

## 6. Configurar referencias

Cambie el tipo de las siguientes columnas a `Ref` y seleccione la tabla referenciada:

| Tabla | Columna | Referencia |
|---|---|---|
| `Recetas` | `id_producto` | `Productos_Terminados` |
| `Recetas` | `id_materia_prima` | `Materias_Primas` |
| `Ingresos_MP` | `id_materia_prima` | `Materias_Primas` |
| `Ingresos_MP` | `id_proveedor` | `Proveedores` |
| `Ordenes_Produccion` | `id_producto` | `Productos_Terminados` |
| `Consumos_MP_OP` | `id_orden_produccion` | `Ordenes_Produccion` |
| `Consumos_MP_OP` | `id_materia_prima` | `Materias_Primas` |
| `Detalle_Ventas` | `id_venta` | `Ventas` |
| `Detalle_Ventas` | `id_producto` | `Productos_Terminados` |

Active `IsPartOf` en:

```text
Detalle_Ventas[id_venta]
Consumos_MP_OP[id_orden_produccion]
```

Resultado esperado: AppSheet genera columnas inversas relacionadas y permite gestionar los detalles desde el registro padre.

## 7. Revisar tipos de datos

| Campo | Tipo recomendado |
|---|---|
| Fechas sin hora | `Date` |
| Fecha y hora de venta | `DateTime` |
| Cantidades | `Decimal` |
| Precios y costos | `Price` |
| Correo | `Email` |
| Teléfono | `Phone` |
| Observaciones | `LongText` |
| Estados y categorías | `Enum` |
| Relaciones | `Ref` |

En un entorno colombiano, revise la localización y la moneda en `Settings` para que fechas y valores monetarios se interpreten de forma consistente.

## 8. Configurar listas Enum

Configure opciones controladas:

```text
estado: Activo, Inactivo
estado_orden: Planificada, En proceso, Cerrada, Cancelada
medio_pago: Efectivo, Transferencia, Tarjeta, Mixto
unidad_medida: kg, g, L, ml, unidad
categoria_producto: Panadería, Pastelería, Bebidas, Otros
categoria_materia_prima: Harinas, Lácteos, Grasas, Endulzantes, Empaques, Otros
```

Desactive la posibilidad de agregar valores no previstos cuando la consistencia sea prioritaria.

## 9. Configurar cálculos

### 9.1. Costo total del ingreso

Tabla: `Ingresos_MP`  
Columna: `costo_total`  
Ubicación: `App formula`

```appsheet
[cantidad] * [costo_unitario]
```

### 9.2. Costo total del consumo

Tabla: `Consumos_MP_OP`  
Columna: `costo_total_consumo`  
Ubicación: `App formula`

```appsheet
[cantidad_consumida] * [costo_unitario_estimado]
```

### 9.3. Precio unitario

Tabla: `Detalle_Ventas`  
Columna: `precio_unitario`  
Ubicación: `Initial value`

```appsheet
[id_producto].[precio_venta]
```

Para conservar el precio histórico de la venta, no use esta expresión como `App formula`; el precio debe copiarse al crear el detalle y permanecer almacenado.

### 9.4. Subtotal

Tabla: `Detalle_Ventas`  
Columna: `subtotal`  
Ubicación: `App formula`

```appsheet
[cantidad] * [precio_unitario]
```

### 9.5. Total de la venta

Tabla: `Ventas`  
Columna virtual: `total_venta`  
Tipo: `Price`

```appsheet
SUM(
  SELECT(
    Detalle_Ventas[subtotal],
    [id_venta] = [_THISROW].[id_venta]
  )
)
```

### 9.6. Stock de materia prima

Tabla: `Materias_Primas`  
Columna virtual: `stock_actual_mp`  
Tipo: `Decimal`

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

### 9.7. Stock de producto terminado

Tabla: `Productos_Terminados`  
Columna virtual: `stock_actual_producto`  
Tipo: `Decimal`

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

### 9.8. Alertas de stock

Materia prima:

```appsheet
IF(
  [stock_actual_mp] <= [stock_minimo],
  "Revisar compra",
  "Stock suficiente"
)
```

Producto terminado:

```appsheet
IF(
  [stock_actual_producto] <= [stock_minimo],
  "Revisar producción",
  "Stock suficiente"
)
```

## 10. Configurar validaciones

Cantidad positiva:

```appsheet
[_THIS] > 0
```

Cantidad producida no negativa:

```appsheet
[_THIS] >= 0
```

Fecha de vencimiento:

```appsheet
OR(
  ISBLANK([_THIS]),
  [_THIS] >= [fecha_ingreso]
)
```

Producto activo en una venta:

```appsheet
SELECT(
  Productos_Terminados[id_producto],
  [estado] = "Activo"
)
```

Agregue un mensaje de error comprensible en cada validación.

## 11. Organizar formularios

Orden recomendado:

### `Proveedores`

```text
nombre_proveedor
tipo_documento
numero_documento
telefono
correo
ciudad
estado
```

### `Materias_Primas`

```text
codigo_mp
nombre_materia_prima
categoria
unidad_medida
stock_inicial
stock_minimo
estado
```

### `Productos_Terminados`

```text
codigo_producto
nombre_producto
categoria_producto
unidad_venta
precio_venta
stock_inicial
stock_minimo
estado
```

### `Ingresos_MP`

```text
fecha_ingreso
id_materia_prima
id_proveedor
cantidad
costo_unitario
lote
fecha_vencimiento
responsable
costo_total
```

### `Ordenes_Produccion`

```text
fecha_orden
id_producto
cantidad_planificada
cantidad_producida
estado_orden
responsable
observacion
Related Consumos_MP_OP
```

### `Ventas`

```text
fecha_venta
cliente
medio_pago
responsable
observacion
Related Detalle_Ventas
total_venta
```

Las vistas `Form` se crean automáticamente para las tablas que permiten altas o actualizaciones; pueden personalizarse desde `App > Views`.

## 12. Crear vistas

Abra `App > Views`.

Cree o ajuste:

| Vista | Datos | Tipo | Ubicación |
|---|---|---|---|
| Inicio | Vistas operativas | `Dashboard` | Primary |
| Materias primas | `Materias_Primas` | `Table` o `Deck` | Primary |
| Productos | `Productos_Terminados` | `Table` o `Deck` | Primary |
| Producción | `Ordenes_Produccion` | `Deck` | Primary |
| Ventas | `Ventas` | `Table` | Primary |
| Proveedores | `Proveedores` | `Table` | Menu |
| Ingresos | `Ingresos_MP` | `Table` | Menu |
| Recetas | `Recetas` | `Table` | Menu |

En el dashboard combine, como mínimo:

- Materias primas con stock bajo.
- Productos con stock bajo.
- Órdenes por estado.
- Ventas recientes.

## 13. Aplicar formato visual

Cree reglas de formato para resaltar:

```text
[stock_actual_mp] <= [stock_minimo]
[stock_actual_producto] <= [stock_minimo]
[estado_orden] = "Cerrada"
[estado_orden] = "Cancelada"
```

Use iconos y énfasis con moderación. El color no debe ser el único medio para comunicar un estado.

## 14. Configurar seguridad para el piloto

1. Abra `Security > Require sign-in`.
2. Active el inicio de sesión.
3. Seleccione el proveedor de autenticación apropiado.
4. Comparta la app únicamente con cuentas de prueba o usuarios autorizados.
5. Revise el acceso al archivo fuente.
6. No use vistas ocultas como mecanismo de protección.
7. Si se requiere separación por usuario, evalúe filtros de seguridad con `USEREMAIL()`.

## 15. Revisar Settings

En `Settings` revise:

- Tema y logotipo.
- Localización.
- Comportamiento de sincronización.
- Funcionamiento sin conexión, si aplica.
- Rendimiento.

No habilite trabajo sin conexión sin probar primero la sincronización inicial y los posibles conflictos.

## 16. Ejecutar la prueba funcional

Use datos claramente marcados como prueba.

### 16.1. Proveedor

```text
nombre_proveedor: PROVEEDOR_PRUEBA_01
numero_documento: NIT-PRUEBA-001
correo: proveedor.prueba@example.com
estado: Activo
```

### 16.2. Materia prima

```text
codigo_mp: MP-PRUEBA-001
nombre_materia_prima: Harina de trigo - prueba
unidad_medida: kg
stock_inicial: 10
stock_minimo: 5
estado: Activo
```

### 16.3. Producto

```text
codigo_producto: PT-PRUEBA-001
nombre_producto: Pan de prueba
precio_venta: 800
stock_inicial: 0
stock_minimo: 20
estado: Activo
```

### 16.4. Ingreso

```text
cantidad: 50
costo_unitario: 3500
lote: LOTE-PRUEBA-001
```

Resultado esperado:

```text
costo_total = 175000
stock_actual_mp antes del consumo = 60
```

### 16.5. Orden y consumo

```text
cantidad_planificada: 100
cantidad_producida: 100
estado_orden: Cerrada
cantidad_consumida: 8
```

Resultado esperado:

```text
stock_actual_mp = 52
stock_actual_producto antes de la venta = 100
```

### 16.6. Venta

```text
cantidad: 10
precio_unitario: 800
```

Resultado esperado:

```text
subtotal = 8000
total_venta = 8000
stock_actual_producto = 90
```

## 17. Comprobar errores

1. Guarde la aplicación.
2. Abra el panel de errores y advertencias.
3. Corrija errores de columnas, referencias o expresiones.
4. Revise que las listas `Ref` muestren etiquetas y no identificadores.
5. Confirme que el detalle pueda agregarse desde la venta y la orden.
6. Verifique que las expresiones devuelvan valores numéricos.

## 18. Regenerar el esquema cuando cambie la fuente

Después de agregar, eliminar o reordenar columnas directamente en la hoja:

1. Abra `Data`.
2. Seleccione la tabla.
3. Use `Regenerate schema` en el encabezado de la tabla, o `More > Regenerate schema`.
4. Confirme la regeneración.
5. Revise tipos, llaves, referencias y expresiones.
6. Guarde la app.

La regeneración puede afectar configuraciones existentes; no debe ejecutarse como una acción rutinaria sin revisar previamente la modificación.

## 19. Comprobar despliegue

1. Abra `Manage > Deploy`.
2. Seleccione `Deployment Check`.
3. Ejecute `Run deployment check`.
4. Corrija los hallazgos.
5. Publique únicamente cuando la aplicación, la fuente de datos, la seguridad y el plan de licenciamiento sean adecuados.

Para una actividad académica, la app puede permanecer en estado de prototipo cuando solo se use con el grupo autorizado y dentro de los límites aplicables.

## 20. Problemas frecuentes

| Problema | Causa probable | Corrección |
|---|---|---|
| Se muestran IDs en los desplegables | No se configuró `Label`. | Marcar la columna descriptiva como etiqueta. |
| Aparecen referencias inválidas | La columna no contiene llaves existentes. | Corregir datos y configurar `Ref`. |
| El total de venta permanece en cero | Los detalles no están relacionados con la venta. | Revisar `id_venta`, `Ref` e `IsPartOf`. |
| El precio cambia en ventas históricas | Se usó `App formula` en precio_unitario. | Usar `Initial value` para copiar el precio. |
| La app no reconoce una columna nueva | Esquema desactualizado. | Ejecutar `Regenerate schema`. |
| Se duplican filas o llaves | La llave no es estable o se edita. | Usar `UNIQUEID()` y bloquear edición. |
| La vista previa alteró los datos | La vista previa es la app activa. | Restaurar datos de prueba y repetir con precaución. |
| El inventario no coincide | Faltan transacciones o hay estados incorrectos. | Revisar ingresos, consumos, órdenes cerradas y ventas. |

## 21. Lista de cierre

- [ ] Tablas agregadas.
- [ ] Llaves y etiquetas configuradas.
- [ ] Referencias e `IsPartOf` verificadas.
- [ ] Tipos de datos revisados.
- [ ] Expresiones sin errores.
- [ ] Formularios ordenados.
- [ ] Vistas y dashboard funcionales.
- [ ] Prueba integral documentada.
- [ ] Seguridad revisada.
- [ ] Deployment Check ejecutado.
