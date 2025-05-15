# Projects

## Contenido

- [Referencias](#referencias)

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
