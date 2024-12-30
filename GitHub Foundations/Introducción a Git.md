# Introducción a GIT

## ¿Qué es el control de versiones?

Un sistema de control de versiones (VCS) es un programa o conjunto de programas que realiza un seguimiento de los cambios en una colección de archivos. Uno de los objetivos de un VCS es recuperar fácilmente versiones anteriores de archivos individuales o de todo el proyecto. Otro objetivo es permitir que varios miembros de un equipo trabajen en un proyecto, incluso en los mismos archivos, al mismo tiempo sin que eso afecte al trabajo de los demás.

* Ver todos los cambios realizados en el proyecto, cuándo se hicieron los cambios y quién los efectuó.
* Incluir un mensaje con cada cambio para explicar los motivos.
* Recuperar versiones anteriores del proyecto completo o de archivos individuales.
* Crear ramas, donde los cambios se pueden hacer experimentalmente. Esta característica permite que se trabaje en varios conjuntos de cambios diferentes (por ejemplo, características o correcciones de errores) al mismo tiempo, posiblemente personas distintas, sin que ello afecte a la rama principal. Más adelante se pueden combinar los cambios que se quieren mantener en la rama principal.
* Adjuntar una etiqueta a una versión, por ejemplo, para marcar una nueva versión.

Git es un VCS de código abierto rápido, versátil, muy escalable y gratuito. Su autor principal es Linux Torvalds, creador de Linux.

### Control de versiones distribuido

Las instancias anteriores de los VCS, como CVS, Subversion (SVN) y Perforce, usaban un servidor centralizado para almacenar el historial de un proyecto. Esta centralización significaba que un solo servidor también era un único punto de error en potencia.

Git es un sistema distribuido, lo que significa que el historial completo de un proyecto se almacena en el cliente y en el servidor. Se pueden editar archivos sin conexión de red, protegerlos localmente y sincronizarlos con el servidor cuando una conexión esté disponible. Si un servidor deja de funcionar, todavía tendrá una copia local del proyecto. Técnicamente, ni siquiera es necesario tener un servidor. Los cambios pueden pasarse por correo electrónico o compartirse mediante medios extraíbles, pero, en la práctica, nadie usa Git así.

### Terminología de Git

* **Árbol de trabajo**: conjunto de directorios y archivos anidados que contienen el proyecto en el que se trabaja.

* **Repositorio (repo)**: directorio, situado en el nivel superior de un árbol de trabajo, donde Git mantiene todo el historial y los metadatos de un proyecto. A veces se hace referencia a los repositorios como repos. Un repositorio vacío es aquel que no forma parte de un árbol de trabajo; se usa para compartir o realizar copias de seguridad. Un repositorio vacío suele ser un directorio con un nombre que acaba en .git, por ejemplo, project.git.
 
* **Hash**: número generado por una función hash que representa el contenido de un archivo u otro objeto como un número de dígitos fijo. Git usa hashes de 160 bits de longitud. Una ventaja de usar códigos hash es que Git puede indicar si un archivo ha cambiado aplicando un algoritmo hash a su contenido y comparando el resultado con el hash anterior. Si se cambia la marca de fecha y hora del archivo, pero el hash del archivo no, Git sabe que el contenido del archivo no se ha modificado.
 
* **Objeto**: un repositorio de Git contiene cuatro tipos de objetos, cada uno identificado de forma única por un hash SHA-1. Un objeto blob contiene un archivo normal. Un objeto árbol representa un directorio, y contiene nombres, valores hash y permisos. Un objeto de confirmación representa una versión específica del árbol de trabajo. Una etiqueta es un nombre asociado a una confirmación.
 
* **Confirmación**: cuando se usa como verbo, confirmar significa crear un objeto de confirmación. Esta acción toma su nombre de las confirmaciones en una base de datos. Significa que se confirman los cambios realizados para que otros usuarios también puedan verlos.
 
* **Rama**: serie con nombre de confirmaciones vinculadas. La confirmación más reciente en una rama se denomina nivel superior. La rama predeterminada, que se crea al inicializar un repositorio, se denomina main, y suele tener el nombre master en Git. El nivel superior de la rama actual se denomina HEAD. Las ramas son una característica increíblemente útil de Git porque permiten a los desarrolladores trabajar de forma independiente (o conjunta) en ramas y luego combinar los cambios en la rama predeterminada.
 
* **Remoto**: referencia con nombre a otro repositorio de Git. Cuando se crea un repositorio, Git crea un remoto denominado origin, que es el remoto predeterminado para las operaciones de envío e incorporación de cambios.
 
* **Comandos, subcomandos y opciones**: las operaciones de Git se realizan mediante comandos como git push y git pull. git es el comando, mientras que push o pull es el subcomando. El subcomando especifica la operación que quiere que Git realice. Los comandos suelen ir acompañados de opciones, que usan guiones (-) o guiones dobles (--). Por ejemplo, git reset --hard.

## Comandos básicos de Git

### Git status

Muestra el estado del árbol de trabajo (y del área de almacenamiento provisional, de la que pronto hablaremos más). Permite ver los cambios que Git está siguiendo en ese momento para poder decidir si quiere pedir a Git que tome otra instantánea.

### Git add

Se usa para indicar a Git que empiece a realizar un seguimiento de los cambios en determinados archivos. El término técnico es almacenamiento provisional de estos cambios. Va a usar **git add** para almacenar provisionalmente los cambios a fin de prepararse para una confirmación. Todos los cambios en los archivos que se han agregado pero que aún no se han confirmado se almacenan en el área de almacenamiento provisional.

### Git commit

Guardar el trabajo en una instantánea. Como verbo, la confirmación de cambios significa que se coloca una copia (del archivo, el directorio u otra "cosa") en el repositorio como una nueva versión. Como sustantivo, una confirmación es el pequeño fragmento de datos que asigna una identidad única a los cambios que se confirman. Los datos que se guardan en una confirmación incluyen el nombre del autor y la dirección de correo electrónico, la fecha, los comentarios sobre lo que se ha hecho (y por qué), una firma digital opcional y el identificador único de la confirmación anterior.

### Git log

Permite ver información sobre las confirmaciones anteriores. Cada confirmación tiene un mensaje adjunto (un mensaje de confirmación), y el comando **git log** permite imprimir información sobre las confirmaciones más recientes, como su marca de tiempo, el autor y un mensaje de confirmación. Este comando ayuda a realizar un seguimiento de lo que ha estado haciendo y de los cambios que se han guardado.

### Git help

Use este comando para obtener información fácilmente sobre todos los comandos que conoce hasta ahora y más. Escriba **git <command> --help** para obtener la ayuda del comando indicado.