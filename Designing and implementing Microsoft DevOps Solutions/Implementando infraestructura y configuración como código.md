# Implmenentando infraestructura y configuración como código

## Requerimientos técnicos

* Una suscripción de Azure, para ejecutar plantillas ARM y Azure Automation.
* PowerShell con el módulo de Azure PowerShell ([Azure PowerShell](https://learn.microsoft.com/en-us/powershell/azure/install-azure-powershell?view=azps-11.2.0&viewFallbackFrom=azps-7.3.0)).
* Azure CLI para ejecutar plantillas ARM ([Azure CLI](https://docs.microsoft.com/en-us/cli/azure/)). 

## Teniendo todo como código

La causa más común de una deriva de configuración es un cambio manual. Cuando haces cambios manuales existe siempre el riesgo que aplique diferentes ajustes a diferentes servidores o hosts. Si necesitas poner a escala y añadir otro servidor en tu entorno productivo, la oportunidad de que ese servidor tome la misma configuración como todos los existentes es muy pequeña.

> [!TIP]
> Declarativo e imperativo son dos enfoques principales adopatados para implementar **Infrastructure as Code (IaC)** y **Configuration as Code (Cac)**.

El primer paso para hacer esto es especificando el estado deseado de la configuración e infraestructura. El estado deseado es entonces alimentado dentro de la configuración gestionada que refuerza esta configuración en tu infraestructura. Especificando solo el estado deseado es llamado un acercamiento declarativo, con el que difiere de un acercamiento imperativo, donde tu especificas todos lso pasos que necesitas ser dados. 

Algunas de esas herramientas son a menudo capaces de comprobar el estado actual de tu infraestructura y configuración en intervalos regulares y replicando tu estado deseado if alguna desviación es detectada. Esto hace aplicar una operación idempotente.

> [!TIP]
> Una operación es idempotete is puede ser repetida una o más veces, mientras la salida siempre sea la misma.

Cuando adpotas IaC y CaC, tú puedes ir más rápido para recrear la infraestructura completa antes de desplegar una aplicación, desplegando una aplicación en una nueva infraestructura y entonces sin tener en cuenta la antigua infraestructura después cambiando al nuevo despliegue. El beneficio añadido de este enforque es que tu ahora estas garantizado que no habrá rastros de algúna configuración o binarios del despliegue previo. 

Es importante entender que eso es complementario y es usado junto a menudo. Las plantillas ARM pueden ser usadas para crear máquinas virtuales en Azure, PowerShell DSC o Ansible pueden ser usadas para configurar esas máquinas virtuales.

## Trabajando con plantillas ARM

Las plantillas ARM son escritas en JSON

            {
                "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#",
                "contentVersion": "1.0.0.0",
                "parameters": {
                },
                "variables": {
                },
                "resources": {
                },
                "outputs": {
                }
            }

La propiedad **$schema** es requerido y el número de la versión depende del ambiente de despliegue y del editor JSON. La propiedad **contentVersion** especifica la versió del contenido.

### Parámetros

La sección de parámetros esta usualmente cerca de la parte superior de la plantilla. Antes iniciar despliegues, ARM resolverá los valores de los parámetros. Los valores son referenciados cuando el parámetro es encontrado en la plantilla por ARM.

El uso de esta sección es para declarar uno o más parámetros que pueden ser especificos por el llamador de la plantilla ARM antes de desplegarlo. Una razón común para usar la sección de parámetros es usar la misma plantilla para los entornos de test y producción pero varia los nombres de los recuersos entre ambos. 

            {
                "appServiceName": {
                    "type": "string",
                    "metadata": {
                        "description": "a free to choose text
                    }
                }                
            }

Para cada parámetro, una nueva clave es especificada con el nombre del parámetro. El valor como objeto tiene una clave requerida, **type**. Los valores para **type** son: *string*, *int*, *bool*, *object*, *array*, *secureString*, y *secureObject*. Los valores *secureString* y *secureObject* pueden ser usados para hacer seguro que los valores en tiempo de ejecución de esos parámetros son eliminados de cualquier log y salida. Son intencionados para mantener contraseñas, claves y otros secretos. 

El objecto metadata con su clave **description** es opcional y puede ser usada para añadir una descripción de los parámetros para una futura referencia.

Otras proiedades que pueden ser especificadas:

* **minValue** and **maxValue** para especificar los límites en un valor entero.
* **minLength** and **maxLength** para especificar los límites de la longitud de un texto.
* **defaultValue** para especificar el valor por defecto que usará si el valor no es especificado cuando se aplique la plantilla.
* **allowedValues** para especificar un array de valores permitidos limitando los valores de entrada.

### Parámetros de fichero

Puedes hacer uso de un fichero JSON que contiene los parámetors especificandolos como valores en tu script. Una simple plantilla es acompañado por más de un parámetro de fichero, por ejemplo, uno para test y otro para producción.

            {
                "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentParameter s.json#",
                "contentVersion": 1.0.0.0",
                "parameters": {
                    "exampleParameter": {
                        "value": "exampleValue"
                    }
                }
            }

Cada parámetro de fichero es un objeto JSON con las propiedades requeridas **$schema** y **contentVersion**. La tercera propiedad **parameters** es usada para especificar uno o más parámetros, especificando nombre como clave y objeto como valor. 

Esta solución no es últil para secretos. 

![Figure8.1](Figure8.1.png)

Keys passwords, and other secrets should not be stored as paintext in source control in a paramter file.

            {
                "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentParameters.json#",
                "contentVersion": "1.0.0.0",
                "parameters": {
                    "exampleSecretParameter": {
                        "reference": {
                            "keyvault": {
                                "id": "/subscriptions/.../Microsoft.KeVault/vaults/<vaultname>"
                            },
                            "secretName": "myKeyVaultSecretName"
                        }
                    }
                }
            }

Cuando desplieguas la plantilla, este secreto es tomado desde el key vault y usado en el despliegue. Esto es permitido solo is el usuario o servicio inicia el despliegue tiene role de propietario o contribuidor en relación al key vault, y el key vault esta habilitado para el despliegue de plantillas.

> [!TIP]
> Algún rol que incluya permisos *Microsoft.KeyVault/vaults/deploy/action* podrá trabajarlo. Puedes crear roles personalizados que incluya esta acción.

### Variables

La sección variables es usada para especificar uno o más valores que serán usados mediante la plantilla. El nombre del párametro es *environmentName*. Las variables son usadas para especificar que no pueden ser especificadas desde fuera de la template pero deben ser reconocidas como configurables. 

            "Variables": {
                "appServicePlanType": "B1",
                "appServiceName": "[concat('myAppService-', parameteres('environmentName'))]
            }

### Functions

Son usadas para permitir la dinámica evaluación de propiedades en las plantillas ARM. Pueden retornar valores como texto o numérico, o como array de objetos. Alguna propiedad puede ser accedida usando la notación *.propertyName*.

            "myVariable": "[concat('myAppServices-', parameters('environmentName'))]"

Ello puede ser usado para manipular textos, recuperar detalles sobre la subscripción actual, grupo de recursos, o tenant de Azure Active Directory (AAD), u obtener detalles de los recursos.

Las funcionaes pueden ser también usadas para recuperar claves u otros secretos.Inserta claves directamente desde el servicio que expone la clave para los ajustes de la aplicación o key vault.

### Comments and metadata

Una plantilla ARM puede contener secciones, comentarios y metadatos.

#### Comentarios

// es usado para comentar un línea, /* */ es usado para comentar un bloque.

            {
                "appServiceName": {
                    // this is a single line comment
                    "type": "string",
                    /*
                        This is a multi-line comment
                    */
                    "metadata": {
                        "description": "The name of the web app that you wish to create.",
                        "author": author Name"
                    },
                    "location": "[
                        parameters('location')
                    ]" // defaults to resource group location
                }                
            }

> [!TIP]
> Para desplegar plantillas con textos multilinea y comentar, usa Azure PowerShell o Azure CLI. Para CLI usa la versión 2.3.0 or posterior, y especifica el formato --handle-exteded-json.

#### Metadata

El texto que añades a la descripción metadata es automaticamente usada como consejo para ese parámetro.ARM ignorará el objeto metadata, y esto puede ser usado en cualquier lugar de la plantilla.

### Resources

Los recursos son la parte principal de la plantilla, donde todos los recursos para ser creados son especificados.

            {
                "type": "Microsoft.Sql/servers",
                "apiVersion": "2021-02-01-preview",
                "name": "mySqlServer",
                "location": "West Europe",
                "properties": {
                    "administratorLogin": "myUsername",
                    "administratorLoginPassword": "myPassword",
                    "version": "12.0"
                }
            }

* El tipo de recurso para ser creado o modificado necesita ser especificado. *resourceProvider* y el nombre del tipo de recurso que pertenece.
* La versión del REST API para usar este recurso. [](https://docs.microsoft.com/en-us/azure/templates/microsoft.resources/allversions)
* El nombre para el recurso: cada tipo de recurso tiene sus reglas para determinar un nombre válido.
* Requiere una localización, debes especificar uno para cada recurso. La localización debe ser una región de Azure.

### Recursos dependientes

Un tipo especial de recursos es el recurso dependiente. Para un tipo de recurso anidado, el tipo y nombre reflejan este anidameniento.

            {
                "apiVersion": "2021-11-01",
                "name": "myNamespaceName/myTopicName",
                "type": "Microsoft.Servicebus/namespaces/topics",
                "dependsOn": ["Microsoft.ServiceBus/namespaces/myNamespaceName]
            }

La propiedad extra, *dependsOn*, es requerida para especificar el recurso aninado que solo puede ser creado después del recurso contendor existente. La propiedad *location* no es necesario.

Cuando la propiedad *dependson* es utilizada, una dependencia explicita de despliegue entre el recurso hijo y el recurso padre es establecido automátcamente. El recurso hijo será desplegado después del padre. La función *resourceID* retorna el identificador único del recurso.

            {
                "type": "Microsoft.Sql/Servers",
                "apiVersion": "2020-02-02-preview",
                "name": "[parameteres('serverName')]",
                "location": "[parameters('location')]",
                "resources": [
                    {
                        "type": "databases",
                        "name": "[parameters('sqlDBName')]",
                        "location": "[parameters('location')]",
                        "dependsOn": [
                            "[resourceId('Microsoft.Sql/servers', concat(parameters('serverName')))]
                        ]
                    }
                ]
            }

> [!IMPORTANT]
> Una dependencia circular es un problema con el orden de dependencia, resultando en el despliegue un bucle que le impide completar el despliee. ARM identifica las dependencias circulares durante la validación de la plantilla.

### Plantillas anidadas

Otro tipo especial de recurso son las plantillas anidadas, que pueden lanzar el despliegue de otra plantilla.

            {
                "ype": "Microsoft.Resources/deployments",
                "apiVersion": "2021-04-01",
                "name": "linkedTemplate",
                "properties": {
                    "mode": "Incremental",
                    "templateLink": {
                        "uri": "https://.../myLinkedTemplate.json"
                    },
                    "parametersLink": {
                        "uri": "httsp://.../myParameters.json"
                    }
                }
            }

La localización de las plantillas y ficheros de parámetros son HTTP y HTTPS con un **Identificador uniforme de recursos - Uniform Resource Identifier (URI)**, pero tienen que ser localizaciones publicas. La plantilla URI necesita ser accedida externamente. Para ganar acceso durante el despliegue, añade token SAS a la plantilla como alternativa, una propiedad de plantilla puede ser especificada. No puedes usar ambos, parámetros en linea y un vínculo de un fichero de parámetros.

### Salidas

Las claves son retornadas al llamante de la plantilla. El llamante puede usar esos valores para iniciar otra tarea o script y usar una o más de los valores creados o usarlos por la plantilla. 

El principal uso de esto es prevenir harcodear nombres y otros valores dinámicos, especialmente IP's en una automatización. La sección de salida es un objeto JSON.

            {
                "outputName": {
                    "type": "string",
                    "value": "myValue"
                }
            }

Las funciones son usadas para recuperar valores desde parámetros, variables o otros recursos creados. 

            "outputs": {
                "SqlServerURL": {
                    "type": "string",
                    "value": "[reference (parameters('serverName')).fullyQualifiedDomainName]"
                }
            }

Resultado:

            sqlServerURL String serverName,database.windows.net

## Desplegando plantillas ARM

Hay cmdlet en PowerSHell y comandos de Azure CLI disponible para aplicar una plantilla ARM desde el entorno de scripting. Azure Pipelines puede ser usado para desplegar no sólo código, también plantillas ARM. Otras alternativas son Azure portal, Azure CLI, REST API, y Azure Cloud Shell o specificaciones de las plantillas ARM.

Tienes el modo de despliegue: *Incremental* o *Complete*. En el modo incremental, todos los recursos especificados en la plantilla serán creados en Azure o sus propiedades serán modificadas si el recuroso ya existe. En el modo completo, los recursos no definidos en la plantilla ARM serán eliminados. 

El modo por defecto es el *Incremental*.

### PowerShell

Para el entorno local y testear plantillas ARM en una máquina local, PowerShell tiene un comando rápido para aplicar una plantilla ARM:

            New-AzResourceGroupDeployment -ResourceGroupName myResourceGrRoup -TemplateFile "c:\my\template.json" -TemplateParameterFile "c:\my\parameters.json"

El comando desplegará y aplicará el fichero de parémtros en el grupo de recursos indicado. Este comando asume que la sesión actual ya está logueada en Azure.

* El parámetro -Mode indica si es *Complete* o *Incremental*.
* Si no especificas el parámetro fichero y la plantilla requiere parámetros, el cmdlet preguntará por esos valores en la línea de comandos.
* Las opciones *-TemplateUri* y *-TemplateParametersUri* pueden ser usados para especificar la localización de la plantilla y parámetros para ser recuperados de otra localización.

### Azure CLI

El beneficio de CLI es que es para todas las plataformas y corre en Windows, macOS y Linux.

            az group deployment create -resource-group myResourceGroup -template-file "c:\my\template.json" -parameters "c:\my\parameters.json"

### Azure Pipelines

Su uso es para desplegar la infraestructura y confirgurar una aplicación. 

> [!TIP]
> [Herramienta para testear plantillas ARM](https://github.com/azure/arm-tkk)

El primer despliegue que crearás para crear toda la infraestructura que necesita la nueva versión de la aplicación. El segundo despliegue, eliminará esos elementos después de que la el código sea desplegado. 

### ARM REST API

ARM provee una API REST para desplegar y gestionar infraestructura para Azure.

        GET https://management.azure.com/subscriptions/{subscriptionId}/resources?api-version-2021-04-01

Puedes usar ARMClient, una línea de comandos para enviar llamadas HTTP a la nueva REST API:

        armclient GET /subscriptions/{subscriptionId}/resources?api-version=2021-04-01

El comando precedido obtiene una lista de recursos de la suscripción. ARM client no es una herramienta oficial de Microsoft. Es un proyecto OOSS que es mantenido en GitHub.

Puedes usar el comando az rest para eejcutar esos comandos.

        az rest --method get --ur /subscriptions/{subscriptionId}/resources?api-version=2021-04-01

### Azure Cloud Shell

Azure Cloud Shell provee un Bash y PowerShell experiencia para gestionar y desplegar recursos de Azure.

        az deployment group create --resource-group testrg --name rollout01 --template-uri https://myresource/azuredeploy.json --parameters @myparameters.json

### Ingenieria inversa de una plantilla

Dos enfoques son disponiblesp ara generar plantillas ARM:

* Usar **Export template**
* Usar **Resource Explorer**

#### Usando Export template

Generará una plantilla ARM del estado actual del grupo de recursos. No todos los servicios actualmente soporta ingeniería inversa, si esto ocurriera serás avisado en la parte superiro de la pantalla. La opción *Export template* creará una plantilla ARM reusable.

#### Usando Resource Explorer

Para recueprar el JSON de un recurso, puedes usar Resource Explorer. La opción Resource Explorer tiene dos paneles, uno a la izquierda en el que puedes navegar por las subscripciones, grupos de recursos y por sus recursos. Por cada recurso seleccionado, el JSON aparecerá a la derecha. Este JSON puede ser usado en el array de recursos de na plantilla ARM exceptuando el elemento ID.  

> [!Important]
> La salida JSON y la plantilla del recurso pueden variar.

#### Plantillas a nivel suscripción

Una plantilla describe uno o más recursos que son desplegados en un grupo de recursos. Estos también están a nivel de suscripción.

            {
                "$schema": "https://schema.management.azure.com/schemas/2018-05-01/subscriptionDeploymentTemplate.json#",
                "contentVersion": "1.0.0.1",
                "parameters": {},
                "variables": {},
                "resources": [{
                    "type": "Microsoft.REsources/resourceGroups",
                    "apiVersion": "2021-04-01",
                    "location": "West Europe",
                    "name": "MyResourceGroup",
                    "properties": {}
                }],
                "ouptputs": {}                
            }

El formato para una plantilla de suscripción es la misma que para un grupo de recursos. LA diferencia es *$schema*, que indica la localización del esquema y los tipos de recursos que son soportados. No soporta la creación de recursos directamente y soporta sólo la creación de grupos de recursos, la inicialización de despliegues, creando y asignando politicas de Azure y la creación de asignaciones de roles. 

#### Azure Bluprints

Pueden ser usados para describir el estado de una suscripción de Azure y apliar aquello que existe ne una suscripción. Sólo soporta los siguientes constructores:

* Asignación politicas
* Asignación de roles (RBAC)
* Creación de grupos de recursos
* Plantillas ARM anidadas a la suscripción o a nivel de grupo de recursos

Claves diferentes entre Blueprints y plantilla ARM:

* Un bluerint es un recurso que puede crear y navegaor en el portal. La experiencia de autoria es la del portal, no ficheros de texto en un pc local.
* La relación entre suscripción y blueprint que se usó para crearlo permanece, despues incluso de los despliegues completados.
* Es posible marcar la asignación como bloqueada. Todos los recursos deslegados mediante blueprint no puede ser eliminado o editado a lo largo que el blueprint es aplicado.
* HAy alguna construcción en blueprints disponible que puede ser usado para implementar controles desde el conoceimiento como ISO, NIST o HIPAA.

USando blueprints puedes instalar roles RBAC, plantillas ARM, y politicas de azure todo como uno y asignado para un cierto ámbito. Eliminando la asignación eliminas o remueves los recursos, de este modo esto se convierte en tedioso, y Azure DevOps no tiene tareas o automatización para gestionar blueprints en escala.

#### Bicep

Es un lenguaje específico de dominio **(DSL - Domain-Specic Language)** que permite el despliegue declarativo de recursos de Azure.

Bicep provee todos los tipos de recursos y versiones de API. Provee una mejor experiencia de autoridad, soporttipos seguros y sintaxis simple declaraitiva. Los ficheros Bicep son idempotentes, y un fichero representa el estado deseado. Usa ese fichero para repetidamente desplegar tu infraestructura de una manera constante.

Bicep es una abastracción transparente sobre las plantillas ARM en JSON y soporte capcidadees de las plantillas JSON. El CLI de Bicep convierte a los ficheros Bicep en plantillas ARM. [https://aka.ms/bicepdemo](https://aka.ms/bicepdemo)

            az bicep decompile --file deployment.json

#### Azure automatización

Es un servicio en Azure para ayudar a usuarios a crear, manejar, desplegar y mantener sus recursos de Azure. Permite para la formulación de workflows en el formulario de manuales. Puede ser ejecutado contra recursos de Azure en beneficio del usuario.

#### Recursos de cuenta de automatización

Esos recursos son compartidos a nivel de la cuenta de automatización y por ello puede ser reusado con múltiples manuales.

##### Ejecutar como cuenta

La primera construcción es ejecutar como cuenta (Run As account). Esta cuenta es un servicio principal que será creada en AAD que la suscripción de Azure contiene la cuenta de automatización asociada. Las credenciales para autenticarse como este servicio principal son almacenadas de forma segura con la cuenta de automatización. Manuales pueden ahora ser configuradas para ejecutar usando esta cuenta. Puede ser automaticamente creada cuando creas la cuenta de automatización.

Ejecutar como cuenta se mantiene para la actual y nuevas cuentas de Automatización. Ha sido reemplazado con identidades gestionadas. Las identidades gestionadas es una manera de autenticación recomendada en tus manuales y la autenticación por defecto para tu cuenta de automatización. Las credenciales no son salvadas, la identidad gestionada es más segura y fácil de usar. Debes chambiarlo para usar para usar identidades gestionadas.

##### Horarios

Una manera común de automatizar flujos de trabajo es programandolos para ejecutarse en una fecha y hora especifica o en un intervalo fijo. Para crear un nuevo horario, primero, abre el listado de todos los horarios. Un nuevo horario puede ser añadido. Tiene nombre y descripción. La fecha y hora pueden ser configurados a lo largo coun intervalo recurrente opcional, y si se especifico el intervalo, una fecha y hora de expiración.

##### Módulos

Los manuales son escritos en PowerSHell o Pythno. PowerShell tiene modulos con funcioanlidades predefinidas que pueden ser usadas. Sólo los módulos que tienen que ser subidos a la sección de módulosp ara ser usados. Fijar la versión del módulo a usar garantiza mantener trabajando y no romper en caso de actualizacaciones.

Los módulos de PowerShell interactuan con Azure siendo por defecto installado en cada cuenta de automatización. Más módulos puedes ser añadidos, y módulos existentes pueden ser mejorados o eliminados por el administador.

##### Variables

Algunas variales podrían entrar en juego: los nombres de los grupos de recursos, máquinas virtuales, tiempos de inicio y apagado, ... Harcodeando esos valores denrto de un script no es una buena práctica. Es posible almacenar variables a nivel de la cuenta de automatización, donde podrán ser reusadas mediante cada manual que es ejecutado en la cuenta.

Acceder desde manual:

            $exampleVar = Get-AutomationVariable -NAme 'ExampleVar'

Puede ser actualizada:

            Set-AutomationVariable -name 'ExampleVar' -value 'ExampleValue'

Puede tener consecuencias no esperadas. Si una variable que es usada en multiples manuales oes actualizada por uno de ellos, esto puede romper otros manuales.

##### Credenciales

Un tipo especial de variable es la credencial. Las credenciales contienen un nombre de usuario y una constraseña. Son tratados como secretos. Esto significa que ellos no aparecerán en logs y que tienen que ser recuperados usando una sintaxis específica de PowerShell. 

            $myCredential = Get-AutomationPSCredential -Name 'MyCredential'

El objecto *myCredencial* puede ser usado para recueperar ambos el nombre de usuario y la contraseña.

##### Conexiones

Para conectar con uno o más servicios externos desde un manual. Las cuentas de automatización permiten la creación de ntemano de uno o más conexiones.

> [!Tip]
> No es necesario crear conexiones manualmente como son proveistos con ejecutar como cuenta (Run As account).

##### Manuales

Azure automatización soporte un nnumero de tipos de manuales: PowerShell, Python 2 y gráfico. Manaules gráficos permiten componer un manual desde todos los módulos de PowerShell subidos, activos, y manuales existentes usando arrastrar y soltar.

El flujo de trabajo de PowerShell y el flujo de trabajo de gráfico son tipos disponibles. La diferencia entre manuales y manuales de flujos de trabajo es que estos últimos soportan paralelismo. Los flujos de trabajo de PowerShell soporta el uso de puntos de control.

###### Ejecución de manuales

* **Manualmente**: los manuales pueden ser ejecutados abriendolos desde el portal de Azure y presionando Inicio. También esta disponibel usando PowerShell o Azure CLI.

* **Adjuntando a webhook**: una vez el manual haya es publicado, uno o más manuales pueden ser generados para ejecutar el manual. Puede ser hablitado o deshabilitado o obteniendo una fecha de expiración. Permiten a un nuevo webhook ser generado para cada usuario. En el futuro, el acceso debe no ser acordado por un usuario particular.

* **En un horario**: puede ser adjuntado para uno o más de los compartidos horarios. 

Cuando ejecutas un manual desde un webhook o en un horario, la opción para ejecutarlo manualmente estará disponible.

##### Jobs 

Un manual es ejecutado, una nueva entrada es creada en los Jobs logs. No importa como la ejecución es inicializada. Cada entreada contendrá la fecha y hora de la ejecución fue iniciada, si occurrió algún error y un log completo de ejecución.

##### Galería de manuales

Manuales son una gran manera de automatizar tareas comunes. Hay tareas que sólo son para especificos clientes, pero hay otras que son aplicables a todos los clientes de Azure.

En la galeria, cientos de manuales pueden ser buscados y explorados. Puede ser importados directamente en una cuenta de manuales.

Antes que ejecutes un nuevo manual que has creado o importado, debes publicarlo primero. Tienes un *Borrador* y un edición *Publicado*. Sólo la versión *Publicado* puede ejecutarse, y la versión *Borrador* puede ser modificado. Cuando la versión *Borrador* esta lista, puedes publicarlo, reemplazando la existente versión *Publicado* con la versión *Borrador*.

#### PowerShell DSC

Es una noción para espeicificar la configuración de los servidores. Esta configuración es almacenada en un servidor externo, donde puede ser accedido por uno o más máquinas virtuales. Esas máquinas virtuales son conifguradas para comprobar ese servidor en un intervalo especifico para la última configuración DSC y actualizar ellos mismos para completar con su configuración.

PowerShell DSC es una extensión de la especificación del lenguaje PowerShell que es usada para escribir los estados deseados de configuraciones. Habilita los estados deseados en uno o más nodos para ser espeficiados. Un nodo especificado con servidor, o conjunto de servidores es para ser configurado. La configuración para un nodo es escrito en el formulario para uno o más recursos.

            configuration serverFarmConfig {
                Node FrontEndServer {
                    WindowsFeature IIS {
                        Ensure = 'Present'
                        Name = 'Web-Server'
                        IncludeAllSubFeature = $true
                    }
                    FileLogDirectory {
                        Type = 'Directory'
                        DestinationPath = 'C:\logs'
                        Ensure = "Present"
                    }
                }
            }

La primera, del tipo *WindowsFeature*, con el nombre **Internet Inofrmation Services (IIS)**, asegura que IIS es instalado conjuntamente con todas sus subcarácteristicas. El segundo recurso, de tipo *File*, asegura que el directorio *c:\logs* existe. El tipo de recurso de *IIS* y *File* and alguno más son construidos dentro de la especificación PowerShell DSC.

##### Compilando y aplicando PowerShell DSC

Los ficheros PowerShell DSC son guardados en texto plano, a menudo en ficheros *.ps1*. Pueden ser compilados dentro de ficheros **Managed Object Format (MOF)**. Pueden ser puestos para uno o más servidores para modificar el estado del servidor para el estado descrito en el fichero MOF. Esto es llamado **push mode**.

Otra manera de desplegar ficheros MOF es almacenandolos en un servidor central, con el que es llamado **pull server**. El pull server tiene un registro completo de todas las configuraciones y definiciones de nodos con esas configuraciones. 

Una vez que el pull server es levantado y ejecutado, servidores individuale son configurados para su configuración DSC y fijado el intervalo y aplicada su configuración. Esto puede ser realizado sin hacer nada, si el estado actual actualmente tiene el estado deseado, o ejecutando comandos para lograr el estado actual. En este proceso será revertido si es necesario.

##### Usando PowerShell DSC con Azure Automatización

Azure automatización tiene capacidades compilar para PowerShell DSC y puede rellenar el role del pull server para una o más máquinas virtuales.

Para iniciar usando la compilación de las capacidades, sube uno o más ifcheros de configuración a al cuenta de automatización. 

1. Are haciendo clicen la opción de la izquierda.
2. Selecciona **Configuraciones** en la pestaña de arriba.
3. Nuevas configuraciones pueden ser añadidas usando el botón **Añadir**. Puede seleccionar un fichero, y será añadido a la lista. Algúna configuración valida en el listado puede ser clicada y compilada en el sitio. 
4. La configuración podrá ser mostrada en la pestaña con configuraciones compiladas y puede ser aplicada a una o más máquinas virtuales.
5. La pestaña **Nodos** puede ser usada para añadir una o más máquinas virtuales desde una suscripción  para un nodo de configuración.
6. Clicando el botón **Añadir**, lo añadirás.
7. Una máquina virtual puede ser seleccionada para seleccionar la configuración a aplicar.
8. La configuración local gestionada en esa máquina será configurada para refrescar la configuración de intervalos fijados.
9. Cuando sea la configuración es refrescada, será reaplicada al servidor.

Azure automatización hablita usuarios para gestionar las máquinas virtuales. Cuando trabajas con ofertas PaaS, esto no puede ser hecho usando tecnicas como PowerShell DSC; otras técnicas deben de usarse para gestionar los ajustes de la aplicación.

#### Gestionando los ajustes de la aplicación

Otra parte de la infraestructura es la configuración de la aplicación. Un número de enfoques para almacenar y cargar la configuración de la aplicación para un Azure App Service. 

* Almacenando la configuración en un App Settings.

* Usando una combinación de identidades gestionadas y key vault.

* Usando el servicio Azure App Configuration.

La desventaja del primer enfoque es que la configuración de la aplicaciónp uede ser leída poralgún usuario quien tiene acceso administrativo (lectura) para el App service que es configurado.

#### Ajustes Azure App Service desde una plantilla ARM

Los adjustes son un recurso dentro de la plantilla ARM. Esto debe ser especificado como un recurso anidado. 

            {
                "name": "[concat(variables('websiteName'), '/appSettings')]",
                "type": "config",
                "apiVersion": "2021-03-01",
                "dependsOn": [
                    "[concat('Microsoft.Web/sites/', variables('webSiteName'))]"
                ],
                "properties": {
                    "key1": " [listKeys(parameters('storagename'), 2021-03-01').keys[0].value]",
                    "key2": "value2"
                } 
            }

El uso de la fucnión *listKeys* es especialmente usado en estos escenarios. Esto permite directamente copiar los secretos desde un servicio soportado a los ajustes de la aplicación sin almacenarlos en una solución intermedia. Para secretos que no vuelven desde fuentes Azure, los parámetros de la plantilla deben ser usados. 

La configuración especifica en la plantilla ARM corresponde para la configuración e un appservice. Sobreescriben los ajustes de los ficheros *appserttings.json* o *appsettings.config*. Actualizando automáticamente la configuración recargas la aplicación. 

Algún usuario con acceso de lectura al app service puede recuperar todos los secretos de esta manera.

##### Cargando ajustes en tiempo de ejecución desde un key vault

La localización para almacenar los ajustes es en Azure key vault, donde la aplicación los carga en tiempo de ejecución. 

La aplicación primero tiene habilitado la autencicación mediante AAD. Esto puede ser echo registrando el servicio principal manualmente, pero esto deberá retornar un uusario y contraseña que deberá ser almacenado en algún lugar. Los nombres de usuario y contraseñas son secretos pero no son almacenados en el key vault desde que ellos son necesarios para acceder. Este problema puede ser resuelto con la **identidad gestionada**.

> [!Important]
> El problema de securizar secretos almacenados pero obteniendo otros secretos en retorno para acceder a aellos es a menudo referidos como el problma de las *turtles all the way down*.

Con las identidades gestionadas de azure habilitadas en el app service, Azure automaticamente genera un servicio principal con un nombre de usuario y contraseña quno son recuperables. Sólo en tiempo de ejecución, usando un código especifico, puede una aplicación autenticarse como principal. Azure asegurara que esto sólo trabajará para el código que estas ejecutando con el app service que gestiona la identidad gestionada.

Esa identidad tiene el acceos garantizado al key vault. Esto puede ser echo en la descripción key vault en una plantilla ARM.

            {
                "type": "Microsoft.KeyVault/vaults",
                "name": "[parameters('keyVaultNa')]",
                "apiVersion": " 2021-11-01-preview",
                "location": "[resourceGroup().location]",
                "dependsOn": [
                    "[resourceId('Microsoft.Web/sites/', parameters('appServiceName'))]"
                ],
                "properties": {
                    "enabledForTemplateDeployment": false,
                    "tenantId": "[subscription().tenantId]",
                    "accessPolicies": [
                        {
                            "tenantId": "[subscription().tenantId]",
                            "objectId": [reference(concat(resourceId('Microsoft.web/sites', parameters('appServiceName')), '/providers/Microsoft.ManagedIdentity/Identities/default'), '2021-11-01-preview').principalId]", 
                            "permissions": { "secrets": ["get", "list"] }
                        }
                    ],
                    "sky": {
                        "name": "standard",
                        "family": "A"
                    }
                }
            }

La función *reference()* es usada para recuperar la información de la identidad gestionada y usa esto para crear una politica de acceso en el key vault.

Con el key vault y acceso establecidos, la aplicación puede recuperar el contenido en tiempo de inicio. Los constructores de configuración pueden ser dusados en la clase *StartUp*.

            var tokenProvider = new AzureServiceTokenProvider();
            var kvClient = new KeyVaultClient((autohoritiy, resource, scope) => tokenProvider.KeyVaultTokenCallback(authoritiy, resource, scope));

            var configurationBuilder = new ConfigurationBuilder().AddAzureKeyVault($"https://{Configuration["keyVaultName"]}.vault.azure.net/", kvClient, new DefaultKeyVaultSecretManager());
            Cofniguration = configurationBuilder.Build();

> [!Trip]
> Ejemplos de código en el paquete nuget *Microsoft.Configuration.ConfigurationBuilders.Azure*.

#### Azure App Configuration

Permite la creación central de parejas clave-valor que pueden ser usadas como configuración como un registrador, pero para multiples aplicaciones. El componente principal es el **Explorador de configuración**.

La sección claves para recuperar las claves de acceso que la aplicación puede usar para leer la configuración. Hay opciones para ver los cambios recientes y restaurar una versión anterior y para importar o exportar configuraciones.

Despues de haber creado un App Configuration y añadir las claves, puede ser recuperado desde la aplicación mediane un método de la interfaz **IConfiguration**.

            config.AddAzureAppCnfiguration(settings["ConnectionStrings: AppConfig"])

> [!Trip]
> *Nuget Mcrosoft.Azure.AppConfiguratn.AspNetCore package*.

Comparando para almacenar ajustes en Azure Key Vault, AppConfiguration hay dos puntos:

* La aplicación necesita para ser conifgurada una connection string para Azure App Configuration, almacenada al menos en un secreto en los ajustes de la aplicación.
* App onfiguration no tiene opciones de acceso tan rigidas como Key Vault. Podría tener sentido distribuir la configuración entre ambos, dependiendo del tipo de configuración.

#### Otras herrramientas

Otras herramientas disponibles para gestionar la infraestructura y la configuración mediante código.

##### CloudFormation

Es un lenguage IaC para la nube AWS. Las plantillas son escritas en JSON o YAML. 

            Resources:
                HelloBucket:
                Type: AWS::S3::Bucket
                Properties:
                AccessControl: PublicRead

Existe una extensión disponible que permite la ejecución de CloudFormation en AWS desde Azuer DevOps para crear, modificar o eliminar recursos en AWS.

##### Chef

Es una herramienta para CaC, con soporte para describir la configuración de los servidores. El **Chef server** es donde la confiugración del servidor es guardada. El **Check cliente** es un agente que ejecuta en el nodo la configuración especifica.

Definiendo el estado deseado para un servidor es echo usando un número de constructores. El nivel más bajo es la *receta*, que puede contener uno o más recursos. Una o más recetas son combinadas en *libros de cocina*, que describe la capacidad que es asignada a un nodo. La asignación de uno o más libros de cocina para un nodo se hace ejecutando una lista. La ejecución de la llista contiene todos los libros de cocicna que pueden ser aplicados al nodo.

La interacción con *Chef server* es usando una herraienta de línea de ocmandos llamada *knife*.

Hay conceptos paralelos entre PowerShell DSC y chef.

##### Puppet

Es una herramienta de despliegues y gestión de configuración que opera usando el modelo servidor-cliente. Esta centralizado en un servidor llamado **Puppet master** que es el responsable de tomarlo todo y compilarlo en un catalogo interno que mantiene el estado deseado para cada servidor gestionado. En los servidores locales se instalan un agente que conecta con el servidor. El servidor gestionado se llama **node**.

El bloque base de construcción se llama **resource**, que es definido especificnado el tipo y una serie de atributos. Son agrupados en una o más *classes*.

Puede ser instalado en máquinas virtuales de Linux o Windows en Azure.  También existen imágenes precargadas en el Azure Marketplace.

Chef, PowerShell DSC y Puppet tienen un modelo comparable para describir el estado deseado y sirven al mismo propósito. 

##### Ansible

Es la herramienta de gestión de configuración más usado en Linux pero también soporta Windows.  No tiene un servidor centralizado para todos los hosts, y tampoco trabaja con agentes. Todos los compandos ejecutados por Ansible son ejecutados usando SSH u otros protocolos HTTP(S), WinRM u otros.

Algún servidor puede iniciar el despleigue de un *playbook* contra uno o más *items* en un *inventory*. Un inventario contiene todos los servidores gestionados, yse puede agrupar en uno o más grupos. CAda servidor individual y cada grupo es un elemento de inventario. El estado es descrito en playbooks, que es una serie de tareas o roles que necesita para ser ejecutado en el servidor objetivo.  Un role es un grupo de tareas, que son entendidas para ser reusadas en más de una plabook y debe ser suficientemente general para ser usada en multiples situaciones. Los roles son idempotentes. Esto significa que las tareas en el role deben asegurar que la devolución de la ejecución de un playbook es el mismo, sin tener encuenta el número de veces ejecutado.

Los scripts de Ansible pueden ser ejecutados usando herramientas de línea de comandos o una extensión de Azure DevOps que envuelve esta herramienta. Ansible Tower provee a una interfaz gráfica en el top de las capacidades de herramientas de líneas de comandos de Ansible. 

##### Terraform

Es una solución de gestión de infraestructura multicloud. Es comparalbe con ARM templates o Bicep, la diferencia está que sólo soporta Amazon Web Services Google Cloud Platform, y otros servicios de nubes soportados. Usa un fichero de formato personalizado especificanod uno o más recursos para ser creadosusando uno o más proveedores. 

Puedes usar el formato JSON propietario de Terraform llamado **HashiCorp Configuration Language (HCL)**.

Los ficheros de configuración de Terraform son ejecutados usando CLIs.

[https://learn.hashicorp.com/collections/terraform/cli](https://learn.hashicorp.com/collections/terraform/cli)