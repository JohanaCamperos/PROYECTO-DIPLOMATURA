# 🛡️ Central de Seguridad - Sistema de Control Interno (Web App)

Aplicación web integral diseñada para correr sobre la arquitectura de **Google Apps Script**, utilizando **Google Sheets** como base de datos persistente. Su función principal es la recolección, distribución, visualización y gestión de novedades en tiempo real para una empresa de seguridad a distancia, segmentando los accesos de forma estricta según las áreas de trabajo.

---

## 📊 Arquitectura de Datos (Google Sheets)

Para el correcto funcionamiento del sistema, el libro de Google Sheets activo debe contener exactamente tres pestañas con las siguientes columnas estructuradas en la primera fila:

1. **`Usuarios`**
   * Columnas: `Usuario` | `Email` | `Password` | `Area` | `TempPassword` (TRUE/FALSE)
2. **`Informes`**
   * Columnas: `ID` | `Fecha` | `Hora` | `AreaDestino` | `Código` | `TextoLibre` | `UsuarioOrigen`
3. **`Respuestas`**
   * Columnas: `ID_Informe` | `AreaRespuesta` | `TextoRespuesta` | `UsuarioRespuesta`

---

## 🚀 Características Clave

* **One Page Login:** Menú central interactivo corporativo para segmentar accesos por áreas (`Monitoreo`, `Operaciones`, `Técnica`, `Comercial`).
* **Administrador Global:** Permite al rol de supervisión ingresar sin restricciones y simular entornos mediante un selector vivo en la barra de navegación para verificar la operación de cada área.
* **Seguridad Avanzada:** Contraseñas temporales autogeneradas enviadas por correo electrónico, con política estricta de cambio obligado en el primer ingreso (Mínimo 6 caracteres, alfanumérica y al menos una mayúscula).
* **Bandeja de Notificaciones Desplegable:** Diseño limpio según requerimientos tácticos con flechas `▼` interactivas para leer texto libre y enviar respuestas (Máx. 100 caracteres) sin recargar la página.
* **Filtros de Búsqueda Independientes:** Motor de búsqueda capaz de segmentar por rangos de fecha, rango de horas en formato militar (`HH:MM`) o códigos de edificio de forma aislada o combinada.
* **Visualizador en Tiempo Real (Monitoreo):** Panel dinámico que lista cronológicamente todos los informes levantados durante el día actual en curso (00:00 a 23:59).
* **Tablas Ordenables:** Columnas de datos (`Código`, `Fecha`, `Hora`, `Área`) ordenables de forma ascendente y descendente con un solo clic.
* **Experiencia de Usuario Fluida (No Alerts):** Reemplazo absoluto de ventanas emergentes molestas por un sistema nativo de notificaciones *Toast* desvanecibles a los 3.5 segundos. Soporte nativo para inicio de sesión mediante la tecla `Enter`.

---

## 🛠️ Instrucciones de Instalación y Despliegue

1. Cree una hoja de cálculo en **Google Sheets** y configure las 3 pestañas mencionadas en la sección de *Arquitectura de Datos*.
2. Diríjase a la barra superior y seleccione **Extensiones** > **Apps Script**.
3. En el entorno de desarrollo de Apps Script, configure los siguientes 4 archivos respetando mayúsculas y minúsculas de manera estricta:
   * `Código.gs` (Código de Servidor)
   * `Index.html` (Estructura de Interfaz)
   * `Styles.html` (Estilos Visuales Corporativos)
   * `JavaScript.html` (Lógica de Cliente e Interacciones)
4. Presione el ícono del **Disco (Guardar Proyecto)** para asegurar la compilación de la función `doGet()`.
5. Haga clic en **Implementar** > **Nueva implementación** (Esquina superior derecha).
6. Seleccione el engranaje de configuración y elija **Aplicación Web**.
7. Configure las propiedades de ejecución de la siguiente forma:
   * **Ejecutar como:** Tu cuenta (Tu correo institucional).
   * **Quién tiene acceso:** Cualquiera.
8. Haga clic en **Implementar**, autorice los permisos requeridos por Google utilizando su cuenta y copie la **URL de la aplicación web** generada.

> ⚠️ **Nota Operativa Importante:** Cada vez que realice modificaciones en cualquiera de los archivos del código, es obligatorio dirigirse a *Gestionar implementaciones*, editar la versión activa seleccionando **Nueva versión** e implementar nuevamente para forzar la limpieza de la caché de datos en los navegadores de los operadores.

---

## 🎨 Paleta de Colores Corporativa
* **Principal:** Azul Rey corporativo y variantes oscuras (`Slate-900`, `Slate-800`, `Slate-950`).
* **Acentuaciones:** Rojo Alerta para paneles de novedades, Verde Esmeralda para despachos exitosos y Naranja de Inspección para los filtros de búsqueda.