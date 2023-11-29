# App Configuration

Azure App Configuration proporciona un servicio para administrar la configuración de la aplicación y las marcas de características de forma centralizada.

## Exploración del servicio Azure App Configuration

Use App Configuration para almacenar toda la configuración de la aplicación y proteger sus accesos en un solo lugar.

Ventajas:

+ Un servicio totalmente administrado que puede configurar en cuestión de minutos.
+ Representaciones y asignaciones de claves flexibles.
+ Etiquetado con etiquetas.
+ Reproducción de la configuración en un momento dado.
+ Interfaz de usuario dedicada para la administración de marcas de características.
+ Comparación de dos conjuntos de configuraciones en dimensiones definidas de forma personalizada.
+ Seguridad mejorada mediante las identidades administradas de Azure.
+ Cifrado de información confidencial en reposo y en tránsito.
+ Integración nativa con plataformas conocidas.

__App Configuration complementa Azure Key Vault, que se usa para almacenar secretos de aplicación.__

Implementaciones:

+ La administración centralizada y la distribución de datos de configuración jerárquicos para diferentes entornos y regiones geográficas.
+ Los cambios de configuración dinámica sin necesidad de volver a implementar o reiniciar una aplicación.
+ El control de la disponibilidad de las características en tiempo real.

### Use de AppConfiguration

|Lenguaje y plataforma de programación|Conexión|
|-------------------------------------|--------|
|.NET Core y ASP.NET Core|[Proveedor](https://learn.microsoft.com/es-es/dotnet/api/Microsoft.Extensions.Configuration.AzureAppConfiguration) de AppConfiguration para .NET Core|
|.NET Framework y ASP.NET|[Generador](https://github.com/aspnet/MicrosoftConfigurationBuilders/blob/main/README.md#azureappconfigurationbuilder) de AppConfiguration para .NET Core|
|Java Spring|[Cliente](https://microsoft.github.io/spring-cloud-azure/docs/azure-app-configuration/2.9.0/reference/html/index.html) de App Configuration para Spring Cloud|
|JavaScript/Node.js|[Cliente](https://github.com/Azure/azure-sdk-for-js/tree/main/sdk/appconfiguration/app-configuration) de App Configuration para JavaScript|
|Python|[Cliente](https://github.com/Azure/azure-sdk-for-python/tree/main/sdk/appconfiguration/azure-appconfiguration) de App Configuration para Python|
|Otros|[API REST](https://learn.microsoft.com/es-es/rest/api/appconfiguration/) de App Configuration|

## Creación de claves y valores emparejados

Azure App Configuration almacena los datos de configuración como pares clave-valor.

### Claves

Las claves sirven como nombre de los pares clave-valor y se usan para almacenar y recuperar los valores correspondientes. Es una práctica habitual la organización de las claves en un espacio de nombres jerárquico mediante un delimitador de caracteres como / o :. 

Las claves almacenadas en App Configuration distinguen entre mayúsculas y minúsculas y son cadenas basadas en Unicode, excepto los caráceteres reservados (`*`, `,` y `\`). Si tiene que usar un carácter reservado, deberá especificar un carácter de escape con `\{Reserved Character}`.

Hay un límite de tamaño combinado de diez mil caracteres en un par clave-valor

### Diseño de espacios de nombres de clave

Hay dos enfoques generales en relación con la nomenclatura de las claves que se usa en los datos de configuración: plano o jerárquico. La nomenclatura jerárquica ofrece varias ventajas:

+ Es más fácil de leer. En lugar de una secuencia larga de caracteres, los delimitadores de una función de nombre de clave jerárquico funciona como los espacios de una frase.
+ Es más fácil de administrar. Un nombre de clave jerárquico representa grupos lógicos de datos de configuración.
+ Es más fácil de usar. Resulta más fácil escribir una consulta cuyos patrones coinciden con las claves de una estructura jerárquica y que recupera solo una porción de los datos de configuración.

En los ejemplos siguientes se muestra cómo puede estructurar los nombres de clave en una jerarquía:

+ Según los servicios de los componentes.

        AppName:Service1:ApiEndpoint
        AppName:Service2:ApiEndpoint

+ Según las regiones de implementación.

        AppName:Region1:DbEndpoint
        AppName:Region2:DbEndpoint

### Claves de etiqueta

Los valores de clave de App Configuration pueden tener un atributo de etiqueta. Las etiquetas se utilizan para diferenciar los valores de clave con la misma clave. De forma predeterminada, la etiqueta de un valor de clave está vacía o es null.

Las etiquetas proporcionan una manera cómoda de crear variantes de una clave. Un uso habitual de las etiquetas consiste en especificar varios entornos para la misma clave:

        Key = AppName:DbEndpoint & Label = Test
        Key = AppName:DbEndpoint & Label = Staging
        Key = AppName:DbEndpoint & Label = Production

### Valores de clave de versión

App Configuration no crea valores de clave de versión automáticamente a medida que se modifican. Use etiquetas como una manera de crear varias versiones de un valor de clave. Por ejemplo, puede escribir un número de versión de la aplicación o un identificador de confirmación de Git en las etiquetas para identificar los valores de clave asociados con una compilación de software en particular.

### Valores de clave de consulta

Cada valor de clave se identifica por su clave más una etiqueta que puede ser null. Si desea consultar los valores de las claves en un almacén de App Configuration, especifique un modelo. El almacén de App Configuration devuelve todos los valores de claves que coincidan con el modelo, así como sus valores y atributos correspondientes.

### Valores

Los valores asignados a las claves también son cadenas unicode. Hay un tipo de contenido opcional definido por el usuario que se asocia a cada valor. Utilice este atributo para almacenar información.

Los datos de configuración que se encuentran en un almacén de App Configuration, entre los que se incluyen todas las claves y los valores, se cifran tanto en reposo como en tránsito. App Configuration no es una solución de reemplazo para Azure Key Vault. No almacene secretos de aplicación en ella.

## Administración de características de la aplicación

La administración de características es una práctica moderna de desarrollo de software que separa el lanzamiento de las características de la implementación del código y permite hacer cambios rápidos relacionados con la disponibilidad de las características a petición. Usa una técnica denominada marcas de características (también conocida como activación/desactivación de funcionalidad o modificador de características, entre otros) para administrar el ciclo de vida de una característica dinámicamente.

### Conceptos básicos

+ __Marca de característica__: una marca de características es una variable con un estado binario de activado o desactivado. La marca de características también tiene un bloque de código asociado. El estado de la marca de características se desencadena tanto si el bloque de código se ejecuta como si no.

+ __Administrador de características__: un administrador de características es un paquete de aplicación que controla el ciclo de vida de todas las marcas de características de una aplicación. Normalmente, el administrador de características proporciona funcionalidad adicional, como el almacenamiento en caché de las marcas de características y la actualización de sus estados.

+ __Filtro__: Un filtro es una regla para evaluar el estado de una marca de características. Un grupo de usuarios, un tipo de explorador o dispositivo, una ubicación geográfica y un período de tiempo son todos ellos ejemplos de lo que puede representar un filtro.

Una implementación eficaz de la administración de características consta de al menos dos componentes que funcionan conjuntamente:

+ Una aplicación que hace uso de las marcas de características.
+ Un repositorio independiente que almacena las marcas de características y sus estados actuales.

### Uso de la marca de características en el código

El patrón básico para implementar las marcas de características en una aplicación es sencillo. Puede considerar una marca de características como una variable de estado booleana usada con una declaración condicional if en su código:

        if (featureFlag) {
           // Run the following code
        }

Si featureFlag está establecido en True, se ejecuta el bloque de código incluido; en caso contrario, se omite. Puede establecer el valor de featureFlag estáticamente, como se muestra en el ejemplo de código siguiente:

        bool featureFlag = true;

También puede evaluar el estado de la marca según ciertas reglas:

        bool featureFlag = isBetaUser();

Un patrón de marca de características un poco más complicado incluye también una instrucción else:

        if (featureFlag) {
            // This following code will run if the featureFlag value is true
        } else {
            // This following code will run if the featureFlag value is false
        }

### Declaración de la marca de características

Cada marca de características tiene dos partes: un nombre y una lista de uno o varios filtros que se utilizan para evaluar si el estado de la característica está activo. Un filtro define un caso de uso en el que debe activarse una característica.

Cuando una marca de características tiene varios filtros, la lista de filtros se recorre en orden hasta que uno de los filtros determina que se debe habilitar la característica. En ese momento, la marca de característica está activa y se omiten los resultados del filtro restantes. Si ningún filtro indica que se debe habilitar la característica, la marca de características está desactivada.

El administrador de la característica admite appsettings.json como origen de configuración para las marcas de características. El ejemplo siguiente muestra cómo establecer las marcas de características en un archivo JSON:

        "FeatureManagement": {
            "FeatureA": true, // Feature flag set to on
            "FeatureB": false, // Feature flag set to off
            "FeatureC": {
                "EnabledFor": [
                    {
                        "Name": "Percentage",
                        "Parameters": {
                            "Value": 50
                        }
                    }
                ]
            }
        }

### Repositorio de marcas de características

Para usar marcas de características de forma eficaz, debe externalizar todas las marcas de características usadas en una aplicación. Ese enfoque le permite cambiar los estados de las marcas de características sin modificar y volver a implementar la propia aplicación.

Azure App Configuration está diseñado para ser un repositorio centralizado para las marcas de características. Puede usarla para definir distintos tipos de marcas de características y manipular sus estados con rapidez y confianza. Luego, puede usar las bibliotecas de App Configuration con diversos marcos de lenguajes de programación para acceder fácilmente a estas marcas de características desde su aplicación.

## Protección de los datos de configuración de aplicaciones

### Cifrado de datos de configuración mediante claves administradas por el cliente

Azure App Configuration cifra la información confidencial en reposo mediante una clave de cifrado AES de 256 bits proporcionada por Microsoft. Cada instancia de App Configuration tiene su propia clave de cifrado que administra el servicio y que se usa para cifrar la información confidencial. La información confidencial incluye los valores que se encuentran en los pares clave-valor. Cuando está habilitada la funcionalidad de claves administradas por el cliente, App Configuration usa una identidad administrada asignada a la instancia de App Configuration para autenticarse con Microsoft Entra ID. Luego, la identidad administrada llama a Azure Key Vault y encapsula la clave de cifrado de la instancia de App Configuration. La clave de cifrado encapsulada se almacena y la clave de cifrado desencapsulada se almacena en caché en App Configuration durante una hora. App Configuration actualiza la versión desencapsulada de la clave de cifrado de la instancia de App Configuration cada hora. De esta forma, se garantiza la disponibilidad en condiciones de funcionamiento normales.

#### Habilitación de la funcionalidad de clave administrada por el cliente

Los componentes siguientes son necesarios para habilitar correctamente la funcionalidad de clave administrada por el cliente en Azure App Configuration:

+ Instancia de Azure App Configuration de nivel estándar.
+ Azure Key Vault con las características de eliminación temporal y protección de purga habilitadas.
+ Una clave RSA o RSA-HSM dentro de Key Vault: la clave no debe haber expirado, debe estar habilitada y debe tener habilitadas las funcionalidades de encapsular y desencapsular.

Una vez configurados estos recursos, quedan dos pasos para permitir que Azure App Configuration use la clave de Key Vault:

+ Asignación de una identidad administrada a la instancia de Azure App Configuration.
+ Conceda los permisos `GET`, `WRAP` y `UNWRAP` en la directiva de acceso de Key Vault de destino.

### Uso de puntos de conexión privados para Azure App Configuration

El punto de conexión privado usa una dirección IP del espacio de direcciones de la red virtual para el almacén de App Configuration. El tráfico de red entre los clientes de la red virtual y la cuenta de App Configuration atraviesa la red virtual usando un vínculo privado en la red troncal de Microsoft, lo que elimina la exposición a la red pública de Internet.

+ Proteger los detalles de configuración de la aplicación mediante la configuración del firewall para bloquear todas las conexiones a App Configuration en el punto de conexión público.
+ Aumentar la seguridad de la red virtual, lo que garantiza que los datos no escapen de ella.
+ Conectarse de forma segura al almacén de App Configuration desde las redes locales que se conectan a la red virtual mediante VPN o ExpressRoute con emparejamiento privado.

#### Identidades administradas

Una identidad administrada de Microsoft Entra ID permite a Azure App Configuration acceder fácilmente a otros recursos protegidos por Microsoft Entra ID, como Azure Key Vault. La plataforma de Azure administra la identidad. No es necesario que aprovisione ni rote ningún secreto.

La aplicación puede tener dos tipos de identidades:

+ Una identidad asignada por el sistema está asociada al almacén de configuración. Se elimina si se elimina el almacén de configuración. Un almacén de configuración solo puede tener una identidad asignada por el sistema.
+ Una identidad asignada por el usuario es un recurso de Azure independiente que se puede asignar al almacén de configuración. Un almacén de configuración puede tener varias identidades asignadas por el usuario.

#### Adiciónde una identidad asignada por el sistema

Para configurar una identidad administrada mediante la CLI de Azure, use el comando `az appconfig identity assign` en un almacén de configuración existente.

        az appconfig identity assign \ 
            --name myTestAppConfigStore \ 
            --resource-group myResourceGroup

#### Adición de una identidad asignada por el usuario

La creación de un almacén de App Configuration con una identidad asignada por el usuario requiere que se cree la identidad y luego se asigne su identificador de recurso al almacén.

Cree una identidad mediante el comando `az identity create`:

        az identity create --resource-group myResourceGroup --name myUserAssignedIdentity

Asigne la nueva identidad asignada por el usuario al almacén de configuración `myTestAppConfigStore`:

        az appconfig identity assign --name myTestAppConfigStore \ 
            --resource-group myResourceGroup \ 
            --identities /subscriptions/[subscription id]/resourcegroups/myResourceGroup/providers/Microsoft.ManagedIdentity/userAssignedIdentities/myUserAssignedIdentity