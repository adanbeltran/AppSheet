# Taller académico: aplicación de gestión para una panadería con AppSheet

**Versión del material:** 2.0  
**Revisión de vigencia:** 17 de junio de 2026  
**Herramienta:** Google AppSheet, editor mejorado actual  
**Nivel:** introductorio–intermedio  
**Duración sugerida:** 4 a 6 horas de trabajo guiado y 2 horas de prueba, ajuste y sustentación.

> **Nota de vigencia:** AppSheet es un servicio en la nube con actualización continua y no se distribuye mediante un número de versión de escritorio convencional. Este material fue revisado con la documentación oficial disponible al 17 de junio de 2026. Las rutas emplean la navegación vigente del editor: **Data, App, Actions, Automation, Security, Settings y Manage**. Las denominaciones **UX** y **Behavior** solo se mencionan como equivalencias del editor heredado.



<img width="1055" height="1491" alt="7fea3867-4f57-44ce-b857-9b8f01c9ff8f" src="https://github.com/user-attachments/assets/2fe64f63-897a-423c-b7e3-f5c6374748e0" />


## Objetivo del taller

Construir y validar una primera versión funcional de una aplicación en AppSheet para apoyar la gestión básica de una panadería, utilizando un modelo de datos relacional que permita registrar proveedores, materias primas, productos terminados, recetas, ingresos de insumos, órdenes de producción, consumos y ventas; configurar llaves, referencias, formularios, validaciones, cálculos de inventario estimado y vistas de consulta; y ejecutar una prueba integral desde el ingreso de materia prima hasta la venta del producto terminado.

## Recursos del taller

| Recurso | Propósito |
|---|---|
| [Plantilla Excel para AppSheet](./plantilla_appsheet_panaderia.xlsx) | Fuente estructurada con las tablas, datos de prueba, modelo de datos, expresiones y documentación de apoyo. |
| [1. Conceptos Básicos de AppSheet](./1_Conceptos_Basicos_de_AppSheet.md) | Explica la arquitectura de AppSheet, el editor vigente, las fuentes de datos, las llaves, referencias, expresiones, vistas, seguridad y despliegue. |
| [2. Contexto del taller](./2_Contexto_del_taller.md) | Presenta el caso de la panadería, el alcance, los objetivos, las competencias, los criterios de aceptación, los entregables y la rúbrica. |
| [3. Guía paso a paso](./3_Guia_paso_a_paso.md) | Orienta la construcción completa de la aplicación con las rutas actuales del editor de AppSheet. |

## Ruta recomendada

1. Extraiga todos los archivos del paquete en una misma carpeta para conservar los hipervínculos relativos.
2. Lea **Conceptos Básicos de AppSheet**.
3. Revise el **Contexto del taller** y los criterios de aceptación.
4. Abra la **Plantilla Excel** y examine las hojas `README`, `Modelo_Datos` y `Guia_AppSheet`.
5. Ejecute la **Guía paso a paso**.
6. Realice la prueba funcional completa y documente los resultados.

## Producto final esperado

Una aplicación AppSheet operativa, conectada a la plantilla suministrada o a una copia convertida a Google Sheets, con tablas relacionadas, formularios de captura, cálculos de costos e inventarios estimados, vistas de consulta, un tablero básico y una prueba funcional documentada.

## Criterio de uso de la plantilla

El archivo contiene datos de prueba claramente identificados. No deben utilizarse datos personales reales, credenciales, información financiera sensible ni datos productivos durante la construcción y validación académica.

## Lista mínima de verificación

- [ ] Las nueve tablas operativas están agregadas a la aplicación.
- [ ] Cada tabla tiene una llave estable generada con `UNIQUEID()`.
- [ ] Las columnas de relación están configuradas como `Ref`.
- [ ] `Detalle_Ventas[id_venta]` y `Consumos_MP_OP[id_orden_produccion]` funcionan como relaciones padre–hijo.
- [ ] Los subtotales, totales e inventarios estimados se calculan sin digitación manual.
- [ ] Las vistas principales permiten registrar y consultar la operación.
- [ ] La prueba de extremo a extremo finaliza sin errores.
- [ ] Se ejecutó **Manage > Deploy > Deployment Check** antes de la sustentación o publicación.
