# Azure Containers Apps

Azure Container Apps proporciona la flexibilidad que necesita con un servicio de contenedor sin servidor creado para aplicaciones de microservicios y sólidas funcionalidades de escalado automático sin la sobrecarga de administrar una infraestructura compleja.

## Exploración de Azure Container App

Azure Container Apps permite ejecutar microservicios y aplicaciones en contenedor en una plataforma sin servidor que se ejecuta sobre Azure Kubernetes Service. Entre los usos comunes de Azure Container Apps se incluyen:

+ Implementación de puntos de conexión de API.
+ Hospedaje de aplicaciones de procesamiento en segundo plano.
+ Control del procesamiento controlado por eventos.
+ Ejecución de microservicios.

Se pueden escalar de forma dinámica en función del tráfico HTTP, el procesamiento controlado por eventos, la CPU o la carga de memoria.

Con Azure Container Apps, puede:

+ Ejecutar varias revisiones del contenedor y administrar el ciclo de vida de la aplicación del contenedor.
+ Escalar automáticamente las aplicaciones en función de cualquier desencadenador de escalado compatible con KEDA.
+ Habilitar la entrada HTTPS sin tener que administrar otra infraestructura de Azure.
+ Dividir el tráfico entre varias versiones de una aplicación para las implementaciones azul-verde y los escenarios de prueba A-B.
+ Usar la entrada interna y la detección de servicios para proteger los puntos de conexión solo internos con la detección de servicios basada en DNS integrada.
+ Crear microservicios con Dapr y acceder a su amplio conjunto de API.
+ Ejecutar contenedores desde cualquier registro, público o privado, incluidos Docker Hub y Azure Container Registry (ACR).
+ Usar la extensión de la CLI de Azure, Azure Portal o plantillas de ARM para administrar las aplicaciones.
+ Proporcionar una red virtual existente al crear un entorno para las aplicaciones de contenedor.
+ Administrar secretos de forma segura directamente en una aplicación.
+ Supervisar registros mediante Azure Log Analytics.

### Entornos de Azure Container Apps

Las aplicaciones de contenedor individuales se implementan en un único entorno de Container Apps, que actúa como un límite seguro alrededor de los grupos de aplicaciones de contenedor. La instancia de Container Apps en el mismo entorno se implementa en la misma red virtual y escribe registros en la misma área de trabajo de Log Analytics. Puede proporcionar una red virtual existente al crear un entorno.

Las razones para implementar aplicaciones de contenedor en el mismo entorno incluyen situaciones en las que necesita:

+ Administrar servicios relacionados.
+ Implementar aplicaciones diferentes en la misma red virtual.
+ Instrumentación de aplicaciones Dapr que se comunican mediante la API de invocación del servicio Dapr
+ Hacer que las aplicaciones compartan la misma configuración de Dapr.
+ Hacer que las aplicaciones compartan la misma área de trabajo de Log Analytics.

Las razones para implementar aplicaciones de contenedor en distintos entornos:

+ Que dos aplicaciones nunca comparten los mismos recursos del proceso.
+ Dos aplicaciones Dapr no se pueden comunicar a través de la API de invocación del servicio Dapr

### Microservicios con Azure Container Apps

Las arquitecturas de microservicios permiten desarrollar, actualizar, controlar versiones y escalar áreas básicas de funcionalidad de forma independiente en un sistema general. Azure Container Apps proporciona la base para implementar microservicios con las siguientes características:

+ Escalado, control de versiones y actualizaciones independientes
+ Detección de servicios
+ Integración de Dapr nativa

### Intgración de Dapr

Al implementar un sistema compuesto de microservicios, las llamadas de función se reparten por la red. Para dar cabida a la naturaleza distribuida de los microservicios, debe tener en cuenta los errores, reintentos y tiempos de espera. Dapr incluye características como la observabilidad, la publicación/suscripción y la invocación de servicio a servicio con TLS mutuo, reintentos, etc.

## Exploración de contenedores en Azure Container Apps

Administra los detalles de Kubernetes y las orquestaciones de contenedores. Los contenedores pueden usar cualquier runtime, lengauje de progración o pila de desarrollo de su elección.

![](https://learn.microsoft.com/es-es/training/wwl-azure/implement-azure-container-apps/media/azure-container-apps-containers.png)

Azure Container Apps admite cualquier imagen de contenedor x86-64 (linux/amd64) basada en Linux. No hay ninguna imagen de contenedor base necesaria y, si un contenedor se bloquea, se reinicia de forma automática.

### Configuración

El código siguiente es un ejemplo de la matriz containers en la sección properties.template de una plantilla de recursos de aplicación de contenedor. En el extracto se muestran algunas de las opciones de configuración disponibles al configurar un contenedor al usar plantillas de Azure Resource Manager (ARM). Los cambios en la sección de configuración de la plantilla de ARM desencadenan una nueva revisión de aplicación de contenedor.

        "containers": [
        {
            "name": "main",
            "image": "[parameters('container_image')]",
            "env": [
            {
                "name": "HTTP_PORT",
                "value": "80"
            },
            {
                "name": "SECRET_VAL",
                "secretRef": "mysecret"
            }
            ],
            "resources": {
            "cpu": 0.5,
            "memory": "1Gi"
            },
            "volumeMounts": [
            {
                "mountPath": "/myfiles",
                "volumeName": "azure-files-volume"
            }
            ]
            "probes":[
                {
                    "type":"liveness",
                    "httpGet":{
                    "path":"/health",
                    "port":8080,
                    "httpHeaders":[
                        {
                            "name":"Custom-Header",
                            "value":"liveness probe"
                        }]
                    },
                    "initialDelaySeconds":7,
                    "periodSeconds":3
        // file is truncated for brevity

### Varios contenedores

Puede definir varios contenedores en una sola aplicación contenedora para implementar [el patrón sidecar](https://learn.microsoft.com/es-es/azure/architecture/patterns/sidecar). Los contenedores de una aplicación de contenedor comparten recursos de disco duro y red y experimentan el mismo ciclo de vida de la aplicación.

Ejemplos:

+ Un agente que lee los registros del contenedor de aplicaciones principal en un volumen compartido y los reenvía a un servicio de registro.
+ Un proceso en segundo plano que actualiza una memoria caché usada por el contenedor de aplicaciones principal en un volumen compartido.

> __NOTA: La ejecución de varios contenedores en una sola aplicación de contenedor es un caso de uso avanzado. En la mayoría de los casos en los que quiera ejecutar varios contenedores, como al implementar una arquitectura de microservicio, implemente cada servicio como una aplicación contenedora independiente.__

### Registros de contenedor

Puede implementar imágenes hospedadas en registros privados proporcionando credenciales en la configuración de Container Apps.

Proporcione los cmapos necesarios en la matriz de registros de la sección *properties.configuration* de la plantilla de recurso de la aplicación de contenedor. El campo *passwordSecretRef* identifica el nobmre del secreto en el nombre de la matriz de secretos donde ha definido la contraseña.

        {
        ...
        "registries": [{
            "server": "docker.io",
            "username": "my-registry-user-name",
            "passwordSecretRef": "my-password-secret-name"
        }]
        }

Con la información del registro agregada, las credenciales guardadas se pueden usar para extraer una imagen de contenedor del registro privado cuando se implementa la aplicación.

### Limitaciones

+ __Contenedores con privilegios__: Azure Container Apps no puede ejecutar contenedores con privilegios. Si el programa intenta ejecutar un proceso que requiere acceso raíz, la aplicación dentro del contenedor experimenta un error en tiempo de ejecución.
+ __Sistema operativo__: se necesitan imágenes de contenedor basadas en Linux (`linux/amd64`).

## Implementación de la autenticación y autorización en Azure Container Apps

Proporciona características integradas de autenticación y autorización para proteger la aplicación de contenedor con una cantidad mímima de código. Permite ahorrar tiempo y esfuerzo, ya que proporciona autenticación con proveedores de identidades federados.

+ Proporciona acceso a diversos proveedores de autenticación integrados.
+ Las características de autenticación integradas no requiere idioma, SDK, experiencia en seguridad ni ningún código que escribir.

Solo se debe usar con HTTPS. El atributo `allowInsecure` debe estar deshabilitado en la configuración de entrada de la aplicación de contenedor. Se puede configurar la autenticación con o sin restringir el acceso al contenido.

+ Use la opción *Restringir acceso* en __Requerir autenticación__ para que sólo puedan acceder los usuarios autenticados.
+ Use el valor *Restringir acceso* en __Permitir acceso no autenticado__ para realizar la autenticación sin restringir el acceso. 

### Proveedores de identidades

|Proveedor|Punto de contexión de inicio de sesión|Guía de procedimientos|
|---------|--------------------------------------|----------------------|
|Plataforma de identidad de Microsoft|`/.auth/login/aad`|[Plataforma de identidad de Microsoft](https://learn.microsoft.com/es-es/azure/container-apps/authentication-azure-active-directory)|
Facebook|`/.auth/login/facebook`|[Facebook](https://learn.microsoft.com/es-es/azure/container-apps/authentication-facebook)|
GitHub|`/.auth/login/github`|[GitHub](https://learn.microsoft.com/es-es/azure/container-apps/authentication-github)|
Google|`/.auth/login/google`|[Google](https://learn.microsoft.com/es-es/azure/container-apps/authentication-google)|
Twitter|`/.auth/login/twitter`|[Twitter](https://learn.microsoft.com/es-es/azure/container-apps/authentication-twitter)|
Nuevo proveedor de OpenID Connect|`/.auth/login/<providername>`|[OpenID Connect](https://learn.microsoft.com/es-es/azure/container-apps/authentication-openid)

El punto de conexión de inicio de sesión está disponible para la autenticación de los usuarios y para la validación de tokens de autenticación del proveedor.

### Arquitectura de características

El middleware de autenticación y autorización es una característica que se ejecuta como contenedor sidecar en cada réplica de la aplicación. Cada solicitud HTTP entrante pasa por el nivel de seguridad antes de que la aplicación lo controle.

![](https://learn.microsoft.com/es-es/training/wwl-azure/implement-azure-container-apps/media/container-apps-authorization-architecture.png)

El middleware controla:

+ Autentica usuarios y clientes con los proveedores de identidades específicados.
+ Administra la sesión autenticada.
+ Inserta información de identidad en encabezados de solicitud HTTP. 

El módulo de autenticación y autorización se ejecuta en un contenedor independiente, aislado del código de la aplicación. La información pertinente que necesita la aplicación se proporciona en encabezados de solicitud.

### Flujode autenticación

El flujo es el mismo para todos los proveedores, pero varía en función de si desea iniciar sesión con el SDK del proveedor:

+ __Sin el SDK del proveedor__: la aplicación delega el inicio de sesión federado a Conainer Apps. 
+ __Con el SDK del proveedor__:  la aplicación inicia manualmente la sesión del usuario en el proveedor y, luego, envía el token de autenticación a Container Apps para la validación.

## Administración de revisiones y secretos en Azure Container Apps

Implementa el control de versiones de aplicaciones de contenedor mediantel a creación de revisiones. Una revisión es una instantánea inmutable de una versión de la aplicación de contenedor. Los cambios en una aplicación de contenedor se dividen en dos categorias:

+ Ámbito de la revisión: activan una nueva revisión cuando se implementa la aplicación.
+ Ámbito de la aplicación: cualquier cambio en los parámetros de la sección [*propties.configuration*](https://learn.microsoft.com/es-es/azure/container-apps/azure-resource-manager-api-spec?tabs=arm-template#propertiesconfiguration).

Puede controlar qué revisiones están activas y el tráfico externo que se dirige a cada revisión activa. Los nombres de revisión se usan para identificar una revisión, y en la URL de la revisión.

Container Apps crea un nombre de revisión único con un sufijo que consiste en una cadena semialeatoria de caraceres alfanuméricos. Por ejemplo, para una aplicación contenedor llamada *album-api*, si se establece el nombre del sufijo de revisión como *1st-revision*, se creará una revisión con el nombre *album-api--1st-revision*. Puedes establecer el sufijo de revisión en la plantilla ARM, mediante los comandos `az containerapp create` y `az containerapp update`.

### Actualización de la aplicación de contenedor

Con el comando `az containerapp update` puedes modificar varaibles de entorno, recursos de proceso, parámetros de escalado e implementar otra imagen. 

        az containerapp update \
        --name <APPLICATION_NAME> \
        --resource-group <RESOURCE_GROUP_NAME> \
        --image <IMAGE_NAME>

Para listar todas las revisiones use el comando `az containerapp revision list`.

        az containerapp revision list \
        --name <APPLICATION_NAME> \
        --resource-group <RESOURCE_GROUP_NAME> \
        -o table

### Administración de secretos en Azure Container Apps

Azure Container Apps permite que la aplicación almacene de forma segura valores de configuración confidenciles. Si los secretos se definen a nivel de aplicación, los valores protegidos estarán disponibles para las aplicaciones contenedoreas. Podrá hacer referencia a valores protegidos dentro de las reglas de escalado. 

+ Los secretos están limitados a una aplicación, fuera de cualquier revisión específicada de una aplicación.
+ Agregar, quitar o cambiar secretos no genera nuevas revisiones.
+ Cada revisión de aplicación puede hacer referencia a uno o varios secretos.
+ Varias revisiones pueden hacer referencia a los mismos secretos. 

Cuando un secreto es actualizado o eliminado no afecta automáticamente a las revisiones existentes de la aplicación, puede responder a los cambios de las siguientes maneras:

+ Implementación de una nueva revisión. 
+ Reinicio de una revisión existente. 

Antes de eliminar un secreto, implemente una nueva revisión que ya no haga referencia al secreto anterior. Posteriormente, desactive toas las revisiones que hacen referencia al mismo. 

> __NOTA: Container Apps no admite la integración de Azure Key Vault. Pero puede habilitar la identidad administrada en la aplicación contenedora y suar el SDK de Key Vault en la aplicación para acceder a los secretos.__

### Definición de secretos

Cuando cree una aplicación de contenedor, los secretos se definen mediante el parámetro `--secrets`.

+ El parámetro acepta un conjunto deliminado por espacios de pares nombre-valor.
+ Cada par está delmitado por el signo igual `(=)`.

Declaración de una cadena de conexión en una cuenta de Queue Storage en el parámetro `--secrets`. El valor de queue-connection-string procede de una variable de entorno denominada `$CONNECTION_STRING`.

        az containerapp create \
        --resource-group "my-resource-group" \
        --name queuereader \
        --environment "my-environment-name" \
        --image demos/queuereader:v1 \
        --secrets "queue-connection-string=$CONNECTION_STRING"

Una vez declarados los secretos en el nivel de aplicación, puede hacer referencia a ellos en variables de entorno al crear una revisión en la aplicación de contenedor. Cuando una variable de entorno hace referencia a un secreto, su valor se rellena con el valor definidio en el secreto. Para hacer referencia a un secreto en una avariable de entorno de la CLI de Azure, establezca su valor en `secretref:`, seguido del nombre del secreto. 

        az containerapp create \
        --resource-group "my-resource-group" \
        --name myQueueApp \
        --environment "my-environment-name" \
        --image demos/myQueueApp:v1 \
        --secrets "queue-connection-string=$CONNECTIONSTRING" \
        --env-vars "QueueName=myqueue" "ConnectionString=secretref:queue-connection-string"

### Exploración de la integración de Dapr con Azure Container Apps

Distributed Application Runtime (Dapr) es un conjunto de características qeu se pueden adoptar de forma incremental, que simplifican la creacon de aplicaciones distribuidas basadas en microservicios. Proporciona funcionalidades para hablitar la intercomunicaicones de aplicaciones medinate la mensajería a través de pub/sub o llamadas de servicio a servicio configurables y seguras. 

Es un proyecto de código abierto de __Cloud Native Computing Foundation (CNCF)__. La fundación forma parte de Linux Foundation y proporciona soporte, supervisión y dirección para proyectos nativos de rápido crecimiento en la nube. Como alternativa, la plataforma Container Apps ofrece lo siguiente:

+ Proporciona una integración de Dapr adminsitrada y compatible.
+ Controla las actualizaciones de versiones de Dapr sin problemas.
+ Expone un modelo de interacción de Dapr simplificado para aumentar la productividad del desarrollador. 

### API de Dapr

![](https://learn.microsoft.com/es-es/training/wwl-azure/implement-azure-container-apps/media/azure-container-apps-distributed-application-runtime-building-blocks.png)

|API de Dapr|Desciprción|
|-----------|-----------|
|[Invocación de servicio a servicio](https://docs.dapr.io/developing-applications/building-blocks/service-invocation/service-invocation-overview/)|Descrubra los servicios y realice llamadas de servicio a servicio confiables y directas con autenticación y cifrado automáticos de mTLS.|
|[Administración de estados](https://docs.dapr.io/developing-applications/building-blocks/state-management/state-management-overview/)|Proporciona funcionalidades de administración de estado para transacciones y operaciones CRUD.|
|[Pub/Sub](https://docs.dapr.io/developing-applications/building-blocks/pubsub/pubsub-overview)|Permite que las aplicaciones de contenedor de plublicadores y suscriptores se comuniquen entre ellos a través de un agente de mensajes intermediario.|
|[Enlaces](https://docs.dapr.io/developing-applications/building-blocks/bindings/bindings-overview/)|Desencadene las aplicaciones en función de eventos.|
|[Actores](https://docs.dapr.io/developing-applications/building-blocks/actors/actors-overview/)|Son unidades de trabajo orientadas a mensajes, de un solo subproceso y diseñadas para escalar rápidamente. Como en situaciones de carga de trabajo en ráfaga intensivas.|
|[Observabilidad](https://learn.microsoft.com/es-es/azure/container-apps/observability)|Envíe información de seguimiento a un back-end de Application Insights.|
|[Secretos](https://docs.dapr.io/developing-applications/building-blocks/secrets/secrets-overview/)|Acceda a secretos desde el código de la aplicación o haga referencia a valores seguros en los componentes de Dapr. 

### Conceptos principales de Dapr

El ejemplo siguiente está basado en una API de pub/sub se usa para ilustrar los conceptos básicos relacionados con Dapr en Azure Container Apps. 

![](https://learn.microsoft.com/es-es/training/wwl-azure/implement-azure-container-apps/media/distributed-application-runtime-container-apps.png)

|Etiqueta|Configuración de Dapr|Descripción|
|--------|---------------------|-----------|
|1|Container Apps con Dapr habilitado|Está habilitado en el nivel de aplicación de contenedor mediante la configuración de un conjunto de argumentos. Estos valores se aplican a todas las revisiones de una aplicación de contenedor determinada cuando se ejecutan en modo de varias revisiones.|
|2|Dapr|Las API de Dapr totalmente administradas se exponen a cada aplicación de contenedor mediante un sidecar de Dapr. Las API de Dapr se pueden invocar desde la aplicación de contenedor mediante HTTP o gRPC. El sidecar de Dapr se ejecuta en el puerto HTTP 3500 y el puerto gRPC 50001.|
|3|Configuración de componentes de Dapr|Usa un diseño modular en el que la funcionalidad se entrega como componente. Cada uno se pueden compartir entre varias aplicaciones de contenedor. Los identificadores de aplicación de Dapr proporcionados en la matriz de ámbitos dictan qué aplicaciones de contenedor habilitadas para Dapr cargan un componente determinado en tiempo de ejecución.|

### Habilitación de Dapr

Puede configurar Dapr mediante varios argumentos y notaciones basados en el contexto en tiempo de ejecución. Azure Container Apps proporciona tres canales para configurarlo:

+ CLI deContainer Apps.
+ PLantillas de infraestructura como código (IaC), como en las plantillas Bicep o Azure Resource Manager (ARM).
+ Azure Portal.

### Componentes y ámbitos de Dapr

Dapr usa un diseño modular en el que la funcionalidad se entrega como componente. El uso de compoenentes es opcional y está determinado exclusivamente por las necesidades de la aplicación.

Los componentes de Dapr son recursos de nivel de entorno que hacen los siguiente:

+ Pueden proporcionar un modelo de abstracción enchufable para conectarse a servicios externos compatibles.
+ Se pueden compartir entre aplicaciones de contenedor o limitarse a aplicaciones de contenedor específicas.
+ Pueden usar secretos de Dapr para recuperar de ofrma segura los metadatos de configuración.

Todas las aplicaciones de contenedor habilitadas para Dapr dentro del mismo entorno cargan el conjunto completo de componentes implementados. Se deben usar ámbitos de aplicación para asegurarse que los compoentes se cargan en tiempo de ejecución. 