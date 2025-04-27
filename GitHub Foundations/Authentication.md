# Autenticación

## Contenido

## Introducción

La autenticación en una cuenta individual es mediante usuario y contraseña. Todas las cuentas disponen del segundo factor de autenticación (2FA) y se recomienda su uso. En el caso de una cuenta Enterprise, se puede usar una autenticación SAML.

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

## Referencias

- [GItHub docs](https://docs.github.com/en/authentication/securing-your-account-with-two-factor-authentication-2fa/accessing-github-using-two-factor-authentication)

- [GItHub docs](https://docs.github.com/en/enterprise-cloud@latest/admin/managing-iam/understanding-iam-for-enterprises/about-enterprise-managed-users#about-enterprise-managed-users)