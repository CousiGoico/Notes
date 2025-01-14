# Contribución a proyecto de código abierto

Cualquier usuario puede usar, modificar y compartir libremente software de código abierto. Con software de código abierto, cualquiera puede ver, modificar y distribuir un proyecto para cualquier propósito. La idea detrás del software de código abierto es que el uso compartido de código conduce a un software mejor y más confiable.

## Búsqueda de un proyecto de código abierto que necesite contribuciones

Es posible que, al leer el archivo README de un proyecto, encuentre un vínculo roto o errores tipográficos. Es posible que haya observado que algo no funciona como se esperaba o que la documentación no está actualizada. Son oportunidades excelentes para ayudar y contribuir al proyecto.

> [!TIP]
> Una sugerencia importante: Todos los tipos de contribuciones son valiosos. El nivel de experiencia o conocimiento que tenga del proyecto no importa aquí. Todos tenemos algo que podemos aportar. Tenga confianza en sí mismo. Lo más importante aquí es la disposición a ayudar.

### Uso de la búsqueda de GitHub

Puede usar la búsqueda de GitHub para explorar temas y proyectos relacionados. Vaya a [GitHub search](https://github.com/search) y escriba la palabra correspondiente al tema.

### Familiarización con un proyecto de código abierto

La mayoría de los proyectos tendrán estos documentos en el nivel superior del repositorio:

* LICENSE: el proyecto debe contener una [licencia de código abierto](https://choosealicense.com/). Si el proyecto no tiene una licencia, no es de código abierto.
* README: este archivo suele ser la página de bienvenida del proyecto. Normalmente proporciona información sobre cómo empezar a usar el proyecto. También es habitual que contenga información sobre cómo interactuar con la comunidad.
* CONTRIBUTING: como el nombre sugiere (CONTRIBUIR), en este documento se proporcionan instrucciones sobre cómo contribuir al proyecto. Normalmente describe cómo funciona el proceso de contribución e incluye detalles sobre cómo configurar el entorno de desarrollo.
* CODE_OF_CONDUCT: el código de conducta establece reglas básicas para los miembros de la comunidad. Al hacerlo, ayuda a que la comunidad sea un entorno seguro y de bienvenida para todos.

Canales de comunicación:

* Issue tracker (Seguimiento de incidencias): donde los usuarios hablan sobre las incidencias y tareas relacionadas con el proyecto. Para encontrar incidencias en GitHub, puede ir a la página principal del repositorio en GitHub y agregar `/issues` al final de la dirección URL (por ejemplo, [https://github.com/jupyter/notebook/issues](https://github.com/jupyter/notebook/issues)).
* Pull request (Solicitud de incorporación de cambios): aquí es donde los usuarios debaten y revisan los cambios del proyecto. Se puede encontrar en GitHub si agrega `pulls` a la dirección URL del proyecto (por ejemplo, [https://github.com/jupyter/notebook/pulls](https://github.com/jupyter/notebook/pulls)).
* Chat channels and forums (Canales de chat y foros): algunos proyectos usan canales de chat (como Slack, Gitter e IRC) o foros (como Discourse) para mantener conversaciones y debates.

### Identificación de tareas en las que trabajar

Es posible que ya haya identificado algo en lo que trabajar, como la corrección de vínculos rotos o la actualización de la documentación. Una buena manera de encontrar incidencias descriptivas para los principiantes en las que ayudar consiste en visitar la dirección URL `/contribute` del proyecto.

Observará que la mayoría de las incidencias que se muestran en la dirección URL contribute tendrán etiquetas como `good-first-issue`, `help wanted`, `beginner-friendly`, etc. Las etiquetas se suelen usar para proporcionar información de nivel superior de la incidencia y el tipo de ayuda que se necesita.

### Patrocinador de un proyecto

Hay muchas maneras de contribuir en el código abierto. Puede apoyar financieramente a los que crean y mantienen el ecosistema de código abierto a través de código, liderazgo, tutorías, diseño y mucho más.

El código abierto se basa en gran medida en el trabajo voluntario. Los patrocinadores de GitHub le permiten financiar proyectos y usuarios para ayudarles a mantener su trabajo de código abierto, a la vez que les proporciona el reconocimiento que merecen.

Si un proyecto es válido para patrocinarse a través de los patrocinadores de GitHub, encontrará un botón Sponsor (Patrocinar) en su página principal.

Puede seleccionar el nivel de patrocinio y si quiere que su contribución sea pública.

## Contribución a un repositorio de código abierto

A la hora de colaborar en un proyecto de código abierto, la comunicación es un factor clave del éxito. Puede que le resulte incómodo comunicarles a otros usuarios sus propuestas de cambios o mejoras. A menudo, este diálogo dará lugar a debates y cuestionará su visión original.

Evitar la comunicación activa con otras personas implicadas en un proyecto de código abierto significa arriesgar su tiempo ocupándose de tareas en las que ya está trabajando otra persona. O bien, es posible que trabaje en características o mejoras que no se alineen con los valores o los procedimientos recomendados del proyecto. En cualquier caso, se desperdicia el tiempo de todos. Por el contrario, comprometerse a una comunicación activa garantiza que el trabajo será bien recibido y tendrá sentido.

### Comunicación de la intención a los mantenedores

* Si quiere trabajar en una incidencia existente, consulte la sección **Assignees** (Usuarios asignados) para asegurarse de no haya nadie asignado. Consulte también la sección **Linked pull requests** (Solicitudes de incorporación de cambios vinculadas). Una solicitud de incorporación de cambios vinculada implica que alguien ya está trabajando en ella. Consulte los comentarios para ver si alguien ha manifestado su interés en la incidencia. Publique un comentario sobre la incidencia para indicar que le interesa trabajar en ella. Así indicará a los usuarios que puedan llegar más tarde que alguien está trabajando en la incidencia. ^

* Si quiere trabajar en una característica nueva o en un error que todavía no está presente en el seguimiento de incidencias, cree una incidencia. Asegúrese de seguir la plantilla de incidencias si hay una propuesta y exprese claramente la intención de trabajar en la incidencia. Si se trata de una nueva propuesta de características o si la incidencia requiere muchos cambios, asegúrese de obtener la aprobación del mantenedor antes de continuar con el paso siguiente.

### Creación de una solicitud de incorporación de cambios en un repositorio de GitHub

La contribución adoptará la forma de solicitud de incorporación de cambios o PR. 

* Un título y una descripción de los cambios.
* Una o más confirmaciones que constituyan los cambios que propone.
* Comentarios en los que todos los usuarios puedan participar para debatir los cambios.
* Revisiones de código donde puede encontrar comentarios detallados sobre los cambios y, finalmente, confirmar las sugerencias.
* Comprobaciones de estado procedentes, por ejemplo, de las pruebas automatizadas que los mantenedores puedan haber implementado. Las comprobaciones de estado pueden tener distintos propósitos. Por ejemplo, pueden garantizar que los cambios sigan las reglas del proyecto o que no interrumpan el código.

Después de crear una solicitud de incorporación de cambios, se puede actualizar con nuevas confirmaciones, comentarios o revisiones de código. Este proceso continúa hasta que los mantenedores del proyecto aprueben y combinen la solicitud de incorporación de cambios o rechacen los cambios y cierren la solicitud de incorporación de cambios. Cuando la solicitud de incorporación de cambios se combina, significa que los cambios se han integrado en el código base del proyecto.

### Creación paso a paso de una solicitud de incorporación de cambios

1. Abra la página de GitHub del proyecto en el que quiera contribuir.

2. Seleccione el botón Fork (Bifurcar) para crear una copia del repositorio en la cuenta de GitHub. Este paso es necesario, ya que, de forma predeterminada, no cuenta con los permisos necesarios para realizar cambios en un repositorio público, a menos que sea su propia copia. Al bifurcar el proyecto, se crea una copia en la que puede realizar cambios.

3. Seleccione Los repositorios en el menú de perfil de la cuenta.

4. Seleccione la bifurcación del repositorio.

5. Seleccione el botón Code (Código) para obtener información sobre cómo "clonar" el repositorio de Git en la máquina local.

6. Seleccione el icono del Portapapeles para copiar la dirección URL del repositorio y, después, escriba en un terminal:

        git clone <REPOSITORY_URL>

Este comando creará una copia del repositorio en el equipo local.

También puede usar [GitHub Desktop](https://desktop.github.com/) si prefiere usar una aplicación. O bien, puede usar [GitHub Codespaces](https://github.com/features/codespaces) si se le ofrece la opción. Si es usuario de Visual Studio Code, GitHub Codespaces le resultará familiar.

7. Cuando haya finalizado la clonación del proyecto, acceda a la carpeta del proyecto:

        cd <PROJECT_FOLDER>

8. (Opcional) Cree una rama mediante el comando siguiente:

        git checkout -b <BRANCH_NAME>

9. Realice los cambios deseados en el proyecto y confírmelos:

        git add .
        git commit -m "<COMMIT_MESSAGE>"

Estos comandos agregarán los cambios al "stage" para confirmarlos y, después, crearán una confirmación con el mensaje especificado. Asegúrese de describir los cambios con precisión en el mensaje de confirmación. También es recomendable comprobar si en el archivo CONTRIBUTING se menciona alguna convención para los mensajes de confirmación que tenga que seguir.

10. Inserte los cambios en el repositorio remoto mediante el comando siguiente:

        git push --set-upstream origin <BRANCH_NAME>

Este comando creará una rama en el repositorio ascendente de GitHub (la bifurcación), en la que incluirá todas las confirmaciones. Si antes no ha creado una rama, escriba solo `git push`.

11. Abra la bifurcación del proyecto en GitHub y seleccione el botón Compare & pull request (Comparar y solicitud de incorporación de cambios) en el cuadro de sugerencias que aparece.

12. Rellene el título y la descripción, y seleccione **Create pull request** (Crear solicitud de incorporación de cambios).

Si hay una plantilla para la descripción de la solicitud de incorporación de cambios, dedique el tiempo necesario para rellenar toda la información requerida. También debe volver a vincular a la incidencia relacionada; para ello mencione su número mediante `#<ISSUE_NUMBER>`.

### Superación de las comprobaciones de estado

Estas comprobaciones de estado son comprobaciones automatizadas que los mantenedores han implementado para garantizar la calidad coherente del proyecto.

Para que se acepte la solicitud de incorporación de cambios, debe superar todas las comprobaciones automatizadas. Si se produce un error en alguna, seleccione el botón Details (Detalles) para obtener más información sobre el error y saber lo que tiene que hacer para corregirlo. Si no está seguro de qué hacer con una comprobación con error, siempre puede usar los comentarios para solicitar instrucciones o ayuda para corregirla a los mantenedores.

### Solicitud de instrucciones o revisiones de solicitudes de incorporación de cambios

Es posible que no esté seguro de algunos de los cambios realizados y quiera conocer las opiniones de los mantenedores. La mejor manera de hacerlo es comentar directamente las solicitudes de incorporación de cambios. Si considera que los cambios son un trabajo en curso, también tiene la opción de crear un borrador de solicitud de incorporación de cambios para solicitar instrucciones o ayuda de otros colaboradores.

Cuando los mantenedores del proyecto reciban la solicitud de incorporación de cambios, pueden responder a la conversación o revisar directamente los cambios. 

* Los cambios se aprueban. Felicidades.
* La solicitud de extracción necesita algunos cambios. No se desanime. Observe atentamente los comentarios proporcionados. Si realiza los cambios solicitados, hay bastantes posibilidades de que se acepte la solicitud de incorporación de cambios. Si envía nuevas confirmaciones a la rama, la solicitud de incorporación de cambios se actualizará de forma automática con los nuevos cambios.
* El revisor ha realizado algunos comentarios. Normalmente significa que se necesitan más detalles sobre los cambios o la motivación subyacente.

