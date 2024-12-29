# Introducción a la administración de GitHub

Los administradores de GitHub trabajan para proteger el código y los recursos de contenido de la organización, al mismo tiempo que proporcionan a cada equipo acceso a los repositorios en los que se basan para colaborar y compartir su trabajo.

## ¿Qué es la administración de GitHub?

Como administrador GitHub, el objetivo es hacer que todo funcione a la perfección para los usuarios. 

### Administración en el nivel de equipo

Cada usuario es un miembro de la organización que se puede agregar a un equipo. Puede crear equipos en su organización con permisos de acceso en cascada y menciones que reflejen la estructura de su empresa o grupo. Los equipos son útiles para refinar los permisos de repositorio en un nivel más granular y habilitar la comunicación y notificación entre los miembros del equipo.

GitHub permite sincronizar los equipos con grupos de proveedores de identidades (IdP), como Microsoft Entra ID. Al sincronizar un equipo de GitHub con Microsoft Entra ID, puede replicar los cambios en GitHub automáticamente. Esta sincronización reduce la necesidad de actualizaciones manuales y scripts personalizados. Puede usar Microsoft Entra ID con la sincronización de equipo para administrar tareas administrativas, como la incorporación de nuevos miembros, la concesión de nuevos permisos y la eliminación del acceso de los miembros a la organización.

Los miembros de un equipo con los permisos de **responsable de mantenimiento del equipo** o **administrador de repositorio** pueden:

* Cree un equipo y seleccione o cambie el equipo principal.
* Eliminar un equipo o cambiarle el nombre.
* Agregar miembros de la organización a un equipo o quitarlos de este, así como sincronizar la pertenencia de un equipo de GitHub con un grupo de IdP.
* Agregue o quite colaboradores externos (personas que no sean explícitamente miembros de su organización, como consultores o empleados temporales) de los repositorios de equipo.
* Habilite o deshabilite las discusiones del equipo en la página del equipo.
* Cambiar la visibilidad del equipo dentro de la organización.
* Administrar la asignación automática de revisión de código para las solicitudes de incorporación de cambios mediante el algoritmo de enrutamiento de asignación de revisión de GitHub.
* Programe recordatorios.
* Configure la imagen de perfil de su equipo.

#### Prácticas recomendadas para la administración de nivel de equipo

* Cree equipos anidados para reflejar la jerarquía de su grupo o empresa dentro de la organización de GitHub.
* Cree equipos basados en intereses o tecnología específica (JavaScript, ciencia de datos, etc.) para ayudar a simplificar los procesos de revisión PR. Las personas pueden optar por unirse a estos equipos según sus intereses o aptitudes.
* Habilite la sincronización de equipos entre el IDP y GitHub para permitir que los propietarios de la organización y los responsables de mantenimiento del equipo conecten los equipos de su organización con grupos de IdP.

### Administración de nivel de organización

Las organizaciones son espacios compartidos que permiten a los usuarios colaborar en muchos proyectos a la vez. Los propietarios y los administradores pueden administrar el acceso de los miembros a los datos y los repositorios de la organización con sofisticadas características de seguridad y administración.

Los miembros de una organización con el permiso propietario pueden realizar una amplia variedad de actividades en el nivel de organización:

* Invite a usuarios a unirse a la organización y quite miembros de la organización.
* Organizar a los usuarios en un equipo y conceder permisos de responsable de mantenimiento del equipo a los miembros de la organización.
* Agregue o quite colaboradores externos (personas que no sean explícitamente miembros de su organización, como consultores o empleados temporales) de los repositorios de la organización.
* Conceder niveles de permisos de repositorio a miembros y establecer el nivel de permiso base (predeterminado) para un repositorio determinado.
* Configurar la seguridad de la organización.
* Configurar la facturación o asignar un administrador de facturación para la organización.
* Extraiga varios tipos de información sobre los repositorios mediante el uso de scripts personalizados.
* Aplique cambios en toda la organización, como las migraciones, mediante el uso de scripts personalizados.

Se recomienda configurar solo una organización para los usuarios y repositorios. Si las restricciones específicas de su empresa requieren que cree varias organizaciones, tenga en cuenta lo siguiente:

* **No es posible duplicar una organización ni compartir configuraciones entre dos organizaciones**. Esto significa que debe configurar todo desde cero cada vez que cree una organización, lo que aumenta el riesgo de errores en la configuración.
* En función de las directivas de los proveedores de software, **podría incurrir en costos adicionales** si necesita instalar algunas aplicaciones en varias organizaciones.
* La administración de varias organizaciones es más difícil.

### Administración en el nivel empresarial

Las cuentas de empresa incluyen instancias de GitHub Enterprise Cloud y Enterprise Server y permiten a los propietarios administrar de forma centralizada la directiva y la facturación de varias organizaciones.

En el nivel de empresa, los miembros de una empresa con el permiso propietario pueden:

* Habilitar el inicio de sesión único de SAML para la cuenta de empresa, lo que permite que cada miembro de la empresa vincule su identidad externa del IDP a su cuenta de GitHub existente.
* Agregar organizaciones a la empresa o quitarlas de ella.
* Configurar la facturación o asignar un administrador de facturación para todas las organizaciones de la empresa.
* Configurar directivas de administración de repositorios, directivas del panel de proyecto, directivas de equipo y otras opciones de seguridad que se aplican a todas las organizaciones, repositorios y miembros de la empresa.
* Extraiga varios tipos de información sobre las organizaciones mediante el uso de scripts personalizados.
* Aplique cambios en toda la empresa, como las migraciones, mediante el uso de scripts personalizados.

## ¿Cómo funciona la autenticación de GitHub?

### Opciones de autenticación de GitHub

#### Nombre de usuario y contraseña

Los administradores pueden permitir a los usuarios seguir usando el método predeterminado de autenticación con nombre de usuario y contraseña, lo que a veces se conoce como esquema de autenticación HTTP "básico". Se recomienda encarecidamente usar una (o varias) de las otras opciones.

#### Tokens de acceso personal (PAT)

Los tokens de acceso personal (PAT) son una alternativa al uso de contraseñas para la autenticación en GitHub cuando se usa la API de GitHub o la línea de comandos. Los usuarios generan un token a través de la opción de configuración de GitHub y vinculan los permisos de token a un repositorio u organización. Cuando los usuarios interactúan con GitHub mediante la herramienta de línea de comandos de Git, pueden escribir la información del token cuando se les pida su nombre de usuario y contraseña.

#### Claves SSH

Como alternativa al uso de tokens de acceso personal, los usuarios pueden conectarse y autenticarse en servidores y servicios remotos mediante SSH con la ayuda de claves SSH. Las claves SSH eliminan la necesidad de que los usuarios proporcionen su nombre de usuario y su token de acceso personal con cada interacción.

Al configurar SSH, los usuarios generarán una clave SSH, la agregarán al agente de SSH y, después, la agregarán a su cuenta de GitHub. La adición de la clave SSH al agente de SSH garantiza que la clave SSH tenga un nivel de seguridad adicional mediante el uso de una frase de contraseña. Los usuarios pueden configurar la copia local de Git de modo que proporcione la frase de contraseña automáticamente, o bien pueden proporcionarla de forma manual cada vez que usen la herramienta de línea de comandos de Git para interactuar con GitHub.

Se puede incluso usar las claves SSH con un repositorio que sea propiedad de una organización que use el inicio de sesión único (SSO) de SAML. Si la organización proporciona certificados SSH, los usuarios también pueden usarlos para acceder a los repositorios de la organización sin agregar el certificado a su cuenta de GitHub.

#### Claves de implementación

Las claves de implementación son otro tipo de clave SSH en GitHub que conceden a un usuario acceso a un único repositorio. GitHub adjunta la parte pública de la clave directamente al repositorio en lugar de a una cuenta de usuario personal, y la parte privada de la clave permanece en el servidor del usuario. Las claves de implementación son de solo lectura de forma predeterminada, pero puede darles acceso de escritura al agregarlas a un repositorio.

### Opciones de seguridad agregadas de GitHub

#### Autenticación en dos fases

La autenticación en dos fases (2FA), también conocida como autenticación multifactor (MFA), es un nivel de seguridad adicional que se usa al iniciar sesión en sitios web o aplicaciones. Con 2FA, los usuarios deben iniciar sesión con su nombre de usuario y contraseña y proporcionar otra forma de autenticación a la que solo ellos tengan acceso.

En GitHub, la segunda forma de autenticación es un código generado por una aplicación en el dispositivo móvil de un usuario o enviado como mensaje de texto (SMS). Una vez que un usuario haya habilitado 2FA, GitHub generará un código de autenticación cada vez que alguien intente iniciar sesión en su cuenta de GitHub. Los usuarios solo pueden iniciar sesión en su cuenta si conocen su contraseña y tienen acceso al código de autenticación en su teléfono.

Los propietarios de la organización pueden requerir que los miembros de la organización, los colaboradores externos y los administradores de facturación habiliten 2FA para sus cuentas personales. Esta acción dificulta que los actores malintencionados accedan a los repositorios y la configuración de una organización.

#### SSO de SAML

Si administra centralmente las identidades y aplicaciones de los usuarios con un proveedor de identidades, puede configurar el inicio de sesión único de SAML para proteger los recursos de la organización en GitHub.

Este tipo de autenticación proporciona a los propietarios de la organización y de la empresa en GitHub una manera de controlar y proteger el acceso a los recursos de la organización, como repositorios, incidencias y solicitudes de incorporación de cambios. Los propietarios de la organización pueden invitar a los usuarios de GitHub a unirse a la organización que usa el inicio de sesión único de SAML. De este modo, los usuarios pueden contribuir a la organización y conservar su identidad y sus contribuciones existentes en GitHub.

Cuando los usuarios accedan a los recursos de una organización que usa el inicio de sesión único de SAML, GitHub los redirigirá al proveedor de identidades de SAML de la organización para que se autentiquen. Una vez que se hayan autenticado correctamente con su cuenta en el proveedor de identidades, este los redirigirá a GitHub para que puedan acceder a los recursos de la organización.

GitHub ofrece compatibilidad limitada con todos los proveedores de identidades que implementan el estándar SAML 2.0, con soporte técnico oficial para varios proveedores de identidades populares, entre los que se incluyen:

* Servicios de federación de Active Directory (AD FS).
* Microsoft Entra ID.
* Okta.
* OneLogin.
* PingOne.

#### LDAP

El protocolo ligero de acceso a directorios (LDAP) es un protocolo de aplicación popular para acceder a los servicios de información de directorios y mantenerlos. LDAP le permite autenticar GitHub Enterprise Server en sus cuentas existentes y administrar de forma centralizada el acceso al repositorio. Es uno de los protocolos más comunes utilizados para integrar software de terceros con directorios empresariales de usuarios de gran tamaño.

GitHub Enterprise Server se integra con servicios de LDAP populares, como:

* Active Directory.
* Oracle Directory Server Enterprise Edition.
* OpenLDAP.
* Open Directory.

## ¿Cómo funcionan los permisos y la organización de GitHub?

### Niveles de permisos de repositorio

* Lectura: Se recomienda para colaboradores que no trabajan en el código, pero que quieren ver el proyecto o hablar sobre él. Esto es bueno para cualquier persona que necesite ver el contenido dentro del repositorio, pero que realmente no necesite realizar contribuciones ni cambios.
* Evaluación de prioridades: Se recomienda para colaboradores que necesitan administrar de forma proactiva incidencias y solicitudes de incorporación de cambios sin acceso de escritura. Este nivel podría ser bueno para algunos administradores de proyectos que administran problemas de seguimiento, pero no realizan ningún cambio.
* Escritura: Se recomienda para los colaboradores que insertan cambios activamente en el proyecto. El permiso de escritura es el permiso estándar para la mayoría de los desarrolladores.
* Mantenimiento: Recomendado para gestores de proyectos que necesitan gestionar el repositorio sin acceso a acciones sensibles o destructivas.
* Administrador: Se recomienda para usuarios que necesitan acceso total al proyecto, incluidas acciones confidenciales y destructivas, como administrar la seguridad o eliminar un repositorio. Se trata de propietarios y administradores del repositorio.

#### Crear una plantilla de un repositorio

Después de crear un repositorio con los permisos correctos, puede convertirlo en una plantilla para que cualquier persona que tenga acceso al repositorio pueda generar un nuevo repositorio que tenga la misma estructura de directorios y archivos que la rama predeterminada.

1. Ir a la página principal del repositorio.
2. En el nombre del repositorio, seleccione **Configuración**. Si no puede ver la pestaña Configuración, abra el menú desplegable y seleccione **Configuración**.
3. Seleccione **Template repository**.

### Niveles de permisos de equipo

Los equipos proporcionan una manera sencilla de asignar permisos de repositorio a varios usuarios relacionados al mismo tiempo. Los miembros de un equipo secundario heredan la configuración de permisos del equipo principal, lo que ofrece una manera sencilla de conceder permisos en cascada basados en la estructura natural de la empresa.

<table style="border:1px solid white">
    <tr>
        <th>Nivel de permiso</th>
        <th>Descripción</th>
    </tr>
    <tr>
        <td>Miembro</td>
        <td>Los miembros del equipo tienen el mismo conjunto de capacidades que los miembros de la organización</td>
    </tr>
    <tr>
        <td>Respnsable de mantenimiento</td>
        <td>Los responsables de mantenimiento del equipo pueden hacer lo mismo que los miembros del equipo, además de lo siguiente:<br />
            - Cambiar el nombre, la descripción y la visibilidad del equipo.<br />
            - Solicitar que el equipo cambie los equipos principales y secundarios.<br />
            - Configurar la imagen de perfil de su equipo.<br />
            - Editar y eliminar debates del equipo.<br />
            - Agregar miembros de la organización al equipo y quitarlos.<br />
            - Promover a miembros del equipo para que tengan también el permiso de responsable de mantenimiento del equipo.<br />
            - Quitar el acceso del equipo a los repositorios.<br />
            - Administrar la asignación de revisión de código para el equipo.<br />
            - Administrar avisos programados para solicitudes de incorporación de cambios.
        </td>
    </tr>
</table>

El propietario de una organización también puede promover a cualquier miembro de la organización a responsable de mantenimiento del equipo. Para auditar el acceso a un repositorio que administra, puede ver una lista combinada de equipos y usuarios con acceso al repositorio en la configuración.