# Adminsitración de imágenes de contenedor en Azure Container Registry

Azure Container Registry (ACR) es un servicio de registro de Docker administrado y privado que se basa en Dcoker Registry 2.0 de código abierto. Cree y mantenga los registros de Azure Container para almacenar y adminsitrar las imágenes privad del contenedor Docker. 

## Información sobre Azure Container Registry

El servicio Azure Contianer Registry (ACR) dispone de canalizaciones de implementación y desarrollo de contenedores, y Auzre Container Reigstry Task para compilar imágenes de contenedor en Azure. Puedes compilar a petición o automatizar las compilaciones con desencadenadores como las ocnfirmaciones del código funete y las actualizaciones del a imagen de base.

### Caso de uso

Extraiga imágenes desde un registro de coenedores a varios destinos de implementación:

+ __Sistemas de orquestación esclables__ que administran aplicaciones en contenedores en clústeres de hosts, incluidos Kubernetes, DC/OS y Docker Swarm.
+ __servicios de Azure__ que admiten la creación y eejcucción de aplicaciones a escala, includos Azure Kubernetes Service (AKS), App Service, Batch, Service Fabric y otros. 

Los desarrolladores también pueden insertar en un registro de conteedores como parte de un flujo de trabajo de desarrollo de contenedor. 

Configure ACR Tasks para que recompile utomáticamente imágenes de aplicaciones cuando se actualicen sus imágenes base o automatice las compilaciones de imágenes cuando el equipo guarde el código en un repositorio de GIT. Cree tareas de vario pasos para automatizar la compilación, pureba y aplicación de revisiones de varias imágenes de contenedor en paralelo en la nube. 

### Niveles del servicio Azure Container Reigstry

Está disponbile en varios niveles:

|Nivel|Descripción|
|-----|-----------|
|Básico|Optimizado en costes para que los desarrolladores apredan.Los registros básicos tienen las mismas funcionalidades de programación que Estándar y Premum. El almacenamieo inlcuido y el rendimiento de las imágenes son más adecuadas para escenarios de uso inferior.|
|Estándar|Nivel básico pero con más almacenamiento y un mayor rendimiento de las imágenes. Los registros estándar deberían satisfacer las necesidades de la mayoría de los escenarios de producción.|
|Premium|Proporcionan la mayor cantidad de almacenamiento incluido, mayor rendimiento y operaciones simultáneas, por lo que permite trabajar con escenarios de mayor volumen. También agrega características como replicación geográfica para administrar en varias regiones, la confianza en el contenido para la firma de etieutas de imagen un vínculo privado con puntos de conexión privados para restringir el acceso al registro. |

### Imágenes y artefactos admitidos

Las imágenes se agrupan en un repositorio y cada una es una instantánea de solo elctura de un contenedor compatible con Docker. Los reigstros de contenedor de Azure pueden incluir imágenes de Windows y de Linux. Las imágenes también almacenan los formatos de contenido relacionados, como los *gráficos de Helm* y las imágenes creadas para la *especificación de formato de imagen de Open Container Initiative (OCI)*.

### Compilaciones de imágenes automatizadas

Use [Azure Container Registry Tasks (ACR Tasks)](https://learn.microsoft.com/es-es/azure/container-registry/container-registry-tasks-overview) para simplificar la creación, la pureba, el envío de cambios y la implentación de imágenes en Azure. Configure las tareas de compilación para automatizar el sistema operativo del contenedor y la canalización de aplicaciones de revsión de marcos, y compile imágenes de forma automática cuando el equipo guarde el código en el contrl de origen.

## Exploración de las funcionaliddaes de almacenamiento

Características avanzadas de Azure Container Registry:

+ __Cifrado en reposo__: azure cifra automáticamente una imagen antes de almacenarla y la descifra sobre la marcha cuando se extrae la imagen.

+ __Almacenamiento regional__: se almacena datos en al región donde se crea el registro. En casi todas las regiones también se puede almacenar en una region emparejada de la misma geografía. 

+ __Redundancia de zona__: carácteristica de nivel Premium y usa zonas de disponibilidad para replicar el registro mínimo de tres zonas independientes en cada región habilitada.

+ __Almacnamiento escalable__: permite crer tantos repositorios, imágenes, capas o etiquetas como necesite, hasta el límite de almacenamiento del registro. 

> __INFO__ unas cifras altas de etiquetas y repositorios pueden afectar al rendimiento del registro.

## Compilacon y administración de contenedores con tareas

ACR Tasks es un conjunto de características, proporciona la creación de imágenes de contenedor para Linux, Windows y ARM, y puede automatizar la aplicación de revisiones de sistema operativo y marco para los contenedores de Docker. También permite compilaciones automatizadas activadas por actualizaciociones de código funte, atualizaciones de la imagne base de contenedor o temporaizadores. 

### Escenarios de tareas

+ Tarea rápida: compile e inserte una sola imagen de contenedor en un registro de contenedor a petición, sin teenre que realizar una instalación local de Docker. Considere que `docker build`, es `docker push` en la nube.

+ Tareas desencadenadas automáticamente: habilite uno o varios desencadenadores para compilar una imagen
    + Desencadenar al ctualizar el código fuente.
    + Desencadenar al actualizar la imagen base.
    + Desencadenar de acuerdo con una programación.

+ Tarea de varios pasos: amplíe la funcionalidad de inserción y compilación de una única imagn con flujos de trabajo basados en varios contenedores  y varios pasos.

> __INFO__ Cada tarea de ACR tiene un contexto de código fuenteasociado (la ubicacion de un conjunto de archivos de código fuente que se usa para compilar una imagen de conteendor u otro artefacto). Los ejemplos de contexto incluyen un repositorio GIT o un sistema de archivos local. 

### Tarea rápida

Antes de confirmar la primera línea de código, la característica de tareas rápidas puede proporcionar una expericnecia de desarrollo integrado mediante la descarga de compilacionse de imágenes de contenedor. Pede comprobar sus definiciones de compilación automatizadas y detecta posibles problemas antes de confirmar el código.

Usando el formato conocido `docker build`, el comando `az acr build` toma un contexto, lo envía a ACR Tasts, e inserta la imagen compilada en su registro tras completarse. 

### Desencadenar al actualizar la imagen base

Puede configurar una instancia de ACR Tasks para realizar el seguimiento de una dependencia de una imagen base al compilar una imagen de aplicación. Cuando la imagen base se inserta en el registro, o una imagen base se actualiza en un repositorio, ACR TAsks puede compilar automáticamente cualquier imagen de aplicación basada en ella.

### Programación de una tarea

Puede programar una tarea mediante la configuración de uno o más desencadenadores de temporizador al crear o actualizar la tarea. La programación de una tarea resulta útil para ejecutar cargas de trabajo de conteedor según unaprogramación definida o para ejecutar operaciones de mantenimiento pruebas en imágenes insertadas periódicamente en el registro. 

### Tareas de varios pasos

Las tareas de varios pasos, definidas en un [archivo YAML](https://learn.microsoft.com/es-es/azure/container-registry/container-registry-tasks-reference-yaml) especifican operaciones de compilación e inserción individiduales para imágenes de contenedor u otros artefactos. También pueden definir la ejecución de uno o más contenedores, dónde cada paso utiliza el contenedor como su entorno de ejecución. Ejemplo:

1. Crear una image de aplicación.
2. Ejecutar el conteedor de aplicaciones web.
3. Crear una imagen de prueba de aplicación web.
4. Ejecutar el contenedor de prueba de aplicaciones web, que realizar pruebas en el contenedor de aplicaciones en ejecución.
5. Si se superan las pruebas, compilar un paquete de archivo de gráfico de Helm.
6. Realizar una acción `helm upgrade` con el nuevo paquete de archivo de gráfico de Helm.

### Plataformas de imagen

Especifique la etiqueta `--platform` para compilar imágenes para otras arquitecturas. Especifique el sistema operativo, una arquitectura admitida en formato de arquitectura. En el caso de las arquitecturas ARM, especifique opcionalmente una variante en formato de sistema operativo, arquitectura o variante.

|SO|Architecture|
|--|------------|
|Linux|AMD64/ARM//ARM64/386|
|Windows|AMD64|

## Exploración de los elementos de un Dockerfile

Un Dockerfile es un script que contiene una serie de instrucciones que se usan para compilar una imagen de Docker. Suelen contener la siguiente información:

+ La imagen base o primaria que usamos para crear la nueva imagen.
+ Los comandos para actualizar el sistema operativo base e instalar otro software.
+ Los artefactos de compilación que se incluirán, como una aplicación desarrollada.
+ Los servicios que se expondrán, como la configuración de red y del almacenamiento.
+ Ele ocmando que se ejecutará cuando se inicie el contenedor.

### Creacion de un archivo Dockerfile

El primer paso para cre un Dockerfile es elegir una imagen base que sirva como base para la aplicación.

        # Use the .NET 6 runtime as a base image
        FROM mcr.microsoft.com/dotnet/runtime:6.0

        # Set the working directory to /app
        WORKDIR /app

        # Copy the contents of the published app to the container's /app directory
        COPY bin/Release/net6.0/publish/ .

        # Expose port 80 to the outside world
        EXPOSE 80

        # Set the command to run when the container starts
        CMD ["dotnet", "MyApp.dll"]

+ `FROM mcr.microsoft.com/dotnet/runtime:6.0`: este comando establece la imagen base en el entorno de ejecucicón de .NET 6, que es necesario para ejecutar aplciaciones de .NET 6.
+ `WORKIR /app`: establece el directorio de trabajo en `/app`, que es donde se copian los archivos de la aplicación.
+ `COPY bin/Release/net6.0/publish/ .`: copia el contenido de la aplicación publicada en el directorio `/app` del contenedor. Se supone que la aplicación de .NET 6 ya se ha compilado y publicado en el directorio `bin/Release/net6.0/publish`.
+ `EXPOSE 80`: expone el puerto 80, que es el puerto HTTP, al mundo exterior. Cambie esta línea en consecuencia si la aplicación escucha un puerto diferente. 
+ `CMD ["dotnet", "MyApp.dll]`: el comando que se va a ejecutar cuando se inicie el contenedor. En este caso, estamos ejecutando el comando dotent con el nombre del archivo DLL de nuestra aplciación (`MyApp.ddll`). Camibe esta línea para que coincida con el nombre de las aplicaciones y el punto de entrada. 

### Recursos

+ [Referencia de Dockerfile](https://docs.docker.com/engine/reference/builder/)
+ [Referencia de ejecución de Docker (CLI)](https://docs.docker.com/engine/reference/run)
+ [Referencia de ejecución de Docker (CLI)](https://docs.docker.com/engine/reference/commandline/build)
    
