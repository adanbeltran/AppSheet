<!-- Documento Markdown autocontenido. Las imágenes están incrustadas como datos Base64. -->

# Guía académica: menú de inicio y prueba de una aplicación en AppSheet

## Introducción

En esta actividad se construirá una pantalla inicial para la aplicación de gestión de una panadería. Esta pantalla funcionará como un **menú principal** desde el cual el usuario podrá acceder a módulos como proveedores, materias primas, productos, producción y ventas.

Aunque en ocasiones se denomina “formulario de inicio”, técnicamente se implementará como una vista **Gallery** de AppSheet, porque su función es navegar entre páginas y no capturar información. Al finalizar, la aplicación se compartirá y se probará tanto en un navegador web como en un dispositivo móvil.

## Objetivo

Crear un menú principal gráfico en AppSheet, configurarlo como pantalla de inicio, enlazarlo con las vistas de la aplicación y comprobar su funcionamiento en navegador y móvil.

## Resultado esperado

Al abrir la aplicación, el usuario debe visualizar un menú con iconos. Al seleccionar una opción, AppSheet debe abrir el módulo correspondiente.

---

## 1. Crear la hoja `MENU_INICIAL`

Abra el archivo de Google Sheets conectado con la aplicación y cree una hoja llamada:

```text
MENU_INICIAL
```

Agregue las siguientes columnas:

| Columna | Función |
|---|---|
| `ID_MENU` | Identifica cada opción del menú. |
| `MENU` | Nombre que verá el usuario. |
| `VISTA` | Nombre exacto de la vista que debe abrirse. |
| `IMAGEN` | Icono que representa la opción. |

Ejemplo:

| ID_MENU | MENU | VISTA | IMAGEN |
|---:|---|---|---|
| 1 | Proveedores | Proveedores | proveedores.png |
| 2 | Materias primas | Materias_Primas | materias_primas.png |
| 3 | Productos | Productos_Terminados | productos.png |
| 4 | Producción | Ordenes_Produccion | produccion.png |
| 5 | Ventas | Ventas | ventas.png |

> Los valores de la columna `VISTA` deben coincidir exactamente con los nombres de las vistas creadas en AppSheet.

<img width="357" height="416" alt="figura_01_crear_menu_inicial" src="https://github.com/user-attachments/assets/521c22ce-9f3f-49b3-934d-72771944afe6" />


*Figura 1. Creación de la hoja `MENU_INICIAL` en Google Sheets.*

---

## 2. Agregar `MENU_INICIAL` como tabla

En el editor de AppSheet:

1. Ingrese a **Data**.
2. Presione el símbolo **`+`**.
3. Seleccione el archivo de datos de la panadería.
4. Agregue la hoja `MENU_INICIAL`.
5. Verifique que aparezca en el panel de tablas.

Configure las columnas así:

| Columna | Tipo | Configuración |
|---|---|---|
| `ID_MENU` | Number o Text | Activar **Key**. |
| `MENU` | Text | Activar **Label**. |
| `VISTA` | Text | Mantener visible y editable. |
| `IMAGEN` | Image | Cambiar el tipo a **Image**. |

La tabla puede configurarse como **Read-only**, debido a que los usuarios no necesitan modificar las opciones del menú desde la aplicación.

> Para agregar una hoja nueva se utiliza **Data > +**. La opción **Regenerate schema** solo actualiza las columnas de una tabla que ya fue agregada.

<img width="722" height="356" alt="figura_02_configurar_columnas" src="https://github.com/user-attachments/assets/e960f80c-23b5-4fe7-96dc-cf14819aacff" />


*Figura 2. Configuración de las columnas de `MENU_INICIAL`.*

---

## 3. Preparar los iconos

Utilice imágenes PNG o JPG con una apariencia uniforme.

Recomendaciones:

- emplear iconos cuadrados y de tamaño similar;
- utilizar nombres sencillos, sin tildes ni espacios;
- guardar las imágenes en Google Drive;
- seleccionar cada archivo mediante AppSheet o escribir su nombre relativo en la columna `IMAGEN`.

Ejemplo:

```text
proveedores.png
```

Antes de continuar, confirme en la vista previa que AppSheet muestra correctamente los iconos.

---

## 4. Verificar las vistas de destino

Ingrese a:

```text
App > Views
```

Compruebe que existan las vistas indicadas en la columna `VISTA`, por ejemplo:

```text
Proveedores
Materias_Primas
Productos_Terminados
Ordenes_Produccion
Ventas
```

Si cambia el nombre de una vista en AppSheet, también debe actualizarlo en la hoja `MENU_INICIAL`.

---

## 5. Crear la acción `IR_A_VISTA`

La acción permitirá abrir la vista indicada en cada fila del menú.

1. Ingrese a **Actions**.
2. Seleccione **Create a new action**.
3. Configure:

| Propiedad | Valor |
|---|---|
| Action name | `IR_A_VISTA` |
| For a record of this table | `MENU_INICIAL` |
| Do this | `App: go to another view within this app` |
| Target | `LINKTOVIEW([VISTA])` |
| Position | `Hide` o `Do not display` |

Expresión:

```appsheet
LINKTOVIEW([VISTA])
```

La acción no necesita aparecer como botón, porque se ejecutará cuando el usuario seleccione una opción del menú.

<img width="469" height="314" alt="figura_03_crear_accion_ir_a_vista" src="https://github.com/user-attachments/assets/362b40da-a334-46ba-a06d-fc9539444dfe" />


*Figura 3. Configuración de la acción `IR_A_VISTA`.*

---

## 6. Crear la vista `MENU_INICIO`

1. Ingrese a **App > Views**.
2. Cree una nueva vista.
3. Configure:

| Propiedad | Valor |
|---|---|
| View name | `MENU_INICIO` |
| For this data | `MENU_INICIAL` |
| View type | `Gallery` |
| Position | `Primary` o `Menu` |
| Image | `IMAGEN` |
| Título visible | `MENU` |

En:

```text
Behavior > Event actions > Row selected
```

seleccione:

```text
IR_A_VISTA
```

Con esta configuración, al seleccionar un icono se abrirá la vista indicada en la columna `VISTA`.

<img width="560" height="434" alt="figura_04_crear_vista_menu_inicio" src="https://github.com/user-attachments/assets/fda9be7f-2b93-4f29-80f6-0df6171fc84b" />


*Figura 4. Creación de la vista `MENU_INICIO` y asociación de la acción.*

---

## 7. Configurar el menú como pantalla inicial

1. Ingrese a **Settings**.
2. Abra **Views: General**.
3. En **Starting view**, seleccione:

```text
MENU_INICIO
```

4. Desactive **Start with About**, si aparece habilitado.
5. Presione **Save**.

<img width="562" height="467" alt="figura_05_configurar_vista_inicial" src="https://github.com/user-attachments/assets/859ca972-e67c-436f-9e3b-e59ffa04760e" />


*Figura 5. Configuración de `MENU_INICIO` como pantalla inicial.*

---

## 8. Probar el menú en el editor

Desde la vista previa de AppSheet:

1. recargue la aplicación;
2. confirme que la primera pantalla sea `MENU_INICIO`;
3. seleccione cada icono;
4. verifique que se abra la vista correcta;
5. regrese al menú y repita la prueba con todas las opciones.

Corrija en Google Sheets cualquier nombre de vista que no coincida.

---

## 9. Configurar el acceso

Antes de compartir la aplicación:

1. ingrese a **Security**;
2. revise la opción **Require sign-in**;
3. para el taller, mantenga el inicio de sesión habilitado;
4. guarde la aplicación.

Los estudiantes o usuarios que prueben la app deben utilizar una cuenta autorizada.

<img width="818" height="475" alt="figura_06_configurar_seguridad" src="https://github.com/user-attachments/assets/3a635c3d-ee72-46a8-aafd-1796df3b9566" />

*Figura 6. Revisión del inicio de sesión antes de compartir la aplicación.*

---

## 10. Compartir la aplicación

1. Presione **Save**.
2. Seleccione el icono **Share**, representado por una persona con el signo `+`.
3. Escriba los correos de los usuarios autorizados.
4. Presione **Share**.
5. Seleccione **Share links**.

<img width="255" height="140" alt="figura_07_compartir_aplicacion" src="https://github.com/user-attachments/assets/219147b4-1fdf-4c59-bada-bab42ba3f996" />


*Figura 7. Autorización de usuarios y acceso a los enlaces.*

---

## 11. Seleccionar el enlace correcto

AppSheet muestra diferentes enlaces:

| Enlace | Uso |
|---|---|
| **Install on mobile** | Abrir o instalar el acceso a la app en Android o iOS. |
| **Open in browser** | Ejecutar la aplicación desde un navegador. |
| **View/copy or edit** | Abrir el editor; solo debe usarse por el creador o un colaborador. |

> No comparta la dirección del editor que contiene `/template/AppDef?`. Los usuarios deben recibir **Open in browser** o **Install on mobile**.

<img width="185" height="172" alt="figura_08_enlaces_de_uso" src="https://github.com/user-attachments/assets/a952a0de-f1ad-4f94-b4f1-5b9bd5b08750" />


*Figura 8. Enlaces para móvil, navegador y editor.*

---

## 12. Prueba en navegador

1. Copie el enlace **Open in browser**.
2. Ábralo en una ventana de incógnito o en otro perfil del navegador.
3. Inicie sesión con un correo autorizado.
4. Compruebe que aparezca `MENU_INICIO`.
5. Abra todas las opciones del menú.
6. Registre un dato de prueba en uno de los módulos.
7. Confirme que el registro se guarde y aparezca en la fuente de datos.

---

## 13. Prueba en dispositivo móvil

1. Envíe al usuario el enlace **Install on mobile**.
2. Abra el enlace desde el teléfono.
3. Inicie sesión con la cuenta autorizada.
4. Compruebe que el menú se adapte correctamente a la pantalla.
5. Verifique la legibilidad de los iconos y los títulos.
6. Abra cada módulo.
7. Registre un dato de prueba.
8. Sincronice la aplicación y confirme el registro en Google Sheets.

---

## 14. Lista de verificación

La actividad se considera terminada cuando se cumpla lo siguiente:

- [ ] La hoja `MENU_INICIAL` está agregada como tabla.
- [ ] `ID_MENU` es la llave y `MENU` es la etiqueta.
- [ ] `IMAGEN` está configurada como tipo `Image`.
- [ ] La acción `IR_A_VISTA` contiene `LINKTOVIEW([VISTA])`.
- [ ] La vista `MENU_INICIO` es de tipo `Gallery`.
- [ ] El evento **Row selected** ejecuta `IR_A_VISTA`.
- [ ] `MENU_INICIO` está configurada como **Starting view**.
- [ ] Todos los iconos abren la vista correcta.
- [ ] La aplicación funciona desde **Open in browser**.
- [ ] La aplicación funciona desde **Install on mobile**.
- [ ] El enlace del editor no fue compartido con usuarios finales.

## Evidencia de entrega

El estudiante debe presentar:

1. captura de la hoja `MENU_INICIAL`;
2. captura del menú funcionando;
3. captura de una vista abierta desde el menú;
4. evidencia de prueba en navegador;
5. evidencia de prueba en dispositivo móvil.
