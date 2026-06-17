# 2. Contexto del taller

[Volver al README](./README.md) · [Abrir la plantilla Excel](./plantilla_appsheet_panaderia.xlsx) · [Continuar con la guía](./3_Guia_paso_a_paso.md)

## 1. Identificación

**Nombre:** Desarrollo de una aplicación no-code para la gestión básica de una panadería  
**Herramienta:** Google AppSheet  
**Fuente de datos:** [plantilla_appsheet_panaderia.xlsx](./plantilla_appsheet_panaderia.xlsx)  
**Nivel:** introductorio–intermedio  
**Modalidad:** práctica guiada con sustentación funcional  
**Duración:** 4 a 6 horas de construcción y 2 horas de prueba y ajuste.

## 2. Objetivo general

Construir una aplicación funcional en AppSheet que permita gestionar de manera básica proveedores, materias primas, productos terminados, recetas, ingresos de insumos, órdenes de producción, consumos y ventas, aplicando modelado relacional, configuración de columnas, formularios, validaciones, expresiones, vistas y una prueba de extremo a extremo.

## 3. Objetivos específicos

Al finalizar el taller, el estudiante estará en capacidad de:

1. Diferenciar tablas maestras, transaccionales y de detalle.
2. Configurar llaves, etiquetas y referencias en AppSheet.
3. Crear formularios controlados para la operación.
4. Implementar expresiones para costos, ventas e inventarios estimados.
5. Diseñar vistas y un tablero básico de consulta.
6. Validar el flujo desde la compra de insumos hasta la venta.
7. Sustentar las decisiones técnicas y reconocer las limitaciones del prototipo.

## 4. Situación problemática

Una panadería registra información en cuadernos y archivos aislados. Esta práctica dificulta conocer las materias primas disponibles, los proveedores asociados, los productos elaborados, los consumos por producción, las ventas y las existencias estimadas.

Se requiere un prototipo que centralice la captura y consulta de la información operativa. La solución no reemplaza un ERP, un sistema contable ni una plataforma de facturación electrónica. Su propósito es demostrar cómo un modelo de datos bien estructurado puede convertirse en una aplicación funcional mediante una plataforma no-code.

## 5. Alcance funcional

La primera versión deberá permitir:

- Registrar y consultar proveedores.
- Registrar y consultar materias primas.
- Registrar y consultar productos terminados.
- Definir recetas por producto.
- Registrar ingresos de materia prima.
- Crear y actualizar órdenes de producción.
- Registrar consumos reales asociados a una orden.
- Registrar ventas con uno o varios productos.
- Calcular subtotales y total de la venta.
- Calcular inventarios estimados de materias primas y productos terminados.
- Mostrar alertas básicas de stock.
- Presentar vistas operativas y un tablero de consulta.

## 6. Fuera de alcance

No se exige:

- Facturación electrónica.
- Contabilidad formal.
- Nómina.
- Impuestos.
- Pasarelas de pago.
- Método PEPS/FIFO por lote.
- Impresión POS.
- Integración con dispositivos externos.
- Automatizaciones avanzadas.
- Control detallado de costos indirectos.
- Uso productivo con información real.

## 7. Competencias

| Competencia | Evidencia |
|---|---|
| Modelado de datos | Tablas, llaves y relaciones coherentes. |
| Pensamiento lógico | Expresiones y validaciones correctas. |
| Construcción no-code | App funcional en web o móvil. |
| Gestión de información | Captura normalizada y trazable. |
| Pruebas funcionales | Flujo completo documentado. |
| Comunicación técnica | Sustentación de decisiones y limitaciones. |

## 8. Estructura de datos

| Tabla | Tipo | Propósito |
|---|---|---|
| `Proveedores` | Maestra | Datos de los proveedores. |
| `Materias_Primas` | Maestra | Insumos utilizados en producción. |
| `Productos_Terminados` | Maestra | Productos disponibles para venta. |
| `Recetas` | Asociación | Materias primas requeridas por producto. |
| `Ingresos_MP` | Transaccional | Entradas de materias primas. |
| `Ordenes_Produccion` | Transaccional | Producción planificada y ejecutada. |
| `Consumos_MP_OP` | Detalle | Consumos reales por orden. |
| `Ventas` | Transaccional | Encabezado de la venta. |
| `Detalle_Ventas` | Detalle | Productos y cantidades de una venta. |

## 9. Relaciones

```text
Proveedores 1 ─── N Ingresos_MP
Materias_Primas 1 ─── N Ingresos_MP
Productos_Terminados 1 ─── N Recetas
Materias_Primas 1 ─── N Recetas
Productos_Terminados 1 ─── N Ordenes_Produccion
Ordenes_Produccion 1 ─── N Consumos_MP_OP
Materias_Primas 1 ─── N Consumos_MP_OP
Ventas 1 ─── N Detalle_Ventas
Productos_Terminados 1 ─── N Detalle_Ventas
```

## 10. Flujo funcional

```text
Proveedores y catálogos
        ↓
Ingreso de materias primas
        ↓
Definición de recetas
        ↓
Orden de producción
        ↓
Registro de consumos
        ↓
Cierre de producción
        ↓
Venta y detalle
        ↓
Consulta de inventarios y tablero
```

## 11. Criterios de aceptación

| Código | Criterio |
|---|---|
| CA-01 | La app permite registrar proveedores con identificador automático. |
| CA-02 | La app permite registrar materias primas y productos terminados. |
| CA-03 | Las relaciones se presentan mediante listas legibles y no mediante digitación libre de llaves. |
| CA-04 | Una receta asocia un producto con una o varias materias primas. |
| CA-05 | Un ingreso de materia prima queda relacionado con un proveedor y un insumo. |
| CA-06 | El costo total del ingreso se calcula automáticamente. |
| CA-07 | Una orden de producción queda relacionada con un producto. |
| CA-08 | Los consumos pueden agregarse como registros hijos de la orden. |
| CA-09 | Una venta puede incluir uno o varios detalles. |
| CA-10 | El precio unitario se obtiene del producto y el subtotal se calcula automáticamente. |
| CA-11 | El total de la venta corresponde a la suma de los subtotales. |
| CA-12 | El inventario estimado de materia prima refleja ingresos menos consumos. |
| CA-13 | El inventario estimado de producto refleja producción cerrada menos ventas. |
| CA-14 | Las cantidades inválidas son rechazadas por las reglas de validación. |
| CA-15 | La aplicación presenta vistas de consulta y un tablero básico. |
| CA-16 | El flujo integral se ejecuta sin errores de referencia ni de expresión. |
| CA-17 | El panel de errores no presenta errores bloqueantes. |
| CA-18 | Se ejecuta la comprobación de despliegue antes de publicar o sustentar. |

## 12. Datos de prueba recomendados

Los registros deben identificarse explícitamente como datos de prueba. Ejemplo:

| Entidad | Valor de prueba |
|---|---|
| Proveedor | `PROVEEDOR_PRUEBA_01` |
| Documento | `NIT-PRUEBA-001` |
| Correo | `proveedor.prueba@example.com` |
| Materia prima | `Harina de trigo - prueba` |
| Producto | `Pan de prueba` |
| Lote | `LOTE-PRUEBA-001` |
| Responsable | `USUARIO_PRUEBA_01` |

No se deben usar números de identificación, teléfonos, correos personales o información comercial reales.

## 13. Prueba de extremo a extremo

La evidencia debe demostrar:

1. Creación o consulta de un proveedor de prueba.
2. Creación o consulta de una materia prima.
3. Registro de un ingreso.
4. Creación o consulta de un producto terminado.
5. Definición de una receta.
6. Registro de una orden cerrada.
7. Registro de consumo de materia prima.
8. Registro de una venta y su detalle.
9. Verificación del total.
10. Verificación de los dos inventarios estimados.

## 14. Entregables

- Enlace funcional de la app o evidencia de acceso.
- Copia de la fuente de datos utilizada.
- Capturas de las vistas principales.
- Evidencia de la prueba funcional.
- Documento breve de decisiones técnicas.
- Sustentación o video demostrativo.

## 15. Rúbrica

| Criterio | Peso | Desempeño esperado |
|---|---:|---|
| Modelo de datos | 25 % | Llaves, referencias y cardinalidades correctas. |
| Configuración de AppSheet | 25 % | Tablas, columnas y formularios funcionales. |
| Expresiones y validaciones | 20 % | Cálculos correctos y captura controlada. |
| Experiencia de usuario | 15 % | Navegación clara, vistas pertinentes y tablero legible. |
| Prueba y sustentación | 15 % | Flujo completo, evidencia y justificación técnica. |

## 16. Mejoras posteriores

- Consumo teórico generado desde recetas.
- Control de mermas.
- Costeo de producción.
- Alertas automáticas.
- Roles por perfil.
- Seguridad por usuario.
- Manejo de lotes y vencimientos.
- Reportes PDF.
- Tablero analítico en Looker Studio o Power BI.
