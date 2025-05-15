# Projects

## Contenido

- [Introducción](#introducción)
  - [Creación un proyecto](#creación-un-proyecto)
    - [Crear un proyecto organizacional](#crear-un-proyecto-organizacional)
    - [Crear un proyecto usuario](#crear-un-proyecto-usuario)
    - [Actualizar la descripción y el README de tu proyecto](#actualizar-la-descripción-y-el-readme-de-tu-proyecto)
  - [Adición de metedatos a los elementos](#adcición-de-metadatos-a-los-elementos)
  - [Eliminación de campos personalizados](#eliminación-de-campos-personalizados)
  - [Automatización de los proyectos](#automatización-de-los-proyectos)
    - [Habilitación de un flujo de trabajo integrado](#habilitación-de-un-flujo-de-trabajo-integrado)
  - [Archivado automático de elementos](#archivado-automático-de-elementos)
    - [Configuración del archivado automático en el proyecto](#configuración-del-archivado-automático-en-el-proyecto)
- [Filtrado de projects](#filtrado-de-projects)
  - [Filtrado por campos](#filtrado-por-campos)
  - [Combinación de filtros](#combinación-de-filtros)
  - [Negación de un filtro](#negación-de-un-filtro)
  - [Filtrado de elementos que tienen un valor](#filtrado-de-elementos-que-tienen-un-valor)
  - [Filtrado de elementos a los que les falta un valor](#filtrado-de-elementos-a-los-que-les-falta-un-valor)
  - [Filtrado de elementos negando la falta de un valor](#filtrado-de-elementos-negando-la-falta-de-un-valor)
  - [Filtrado por ubicación de elemento](#filtrado-por-ubicación-de-elemento)
  - [Filtrado por estado del elemento o tipo de elemento](#filtrado-por-estado-del-elemento-o-tipo-de-elemento)
  - [Filtrado por motivo de cierre](#filtrado-por-motivo-de-cierre)
  - [Filtrado por cuándo se actualizó por última vez un elemento](#filtrado-por-cuándo-se-actualizó-por-última-vez-un-elemento)
  - [Filtrado por campos de número, fecha e iteración](#filtrado-por-campos-de-número-fecha-e-iteración)
  - [Filtrado de revisores y usuarios asignados mediante palabras clave](#filtrado-de-revisores-y-usuarios-asignados-mediante-palabras-clave)
  - [Filtrado de campos de iteración y fecha mediante palabras clave](#filtrado-de-campos-de-iteración-y-fecha-mediante-palabras-clave)
  - [Filtrado por campos de texto](#filtrado-por-campos-de-texto)
  - [Filtrado por tipo de incidencia](#filtrado-por-tipo-de-incidencia)
  - [Filtrado por incidencia primaria](#filtrado-por-incidencia-primaria)
- [Gráficos](#gráficos)
  - [Creación de gráficos](#creación-de-gráficos)
  - [Gráficos históricos](#gráficos-históricos)
- [Referencias](#referencias)

## Introducción

Un proyecto es una hoja de cálculo adaptable, panel de tareas y hoja de ruta que se integra con las incidencias y PR en GitHub para ayudarte a planear y realizar el seguimiento del trabajo de forma eficaz. Puedes crear y personalizar varias vistas mediante el filtrado, la ordenación y la agrupación de tus incidencias y solicitudes de incorporación de cambios, visualizar el trabajo con gráficos configurables y la adición de campos personalizados para realizar el seguimiento de metadatos específicos del equipo.

### Creación un proyecto

Projects son una colección adaptable de elementos que permanecen actualizados con los datos de GitHub. Tus proyectos pueden realizar el seguimiento de incidencias, solicitudes de incorporación de cambios e ideas que anotes. Puedes agregar campos personalizados y vistas creativas para propósitos específicos.

También puedes optar por usar un proyecto existente como plantilla y copiar las vistas y los campos personalizados en un nuevo proyecto.

#### Crear un proyecto organizacional

1. En la esquina superior derecha de GitHub, selecciona la foto del perfil y haz clic en `Tus organizaciones`.

2. Haz clic en el nombre de tu organización.

3. En el nombre de la organización, haz clic en `Proyectos`.

4. Haz clic en `Nuevo proyecto`.

5. Selecciona el tipo de proyecto o plantilla que quieras usar.

    - Para crear un proyecto en blanco, en “Comienzo desde cero”, haz clic en `Tabla`, `Plan de desarrollo` o `Panel`.
    - Para crear un proyecto a partir de una plantilla, haz clic en la plantilla que quieras usar. Puedes seleccionar entre las plantillas integradas mantenidas por GitHub, las plantillas creadas por la organización y las plantillas recomendadas elegidas por la organización.

6. Opcionalmente, si seleccionaste una plantilla, revisa los campos, las vistas, los flujos de trabajo y la información que se creará.

7. En el cuadro de texto de “Nombre del proyecto”, escribe un nombre para el nuevo proyecto.

8. Haga clic en `Crear proyecto`.

#### Crear un proyecto usuario

1. En la esquina superior derecha de GitHub, haga clic en su foto de perfil y luego en `Your profile` (Su perfil).

2. En el perfil, haga clic en `Proyectos`.

3. Haz clic en `Nuevo proyecto`.

4. Selecciona el tipo de proyecto o plantilla que quieras usar.

    - Para crear un proyecto en blanco, en “Comienzo desde cero”, haz clic en `Tabla`, `Plan de desarrollo` o `Panel`.
    - Para crear un proyecto a partir de una plantilla, haz clic en la plantilla integrada que quieras usar.

5. Opcionalmente, si seleccionaste una plantilla, revisa los campos, las vistas, los flujos de trabajo y la información que se creará.

6. En el cuadro de texto de “Nombre del proyecto”, escribe un nombre para el nuevo proyecto.

7. Haga clic en `Crear proyecto`.

#### Actualizar la descripción y el README de tu proyecto

1. Navegar a tu proyecto.

2. En la parte superior derecha, haga clic en ... para abrir el menú.

3. En el menú, haga clic en `Configuración` para acceder a la configuración del proyecto.

4. Para agregar una descripción breve al proyecto, en "Add a description", escriba la descripción en el cuadro de texto y haga clic en `Save`.

5. Para actualizar el archivo Léame del proyecto, en "README", escriba el contenido en el cuadro de texto.

    - Puede dar formato al archivo Léame mediante Markdown. Para más información, consulta Sintaxis de escritura y formato básicos.
    - Para alternar entre el cuadro de texto y una vista previa de los cambios, haga clic en el icono de visualizar o editar.

6. Para guardar los cambios en el archivo Léame, haga clic en `Save`.

### Adcición de metadatos a los elementos

Puedes usar campos personalizados para agregar metadatos a incidencias, solicitudes de incorporación de cambios y borradores de incidencias, y crear una vista más completa de los atributos de los elementos.

- Campo de fecha para realizar un seguimiento de las fechas de envío de destino.
- Campo numérico para realizar un seguimiento de la complejidad de una tarea.
- Un único campo de selección para realizar un seguimiento de si una tarea es baja, media o alta prioridad.
- Un campo de texto para agregar una nota rápida.
- Un campo de iteración para planear el trabajo semana a semana, incluida la compatibilidad con interrupciones.

### Eliminación de campos personalizados

1. Navegar a tu proyecto.

2. En la parte superior derecha, haga clic en ... para abrir el menú.

3. En el menú, haga clic en el icono `Configuración` para acceder a la configuración del proyecto.

4. Haz clic en el nombre del campo personalizado que quieras eliminar.

5. Haz clic en `Eliminar` campo.

### Automatización de los proyectos

En Projects se incluyen flujos de trabajo integrados que puedes usar para actualizar el estado de los elementos en función de determinados eventos.

Cuando se inicializa el proyecto, se habilitan dos flujos de trabajo de forma predeterminada: cuando se cierran las incidencias o las solicitudes de incorporación de cambios en el proyecto, su estado se establece en `Done` y, cuando se combinan las solicitudes de incorporación de cambios en el proyecto, su estado también se establece en `Done`.

También puede configurar flujos de trabajo para archivar automáticamente los elementos cuando cumplen los criterios establecidos y para agregar automáticamente elementos de un repositorio cuando coinciden con un filtro.

Hay varias maneras de agregar automatización al proyecto. Los flujos de trabajo integrados permiten establecer automáticamente campos cuando se agregan o cambian elementos, y también se puede configurar el proyecto para archivar automáticamente los elementos cuando cumplan ciertos criterios y agregar automáticamente elementos de un repositorio cuando cumplan criterios establecidos. También puedes usar GraphQL API y GitHub Actions para tomar un mayor control del proyecto.

#### Habilitación de un flujo de trabajo integrado

1. Navegar a tu proyecto.

2. En la parte superior derecha, haz clic en ... para abrir el menú.

3. En el menú, haz clic en `Flujos de trabajo`.

4. En "Default workflows", haga clic en el flujo de trabajo que quiera editar.

5. En la parte superior derecha, haga clic en `Edit`.

6. En función del flujo de trabajo seleccionado, realiza cambios en los campos para configurar el comportamiento del flujo de trabajo.

7. Para guardar los cambios y habilitar el flujo de trabajo, haga clic en `Save and turn on workflow`.

### Archivado automático de elementos

Puedes configurar los flujos de trabajo integrados del proyecto para archivar automáticamente los elementos. Un elemento archivado conserva todos sus datos de campo personalizados y se puede ver o restaurar desde la página de archivo.

El flujo de trabajo de archivado automático admite un subconjunto de filtros. Puedes usar los filtros siguientes al configurar el flujo de trabajo.

|Calificador|Valores posibles|
|-----------|----------------|
|`is`|`open`, `closed`, `merged`, `draft`, `issue`, `pr`|
|`reason`|`completed`, `reopened`, `"not planned"`|
|`updated`|`<@today-14d` (los últimos 14 días), `<@today-3w` (las últimas tres semanas), `<@today-1m` (el último mes)|

GitHub marca un problema o una solicitud de incorporación de cambios al actualizarse cuando es:

- Creado
- Reabierto
- Editado
- Comentado
- Etiquetado
- Los usuarios asignados se actualizan
- Los hitos se actualizan
- Transferido a otro repositorio

El proyecto puede contener hasta 50.000 elementos tanto en vistas activas como en la página de archivo. Una vez alcanzado el límite, deberás eliminar elementos del proyecto para liberar más espacio.

#### Configuración del archivado automático en el proyecto

1. Navegar a tu proyecto.

2. En la parte superior derecha, haz clic en ... para abrir el menú.

3. En el menú, haz clic en `Flujos de trabajo`.

4. En la lista "Flujos de trabajo predeterminados", haz clic en `Archivado automático de elementos`.

5. En la parte superior derecha, haga clic en `Edit`.

6. En el campo "Filtros", escribe los criterios de filtro que quieres usar para archivar elementos de forma automática. Solo puedes usar los filtros `is`, `reason` y `updated`.

7. Para guardar los cambios y habilitar el flujo de trabajo, haga clic en `Save and turn on workflow`.

## Filtrado de projects

Puedes personalizar qué elementos aparecen en las vistas mediante filtros para los metadatos de elementos, como los usuarios asignados y las etiquetas aplicadas a incidencias, así como por los campos del proyecto. Puede combinar filtros y guardarlos como vistas.

Para filtrar una vista, haz clic en el icono de filtrado y empieza a escribir los campos y valores por los que quieres filtrar. En el diseño del tablero, puedes hacer clic en los datos del elemento o filtrar los elementos con este valor. El uso de varios filtros actuará como un filtro AND lógico. Por ejemplo, `label:bug status:"In progress"` devolverá elementos con la etiqueta `bug` y el estado "En curso".

Los mismos filtros están disponibles para los gráficos que se crean mediante conclusiones para Projects, lo que te permite filtrar los datos usados para crear los gráficos.

### Filtrado por campos

|Calificador|Ejemplo|
|-----------|-------|
|`assignee:USERNAME`|assignee:octocat mostrará los elementos asignados a @octocat.|
|`label:LABEL`|label:bug mostrará los elementos con la etiqueta "bug" aplicada.|
|`field:VALUE`|status:done mostrará los elementos con el campo "status" establecido en "done".|
|`reviewers:USERNAME`|reviewers:octocat mostrará los elementos revisados por @octocat.|
|`milestone:"MILESTONE"`|milestone:"QA release" mostrará los elementos asignados al hito "QA release".|

### Combinación de filtros

|Descripción|Calificador|Ejemplo|
|-----------|-----------|-------|
|Coincidan con todos los filtros|`assignee:USERNAME field:VALUE`|assignee:octocat priority:1 mostrará los elementos asignados a @octocat que tienen una prioridad de 1.|
|Coincidan con cualquiera de los valores proporcionados.|`assignee:USERNAME,USERNAME`|assignee:octocat,stevecat mostrará los elementos asignados a @octocat o @stevecat.|
|Coincidan con todos los valores proporcionados|`assignee:USERNAME assignee:USERNAME`|assignee:octocat assignee:stevecat mostrará los elementos asignados a @octocat y @stevecat.|
|Coincidan con algunos y que coincidan con todos los elementos|`field:VALUE,VALUE assignee:USER assignee:USER`|	label:bug,onboarding assignee:octocat assignee:stevecat mostrará los elementos que tienen las etiquetas de error o incorporación, pero que están asignados a @octocat y @stevecat.|

### Negación de un filtro

|Calificador|Ejemplo|
|-----------|-------|
|`-assignee:USERNAME`|-assignee:octocat no mostrará ningún elemento asignado a 
@octocat.|
|`-field:VALUE`|-status:done no mostrará ningún elemento con el estado "done".|
|`-field:VALUE,VALUE`|-priority:1,2 no mostrará ningún elemento con una prioridad de 1 o 2.|

### Filtrado de elementos que tienen un valor

|Calificador|Ejemplo|
|-----------|-------|
|`has:assignee`|has:assignee mostrará elementos con un receptor.|
|`has:label`|has:label mostrará elementos con una etiqueta.|
|`has:FIELD`|has:priority mostrará elementos con un valor de campo de prioridad.|

### Filtrado de elementos a los que les falta un valor

|Calificador|Ejemplo|
|-----------|-------|
|`no:assignee`|no:assignee mostrará los elementos sin asignar.|
|`no:label`|no:reviewers mostrará las solicitudes de incorporación de cambios que no tienen un revisor.|
|`no:FIELD`|no:priority mostrará elementos con un campo de prioridad vacío.|

### Filtrado de elementos negando la falta de un valor

|Calificador|Ejemplo|
|-----------|-------|
|`-no:assignee`|-no:assignee solo mostrará los elementos asignados.|
|`-no:FIELD`|-no:priority solo mostrará los elementos que tienen un valor en el campo de prioridad.|

### Filtrado por ubicación de elemento

|Calificador|Ejemplo|
|-----------|-------|
|`repo:OWNER/REPO`|repo:octocat/game mostrará elementos en el repositorio "octocat/game".|

### Filtrado por estado del elemento o tipo de elemento

|Calificador|Ejemplo|
|-----------|-------|
|`is:STATE`|is:open mostrará incidencias y solicitudes de incorporación de cambios abiertas. - is:closed mostrará incidencias y solicitudes de incorporación de cambios cerradas. - is:merged mostrará las solicitudes de incorporación de cambios combinadas.|
|`is:TYPE`|is:issue mostrará solo las incidencias. - is:pr mostrará solo las solicitudes de incorporación de cambios. - is:draft mostrará los borradores de incidencias y los borradores de solicitudes de incorporación de cambios. - is:issue is:open mostrará las incidencias abiertas.|

### Filtrado por motivo de cierre

|Calificador|Ejemplo|
|-----------|-------|
|`reason:CLOSE REASON`|reason:completed mostrará los elementos cerrados porque se completaron. - reason:"not planned" mostrará los elementos cerrados con el motivo "not planned". - reason:reopened mostrará los elementos que se han vuelto a abrir después de cerrarse anteriormente.|

### Filtrado por cuándo se actualizó por última vez un elemento

|Calificador|Ejemplo|
|-----------|-------|
|`updated:NUMBERdays`|updated:@today mostrará los elementos actualizados hoy. - updated:@today-1d mostrará los elementos actualizados hace un día. - updated:>@today-1w mostrará los elementos que se actualizaron por última vez hace siete días o más. - updated:>@today-30d mostrará los elementos que se actualizaron por última vez hace treinta días o más. - -updated:@today mostrará los elementos actualizados otro día diferente a hoy.|

GitHub marca un problema o una solicitud de incorporación de cambios al actualizarse cuando es:

- Creado
- Reabierto
- Editado
- Comentado
- Etiquetado
- Los usuarios asignados se actualizan
- Los hitos se actualizan
- Transferido a otro repositorio

### Filtrado por campos de número, fecha e iteración

Puedes usar >, >=, < y <= para comparar los campos de número, fecha e iteración. Las fechas deben proporcionarse en el formato YYYY-MM-DD.

|Calificador|Ejemplo|
|-----------|-------|
|`field:>VALUE`|priority:>1 mostrará los elementos con una prioridad mayor que 1.|
|`field:>=VALUE`|date:>=2022-06-01 mostrará elementos con una fecha de "2022-06-01" o posterior.|
|`field:<VALUE`|iteración:<"Iteración 5" mostrará elementos con una iteración antes de "Iteration 5".|
|`field:<=VALUE`|points:<=10 mostrará elementos con 10 o menos puntos.|

También puedes usar .. para filtrar por un intervalo inclusivo. Cuando se trabaja con un intervalo, * se puede proporcionar como operador comodín.

|Calificador|Ejemplo|
|-----------|-------|
|`field:VALUE..VALUE`|priority:1..3 mostrará elementos con una prioridad de 1, 2 o 3. - date:2022-01-01..2022-12-31 mostrará elementos del año 2022. - points:*.. 10 mostrará los elementos con un valor de puntos de cualquier cosa hasta e incluyendo 10. - iteration:"Iteration 1..Iteration 4" mostrará elementos en "Iteration 1", "Iteration 2", "Iteration 3" y "Iteration 4".|

### Filtrado de revisores y usuarios asignados mediante palabras clave

Puedes usar la palabra clave `@me` para representarte en un filtro.

|Calificador|Ejemplo|
|-----------|-------|
|`field:@me`|assignee:@me mostrará los elementos asignados al usuario que ha iniciado sesión. - -reviewers:@me mostrará los elementos que el usuario que ha iniciado sesión no ha revisado.|

### Filtrado de campos de iteración y fecha mediante palabras clave

Puedes usar las palabras clave `@previous`, `@current` y `@next` para filtrar por las iteraciones relativas a la iteración actual. También puedes usar @today para filtrar por el día actual.

|Calificador|Ejemplo|
|-----------|-------|
|`field:@keyword`|iteration:@current mostrará los elementos asignados a la iteración actual. - iteration:@next mostrará los elementos asignados a la siguiente iteración.|
|`field:@today`|date:@today mostrará los elementos con su fecha establecida en el día actual.|

También puedes usar los intervalos `>`, `>=`, `<`, `<=`, `+`, `-` y `..` con palabras clave.

|Calificador|Ejemplo|
|-----------|-------|
|`field:@keyword..@keyword+n`|iteration:@current..@current+3 mostrará los elementos asignados a la iteración actual y las tres iteraciones siguientes. - date:@today..@today+7 mostrará los elementos con una fecha establecida en hoy o los próximos siete días.|
|`field:<@keyword`|iteration:<@current mostrará los elementos asignados a cualquier iteración antes de la iteración actual.|
|`field:>=@keyword`|date:>=@today mostrará los elementos con una fecha establecida en hoy o posterior.|

### Filtrado por campos de texto

Puedes filtrar por campos de texto específicos o usar un filtro de texto general en todos los campos de texto y títulos. Al filtrar con texto que contiene espacios o caracteres especiales, escriba el texto entre comillas `"` o `'`.

|Calificador|Ejemplo|
|-----------|-------|
|`field:"TEXT"`|title:"Corrección de errores" mostrará elementos con títulos que coincidan exactamente con "Corrección de errores".|
|`field:TEXT`|note:complete mostrará elementos con un campo de texto de nota que coincida exactamente con "complete".|
|`TEXT`|API mostrará elementos con "API" en el título o en cualquier otro campo de texto.|
|`field:TEXT TEXT`|label:bug rendering mostrará elementos con la etiqueta "bug" y con "rendering" en el título o en cualquier otro campo de texto.|

También puedes usar * como carácter comodín.

|Calificador|Ejemplo|
|-----------|-------|
|`field:*TEXT*`|label:*bug* mostrará elementos con una etiqueta que contenga la palabra "bug".|
|`field:TEXT*`|title:API* mostrará elementos con un título que comience por "API".|
|`TEXT`|label:*support mostrará elementos con una etiqueta que termina con "support".|

### Filtrado por tipo de incidencia

> [!NOTE]
> Los tipos de incidencias, las subincidencias y la búsqueda avanzada de incidencias se encuentran actualmente en versión preliminar pública para las organizaciones.

|Calificador|Ejemplo|
|-----------|-------|
|`type:"ISSUE TYPE"`|type:"error" mostrará incidencias con el tipo "error".|

### Filtrado por incidencia primaria

> [!NOTE]
> Los tipos de incidencias, las subincidencias y la búsqueda avanzada de incidencias se encuentran actualmente en versión preliminar pública para las organizaciones.

|Calificador|Ejemplo|
|-----------|-------|
|`parent-issue:OWNER/REPO#ISSUE NUMBER`|parent-issue:octocat/game#4 mostrará incidencias con la incidencia 4 en octocat/game como su incidencia primaria.|

## Gráficos

Puedes crear gráficos actuales para visualizar los elementos del proyecto. Puedes usar filtros para manipular los datos usados para crear el gráfico.

### Creación de gráficos

1. Navegar a tu proyecto.

2. En la parte superior derecha, para acceder a la información, haz click en el icono situado arriba a la derecha.

3. En el menú de la izquierda, haz clic en Nuevo gráfico.

4. Opcionalmente, para cambiar el nombre del gráfico nuevo, haz clic en el icono flecha abajo, escribe un nombre nuevo y presiona Enter.

5. Encima del gráfico, escribe filtros para cambiar los datos usados para crear el gráfico. Para más información, consulta Filtrado de projects.

6. A la derecha del cuadro de texto de filtro, haz clic en Guardar cambios.

### Gráficos históricos

Los gráficos históricos realizan un seguimiento de los cambios en el estado de los elementos del proyecto. El gráfico predeterminado "Trabajos terminados" permite visualizar el progreso de las incidencias a lo largo del tiempo, y muestra cuánto trabajo se ha completado y cuánto queda por hacer.

## Referencias

- [GitHub docs](https://docs.github.com/en/issues/planning-and-tracking-with-projects/viewing-insights-from-your-project/about-insights-for-projects)

- [GitHub docs](https://docs.github.com/en/issues/planning-and-tracking-with-projects/managing-your-project/closing-and-deleting-your-projects)

- [GitHub docs - Boards](https://docs.github.com/en/issues/planning-and-tracking-with-projects/customizing-views-in-your-project/customizing-the-board-layout#about-the-board-layout)

- [GitHub docs - Custom fields](https://docs.github.com/en/issues/planning-and-tracking-with-projects/learning-about-projects/about-projects#adding-metadata-to-your-items)

- [GitHub docs - Milestones](https://docs.github.com/en/issues/using-labels-and-milestones-to-track-work/about-milestones)

- [GitHub docs - Labels](https://docs.github.com/en/issues/using-labels-and-milestones-to-track-work/managing-labels)

- [GitHub docs - Templates](https://docs.github.com/en/issues/planning-and-tracking-with-projects/managing-your-project/managing-project-templates-in-your-organization)

- [GitHub docs - Templates II](https://docs.github.com/en/organizations/managing-user-access-to-your-organizations-repositories/managing-repository-roles/repository-roles-for-an-organization#repository-roles-for-organizations)

- [GitHub docs - Differents between Projects and Project Classic](https://docs.github.com/en/issues/planning-and-tracking-with-projects/learning-about-projects/about-projects#differences-from-projects-classic)

- [GitHub docs - Layouts](https://docs.github.com/en/issues/planning-and-tracking-with-projects/customizing-views-in-your-project/changing-the-layout-of-a-view)

- [GitHub docs - Close project](https://docs.github.com/en/issues/planning-and-tracking-with-projects/managing-your-project/closing-and-deleting-your-projects)

- [GitHub docs - Discussions](https://docs.github.com/en/discussions/quickstart#introduction)
