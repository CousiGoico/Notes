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

## Cómo organizar y automatizar el proyecto

### Controlar la visibilidad del proyecto

Tiene la capacidad de controlar si el proyecto es público o privado. Cuando el proyecto es público, todos los usuarios de Internet pueden verlo. Cuando el proyecto es privado, solo los usuarios con al menos acceso de lectura pueden verlo.

1. Vaya al proyecto.
2. En la parte superior derecha, seleccione los tres puntos en el menú superior y elija Configuración.
3. Desplácese hacia abajo hasta Zona de peligro y, en Visibilidad, seleccione Privado o Público en la lista desplegable.

### Administrar el acceso al proyecto

El acceso al proyecto dependerá de si se trata de un proyecto a nivel de organización o de uno a nivel personal o de usuario. La administración del acceso es similar entre los dos niveles.

Los administradores de proyectos a nivel de organización pueden administrar el acceso para toda la organización, para los equipos, para los miembros de la organización y para los colaboradores externos. Los administradores de los proyectos a nivel de usuario pueden invitar a los colaboradores individuales y administrar su acceso.

### Proyecto a nivel de organización

* Sin acceso: Solo los propietarios de la organización y los usuarios a los que se les ha otorgado acceso individual pueden ver el proyecto. Los propietarios de las organizaciones también son administradores del proyecto.
* Lectura: Todos los usuarios de la organización pueden ver el proyecto. Los propietarios de las organizaciones también son administradores del proyecto.
* Escritura: Todos los usuarios de la organización pueden ver y editar el proyecto. Los propietarios de las organizaciones también son administradores del proyecto.
* Administrador: Todos los usuarios de la organización son administradores del proyecto.

### Proyecto a nivel personal o de usuario

* Lectura: La persona puede ver el proyecto.
* Escritura: La persona puede ver y editar el proyecto.
* Administrador: La persona puede ver, editar y agregar nuevos colaboradores al proyecto.

### Invitar a colaboradores y cambiar roles

1. Vaya al proyecto.
2. En la parte superior derecha, seleccione los tres puntos para abrir el menú y elija Configuración.
3. En la barra de navegación izquierda, seleccione Administrar acceso.
4. Una vez en la página, puede:
    * Invitar a usuarios y equipos mediante la búsqueda en la barra de búsqueda Invitar colaboradores.
    * Cambie su rol o quítelos en Administrar el acceso.

### Agregar un proyecto a un equipo

1. En la esquina superior derecha de GitHub.com, seleccione su foto de perfil y elija Sus organizaciones.
2. Seleccione el nombre de la organización.
3. Vaya a la pestaña Equipos y seleccione el nombre del equipo al que desea conceder acceso.
4. Seleccione Proyectos y elija Vincular un proyecto.
5. Empiece a escribir el nombre del proyecto que quiera agregar y, luego, seleccione el proyecto en la lista de coincidencias.

### Agregar un proyecto a un repositorio

Puede enumerar los proyectos pertinentes en un repositorio para que el equipo pueda acceder a la información que necesita para mantenerse al día. Sin embargo, solo puede enumerar proyectos si el mismo usuario u organización posee los proyectos y el repositorio. Para que los miembros de los repositorios vean un proyecto que se lista en dichos repositorios, deben tener visibilidad del proyecto.

1. Vaya a la página principal del repositorio.
2. Seleccione la pestaña Proyectos y elija Vincular un proyecto.
3. Buscar proyectos que pertenezcan al mismo usuario u organización que el propietario del repositorio.
4. Seleccione un proyecto para mostrarlo en el repositorio.

### Cerrar y eliminar proyectos

Cerrar un proyecto permite quitarlo de la lista de proyectos, pero se conservan el contenido y la capacidad de volver a abrirlo más adelante. Se recomienda esta opción para conservar los datos.

La eliminación de un proyecto lo elimina permanentemente de la plataforma junto con las vistas guardadas, los campos personalizados y los valores asociados, los datos de las conclusiones y los problemas registrados.

1. Vaya al proyecto.
2. En la parte superior derecha, seleccione los tres puntos para abrir el menú y elija Configuración.
3. Desplácese hacia abajo hasta la sección Zona de peligro y seleccione Cerrar proyecto o Eliminar proyecto.
    * Al seleccionar Eliminar proyecto se le pide que lea las advertencias y, a continuación, escriba el nombre del proyecto en el cuadro de texto.

## Insight y automatización con Projects

### Insights y cómo pueden ser útiles

Insights con los proyectos le permite ver, crear y personalizar gráficos que utilizan elementos agregados a su Project como datos de origen. Al crear un gráfico, se establecen los filtros, el tipo de gráfico y la información mostrada. El gráfico está disponible para cualquiera que pueda ver el proyecto. Puede generar dos tipos de gráficos: gráficos actuales y gráficos históricos.

#### Gráficos actuales

Puede crear gráficos actuales para visualizar los elementos del proyecto. Puede crear gráficos para mostrar el número de elementos asignados a cada persona, o el número de problemas asignados a cada iteración próxima.

Puede utilizar filtros para manipular los datos utilizados para crear el gráfico. Puede crear un gráfico en el que se muestre la cantidad de trabajo pendiente, pero limitar esos resultados a etiquetas o usuarios asignados concretos.

#### Gráficos históricos

Los gráficos históricos están disponibles con GitHub Team y GitHub Enterprise Cloud para organizaciones. Los gráficos históricos son gráficos basados en el tiempo que permiten ver las tendencias y el progreso del proyecto. Puede ver el número de artículos a lo largo del tiempo agrupados por estado y otros campos. El gráfico Burn up por defecto muestra el estado de los artículos a lo largo del tiempo, lo que le permite visualizar el progreso y detectar patrones.

### Crear y personalizar gráficos

Crear el gráfico:

1. Vaya al proyecto.
2. En la parte superior derecha, seleccione el botón del gráfico de líneas. Al pasar el ratón por encima del botón, aparece la etiqueta Insights.
3. En el menú de la izquierda, seleccione Nuevo gráfico.
4. Filtre por palabra clave o campo para cambiar los datos utilizados para crear el gráfico.
5. A la derecha del cuadro de texto del filtro, seleccione Guardar.

Personalizar el gráfico:

1. En el menú de la izquierda, seleccione el gráfico que desea configurar.
2. En la parte derecha de la página, seleccione Configurar, y se abrirá un panel.
3. Seleccione el menú desplegable Diseño para cambiar el tipo de gráfico que desea utilizar.
4. Seleccione el menú desplegable del eje X y elija el campo que desea utilizar.
5. Opcionalmente, seleccione Agrupar por para agrupar elementos en su eje X. Elija el campo que desea utilizar o Ninguno para deshabilitar la agrupación.

### Automatización con Projects

* Flujos de trabajo automatizados integrados
* GraphQL API
* Acciones de GitHub con flujos de trabajo

La forma más sencilla de automatizar su proyecto son los flujos de trabajo integrados. GraphQL y Acciones dan más control sobre la personalización de la automatización. 

#### Configurar flujos de trabajo integrados

Su proyecto toma las incidencias o solicitudes de incorporación de cambios recién creadas y las coloca automáticamente en su proyecto con el estado Todo. 

1. En la esquina superior derecha de su proyecto, seleccione el menú de tres puntos y elija Flujos de trabajo.
2. En la columna izquierda, en Flujos de trabajo predeterminados, seleccione Elemento agregado al proyecto.
3. Seleccione el botón Editar para realizar cambios en el flujo de trabajo.
4. En la sección **Cuando se agrega un elemento al proyecto**, asegúrese de que tanto las incidencias como las solicitudes de incorporación de cambios están seleccionadas.
5. En la sección Establecer valor, seleccione **Estado: Todo**.
6. Seleccione **Guardar y activar el flujo de trabajo**.

#### Acciones de GitHub con flujos de trabajo

Acciones de GitHub permite la mayor personalización para la automatización de sus proyectos. Puede usar Acciones de GitHub para automatizar las tareas de administración de proyectos mediante la creación de flujos de trabajo. Cada flujo de trabajo contiene una serie de tareas que se llevan a cabo automáticamente cada que se ejecuta el flujo de trabajo. Un flujo de trabajo de ejemplo se activa al crear una incidencia, añade una etiqueta, deja un comentario y mueve la incidencia a un panel de proyecto.

La creación de una incidencia desencadena un flujo de trabajo que agrega una etiqueta, deja un comentario y mueve la incidencia a un tablero de proyecto.

#### GraphQL API

Si utiliza GraphQL en GitHub, puede utilizar una API para automatizar su proyecto.