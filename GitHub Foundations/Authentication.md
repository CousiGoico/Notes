# Autenticación

## Contenido

## Introducción

La autenticación en una cuenta individual es mediante usuario y contraseña. Todas las cuentas disponen del segundo factor de autenticación (2FA) y se recomienda su uso. En el caso de una cuenta Enterprise, se puede usar una autenticación SAML.

## Autenticación

### Administración de la organización mediante SAML SSO

El SSO de SAML proporciona un vínculo entre la autorización del proveedor de identidades (IdP) y el acceso a proveedores de servicios (SaaS). Esta forma de autenticación permite a los usuarios iniciar sesión en todas sus aplicaciones con un único conjunto de credenciales. Mediante SAML, el IdP autentica a los usuarios y concede autorización a servicios como GitHub. Cuando un usuario inicia sesión en GitHub, puede ver de qué empresas es miembro. Pero si el usuario intenta acceder a los datos del repositorio, GitHub solicitará las credenciales de empresa (id. de empresa).

Como administrador de la empresa, es responsable de autorizar el acceso y los permisos de los usuarios. Incluye eventos de auditoría rutinarios y el mantenimiento de un acceso muy restringido. Como administrador de un repositorio, tiene información general de cada usuario con su acceso específico dentro del repositorio. También puede exportar fácilmente estos datos a un archivo .csv.

Lista de los IdP de SAML que admite GitHub actualmente:

- Active Directory Federation Services (AD FS)
- Microsoft Entra ID
- Okta
- OneLogin
- PingOne
- Shibboleth

> [!NOTE]
> GitHub ofrece compatibilidad limitada con todos los proveedores de identidades que implementan el estándar SAML 2.0.

Se puede lograr una mayor administración de los accesos cuando se utilizan varias organizaciones. Puede usar organizaciones para crear distintos grupos de usuarios dentro de su empresa, como departamentos o grupos que trabajen en proyectos similares. Los repositorios públicos e internos que pertenecen a una organización son accesibles para los miembros de otras organizaciones de la empresa. Los repositorios privados son inaccesibles para cualquier persona que no sea miembro de la organización.

### Información privada de la organización

Al crear el repositorio en una organización gestionada por una cuenta empresarial, pueden optar por que el repositorio sea interno. Un repositorio interno es accesible por los miembros de la organización. Un repositorio privado sólo será accesible por el creador y por quién tenga permisos para acceder a él.

### Autenticación mediante el inicio de sesión único de SAML

La autenticación de SAML es un proceso que se usa para comprobar la identidad del usuario y sus credenciales en un proveedor de identidades conocido. Puede vincular su IdP existente a GitHub para administrar el inicio de sesión de los usuarios. Proceso de inicio de sesión único de SAML:

- Antes de habilitar el inicio de sesión único de SAML en su instancia de GitHub Enterprise, un administrador debe conectar la organización de GitHub a un IdP admitido.
- Después, cuando un miembro accede a los recursos de una organización que usa el inicio de sesión único de SAML, GitHub redirige al miembro al IdP para autenticarse.
- Una vez autenticado correctamente, el IdP redirige al miembro a GitHub, donde puede acceder a los recursos de la organización. Esto significa que, incluso después de configurar el inicio de sesión único de SAML, se seguirá solicitando a los miembros de la organización de GitHub que inicien sesión en sus cuentas de usuario en GitHub.

### Aplicación del inicio de sesión único de SAML en la organización

Si ha habilitado el inicio de sesión único de SAML en toda la organización, deberá aplicar la autenticación una vez habilitada la configuración. Como administrador de la organización, puede aplicar esta configuración; para ello, seleccione `Sus organizaciones`, `Configuración` y, a continuación, `Seguridad de la organización`. En las opciones para el inicio de sesión único de SAML, seleccione `Require SAML SSO authentication for all members of the organization` (Requerir la autenticación de SSO de SAML para todos los miembros de la organización).

> [!IMPORTANT]
> Tenga en cuenta que GitHub no quitará a los miembros de la empresa que aún no se han autenticado correctamente con el IdP de SAML. Se pedirá al miembro que se autentique con el IdP de SAML la próxima vez que acceda a los recursos de la empresa o cuando intente autenticarse una vez habilitada la configuración.

### Autenticación multifactor o 2FA

La autenticación en dos fases es un nivel adicional de seguridad disponible para las cuentas de GitHub. Con 2FA, se requiere que los miembros de la organización inicien sesión con su nombre de usuario y su contraseña, y también que proporcionen una forma secundaria de autenticación, que debe ser algo que solo el usuario conoce o a lo que solo él tiene acceso. Puede requerir que los miembros de la organización, los colaboradores externos y los administradores de facturación habiliten la autenticación en dos fases para sus cuentas personales.

> [!CAUTION]
> Cuando exija el uso de la autenticación en dos fases para su organización, todas las cuentas que no usen 2FA se quitarán de la organización y perderán el acceso a sus repositorios. Esto incluye las cuentas de bots.

En su instancia de GitHub Enterprise, los usuarios tienen tres maneras de autenticarse con 2FA: mediante claves de seguridad, TOTP y SMS.

#### Llaves de seguridad

Las claves de seguridad son una opción segura, cómoda y a prueba de suplantación de identidad (phishing) para 2FA. La autenticación con una clave de seguridad requiere que la autenticación mediante TOTP (contraseña única basada en tiempo) o por SMS ya se haya completado. Para registrar una nueva clave de seguridad, el usuario debe acceder a su configuración de perfil y seguir la documentación de la clave de seguridad. Cuando se usa una clave de seguridad, ninguna información confidencial sale nunca del dispositivo físico de la clave de seguridad

#### TOTP

GitHub recomienda usar una aplicación de TOTP basada en la nube para configurar la autenticación en dos fases. Las aplicaciones de TOTP son más fiables que los SMS. Las aplicaciones de TOTP permiten realizar la copia de seguridad de los códigos de autenticación en la nube y restaurarlos si pierde el acceso a su dispositivo.

#### SMS

Si los usuarios no pueden autenticarse mediante una aplicación móvil de TOTP, pueden hacerlo mediante mensajes SMS. GitHub no admite la autenticación mediante SMS en todos los países y regiones. Antes de permitir que los usuarios se autentiquen mediante SMS, un administrador debe confirmar que este método se admite en el país o la región donde se encuentran los usuarios.

### Auditoría de 2FA para el cumplimiento de los usuarios

Puede revisar qué propietarios de la organización, miembros y colaboradores externos han habilitado la autenticación en dos fases; para ello, vaya a la esquina derecha de GitHub.com, haga clic en su foto de perfil, seleccione `Sus organizaciones` y, después, seleccione el nombre de la organización que quiera. Debajo del nombre de la organización, seleccione la pestaña `Personas` y seleccione la opción `2FA`. Aquí puede ver qué miembros de la organización y qué colaboradores externos han habilitado la autenticación en dos fases.

Es posible revocar el acceso a los usuarios de la empresa que no cumplen los requisitos, pero deberá ponerse en contacto con ellos fuera de GitHub para comunicarles por qué ya no tienen acceso a su organización. La comunicación con los usuarios que no cumplen los requisitos se realiza tradicionalmente mediante notificaciones por correo electrónico.

## Autorización de usuario

Una vez que el usuario se ha autenticado, debe autorizar cualquier token de acceso personal, clave SSH o aplicación de OAuth que quiera que use el usuario para acceder a los recursos de la organización.

### Autorización con el SSO de SAML mediante SCIM

El inicio de sesión único (SSO) de SAML proporciona a los propietarios de la organización y de la empresa en GitHub una manera de controlar y proteger el acceso a los recursos de la organización, como repositorios, incidencias y solicitudes de incorporación de cambios. Si usa el inicio de sesión único de SAML en su organización, puede implementar SCIM, o System for Cross-domain Identity Management. SCIM le permite agregar, administrar o quitar el acceso de los miembros de la organización en GitHub.

SCIM es un protocolo que indica al directorio que se ha creado una cuenta y permite automatizar el intercambio de información de identidad de usuario entre sistemas. Al incorporar un nuevo empleado, el uso de un directorio central permite aprovisionar automáticamente al usuario para que acceda a servicios como GitHub. Un administrador puede desaprovisionar a un miembro de la organización mediante SCIM y quitarlo automáticamente de la organización.

> [!NOTE]
> Si usa el inicio de sesión único de SAML sin implementar SCIM, no podrá usar el desaprovisionamiento automático.

Las integraciones de SCIM permiten el intercambio seguro de datos de identidad de usuario entre el IdP y su empresa en GitHub. Cuando las sesiones de los miembros de una organización expiran después de quitar su acceso del IdP, los miembros no se quitan automáticamente de la organización. Los tokens autorizados conceden acceso a la organización incluso después de que expiren sus sesiones. Para quitar este acceso, puede quitar manualmente el token autorizado de la organización o automatizar su eliminación con SCIM.

### Clave SSH y PAT con el SSO de SAML

El IdP de SAML y el cliente de SCIM deben usar los mismos valores de NameID y userName para cada usuario.  Cada vez que realice cambios en la pertenencia a grupos en su IdP, el IdP realizará una llamada SCIM a GitHub.com para actualizar la pertenencia de la organización correspondiente.

Para acceder a los recursos protegidos de la organización mediante la API y Git en la línea de comandos, los usuarios tendrán que estar autorizados y autenticarse con un PAT (token de acceso personal) o una clave SSH. Los usuarios pueden autorizar un PAT o una clave SSH existentes, o bien crear unos nuevos y luego autorizarlos. Como administrador, puede revisar cada token de acceso personal y cada clave SSH que un miembro ha autorizado para el acceso a la API y a Git.

Los propietarios de la organización pueden invitar a nuevos miembros manualmente desde GitHub o mediante la API. Para aprovisionar nuevos usuarios sin una invitación de un propietario de la organización, puede usar la dirección URL `https://github.com/orgs/ORGANIZATION/sso/sign_up`, reemplazando ORGANIZATION por el nombre de su organización.

La primera vez que un miembro usa el inicio de sesión único de SAML para acceder a la organización, GitHub crea automáticamente un registro que vincula la organización, la cuenta del miembro de GitHub y la cuenta del miembro en el IdP. La automatización de estas tareas reduce el tiempo necesario para que un administrador administre las credenciales de usuario.

### Conexión del IdP a la organización

Para usar el inicio de sesión único de SAML y SCIM, debe conectar su proveedor de identidades a su organización de GitHub. Lista de los proveedores de identidades que admite GitHub para SCIM:

- Microsoft Entra ID
- Okta
- OneLogin

Las solicitudes sobre los temas siguientes estén fuera del alcance del soporte técnico de GitHub:

- Integración con productos de terceros
- Configuración de hardware
- CI/CD, como Jenkins
- Escritura de scripts
- Configuración de sistemas de autenticación externos, como proveedores de identidades de SAML
- Proyectos de código abierto

El soporte técnico de GitHub en relación con los cambios en la forma en que GitHub.com usa SCIM y SAML está disponible para las empresas que usan uno de los proveedores anteriores.

## Sincronización de equipos

Si su empresa usa Microsoft Entra ID u Okta como IdP para su empresa en la nube de GitHub, puede usar la sincronización de equipos para administrar la pertenencia a equipos dentro de cada organización mediante grupos de IdP. Puede administrar las identidades de los usuarios de forma centralizada, lo que permite la autorización, la revisión y la revocación de permisos.

|Características|Descripción|
|---------------|-----------|
|Sync Users (Sincronización de usuarios)|Agrega o quita usuarios de `Teams` en GitHub para mantener la sincronización con los grupos de Active Directory.|
|Sync on new team (Sincronización en un nuevo equipo)|Sincroniza los usuarios cuando se crea un nuevo equipo.|
|Custom team/group maps (Asignaciones personalizadas de grupo o equipo)|El `slug` del equipo y el nombre del grupo se harán coincidir automáticamente, a menos que defina una asignación personalizada con `syncmap.yml`.|
|Dynamic Config (Configuración dinámica)|Usa un archivo `settings` para derivar la configuración de Active Directory y GitHub.|

### Usuarios administrados de Enterprise

Usuarios administrados de Enterprise es una característica de GitHub Enterprise Cloud que proporciona un mayor control sobre los miembros y recursos empresariales.

Cuando se usan usuarios administrados de Enterprise, todos los miembros se aprovisionan y administran a través del IdP. Los usuarios no crean sus propias cuentas en GitHub. Puede administrar la pertenencia a la organización y al equipo mediante grupos en el IdP. Las cuentas de usuario administradas están restringidas a su empresa y no pueden insertar código, colaborar ni interactuar con usuarios, repositorios u organizaciones fuera de su empresa.

#### Límites de uso

A la hora de usar la característica de sincronización de equipos, hay límites de uso específicos que debe conocer. Sobrepasar estos límites puede provocar un rendimiento inesperado y errores de sincronización.

- Número máximo de miembros en un equipo de GitHub: 5000
- Número máximo de miembros en una organización de GitHub: 10 000
- Número máximo de equipos en una organización de GitHub: 1500

#### Habilitación de la sincronización de equipos

Con la sincronización de equipos, puede usar el IdP para administrar tareas administrativas como la incorporación de nuevos miembros, la concesión de nuevos permisos en la organización y la eliminación del acceso de los miembros.

Puede habilitar y usar la sincronización de equipos, pero solo con los siguientes IdP admitidos:

- Microsoft Entra ID
- Okta

Para habilitar la sincronización de equipos con su IdP, debe obtener acceso administrativo o trabajar con el administrador de su IdP para configurar la integración y los grupos de IdP.

**Microsoft Entra ID**: El administrador del sistema de GitHub para la organización de GitHub tendrá que identificar al administrador de Microsoft Entra y trabajar con él para configurar la sincronización de equipos. En el lado de Microsoft Entra ID, el servicio se denomina "aprovisionamiento automático de cuentas de usuario". Para habilitar la sincronización de equipos para Microsoft Entra ID, la instalación necesita los siguientes permisos:

- Leer los perfiles completos de todos los usuarios
- Iniciar sesión y leer perfiles de usuario
- Leer datos de directorio

**Okta**: para habilitar la sincronización de equipos para Okta, usted o el administrador de su IdP deben:

- Habilitar el SSO de SAML y SCIM para su organización mediante Okta.
- Proporcionar la dirección URL del inquilino para la instancia de Okta.
- Generar un token de SSWS válido con permisos administrativos de solo lectura para la instalación de Okta como usuario de servicio.

#### Deshabilitación de la sincronización de equipos

Al deshabilitar la sincronización de equipos, los miembros del equipo que se asignaron a un equipo de GitHub mediante un grupo de IdP se quitan del equipo y pueden perder el acceso a los repositorios de su organización. Puede deshabilitar esta característica en la configuración de la organización; para ello, haga clic en `Su organización` y luego seleccione `Configuración`. Después, haga clic en `Seguridad de la organización` y elija `Deshabilitar` la sincronización de equipos.

## Referencias

- [GItHub docs](https://docs.github.com/en/authentication/securing-your-account-with-two-factor-authentication-2fa/accessing-github-using-two-factor-authentication)

- [GItHub docs](https://docs.github.com/en/enterprise-cloud@latest/admin/managing-iam/understanding-iam-for-enterprises/about-enterprise-managed-users#about-enterprise-managed-users)