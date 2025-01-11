# Code with GitHub Codespaces

## The Codespace lifecycle

Le permite crear un entorno de desarrollo personalizado para el proyecto. La configuración de un entorno de desarrollo puede ser repetible para todos los usuarios del proyecto.

El ciclo de vida de un codespace comienza cuando se crea y termina cuando se elimina. Puede desconectarse y reconectarse a un codespace activo sin que esto afecte a sus procesos en ejecución. También puede detener y reiniciar un codespace sin perder los cambios que haya realizado en su proyecto.

### Crear un codespace

Puede crear un codespace en GitHub.com, en Visual Studio Code o en la CLI de GitHub.

* Desde una plantilla de GitHub o desde cualquier repositorio de plantillas de GitHub.com para iniciar un nuevo proyecto.
* Desde una rama del repositorio, para el trabajo de nuevas características.
* Desde una solicitud de incorporación de cambios abierta, para explorar el trabajo en curso.
* Desde una confirmación en el historial de un repositorio para investigar un error en un punto específico del tiempo.

Puede crear más de un codespace por repositorio o incluso por rama. Hay límites respecto al número de codespaces que puede crear y ejecutar al mismo tiempo. Cuando se alcanza el número máximo de codespaces y se intenta crear otro, aparece un mensaje.

![](../Images/codepace-lifecycle.png)

Al crear un codespace de GitHub tienen lugar cuatro procesos:

1. Se asignan al codespace una máquina virtual y almacenamiento.
2. Se crea un contenedor.
3. Se establece una conexión con el codespace.
4. Se realiza una configuración posterior a la creación.

### Guardar cambios en un codespace

Cuando se conecta a un codespace a través de la web, se habilita de forma automática la opción de autoguardado para guardar los cambios cuando transcurra una cantidad de tiempo específica. Al conectarse a un codespace a través de Visual Studio Code en ejecución en el escritorio, debe habilitar Autoguardado.

Si el codespace se elimina, se pierde el trabajo. Para guardar el trabajo, debe confirmar los cambios y enviarlos al repositorio remoto o publicar el trabajo en uno nuevo si ha creado el codespace a partir de una plantilla.

### Apertura de un codespac existente

Para reanudar un codespace existente, puede ir al repositorio donde existe el codespace, seleccionar la clave , y, a continuación, seleccionar Reanudar este codespace. O bien, puede abrir (https://github.com/codespaces)[https://github.com/codespaces] en el explorador, seleccionar el repositorio y, a continuación, seleccionar el codespace existente.

### Tiempos de espera de un codespace

Si un codespace está inactivo o si sale del codespace sin detenerlo de forma explícita, la aplicación agota el tiempo de espera después de un período de inactividad y deja de ejecutarse. El tiempo de espera predeterminado es después de 30 minutos de inactividad. Cuando se agota el tiempo de espera de un codespace, se preservan los datos de la última vez que haya guardado los cambios.

### Conexión a Internet al usar GitHub Codespaces

Un codespace requiere conexión a Internet. Si la conexión a Internet se pierde mientras trabaja en un codespace, no podrá acceder a este. Sin embargo, cualquier cambio pendiente de confirmación se guarda. Al restablecer la conexión a Internet, puede acceder al codespace en el mismo estado que se dejó cuando se perdió la conexión.

### Cerrar o detener un codespace

Si sale del codespace sin ejecutar el comando para detenerlo o si deja el codespace en ejecución sin interacción, el codespace y sus procesos en ejecución continuarán durante el período de tiempo de espera de inactividad. Puede definir su configuración de tiempo de espera personal para los codespaces que cree, pero una directiva de tiempo de espera de la organización puede invalidar la configuración.

Solo los codespaces en ejecución conllevan cargos de CPU. Un codespace detenido solo conlleva costos de almacenamiento.

Puede detener y reiniciar un codespace para aplicar cambios. 

### Recompilación de un codespace

Puede recompilar el codespace para implementar cambios en la configuración de contenedor de desarrollo. Al recompilar su codespace, las imágenes de la memoria caché aceleran el proceso de recompilación. También puede realizar una recompilación completa para borrar la memoria caché y recompilar el contenedor con imágenes nuevas.

Al recompilar el contenedor en un codespace, los cambios realizados fuera del directorio /workspaces se borran. Los cambios realizados dentro del directorio /workspaces, incluido el clon del repositorio o la plantilla desde la que ha creado el codespace, se conservan al recompilar.

### Eliminar un codespace

Si intenta eliminar un codespace con confirmaciones de GIT sin enviar, el editor le notifica que tiene cambios que aún no se han enviado a una rama remota.

Los codespaces detenidos que permanecen inactivos durante un período de tiempo especificado se eliminan automáticamente. Los codespaces inactivos se eliminan después de 30 días, pero puede personalizar los intervalos de retención de codespaces.