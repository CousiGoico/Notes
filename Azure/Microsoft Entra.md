# Microsoft Entra

## Tipos

Las entidades de servicio pueden ser de dos tipos: 
+ Aplicación: es la representación local o la instancia de aplicación de un objeto de aplicación global en un único inquilino o directorio. Se crea en cada inquilino donde se usa la aplicación y hace referencia al objeto de aplicación único global. Define lo que la aplicación puede hacer en el inquilino específico, quién puede acceder a la aplicación y a qué recursos tiene acceso la aplicación.
+ Identidad administrada: representa una identidad administrada. Proporciona una identidad que usan las aplicaciones al conectarse a los recursos que admiten la autenticación de Microsoft Entra. Se les puede conceder acceso y permisos, pero no se pueden actualizar ni modificar directamente.
+ Heredada: puede tener credenciales, nombres de entidad de servicio, direcciones URL de respuesta y otras propiedades. No tiene registro de aplicación asociado. Sólo se puede usar en el inquilino en el que se creó.

## PERMISOS

+ Permisos delegados: el usuario o un administrador dan su consentimiento para los permisos que la aplicación requiere. A la aplicación se le delega el permiso para actuar como el usuario que inició sesión al realizar llamadas al recurso de destino.
+ Acceso exclusivo de aplicación: los susan las aplicaciones que se ejecutan sin la presencia de un usuario. Sólo los puede otorgar un adminsitrador.

## CONSENTIMIENTOS

+ Consentimiento del usuario estático: debe especificar todos los permisos que necesita en la configuración de la aplicación. Si no tiene consentimiento, Microsoft Entra pedirá al usuario que proporcione su consentimiento en ese momento.
    + Una aplicación tiene que solicitar todos los permisos que podría necesitar tras el primer inicio de sesión. 
    + La aplicación tiene que conocer por adelantado los recursos a los que va a tener acceso.
+ Consentimiento del usuario incremental y dinámico: puede solicitar un conjunto mínimo de permisos por adelantado y solicitar más con el tiempo, a medida que el cliente use características de aplicación adicionales. El consentimiento incremental o dinámico solo se aplica a los permisos delegados y no a los permisos de acceso exclusivo.
+ Consentimiento del administrador: garantiza que los administradores dispone de algunos controles adicionales antes de autorizar a las aplicaciones o a los usuarios el acceso a datos con privilegios eleveados de la organización. 
+ Cosnentimiento de usuario individual: una aplicación puede solicitar los permisos que necesita mediante el parámetro de consulta del ámbito. El parámetro scope es una lista separada por espacios que incluye los permisos delegados que la app solicita. Cada permiso se indica anexando el valor del permiso al identificador del recurso. 

## Graphics

![](../Graphics/Images/MicrosoftEntra.png)