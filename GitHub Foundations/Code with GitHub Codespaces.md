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

## Personalizar su codespace

### Qué se puede personalizar

* Sincronización de configuración: puede sincronizar la configuración de Visual Studio Code (VS Code) entre la aplicación de escritorio y el cliente web de VS Code.
* Dotfiles: puede usar un repositorio dotfiles para especificar scripts, preferencias del shell y otras configuraciones.
* Cambio de nombre de un Codespace: Al crear un codespace, se le asigna un nombre para mostrar generado automáticamente. Si tiene varios codespaces, el nombre para mostrar le ayuda a diferenciar entre ellos. Puede cambiar el nombre para mostrar del codespace.
* Cambiar el shell: puede cambiar el shell en un codespace para mantener su configuración habitual. Al trabajar en un codespace, puede abrir una nueva ventana de terminal con un shell de su elección, cambiar el shell predeterminado para las nuevas ventanas de terminal o instalar un nuevo shell. También puedes usar dotfiles para configurar el shell.
* Cambiar el tipo de máquina: puede cambiar el tipo de máquina que ejecuta el codespace para usar los recursos adecuados para el trabajo que lleva a cabo.
* Establecer el editor predeterminado: puede establecer el editor predeterminado para codespaces en su página de configuración personal. Establezca el editor de su preferencia para que, al crear un codespace o abrir un codespace existente, se abra en el editor predeterminado.
    * Visual Studio Code (aplicación de escritorio)
    * Visual Studio Code (aplicación cliente web)
    * JetBrains Gateway: para abrir codespaces en un IDE de JetBrains
    * JupyterLab (interfaz web para Project Jupyter)
* Establecer la región predeterminada: puede configurar la región predeterminada en la página de configuración de perfil de GitHub Codespaces para personalizar el lugar donde se conservan sus datos.
* Establecer el tiempo de espera: un codespace dejará de ejecutarse después de un período de inactividad. De manera predeterminada, este período es de 30 minutos, pero puede especificar un período de tiempo de espera predeterminado más largo o más corto en su configuración personal en GitHub. La configuración actualizada se aplica a los codespaces que cree o a los ya existentes la próxima vez que los inicie.
* Configuración de eliminación automática: los codespaces inactivos se eliminan de forma automática. Puede elegir cuánto tiempo se conservan los codespaces detenidos, hasta un máximo de 30 días.

### Agregar al codespace con extensiones o complementos

#### Extensiones de VS Code

Puede agregar cualquier extensión que necesite desde Visual Studio Code Marketplace. (compatibilidad con el desarrollo remoto y GitHub Codespaces)[https://code.visualstudio.com/api/advanced-topics/remote-extensions].

Si ya utiliza VS Code, puede usar Sincronización de configuración para sincronizar automáticamente las extensiones, configuraciones, temas y métodos abreviados de teclado entre la instancia local y cualquier codespace que cree.

#### Complementos de JetBrains

Si trabaja con los codespaces en un IDE de JetBrains, puede agregar complementos desde el Marketplace de JetBrains.

## Codespaces versus GitHub.dev editor

Puede usar GitHub.dev para navegar por archivos y repositorios de código fuente desde GitHub, así como hacer cambios de código y confirmarlos. Puede abrir cualquier repositorio, bifurcación o solicitud de incorporación de cambios en el editor GitHub.dev.

Si quiere realizar tareas más complicadas, como probar el código, use GitHub Codespaces. Se asocia con un proceso, por lo que puede compilar el código, ejecutarlo y tener acceso de terminal. GitHub.dev no incluye ningún proceso. 

### Compración entre Codespaces y GitHub.dev

||GitHub.dev|GitHub Codespaces|
|-|---------|-----------------|
|Costee|Gratuito|Cuota mensual gratuita de uso para cuentas personales|
|Disponibilidad|Disponible para todos en GitHub.com|Disponible para todos en GitHub.com|
|Startup|GitHub.dev se abre instantáneamente al presionar una tecla y puede comenzar a usarlo de inmediato sin tener que esperar a su configuración o instalación.|Al crear o reanudar un codespace, se le asigna una máquina virtual a Codespace. A continuación, el contenedor se configura en función del contenido de un archivo devcontainer.json. Esta configuración tarda unos minutos en crear el entorno de desarrollo.|
|Proceso|No hay recursos de proceso asociados, por lo que no puede compilar ni ejecutar el código ni usar el terminal integrado.|Con GitHub Codespaces se obtiene la eficacia de una máquina virtual dedicada para ejecutar y depurar la aplicación.|
|Acceso al terminal|Ninguno|	GitHub Codespaces proporciona un conjunto común de herramientas de manera predeterminada, lo que significa que puede utilizar el terminal exactamente como lo haría en su entorno local.|
|Extensiones|En la vista de extensiones solo aparece un subconjunto de las extensiones que pueden ejecutarse en la web y que se pueden instalar.|Con GitHub Codespaces se pueden usar la mayoría de las extensiones de Visual Studio Code Marketplace.|

### Continuación del trabajo en Codespaces

Puede iniciar el flujo de trabajo en Github.dev y seguir trabajando en un codespace. Si intenta acceder a la vista Ejecutar y depurar o terminal, verá una notificación de que no están disponibles en GitHub.dev.

Para continuar el trabajo en un codespace, seleccione Continuar trabajando en.... Seleccione Crear un codespace para crear un codespace en la rama actual. Antes de que elijas esta opción, debes confirmar cualquier cambio.