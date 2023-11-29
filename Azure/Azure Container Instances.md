# Ejecución de imágenes de contenedor en Azure Container Instances

Azure Container Instances (ACI) ofrece la manera más rápida y sencilla de ejecutar un contenedor en Azure, sin tener que administrar ninguna máquina virtual ni que adoptar un servicio de nivel superior.

## Exploración de Azure Container Instances

Es una excelente solución para cualquier escenario que pueda funcionar en contenedores aislados, incluidas las aplicaciones simples, la automatización de tareas y los trabajores de compilación. Ventajas:

+ __Inicio rápido__: ACI puede iniciar contenedores en Azure en cusestión de segundos, sin necesidad de aprovisionar y administrar máquinas virtuales.
+ __Acceso al contenedor__: permite exponer los grupos de contenedores directamente a INteernet con uan dirección IP y un nombre de dominio completo (FQDN).
+ __Seguridad de nivel de hipervisor__: la aplicación se aísla completamente, como si estuviera en una máquina virtual.
+ __Datos del cliente__: el servicio ACI almacena los datos mínimos del cliente necesarios para asegurarse de que los grupos de contenedores se ejecutan según lo previsto.
+ __Tamaños personalizados__: proporciona un uso óptimo al permitir especificaciones exactas de los núcleos y la memoria de la CPU.
+ __Almacenamiento persistente__: monte recursos compartidos de Azure Files directamenten un contenedor para recuperar y conservar el estado.
+ __Linux y Windows__: programe contenedores Windows y Linux con la misma API. 

> __NOTA__: en aquellos escensarios donde se necesita una orquestación completa de contenedores, incluida la detección de servicios en varios contenedores, el escalado automático y las actualizaciones de aplicaciones coordinadas, se recomienda [Azure Kubernetes Service(AKS)](https://learn.microsoft.com/es-es/azure/aks/).

### Grupos de contenedores

El recurso de nivel superior de Azure Container Instances es el *grupo de contenedores*. Un grupo de contenedores es una colección de contenedores que se programan en la misma máquina host. Los conteneodres de un grupo comparten un ciclo de vida, los recursos, la red local y los volúmenes de alamcenamiento. Es similar en concepto a un *pod* en Kubernetes.

![](https://learn.microsoft.com/es-es/training/wwl-azure/create-run-container-images-azure-container-instances/media/container-groups-example.png)

Este grupo de contenedores de ejemplo:

+ Se programóen una única máquina host.
+ Se le asigna una etiqueta de nombre DNS.
+ Expone una única dirección IP pública, conun puerto expuesto.
+ Consta de dos contenedores. Un contenedor escucha en el puerto 80, mientras el otro escucha el puerto 5000. 
+ Incluye dos recursos compartidos de archivos de Azure como montajes de volumen y cada contenedor monta uno de los recursos compartidos de forma local. 

> __NOTA__: los grupos de varios contenedores solo admiten actualmente contenedores Linux. PAra los contendores Windows, Azure Container Instances solo admite la implementación de una única instancia.

### Implementación

Hay dos maneras comunes de implmeentar un grupo de varios contenedores: usar una plantilla de Resource Manager o un archivo YAML. Se recomienda usar una lantilla de Resource Manager cuando se necesite implementar recursos adicionales de un servicio de Azure al implementar instancias del contenedor. Se recomienda usar un archivo YAML cuando la implementación incluya solo instnacias de contenedor.

### Asignación de recursos

ACI asigna recursos como CPU, memoria y opcionalmente GPU a un grupo de contnedores mediante la adición de solicitudes de recursos de las instancias del grupo. Usando recursos de CPU, se asginan las CPU's al grupo de contnedores.

### Redes

Los grupos de contenedores comparten una dirección IP y un espacio de nombres de puerto en esa dirección IP. Para permitir que los clientes externos lleguen a un contenedor dentro del grupo, debe exponer el puerto en la dirección IP y desde el contenedor. Dado que los contenedores dentro del grupo comparten un espacio de nombres de puerto, no se admite la asignación de puertos. Los contenedores dentro de un grupo pueden comunicarse entre sí a través de localhost en los puertos que han expuesto, incluso si estos puertos no se exponen externamente en la dirección IP del grupo.

### Storage

Puede especificar volúmenes externos para montar dentro de un grupo de contenedores. Puede asignar los volúmenes en rutas de acceso específicas dentro de los contenedores individuales en un grupo.

+ Recurso compartido de archivos de Azure.
+ Secreto.
+ Directorio vacío.
+ Repositorio de GIT clonado.

### Escenarios frecuentes

Los grupos de varios contenedores son útiles en los casos en los que se quiere dividir una sola tarea funcional en varias imágenes de contenedor.

Ejemplos:

+ Un contenedor para servir una aplicación web y un contenedor para extraer el contenido más reciente desde el control de código fuente.
+ Un contenedor de aplicación y un contenedor de registro. El contenedor de registro recopila la salida de registros y métricas de la aplicación principal y los escribe en un almacenamiento a largo plazo.
+ Un contenedor de aplicación y un contenedor de supervisión. Periódicamente, el contenedor de supervisión realiza una solicitud a la aplicación para asegurarse de que se está ejecutando y responde correctamente, y genera una alerta si no es así.
+ Un contenedor de front-end y un contenedor de back-end. El front-end puede servir una aplicación web y el back-end ejecutar un servicio para recuperar datos.