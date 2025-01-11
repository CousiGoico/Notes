# Gestiona tu trabajo con GitHub Projects

## Projects en comparación con Projects (clásico)

### Projects en comparación con Projects (clásico)

||Proyectos|Projects(clásico)|
|-|--------|-----------------|
|Tablas y paneles|Paneles, listas, diseño de escala de tiempo|Boards|
|data|Ordena, clasifica y agrupa elementos por campos personalizados, como texto, número, fecha, iteración y selección única|Columnas y tarjetas|
|Información detallada|Crea objetos visuales para ayudar a comprender el trabajo mediante gráficos históricos y actuales con proyectos|Barra de progreso|
|Automatización|Usa los valores preestablecidos de GraphQL API, Acciones y Columna para administrar el proyecto|Configura los valores preestablecidos de columna para cuando se agregan, editan o cierran problemas y solicitudes de incorporación de cambios (PR)|

### Listas completas de mejoras de Projects

#### Tablas y paneles

* Planeación y seguimiento del trabajo en una vista de tabla o panel
* Clasificación, ordenación y agrupación dentro de una tabla mediante cualquier campo personalizado
* Creación de problemas de borrador con descripciones detalladas y metadatos
* Materialización de cualquier perspectiva con filtrado tokenizado y vistas guardadas
* Personalización de tarjetas y agrupación en paneles de Projects
* Actualizaciones de Projects en tiempo real e indicadores de presencia de usuario

#### data

* Definición de campos personalizados del tipo: texto, número, fecha, iteración y selección única
* Configuración de iteraciones con intervalos de fechas flexibles y saltos para representar los sprints, ciclos u hoja de ruta trimestral
* Visualización de solicitudes de incorporación de cambios vinculadas y revisores en las vistas de tabla y panel

#### Conclusión

* Creación y configuración de gráficos de barras, columnas, líneas y áreas apiladas personalizados
* Uso de funciones de agregación como sum, count, average, min y max para obtener la información adecuada
* Conservación de gráficos y uso compartido de estos con una dirección URL para que todos los usuarios estén al tanto

#### Automatización

* GraphQL ProjectsV2 API
* Ámbitos del proyecto de aplicación de GitHub
* Eventos de webhooks para actualizaciones de metadatos de elementos de proyectos
* Acción de GitHub para automatizar la adición de problemas a Projects

## Creación de un proyecto

### Creación de un proyecto de nivel de organización

1. En la esquina superior derecha de GitHub.com, seleccione la foto del perfil y después, seleccione Sus organizaciones.
2. Desplácese hacia abajo para seleccionar la organización del nuevo Proyecto.
3. Vaya desde la pestañaInformación general a la pestaña Proyectos.
4. Seleccione el botón verde etiquetado Nuevo proyecto.
5. Un elemento emergente le pide que seleccione una plantilla o empiece desde cero. Vamos a elegir la opción Iniciar desde cero y seleccionar Tabla.
6. Seleccione el botón verde Crear proyecto.

### Establecer el nombre, la descripción y el ARCHIVO LÉAME del proyecto

1. Vaya al proyecto recién creado para editar el nombre, la descripción y el ARCHIVO LÉAME del proyecto.
2. En la parte superior derecha de la página, seleccione los tres puntos para abrir el menú y seleccione Configuración.
3. Nombre del proyecto es donde se edita el nombre del proyecto.
4. Descripción breve le permite agregar algunas palabras sobre el proyecto.
5. README le permite agregar información a su equipo para comprender por qué ha creado este Proyecto y lo que espera lograr con él. Una vez finalizado, seleccione Guardar cambios.

### Adición de problemas y solicitudes de incorporación de cambios al Proyecto

#### Adición de un problema existente y una solicitud de incorporación de cambios

1. Copie la dirección URL de un problema o una solicitud de incorporación de cambios existentes.
2. Coloque el cursor en la fila inferior del proyecto junto al + y pegue la dirección URL del problema o la solicitud de incorporación de cambios.
3. Presione Entrar y el problema o la solicitud de incorporación de cambios aparece como una tarea en el proyecto.

#### Buscar un problema existente y una solicitud de incorporación de cambios

1. Escriba # para buscar repositorios. Puede teclear la parte del nombre de repositorio para reducir sus opciones.
2. Seleccione el repositorio donde se encuentra la solicitud de incorporación de cambios o el problema, que solicita buscar problemas y solicitudes de incorporación de cambios.
3. Comience a escribir el título del problema o la solicitud de incorporación de cambios para encontrar el que desee.
4. Seleccione la propuesta o solicitud de cambios.

#### Incorporación masiva de problemas y solicitudes de incorporación de cambios

1. Seleccione + en la fila inferior del proyecto.
2. Seleccione Agregar elemento desde el repositorio.
3. Para cambiar el repositorio, seleccione la lista desplegable y elija un repositorio. A continuación, se rellenan los problemas y las solicitudes de incorporación de cambios.
4. Puede seleccionar todos o seleccionar esos problemas o las solicitudes de incorporación de cambios que quiera incluir.
5. Una vez que esté listo para agregar los problemas y las solicitudes de incorporación de cambios al proyecto, seleccione el botón verde titulado Agregar elementos seleccionados en la esquina inferior derecha.

## Cómo organizar el proyecto

### Creación de un campo para realizar un seguimiento y agrupar por prioridad

1. En la vista de tabla, en el encabezado de campo situado más a la derecha, seleccione +.
2. Seleccione Nuevo campo.
3. Escriba el nombre del campo. En este caso, es Prioridad.
4. Seleccione la lista desplegable Tipo de campo.
5. Para crear su propia clasificación para el nuevo campo, seleccione la opción Único.
6. En el cuadro de texto Opciones, empiece a agregar los distintos niveles de prioridad. Puede etiquetarlos como Urgente, Alta, Media y Baja.
7. Seleccione Guardar.

Ahora que tiene configurada la clasificación de prioridad, debe clasificar los problemas y las solicitudes de incorporación de cambios en función de la prioridad. Para realizar una clasificación, seleccione el problema o la solicitud de incorporación de cambios que desea clasificar en la fila de campo titulada Prioridad. Ahora, en el campo desplegable, seleccione la prioridad que quiere elegir para esta incidencia o solicitud de cambios concreta.

Agrupar las incidencias y las solicitudes de cambios por prioridad para que sea más fácil centrarse en los elementos urgentes y de prioridad alta.

1. Seleccione la flecha hacia abajo situada junto al nombre de la vista abierta actualmente.
2. Seleccione la opción Agrupar por.
3. Seleccione Prioridad.

### Agregar un campo de iteración

1. Para agregar un campo de iteración, vaya a la vista de tabla del proyecto.
2. En el encabezado de campo situado más a la derecha, seleccione +.
3. Seleccione Nuevo campo.
4. Agregue un Nombre de campo, como Project Phase o Sprint.
5. En Tipo de campo, seleccione Iteración.
6. Elija una fecha de inicio.
7. Cambie la Duración de cada iteración escribiendo un nuevo número y seleccione la lista desplegable para días o semanas como se indica a continuación.
8. Seleccione Guardar y crear.

### Creación de una vista de placa

1. En la vista abierta actualmente, seleccione la flecha hacia abajo.
2. En Diseño, seleccione Panel. Al cambiar el diseño, el proyecto muestra un indicador para mostrar la vista que se modificó.
3. Seleccione el botón Guardar situado en la parte superior derecha del panel.
4. Puede cambiar el nombre de la vista haciendo doble clic en la pestaña de la vista y seleccionando fuera de la pestaña para guardarla automáticamente.
5. Tenga en cuenta que estos pasos también se pueden realizar seleccionando Nueva vista a la derecha de las vistas existentes.
