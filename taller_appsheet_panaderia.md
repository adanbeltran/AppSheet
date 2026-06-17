# Taller académico: construcción de una aplicación de panadería en AppSheet

## 1. Identificación del taller

**Nombre del taller:** Desarrollo de una aplicación low-code para la gestión básica de una panadería usando AppSheet  
**Herramienta principal:** Google AppSheet  
**Archivo base de datos:** `plantilla_appsheet_panaderia.xlsx`  
**Producto final esperado:** primera versión funcional de una app para registrar materia prima, proveedores, productos terminados, órdenes de producción y ventas.  
**Nivel sugerido:** introductorio-intermedio  
**Modalidad:** práctica guiada con sustentación funcional  
**Duración sugerida:** 4 a 6 horas de trabajo guiado, más 2 horas de prueba y ajuste.

---

## 2. Propósito formativo

El propósito del taller es que el estudiante diseñe y construya una primera versión de una aplicación empresarial sencilla utilizando AppSheet, a partir de un archivo estructurado en Excel o Google Sheets. La aplicación permitirá apoyar procesos básicos de una panadería: administración de proveedores, control de materias primas, definición de productos terminados, registro de órdenes de producción y registro de ventas.

Desde el punto de vista académico, el taller integra conceptos de bases de datos, modelo relacional, formularios, reglas de validación, automatización básica de cálculos, experiencia de usuario y control operativo en un pequeño negocio.

---

## 3. Objetivo general

Construir una aplicación funcional en AppSheet para gestionar de manera básica los procesos de ingreso de materia prima, productos terminados, proveedores, órdenes de producción y ventas de una panadería, aplicando principios de modelado de datos, relaciones entre tablas, formularios, validaciones y vistas de consulta.

---

## 4. Objetivos específicos

Al finalizar el taller, el estudiante estará en capacidad de:

1. Identificar las entidades principales de un proceso operativo de panadería.
2. Reconocer la diferencia entre tablas maestras, tablas transaccionales y tablas de detalle.
3. Configurar tablas, llaves primarias y relaciones tipo referencia en AppSheet.
4. Construir formularios para capturar información operativa.
5. Implementar fórmulas básicas para calcular subtotales, totales e inventarios estimados.
6. Crear vistas funcionales para consultar productos, materias primas, proveedores, producción y ventas.
7. Validar el funcionamiento de la aplicación mediante un flujo de prueba completo.
8. Justificar técnicamente las decisiones de diseño aplicadas en la primera versión de la app.

---

## 5. Competencias a desarrollar

| Competencia | Descripción |
|---|---|
| Modelado de datos | Capacidad para identificar entidades, atributos, llaves y relaciones. |
| Pensamiento lógico | Capacidad para estructurar procesos operativos mediante reglas y fórmulas. |
| Uso de herramientas low-code | Capacidad para construir aplicaciones funcionales sin programación tradicional intensiva. |
| Gestión de información | Capacidad para organizar datos de negocio de manera consistente y reutilizable. |
| Validación funcional | Capacidad para probar que una solución cumpla un flujo operativo mínimo. |
| Comunicación técnica | Capacidad para explicar y justificar la estructura de la aplicación desarrollada. |

---

## 6. Contexto del caso

Una panadería requiere una aplicación sencilla para controlar sus operaciones básicas. Actualmente registra información en cuadernos o archivos aislados, lo que genera dificultades para conocer:

- Qué materias primas tiene disponibles.
- Qué proveedores suministran cada insumo.
- Qué productos terminados vende.
- Qué materias primas se consumen en la producción.
- Qué productos se venden diariamente.
- Cuál es el inventario estimado de materias primas y productos terminados.

La solución propuesta será una primera versión de una app construida en AppSheet, conectada a un archivo Excel o Google Sheets. Esta primera versión no reemplaza un sistema ERP completo, pero permite modelar los procesos esenciales de una panadería y construir una base funcional para futuras mejoras.

---

## 7. Alcance funcional de la primera versión

La aplicación deberá permitir:

1. Registrar proveedores.
2. Registrar materias primas.
3. Registrar productos terminados.
4. Definir recetas o composición de productos terminados.
5. Registrar ingresos de materia prima.
6. Registrar órdenes de producción.
7. Registrar consumo de materia prima por orden de producción.
8. Registrar ventas de productos terminados.
9. Consultar inventario estimado de materias primas.
10. Consultar inventario estimado de productos terminados.
11. Consultar ventas y sus respectivos detalles.
12. Visualizar un tablero básico de control operativo.

---

## 8. Alcance no incluido en la primera versión

Para mantener el ejercicio dentro de un alcance académico inicial, la primera versión no incluirá:

- Facturación electrónica.
- Integración con pasarelas de pago.
- Contabilidad formal.
- Nómina.
- Impuestos.
- Manejo avanzado de costos indirectos.
- Control automático de lotes por método PEPS/FIFO.
- Integración con impresoras POS.
- Roles avanzados por usuario.
- Automatizaciones complejas con bots.

Estos elementos pueden proponerse como evolución futura del proyecto.

---

## 9. Recurso base: archivo Excel

El taller utiliza el archivo:

```text
plantilla_appsheet_panaderia.xlsx
```

Este archivo contiene varias hojas, cada una diseñada para convertirse en una tabla de la aplicación.

| Hoja | Tipo de tabla | Propósito |
|---|---|---|
| README | Documentación | Explica el propósito general del archivo. |
| Guia_AppSheet | Documentación | Contiene instrucciones base para construir la app. |
| Modelo_Datos | Documentación técnica | Describe campos, tipos de datos, llaves y relaciones. |
| Proveedores | Maestra | Registra los proveedores de la panadería. |
| Materias_Primas | Maestra | Registra los insumos usados en producción. |
| Productos_Terminados | Maestra | Registra los productos listos para venta. |
| Recetas | Relación / detalle técnico | Define qué materias primas usa cada producto. |
| Ingresos_MP | Transaccional | Registra entradas o compras de materia prima. |
| Ordenes_Produccion | Transaccional | Registra producción planificada y realizada. |
| Consumos_MP_OP | Detalle transaccional | Registra consumo real de materias primas por orden. |
| Ventas | Transaccional | Registra encabezados de ventas. |
| Detalle_Ventas | Detalle transaccional | Registra productos vendidos en cada venta. |
| Listas | Apoyo | Contiene valores para listas desplegables. |
| Dashboard | Apoyo | Contiene indicadores o información de resumen. |
| Fuentes | Documentación | Referencias utilizadas para el diseño. |

---

## 10. Fundamento conceptual

### 10.1. Tabla maestra

Una tabla maestra almacena información relativamente estable del negocio. Por ejemplo: proveedores, materias primas y productos terminados.

**Ejemplo:** la tabla `Materias_Primas` contiene datos como código, nombre, unidad de medida, stock inicial y stock mínimo.

**Justificación:** separar datos maestros evita repetir información en cada transacción. Por ejemplo, si se compra harina varias veces, no se debe escribir nuevamente toda la información de la harina en cada ingreso; basta con referenciarla.

---

### 10.2. Tabla transaccional

Una tabla transaccional almacena eventos del negocio, es decir, operaciones que ocurren en una fecha determinada.

**Ejemplos:**

- Ingreso de materia prima.
- Orden de producción.
- Venta.

**Justificación:** las transacciones permiten construir trazabilidad. A partir de ellas se puede consultar qué ocurrió, cuándo ocurrió, quién lo registró y qué impacto tuvo en el inventario.

---

### 10.3. Tabla de detalle

Una tabla de detalle permite representar una relación uno a muchos. Por ejemplo, una venta puede incluir varios productos, y una orden de producción puede consumir varias materias primas.

**Ejemplos:**

- `Detalle_Ventas`: productos vendidos dentro de una venta.
- `Consumos_MP_OP`: materias primas consumidas dentro de una orden de producción.
- `Recetas`: materias primas necesarias para elaborar un producto terminado.

**Justificación:** si se registraran todos los productos vendidos directamente en la tabla `Ventas`, la estructura sería limitada y repetitiva. El diseño con tabla de detalle permite que una venta tenga uno, dos, cinco o más productos sin alterar la estructura de la base de datos.

---

## 11. Modelo de datos propuesto

### 11.1. Entidades principales

| Entidad | Descripción |
|---|---|
| Proveedor | Persona o empresa que suministra materias primas. |
| Materia prima | Insumo utilizado para elaborar productos. |
| Producto terminado | Producto listo para vender al cliente. |
| Receta | Relación entre producto terminado y materia prima requerida. |
| Ingreso de materia prima | Entrada de insumos al inventario. |
| Orden de producción | Registro de producción planificada y ejecutada. |
| Consumo de materia prima | Materias primas realmente utilizadas en una orden. |
| Venta | Encabezado general de una venta. |
| Detalle de venta | Productos específicos vendidos dentro de una venta. |

---

### 11.2. Relaciones principales

| Relación | Cardinalidad | Explicación |
|---|---:|---|
| Proveedor → Ingresos_MP | 1 a muchos | Un proveedor puede estar asociado a muchos ingresos de materia prima. |
| Materia_Prima → Ingresos_MP | 1 a muchos | Una materia prima puede tener muchos registros de ingreso. |
| Producto_Terminado → Recetas | 1 a muchos | Un producto puede estar compuesto por varias materias primas. |
| Materia_Prima → Recetas | 1 a muchos | Una materia prima puede utilizarse en varias recetas. |
| Producto_Terminado → Ordenes_Produccion | 1 a muchos | Un producto puede producirse en varias órdenes. |
| Ordenes_Produccion → Consumos_MP_OP | 1 a muchos | Una orden puede consumir varias materias primas. |
| Materia_Prima → Consumos_MP_OP | 1 a muchos | Una materia prima puede consumirse en varias órdenes. |
| Ventas → Detalle_Ventas | 1 a muchos | Una venta puede contener varios productos vendidos. |
| Producto_Terminado → Detalle_Ventas | 1 a muchos | Un producto puede aparecer en muchas ventas. |

---

## 12. Estructura de tablas sugerida

### 12.1. Tabla `Proveedores`

| Campo | Tipo sugerido en AppSheet | Configuración | Justificación |
|---|---|---|---|
| id_proveedor | Text | Key, Initial value: `UNIQUEID()` | Identifica de manera única cada proveedor. |
| nombre_proveedor | Text | Label, Required | Permite visualizar el proveedor por su nombre comercial. |
| tipo_documento | Enum | Lista desplegable | Normaliza el tipo de identificación. |
| numero_documento | Text | Required | Identifica legal o administrativamente al proveedor. |
| telefono | Phone | Opcional | Facilita contacto operativo. |
| correo | Email | Opcional | Facilita comunicación formal. |
| ciudad | Text | Opcional | Permite segmentar proveedores por ubicación. |
| estado | Enum | Activo/Inactivo | Permite mantener historial sin eliminar registros. |

---

### 12.2. Tabla `Materias_Primas`

| Campo | Tipo sugerido en AppSheet | Configuración | Justificación |
|---|---|---|---|
| id_materia_prima | Text | Key, Initial value: `UNIQUEID()` | Identifica cada insumo de manera única. |
| codigo_mp | Text | Opcional | Código interno legible para el negocio. |
| nombre_materia_prima | Text | Label, Required | Nombre visible del insumo. |
| categoria | Enum | Harinas, Lácteos, Endulzantes, Grasas, etc. | Facilita clasificación. |
| unidad_medida | Enum | kg, g, L, ml, unidad | Normaliza cantidades. |
| stock_inicial | Decimal | Valor inicial | Punto de partida para calcular inventario. |
| stock_minimo | Decimal | Valor de alerta | Permite identificar insumos por debajo del mínimo. |
| estado | Enum | Activa/Inactiva | Evita eliminar materias primas históricas. |

---

### 12.3. Tabla `Productos_Terminados`

| Campo | Tipo sugerido en AppSheet | Configuración | Justificación |
|---|---|---|---|
| id_producto | Text | Key, Initial value: `UNIQUEID()` | Identifica cada producto terminado. |
| codigo_producto | Text | Opcional | Código interno del producto. |
| nombre_producto | Text | Label, Required | Nombre visible en formularios y ventas. |
| categoria_producto | Enum | Panadería, Pastelería, Bebidas, Otros | Clasifica el portafolio. |
| unidad_venta | Enum | unidad, paquete, porción | Define cómo se vende. |
| precio_venta | Price | Required | Base para calcular ventas. |
| stock_inicial | Decimal | Valor inicial | Punto de partida para inventario. |
| stock_minimo | Decimal | Valor de alerta | Permite identificar agotados o bajos inventarios. |
| estado | Enum | Activo/Inactivo | Controla si se ofrece o no en ventas. |

---

### 12.4. Tabla `Recetas`

| Campo | Tipo sugerido en AppSheet | Configuración | Justificación |
|---|---|---|---|
| id_receta | Text | Key, Initial value: `UNIQUEID()` | Identifica cada relación producto-insumo. |
| id_producto | Ref | Referencia a `Productos_Terminados` | Indica a qué producto pertenece la receta. |
| id_materia_prima | Ref | Referencia a `Materias_Primas` | Indica qué insumo se requiere. |
| cantidad_por_unidad | Decimal | Required | Define la cantidad necesaria por unidad producida. |
| unidad_medida | Enum | kg, g, L, ml, unidad | Mantiene consistencia operativa. |
| observacion | LongText | Opcional | Permite aclaraciones técnicas. |

**Ejemplo conceptual:**

| Producto terminado | Materia prima | Cantidad por unidad |
|---|---|---:|
| Pan francés | Harina de trigo | 0,08 kg |
| Pan francés | Levadura seca | 0,002 kg |
| Croissant | Harina de trigo | 0,10 kg |
| Croissant | Mantequilla | 0,04 kg |

---

### 12.5. Tabla `Ingresos_MP`

| Campo | Tipo sugerido en AppSheet | Configuración | Justificación |
|---|---|---|---|
| id_ingreso_mp | Text | Key, Initial value: `UNIQUEID()` | Identifica cada ingreso de materia prima. |
| fecha_ingreso | Date | Required | Registra cuándo ingresó el insumo. |
| id_materia_prima | Ref | Referencia a `Materias_Primas` | Relaciona el movimiento con un insumo. |
| id_proveedor | Ref | Referencia a `Proveedores` | Permite trazabilidad del proveedor. |
| cantidad | Decimal | Required, Valid_If: `[_THIS] > 0` | Registra cantidad positiva ingresada. |
| costo_unitario | Price | Required | Permite valorar el ingreso. |
| costo_total | Price | App formula | Calcula el valor total del ingreso. |
| lote | Text | Opcional | Apoya trazabilidad sanitaria y operativa. |
| fecha_vencimiento | Date | Opcional | Importante en alimentos perecederos. |
| responsable | Enum | Lista de responsables | Identifica quién registró el ingreso. |

**Fórmula sugerida para `costo_total`:**

```appsheet
[cantidad] * [costo_unitario]
```

---

### 12.6. Tabla `Ordenes_Produccion`

| Campo | Tipo sugerido en AppSheet | Configuración | Justificación |
|---|---|---|---|
| id_orden_produccion | Text | Key, Initial value: `UNIQUEID()` | Identifica cada orden. |
| fecha_orden | Date | Required | Fecha de planeación o ejecución. |
| id_producto | Ref | Referencia a `Productos_Terminados` | Producto que será elaborado. |
| cantidad_planificada | Decimal | Required, Valid_If: `[_THIS] > 0` | Cantidad que se espera producir. |
| cantidad_producida | Decimal | Required, Valid_If: `[_THIS] >= 0` | Cantidad realmente obtenida. |
| estado_orden | Enum | Planificada, En proceso, Cerrada, Cancelada | Controla el ciclo de vida de la producción. |
| responsable | Enum | Lista de responsables | Identifica quién gestiona la orden. |
| observacion | LongText | Opcional | Permite registrar novedades. |

---

### 12.7. Tabla `Consumos_MP_OP`

| Campo | Tipo sugerido en AppSheet | Configuración | Justificación |
|---|---|---|---|
| id_consumo_mp | Text | Key, Initial value: `UNIQUEID()` | Identifica cada consumo. |
| id_orden_produccion | Ref | Referencia a `Ordenes_Produccion`, IsPartOf opcional | Asocia el consumo a una orden. |
| id_materia_prima | Ref | Referencia a `Materias_Primas` | Indica qué insumo se consumió. |
| cantidad_consumida | Decimal | Required, Valid_If: `[_THIS] > 0` | Registra consumo real. |
| costo_unitario_estimado | Price | Opcional | Permite estimar costo de producción. |
| costo_total_consumo | Price | App formula | Calcula costo estimado del consumo. |
| observacion | LongText | Opcional | Documenta desperdicios o ajustes. |

**Fórmula sugerida para `costo_total_consumo`:**

```appsheet
[cantidad_consumida] * [costo_unitario_estimado]
```

---

### 12.8. Tabla `Ventas`

| Campo | Tipo sugerido en AppSheet | Configuración | Justificación |
|---|---|---|---|
| id_venta | Text | Key, Initial value: `UNIQUEID()` | Identifica cada venta. |
| fecha_venta | DateTime | Required | Registra fecha y hora de la venta. |
| cliente | Text | Opcional | Permite registrar cliente si aplica. |
| medio_pago | Enum | Efectivo, Transferencia, Tarjeta, Mixto | Normaliza forma de pago. |
| responsable | Enum | Lista de responsables | Identifica quién registró la venta. |
| total_venta | Price | Virtual column o App formula | Suma los subtotales del detalle. |
| observacion | LongText | Opcional | Permite registrar novedades. |

---

### 12.9. Tabla `Detalle_Ventas`

| Campo | Tipo sugerido en AppSheet | Configuración | Justificación |
|---|---|---|---|
| id_detalle_venta | Text | Key, Initial value: `UNIQUEID()` | Identifica cada línea de venta. |
| id_venta | Ref | Referencia a `Ventas`, IsPartOf opcional | Asocia el detalle al encabezado. |
| id_producto | Ref | Referencia a `Productos_Terminados` | Producto vendido. |
| cantidad | Decimal | Required, Valid_If: `[_THIS] > 0` | Cantidad vendida. |
| precio_unitario | Price | Initial value o App formula | Precio del producto. |
| subtotal | Price | App formula | Calcula valor de la línea. |

**Fórmula sugerida para `subtotal`:**

```appsheet
[cantidad] * [precio_unitario]
```

**Fórmula sugerida para traer el precio de venta del producto:**

```appsheet
[id_producto].[precio_venta]
```

---

## 13. Preparación del archivo antes de crear la app

### Paso 1. Revisar nombres de hojas

Verifique que cada hoja tenga un nombre claro, sin caracteres extraños y sin duplicados.

**Hojas operativas mínimas:**

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

**Justificación:** AppSheet interpreta cada hoja como una posible tabla. Nombres consistentes facilitan la administración posterior de vistas, columnas y relaciones.

---

### Paso 2. Revisar encabezados de columnas

Cada hoja debe tener la primera fila con nombres de columnas. Se recomienda:

- No usar tildes en nombres técnicos de columnas.
- No usar espacios en nombres técnicos.
- Usar guion bajo para separar palabras.
- Usar nombres descriptivos.

**Ejemplo recomendado:**

```text
id_materia_prima
nombre_materia_prima
unidad_medida
stock_inicial
stock_minimo
```

**Ejemplo no recomendado:**

```text
ID Materia Prima
Nombre materia prima!!!
Stock mínimo actual aproximado
```

**Justificación:** los nombres técnicos limpios reducen errores al construir fórmulas y relaciones.

---

### Paso 3. Validar que las columnas de identificación existan

Cada tabla debe tener una columna identificadora única.

| Tabla | Columna identificadora |
|---|---|
| Proveedores | id_proveedor |
| Materias_Primas | id_materia_prima |
| Productos_Terminados | id_producto |
| Recetas | id_receta |
| Ingresos_MP | id_ingreso_mp |
| Ordenes_Produccion | id_orden_produccion |
| Consumos_MP_OP | id_consumo_mp |
| Ventas | id_venta |
| Detalle_Ventas | id_detalle_venta |

**Justificación:** una llave primaria permite identificar cada fila de manera única y relacionarla con otras tablas.

---

## 14. Creación de la app en AppSheet

### Paso 4. Subir el archivo a Google Drive

1. Ingrese a Google Drive.
2. Cree una carpeta llamada `AppSheet_Panaderia`.
3. Suba el archivo `plantilla_appsheet_panaderia.xlsx`.
4. Abra el archivo con Google Sheets o conviértalo a hoja de cálculo de Google si desea trabajar directamente con el ecosistema de Google.

**Justificación:** AppSheet puede crear aplicaciones desde fuentes de datos como hojas de cálculo. Usar Google Drive facilita la conexión, sincronización y edición de los datos.

---

### Paso 5. Crear una aplicación nueva

1. Ingrese a AppSheet.
2. Seleccione la opción para crear una nueva aplicación.
3. Elija la opción de crear app desde datos existentes.
4. Seleccione el archivo de la panadería ubicado en Google Drive.
5. Espere a que AppSheet genere la estructura inicial.

**Justificación:** crear la app desde una fuente de datos permite que AppSheet detecte columnas, tipos iniciales y vistas automáticas. Esto acelera la construcción del prototipo.

---

### Paso 6. Verificar tablas importadas

En AppSheet, ingrese a la sección de datos y revise que aparezcan las tablas operativas.

Las tablas mínimas que deben estar disponibles son:

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

Si alguna tabla no aparece, agréguela manualmente desde la fuente de datos.

**Justificación:** si una hoja no se importa como tabla, no podrá tener formularios, vistas ni relaciones dentro de la aplicación.

---

## 15. Configuración de columnas, llaves y etiquetas

### Paso 7. Configurar llaves primarias

Para cada tabla, configure como **Key** la columna correspondiente a su identificador.

| Tabla | Key |
|---|---|
| Proveedores | id_proveedor |
| Materias_Primas | id_materia_prima |
| Productos_Terminados | id_producto |
| Recetas | id_receta |
| Ingresos_MP | id_ingreso_mp |
| Ordenes_Produccion | id_orden_produccion |
| Consumos_MP_OP | id_consumo_mp |
| Ventas | id_venta |
| Detalle_Ventas | id_detalle_venta |

En cada campo identificador, configure:

```appsheet
Initial value: UNIQUEID()
```

**Justificación:** `UNIQUEID()` permite generar un identificador prácticamente único para cada nuevo registro. Esto evita depender de nombres o números manuales que pueden repetirse.

---

### Paso 8. Configurar etiquetas visibles

Configure como **Label** las columnas más comprensibles para el usuario.

| Tabla | Label recomendado |
|---|---|
| Proveedores | nombre_proveedor |
| Materias_Primas | nombre_materia_prima |
| Productos_Terminados | nombre_producto |
| Ordenes_Produccion | id_orden_produccion |
| Ventas | id_venta |

**Justificación:** el usuario operativo no debe seleccionar códigos técnicos difíciles de interpretar. Las etiquetas permiten mostrar nombres legibles en listas desplegables y referencias.

---

### Paso 9. Ocultar campos técnicos de ID en formularios

Para los campos `id_...`, configure que no se muestren en el formulario, pero que sigan existiendo como llaves internas.

Configuración sugerida:

```text
Show: desactivado en formularios
Editable: desactivado
Initial value: UNIQUEID()
```

**Justificación:** el usuario no necesita escribir ni modificar identificadores técnicos. Estos valores deben ser generados automáticamente por la aplicación.

---

## 16. Configuración de relaciones tipo Ref

### Paso 10. Configurar referencias entre tablas

Configure las siguientes columnas como tipo **Ref**:

| Tabla | Columna | Tabla referenciada |
|---|---|---|
| Recetas | id_producto | Productos_Terminados |
| Recetas | id_materia_prima | Materias_Primas |
| Ingresos_MP | id_materia_prima | Materias_Primas |
| Ingresos_MP | id_proveedor | Proveedores |
| Ordenes_Produccion | id_producto | Productos_Terminados |
| Consumos_MP_OP | id_orden_produccion | Ordenes_Produccion |
| Consumos_MP_OP | id_materia_prima | Materias_Primas |
| Detalle_Ventas | id_venta | Ventas |
| Detalle_Ventas | id_producto | Productos_Terminados |

**Justificación:** una columna tipo `Ref` guarda la llave de otra tabla y permite construir relaciones. Gracias a esto, se puede seleccionar una materia prima desde una lista en lugar de escribirla manualmente.

---

### Paso 11. Configurar relaciones padre-hijo con IsPartOf

En una primera versión, se recomienda activar **IsPartOf** en las siguientes columnas `Ref`:

| Tabla hija | Columna Ref | Tabla padre | Recomendación |
|---|---|---|---|
| Detalle_Ventas | id_venta | Ventas | Activar IsPartOf |
| Consumos_MP_OP | id_orden_produccion | Ordenes_Produccion | Activar IsPartOf |

**Justificación:** al activar esta opción, AppSheet puede mostrar el detalle dentro del formulario o vista del registro padre. Esto mejora la experiencia de usuario porque permite registrar una venta y sus productos asociados como parte de un mismo flujo.

---

## 17. Configuración de listas desplegables

### Paso 12. Configurar campos Enum

Use campos tipo **Enum** para datos que deben seleccionarse desde una lista controlada.

| Campo | Valores sugeridos |
|---|---|
| estado | Activo, Inactivo |
| estado_orden | Planificada, En proceso, Cerrada, Cancelada |
| medio_pago | Efectivo, Transferencia, Tarjeta, Mixto |
| unidad_medida | kg, g, L, ml, unidad |
| categoria_producto | Panadería, Pastelería, Bebidas, Otros |
| categoria_materia_prima | Harinas, Lácteos, Grasas, Endulzantes, Empaques, Otros |

**Justificación:** las listas desplegables reducen errores de digitación y permiten estandarizar la información. Por ejemplo, si se escribe `efectivo`, `Efectivo`, `efectibo` o `cash`, luego será difícil consolidar los reportes.

---

## 18. Configuración de fórmulas principales

### Paso 13. Fórmula para costo total de ingreso de materia prima

En la tabla `Ingresos_MP`, configure la columna `costo_total` con la siguiente fórmula:

```appsheet
[cantidad] * [costo_unitario]
```

**Justificación:** el valor total del ingreso depende de la cantidad comprada y el costo unitario. No debe digitarse manualmente porque podría generar errores.

---

### Paso 14. Fórmula para subtotal de venta

En la tabla `Detalle_Ventas`, configure la columna `subtotal` con:

```appsheet
[cantidad] * [precio_unitario]
```

**Justificación:** el subtotal de una línea de venta es el resultado de multiplicar la cantidad vendida por el precio unitario del producto.

---

### Paso 15. Fórmula para traer precio de venta del producto

En la tabla `Detalle_Ventas`, para la columna `precio_unitario`, puede configurar como valor inicial:

```appsheet
[id_producto].[precio_venta]
```

**Justificación:** cuando el usuario seleccione un producto terminado, la aplicación puede traer automáticamente el precio registrado en la tabla de productos. Esto agiliza la venta y reduce errores de digitación.

---

### Paso 16. Fórmula para total de venta

En la tabla `Ventas`, cree una columna virtual o una columna calculada llamada `total_venta`.

Use la siguiente expresión:

```appsheet
SUM(
  SELECT(
    Detalle_Ventas[subtotal],
    [id_venta] = [_THISROW].[id_venta]
  )
)
```

**Justificación:** una venta puede tener varios productos. El total de la venta debe sumar todos los subtotales registrados en `Detalle_Ventas` para esa venta específica.

---

### Paso 17. Fórmula para inventario estimado de materia prima

En la tabla `Materias_Primas`, cree una columna virtual llamada `stock_actual_mp`.

Use esta expresión:

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

**Justificación:** el inventario de materia prima no debe capturarse manualmente. Debe calcularse a partir de:

```text
Stock inicial + ingresos - consumos
```

Esta lógica representa el movimiento básico de inventario.

---

### Paso 18. Fórmula para inventario estimado de producto terminado

En la tabla `Productos_Terminados`, cree una columna virtual llamada `stock_actual_producto`.

Use esta expresión:

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

**Justificación:** el inventario de productos terminados debe aumentar cuando una orden de producción se cierra y debe disminuir cuando se registran ventas.

La lógica básica es:

```text
Stock inicial + producción cerrada - ventas
```

---

### Paso 19. Indicador de alerta para materia prima baja

En `Materias_Primas`, cree una columna virtual llamada `alerta_stock_mp`.

Use esta expresión:

```appsheet
IF(
  [stock_actual_mp] <= [stock_minimo],
  "Revisar compra",
  "Stock suficiente"
)
```

**Justificación:** este campo permite identificar rápidamente qué insumos están por debajo o cerca del mínimo operativo.

---

### Paso 20. Indicador de alerta para producto terminado bajo

En `Productos_Terminados`, cree una columna virtual llamada `alerta_stock_producto`.

Use esta expresión:

```appsheet
IF(
  [stock_actual_producto] <= [stock_minimo],
  "Revisar producción",
  "Stock suficiente"
)
```

**Justificación:** este indicador permite saber qué productos requieren nueva producción.

---

## 19. Validaciones recomendadas

### Paso 21. Validar cantidades positivas

Para campos como `cantidad`, `cantidad_planificada`, `cantidad_producida` y `cantidad_consumida`, use validaciones.

Ejemplo para campos que deben ser mayores que cero:

```appsheet
[_THIS] > 0
```

Ejemplo para campos que pueden ser cero o mayores:

```appsheet
[_THIS] >= 0
```

**Justificación:** no tiene sentido registrar cantidades negativas en compras, consumos, producción o ventas. La validación protege la calidad de los datos.

---

### Paso 22. Validar fechas de vencimiento

En `Ingresos_MP`, para `fecha_vencimiento`, puede usar:

```appsheet
OR(
  ISBLANK([_THIS]),
  [_THIS] >= [fecha_ingreso]
)
```

**Justificación:** una fecha de vencimiento no debería ser anterior a la fecha de ingreso, salvo que el campo esté vacío porque no aplica.

---

### Paso 23. Validar estados de orden

Para `estado_orden`, use una lista controlada:

```text
Planificada
En proceso
Cerrada
Cancelada
```

**Justificación:** el estado de una orden define si está en planeación, ejecución, cerrada o anulada. Esto afecta el cálculo de inventario de productos terminados porque solo se suma la producción cuando la orden está cerrada.

---

## 20. Construcción de formularios

### Paso 24. Formulario de proveedores

Configure un formulario para registrar proveedores con los siguientes campos visibles:

```text
nombre_proveedor
tipo_documento
numero_documento
telefono
correo
ciudad
estado
```

**Justificación:** el registro de proveedores es necesario antes de registrar ingresos de materia prima. Esto permite que cada compra quede asociada a un proveedor real.

---

### Paso 25. Formulario de materias primas

Campos visibles sugeridos:

```text
codigo_mp
nombre_materia_prima
categoria
unidad_medida
stock_inicial
stock_minimo
estado
```

**Justificación:** antes de registrar compras o consumos, el sistema debe conocer cuáles insumos existen y cómo se miden.

---

### Paso 26. Formulario de productos terminados

Campos visibles sugeridos:

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

**Justificación:** las ventas y órdenes de producción requieren un catálogo de productos terminados previamente definido.

---

### Paso 27. Formulario de recetas

Campos visibles sugeridos:

```text
id_producto
id_materia_prima
cantidad_por_unidad
unidad_medida
observacion
```

**Justificación:** la receta permite saber qué materias primas se requieren para elaborar un producto. Aunque en la primera versión el consumo real se registra manualmente, esta tabla sirve como referencia técnica para planear la producción.

---

### Paso 28. Formulario de ingreso de materia prima

Campos visibles sugeridos:

```text
fecha_ingreso
id_materia_prima
id_proveedor
cantidad
costo_unitario
lote
fecha_vencimiento
responsable
```

Campos calculados:

```text
costo_total
```

**Justificación:** este formulario representa la entrada de insumos al inventario. La información de lote y vencimiento es relevante porque se trata de productos alimentarios.

---

### Paso 29. Formulario de orden de producción

Campos visibles sugeridos:

```text
fecha_orden
id_producto
cantidad_planificada
cantidad_producida
estado_orden
responsable
observacion
```

**Justificación:** la orden de producción permite planear y documentar la transformación de materias primas en productos terminados.

---

### Paso 30. Formulario de consumo de materia prima por orden

Campos visibles sugeridos:

```text
id_orden_produccion
id_materia_prima
cantidad_consumida
costo_unitario_estimado
observacion
```

Campos calculados:

```text
costo_total_consumo
```

**Justificación:** este formulario registra el consumo real de insumos. Esto permite analizar desviaciones entre la receta y lo efectivamente consumido.

---

### Paso 31. Formulario de venta

Campos visibles sugeridos:

```text
fecha_venta
cliente
medio_pago
responsable
observacion
```

Campos calculados o virtuales:

```text
total_venta
```

**Justificación:** la venta representa el evento comercial. Separar el encabezado del detalle permite que una venta tenga múltiples productos.

---

### Paso 32. Formulario de detalle de venta

Campos visibles sugeridos:

```text
id_venta
id_producto
cantidad
precio_unitario
```

Campos calculados:

```text
subtotal
```

**Justificación:** este formulario permite registrar cada producto vendido dentro de una venta. El subtotal se calcula automáticamente para evitar errores aritméticos.

---

## 21. Diseño de vistas de usuario

### Paso 33. Crear vista principal de inicio

Cree una vista inicial tipo dashboard o menú, con accesos a:

```text
Materias primas
Productos terminados
Proveedores
Ingresos de materia prima
Órdenes de producción
Ventas
Inventario
```

**Justificación:** la navegación debe estar organizada alrededor de los procesos del negocio, no únicamente alrededor de tablas técnicas.

---

### Paso 34. Crear vista de proveedores

Tipo sugerido:

```text
Table
```

Columnas visibles:

```text
nombre_proveedor
telefono
correo
ciudad
estado
```

**Justificación:** una tabla permite revisar rápidamente los proveedores registrados.

---

### Paso 35. Crear vista de materias primas

Tipo sugerido:

```text
Deck o Table
```

Columnas visibles:

```text
nombre_materia_prima
categoria
unidad_medida
stock_actual_mp
stock_minimo
alerta_stock_mp
```

**Justificación:** esta vista permite revisar el estado del inventario de insumos.

---

### Paso 36. Crear vista de productos terminados

Tipo sugerido:

```text
Deck o Table
```

Columnas visibles:

```text
nombre_producto
categoria_producto
precio_venta
stock_actual_producto
stock_minimo
alerta_stock_producto
```

**Justificación:** esta vista permite revisar el portafolio de productos y su disponibilidad estimada.

---

### Paso 37. Crear vista de ingresos de materia prima

Tipo sugerido:

```text
Table
```

Columnas visibles:

```text
fecha_ingreso
id_materia_prima
id_proveedor
cantidad
costo_total
fecha_vencimiento
responsable
```

**Justificación:** esta vista permite auditar compras o entradas de insumos.

---

### Paso 38. Crear vista de órdenes de producción

Tipo sugerido:

```text
Deck
```

Columnas visibles:

```text
fecha_orden
id_producto
cantidad_planificada
cantidad_producida
estado_orden
responsable
```

**Justificación:** una vista tipo Deck facilita revisar el estado de cada orden de producción.

---

### Paso 39. Crear vista de ventas

Tipo sugerido:

```text
Table o Deck
```

Columnas visibles:

```text
fecha_venta
cliente
medio_pago
total_venta
responsable
```

**Justificación:** esta vista permite consultar la actividad comercial de la panadería.

---

### Paso 40. Crear dashboard operativo

Incluya vistas o gráficos relacionados con:

1. Ventas por fecha.
2. Productos con bajo inventario.
3. Materias primas con bajo inventario.
4. Órdenes de producción por estado.
5. Ingresos de materia prima recientes.

**Justificación:** el dashboard permite pasar de la captura de datos a la toma de decisiones. Aunque sea básico, ayuda a visualizar alertas y movimientos importantes.

---

## 22. Flujo funcional esperado de la aplicación

El flujo mínimo de operación debe ser el siguiente:

```text
1. Registrar proveedores
2. Registrar materias primas
3. Registrar productos terminados
4. Definir recetas
5. Registrar ingresos de materia prima
6. Crear orden de producción
7. Registrar consumos de materia prima asociados a la orden
8. Cerrar orden de producción
9. Registrar venta
10. Consultar inventarios y tablero
```

---

## 23. Prueba funcional guiada

### Escenario 1. Registro inicial de proveedor

**Acción:** registrar un proveedor llamado `Proveedor de Harinas La Espiga`.

**Datos sugeridos:**

| Campo | Valor |
|---|---|
| nombre_proveedor | Proveedor de Harinas La Espiga |
| tipo_documento | NIT |
| numero_documento | 900123456 |
| telefono | 3000000000 |
| correo | contacto@laespiga.com |
| ciudad | Bogotá |
| estado | Activo |

**Resultado esperado:** el proveedor queda disponible para seleccionarse en ingresos de materia prima.

---

### Escenario 2. Registro de materia prima

**Acción:** registrar la materia prima `Harina de trigo`.

| Campo | Valor |
|---|---|
| codigo_mp | MP-001 |
| nombre_materia_prima | Harina de trigo |
| categoria | Harinas |
| unidad_medida | kg |
| stock_inicial | 10 |
| stock_minimo | 5 |
| estado | Activa |

**Resultado esperado:** la materia prima queda disponible para ingresos, recetas y consumos.

---

### Escenario 3. Registro de producto terminado

**Acción:** registrar el producto `Pan francés`.

| Campo | Valor |
|---|---|
| codigo_producto | PT-001 |
| nombre_producto | Pan francés |
| categoria_producto | Panadería |
| unidad_venta | unidad |
| precio_venta | 800 |
| stock_inicial | 0 |
| stock_minimo | 20 |
| estado | Activo |

**Resultado esperado:** el producto queda disponible para recetas, órdenes de producción y ventas.

---

### Escenario 4. Registro de receta

**Acción:** asociar `Pan francés` con `Harina de trigo`.

| Campo | Valor |
|---|---|
| id_producto | Pan francés |
| id_materia_prima | Harina de trigo |
| cantidad_por_unidad | 0,08 |
| unidad_medida | kg |
| observacion | Cantidad estimada por unidad |

**Resultado esperado:** la app registra que cada unidad de pan francés requiere 0,08 kg de harina.

---

### Escenario 5. Registro de ingreso de materia prima

**Acción:** registrar compra de harina.

| Campo | Valor |
|---|---|
| fecha_ingreso | Fecha actual |
| id_materia_prima | Harina de trigo |
| id_proveedor | Proveedor de Harinas La Espiga |
| cantidad | 50 |
| costo_unitario | 3500 |
| lote | LOTE-001 |
| fecha_vencimiento | Fecha posterior |
| responsable | Operario 1 |

**Resultado esperado:** el `stock_actual_mp` de harina debe aumentar.

Cálculo esperado:

```text
Stock inicial: 10 kg
Ingreso: 50 kg
Consumo: 0 kg
Stock actual estimado: 60 kg
```

---

### Escenario 6. Creación de orden de producción

**Acción:** crear una orden para producir 100 unidades de pan francés.

| Campo | Valor |
|---|---|
| fecha_orden | Fecha actual |
| id_producto | Pan francés |
| cantidad_planificada | 100 |
| cantidad_producida | 100 |
| estado_orden | Cerrada |
| responsable | Panadero 1 |
| observacion | Producción inicial de prueba |

**Resultado esperado:** el inventario de producto terminado debe aumentar en 100 unidades, siempre que la orden quede en estado `Cerrada`.

---

### Escenario 7. Registro de consumo de materia prima

**Acción:** registrar consumo de harina para la orden de producción.

| Campo | Valor |
|---|---|
| id_orden_produccion | Orden creada |
| id_materia_prima | Harina de trigo |
| cantidad_consumida | 8 |
| costo_unitario_estimado | 3500 |
| observacion | Consumo según receta |

**Resultado esperado:** el inventario estimado de harina disminuye.

Cálculo esperado:

```text
Stock inicial: 10 kg
Ingreso: 50 kg
Consumo: 8 kg
Stock actual estimado: 52 kg
```

---

### Escenario 8. Registro de venta

**Acción:** registrar una venta de 10 panes franceses.

Encabezado de venta:

| Campo | Valor |
|---|---|
| fecha_venta | Fecha y hora actual |
| cliente | Cliente general |
| medio_pago | Efectivo |
| responsable | Cajero 1 |

Detalle de venta:

| Campo | Valor |
|---|---|
| id_producto | Pan francés |
| cantidad | 10 |
| precio_unitario | 800 |

**Resultado esperado:**

```text
Subtotal: 10 * 800 = 8.000
Total venta: 8.000
Stock producto terminado: 100 - 10 = 90 unidades
```

---

## 24. Criterios de aceptación de la primera versión

La aplicación se considera funcional si cumple los siguientes criterios:

| Código | Criterio de aceptación |
|---|---|
| CA-01 | Permite registrar proveedores con nombre, documento, contacto y estado. |
| CA-02 | Permite registrar materias primas con unidad, stock inicial y stock mínimo. |
| CA-03 | Permite registrar productos terminados con precio de venta, stock inicial y stock mínimo. |
| CA-04 | Permite asociar productos terminados con materias primas mediante recetas. |
| CA-05 | Permite registrar ingresos de materia prima asociados a proveedor y materia prima. |
| CA-06 | Calcula automáticamente el costo total del ingreso de materia prima. |
| CA-07 | Permite registrar órdenes de producción por producto. |
| CA-08 | Permite registrar consumo real de materia prima por orden de producción. |
| CA-09 | Permite registrar ventas con uno o varios productos terminados. |
| CA-10 | Calcula automáticamente subtotales por línea de venta. |
| CA-11 | Calcula automáticamente el total de la venta. |
| CA-12 | Calcula inventario estimado de materia prima. |
| CA-13 | Calcula inventario estimado de producto terminado. |
| CA-14 | Muestra alertas básicas cuando el stock está por debajo del mínimo. |
| CA-15 | Presenta vistas organizadas para proveedores, materias primas, productos, producción y ventas. |
| CA-16 | Permite realizar una prueba completa desde ingreso de materia prima hasta venta. |

---

## 25. Entregables del taller

Cada estudiante o grupo deberá entregar:

1. Enlace funcional de la app en AppSheet o evidencia de funcionamiento.
2. Archivo Excel o Google Sheets utilizado como fuente de datos.
3. Capturas de pantalla de las principales vistas.
4. Evidencia del flujo completo de prueba.
5. Documento breve de justificación técnica.
6. Video corto o sustentación donde se muestre la app funcionando.

---

## 26. Estructura sugerida para la sustentación

La sustentación puede organizarse en cinco momentos:

1. **Contexto del problema:** explicar la necesidad de la panadería.
2. **Modelo de datos:** presentar tablas, llaves y relaciones.
3. **Construcción en AppSheet:** mostrar configuración de tablas, formularios y vistas.
4. **Prueba funcional:** demostrar el flujo completo.
5. **Conclusiones:** explicar limitaciones y mejoras futuras.

---

## 27. Rúbrica sugerida de evaluación

| Criterio | Porcentaje | Nivel alto | Nivel medio | Nivel bajo |
|---|---:|---|---|---|
| Modelo de datos | 25% | Tablas, llaves y relaciones correctamente definidas. | Presenta estructura básica, pero con relaciones incompletas. | No diferencia correctamente entidades ni relaciones. |
| Configuración en AppSheet | 25% | La app tiene tablas, tipos de datos, referencias y formularios funcionales. | La app funciona parcialmente. | La app no permite ejecutar el flujo principal. |
| Fórmulas y cálculos | 20% | Calcula subtotales, totales e inventarios de forma coherente. | Algunos cálculos funcionan, pero hay errores parciales. | No implementa cálculos relevantes. |
| Experiencia de usuario | 15% | Vistas claras, navegación ordenada y formularios comprensibles. | Vistas básicas con algunos problemas de organización. | Navegación confusa o incompleta. |
| Sustentación y justificación | 15% | Explica con claridad decisiones técnicas y resultados. | Explica parcialmente la solución. | No justifica adecuadamente el diseño. |

---

## 28. Errores frecuentes y recomendaciones

### Error 1. Usar nombres como llaves primarias

**Problema:** usar `nombre_producto` como llave puede generar duplicados o errores si se cambia el nombre.

**Recomendación:** usar siempre un campo técnico como `id_producto` generado con `UNIQUEID()`.

---

### Error 2. Registrar productos vendidos directamente en la tabla Ventas

**Problema:** limita la venta a un solo producto o genera muchas columnas repetidas.

**Recomendación:** usar una tabla padre `Ventas` y una tabla hija `Detalle_Ventas`.

---

### Error 3. Editar manualmente el inventario actual

**Problema:** el inventario puede quedar inconsistente con los movimientos reales.

**Recomendación:** calcular inventario mediante ingresos, consumos, producción y ventas.

---

### Error 4. No configurar referencias

**Problema:** el usuario tendría que escribir nombres manualmente y podrían aparecer errores de digitación.

**Recomendación:** usar columnas tipo `Ref` para relacionar tablas.

---

### Error 5. No regenerar estructura después de cambiar el archivo fuente

**Problema:** AppSheet puede no reconocer columnas nuevas o modificadas.

**Recomendación:** después de cambiar columnas en la hoja de cálculo, regenerar la estructura de la tabla en AppSheet.

---

## 29. Mejoras futuras sugeridas

Después de completar la primera versión, se pueden proponer las siguientes mejoras:

1. Automatizar el consumo teórico de materias primas a partir de recetas.
2. Crear alertas automáticas de stock mínimo.
3. Implementar roles de usuario: administrador, panadero, cajero.
4. Registrar desperdicios o mermas.
5. Implementar control de lotes por fecha de vencimiento.
6. Agregar reportes por día, semana y mes.
7. Crear gráficos de productos más vendidos.
8. Agregar control de costos de producción.
9. Integrar código QR o código de barras para productos.
10. Exportar reportes a PDF.
11. Crear automatizaciones para enviar alertas por correo.
12. Diseñar un tablero externo en Looker Studio o Power BI.

---

## 30. Conclusión académica

La construcción de una aplicación de panadería en AppSheet permite integrar de manera práctica conceptos fundamentales de bases de datos, modelado relacional, procesos empresariales y desarrollo low-code. El caso evidencia que una solución digital no inicia con la pantalla, sino con una correcta identificación de entidades, atributos, relaciones y reglas de negocio.

La primera versión propuesta permite registrar proveedores, materias primas, productos terminados, ingresos, producción, consumos y ventas. Además, incorpora cálculos básicos de inventario y ventas, lo que convierte la aplicación en una herramienta inicial de apoyo a la gestión operativa.

Desde una perspectiva formativa, el ejercicio permite que el estudiante comprenda la relación entre datos, procesos y toma de decisiones. También muestra cómo una herramienta low-code puede acelerar el desarrollo de soluciones empresariales, siempre que exista un modelo de datos bien diseñado y una validación funcional rigurosa.

---

## 31. Referencias oficiales de apoyo

Las siguientes fuentes corresponden a documentación oficial de AppSheet consultada para estructurar las recomendaciones técnicas del taller:

1. Google AppSheet Help. **What is a key?**  
   https://support.google.com/appsheet/answer/10106672

2. Google AppSheet Help. **UNIQUEID()**  
   https://support.google.com/appsheet/answer/10108209

3. Google AppSheet Help. **References between tables**  
   https://support.google.com/appsheet/answer/10106510

4. Google AppSheet Help. **Use virtual columns**  
   https://support.google.com/appsheet/answer/10106758

5. Google AppSheet Help. **SUM()**  
   https://support.google.com/appsheet/answer/10107699

6. Google AppSheet Help. **Check form input validity (Valid_If)**  
   https://support.google.com/appsheet/answer/10107949

7. Google AppSheet Help. **Display a drop-down with a simple list of values**  
   https://support.google.com/appsheet/answer/10107878

8. Google AppSheet Help. **Dashboard view type**  
   https://support.google.com/appsheet/answer/10106384

9. Google AppSheet Help. **Add, reorder, or delete columns**  
   https://support.google.com/appsheet/answer/10106675

10. Google AppSheet Help. **Configure column properties**  
    https://support.google.com/appsheet/answer/10106509
