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