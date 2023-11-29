# MSAL

Proporciona acceso seguro a Microsoft Graph, otras API de Microsoft, API web de terceros a su propia API web. Es compatible con muchas arquitecturas y plataformas: .NET, JavaSCript, JAva, Python, Android e iOS.

Ventajas:

+ No es necesario usar directamente las bibliotecas de OAuth ni el código en el protocolo en la aplicación.
+ Adquiere tokens en nombre de un usuario o en nombre de una aplicación (cuando se aplica a la plataforma).
+ Mantiene una caché de tokens y actualiza los tokens de forma automática cuando están próximos a expirar. No es necesario que el usuario controle la expiración de los tokens.
+ Le ayuda a especificar qué audiencia quiere que inicie sesión en la aplicación.
+ Lo ayuda a configurar la aplicación a partir de archivos de configuración.
+ Lo ayuda a solucionar problemas de la aplicación mediante la exposición de excepciones, registros y telemetría que requieren acción.

## Flujos de autenticación

|Flujo|Descripción|
|-----|-----------|
|Código de autorización|Las aplicaciones nativas y web obtienen tokens de forma segura en el nombre del usuario|
|Credenciales de clientes|Las aplicaciones de servicio se ejecutan sin interacción del usuario|
|En nombre de|La aplicación llama a una API web o de servicio, que a su vez llama a Microsoft Graph|
|Impícita|Se usa en aplicacios basadas en el navegador|
|Código del dispositivo|Habilita el inicio de sessión en un dispositivo mediante otro dispositivo que tiene un explorador|
|Integrado en Windows|Los equipos Window adquieren de ofrma silenciosa un token de acceso cuando están unidos a un dominio|
|Interactive|Las aplicacionemóviles y de escritorio llaman a Microsoft Grap nombre de un usuario|
|Nombre de usuario y contraseña|La aplicación inicia la sesión de un uusario con su nombre de usuario y contraseña|

### Aplicaciones clientes públicas y confidenciales

+ Aplicaciones cliente públicas: aplicaciones que no son de confianza para mantener de manera segura secretos, por lo que solo tienen acceso a aPI web en nombre del uaurio. Los clientes públicos no pueden contener secretos de tiempo de configuración, por lo que no tienen secretos de cliente.
+ Aplicaciones cliente confidenciales: aplicaciones ejecutadas en servidores, que se consideran de difícil acceso y pueden mantener un secreto de aplicación. Pueden contener secretos en tiempo de configuración y cada instancia del cliente puede tener una configuración diferente. 

## Inicialización de aplicaciones cliente

Para crear una instancia de la aplicación use los siguientes métodos: _PublicClientApplciationBuilder_ o _ConfidentialClientApplciationBuilder_. Antes de inicializar la aplicación, tendrá que registrarla en Microsoft Entra, del que recibirá la siguiente información:

+ El identificador de cliente (una cadena que representa un GUID).
+ La URL del proveedor de identidades (la instancia) y la audiencia de inicio de sesión para la aplicación. De forma conjunta, estos dos parámetros se conocen como la autoridad.
+ El identificador del inquilino si va a escribir una aplicación de línea de negocio exclusivamente para la organización (también denominada aplicación de un único inquilino).
+ El secreto de aplicación (cadena de secreto de cliente) o el certificado (del tipo X509Certificate2) si se trata de una aplicación cliente confidencial.
+ Con aplicaciones web y, a veces, con aplicaciones cliente públicas (concretamente cuando la aplicación debe usar a un agente), también debe establecer redirectUri donde el proveedor de identidades se conecta de nuevo a la aplicación con los tokens de seguridad.

## Inicialización desde código

Con el siguiente código genera una instancia de una aplicación cliente pública:

    IPublicClientApplication app = PublicClientApplicationBuilder.Create(clientId).Build();

Con el siguiente código genera una instancia de una aplicación cliente confidencial:

    string redirectUri = "https://myapp.azurewebsites.net";
    IConfidentialClientApplication app = ConfidentialClientApplicationBuilder.Create(clientId)
    .WithClientSecret(clientSecret)
    .WithRedirectUri(redirectUri )
    .Build();

La aplicación esta ubicada en (https://myapp.azurewebsites.net) y controla los tokens de los usuarios en la nube pública de Azure con sus cuentas. La aplicación se identifica con el proveedor de identidades compartiendo un secreto. 

## Modificadores del generador

+ Modiicador __.WithAuthority__: establece la autoridad predeterminada de la aplicación en una entidad de Microsoft Entra, con la posiblidad de elegir la nube de Azure, el público, el inquilino o proporcionar directamente el URI de la autoridad.

        var clientApp = PublicClientApplicationBuilder.Create(client_id)
        .WithAuthority(AzureCloudInstance.AzurePublic, tenant_id)
        .Build();

+ Modificador __.WithREdirectUri__: anula el URI de redireccionamiento predeterminado.

        var clientApp = PublicClientApplicationBuilder.Create(client_id)
        .WithAuthority(AzureCloudInstance.AzurePublic, tenant_id)
        .WithRedirectUri("http://localhost")
        .Build();

## Modificadores comunes a las aplicaciones cliente públicas y condidenciales

|Modificador|Descripción!
|-----------|-----------|
|__.WithAuthority()__|Establece la autoridad predeterminada en Microsoft Entra, con la posiblidad de elegir Azure Cloud, la isntancia o el inquilino o de proporcionar directmanete la URI de autoridad.|
|__.WithTenantId(string tenantId)__|Invalida el identificador del inquilino o la descripción del inquilino.|
|__.WithClientId(String)__|Invalida el identificador del cliente.|
|__.WithRedirectUri(String redirectUri)__|Invalida la URI de redirección predeterminada. Esto es útil en escenarios que requieren un agente.|
|__.WithComponent(string)__| Establece el nombre de la biblioteca mendaitne MSAL.NET.|
|__.WithDebugLoggingCallback()__|Si se llama, la aplicación llama a *Debug.Write* simplemente habilitndo seguimiento de depuración.|
|__.WithLogging()__|La aplicación llamará a una devolución de llamada con seguimientos de depuración.|
|__.WithTelemetry(TelemetryCallback telemetryCallback)__|Establece al delegado utilizado para enviar datos de telemetría.|

## Modificadores especificos de aplicaciones cliente confidenciales

|Modificador|Descripción!
|-----------|-----------|
|__.WithCertificate(X509Certificate2 certificate)__|Establece el certificado que identifica la plicación con Microsoft Entra.|
|__.WithCEntSecret(String clientSecret)__|Establece el secreto de cliente (contraseña de la aplicación) que identifica la aplicacion con Microsoft Entra.|