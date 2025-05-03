# Roles

## Contenido

- [Introducción](#introducción)
  - [Roles en una organización](#roles-en-una-organización)
    - [Propietarios de la organización](#propietarios-de-la-organización)
    - [Miembros de la organziación](#miembros-de-la-organziación)
    - [Moderadores de la organización](#moderadores-de-la-organización)
    - [Miembros como gerentes de facturación](#miembros-como-gerentes-de-facturación)
    - [Administradores de seguridad](#administradores-de-seguridad)
    - [GitHub App administradores](#github-app-administradores)
    - [Colaboradores externos](#colaboradores-externos)
- [Gerentes de facturación](#gerentes-de-facturación)
  - [Permisos de los gerentes de facturación](#permisos-de-los-gerentes-de-facturación)
  - [Invitar a un gerente de facturación](#invitar-a-un-gerente-de-facturación)
- [Colaboradores](#colaboradores)
- [Referencias](#referencias)

## Introducción

Puedes personalizar el acceso a cada repositorio en tu organización si asignas roles granulares, lo cual le otorga acceso a las personas para las características y tareas que necesitan.

### Roles en una organización

Desde el menor hasta el mayo acceso, los roles para un repositorio de organización son:

- **Lectura**: se recomienda para colaboradores que no trabajan en el código, pero que quieren ver el proyecto o hablar sobre él
- **Evaluación de prioridades**: recomendado para colaboradores que necesitan administrar de forma proactiva problemas, discusiones y solicitudes de incorporación de cambios sin acceso de escritura
- **Escritura**: se recomienda para los colaboradores que insertan cambios en el proyecto de forma activa
- **Mantenimiento**: se recomienda para los jefes de proyecto que necesitan administrar el repositorio sin acceder a acciones confidenciales o destructivas
- **Administración**: se recomienda para usuarios que necesitan acceso total al proyecto, incluidas acciones confidenciales y destructivas, como administrar la seguridad o eliminar un repositorio
- **Administrador de CI/CD**: concede acceso de administrador para administrar directivas de acciones, ejecutores, grupos de ejecutores, configuraciones de red de equipos host, secretos, variables y métricas de uso para una organización.
- **Administrador de seguridad**: concede la capacidad de administrar directivas de seguridad, alertas de seguridad y configuraciones de seguridad para una organización y todos sus repositorios.

#### Propietarios de la organización

Tienen acceso administrativo integral en tu organización. Este rol debe limitarse a dos personas, por lo mucho, en tu organización.

#### Miembros de la organziación

El rol no administrativo predeterminado para las personas en una organización es el miembro de la misma. Predeterminadamente, los miembros de las organizaciones tienen varios permisos, incluyendo la capacidad de crear repositorios y proyectos.

#### Moderadores de la organización

Pueden bloquear y desbloquear a colaboradores que no son miembros, establecer límites de interacción y ocultar comentarios en repositorios públicos que son propiedad de la organización.

#### Miembros como gerentes de facturación

Pueden administrar los ajustes de facturación de tu organización, tales como la información de pago. Esta es una opción útil si los miembros de tu organización normalmente no tienen acceso a los recursos de facturación.

#### Administradores de seguridad

Rol de nivel de organización que los propietarios de la organización pueden asignar a cualquier miembro o equipo de la organización. Cuando se aplica, concede permiso para ver las alertas de seguridad y administrar la configuración de las características de seguridad en toda la organización, así como permiso de lectura para todos los repositorios de la organización.

#### GitHub App administradores

Únicamente los propietarios de la organización pueden administrar las configuraciones de los registros de GitHub App propiedad de una organización. Para permitir que más usuarios administren los registros de GitHub App propiedad de una organización, un propietario puede otorgarles permisos de administrador de GitHub App.

Cuando designas un usuario como administrador de GitHub App en la organización, puedes otorgarle acceso para administrar las configuraciones de algunos o todos los registros de GitHub App propiedad de la organización. El rol de administrador de GitHub App no concede a los usuarios acceso para instalar y desinstalar GitHub Apps en una organización.

#### Colaboradores externos

Para mantener seguros los datos de su organización y, al mismo tiempo, permitir el acceso a los repositorios, puede agregar colaboradores externos. Un colaborador externo es una persona que tiene acceso a uno o más repositorios de la organización, pero no es explícitamente miembro de la organización, como ser, un consultor o empleado transitorio.

## Gerentes de facturación

Un gerente de facturación es un usuario que administra los parámetros de facturación de tu organización, como la actualización de la información de pago.

Los miembros del equipo de propietarios de la organización pueden conceder permisos de administradores de facturación a los usuarios. Una vez que una persona acepta la invitación para convertirse en gerente de facturación para tu organización, puede invitar a otras personas para convertirse en gerentes de facturación.

> [!NOTE]
> Los responsables de facturación no usan licencias de pago en la suscripción de la organización.

### Permisos de los gerentes de facturación

Los gerentes de facturación pueden:

- Actualización o cambio a una versión anteror entre planes GitHub Free y GitHub Team.
- Agregar, actualizar o eliminar métodos de pago.
- Ver historial de pagos.
- Descargar recibos.
- Ver, invitar y eliminar gerentes de facturación.
- Iniciar, modificar o cancelar los patrocionios.
- Además, todos los gerentes de facturación recibirán recibos de facturación por correo electrónico en la fecha de facturación de la organización.

Los administradores de facturación no pueden:

- Actualización a GitHub Enterprise o cambio a una versión anterior de una cuenta de empresa.
- Crear o acceder a repositorios en sus organizaciones.
- Ver miembros privados de tu organización.
- Ser visto en la lista de los miembros de la organización.
- Comprar, editar o cancelar suscripciones para aplicaciones de GitHub Marketplace.
- Comprar, editar o cancelar suscripciones de GitHub Copilot Business o GitHub Copilot Enterprise.

### Invitar a un gerente de facturación

La persona invitada recibirá una invitación por correo electrónico solicitándole que se convierta en gerente de facturación para tu organización. Una vez que la persona invitada hace clic en el enlace de aceptación en el correo electrónico de la invitación, se agregarán automáticamente a la organización como gerentes de facturación. Si aún no tienen una cuenta de GitHub, se les dirigirá para suscribirse a una y se agregarán automáticamente a la organización como administrador de facturación después de crear una cuenta.

1. En la esquina superior derecha de cualquier página en GitHub, haga clic en la fotografía de perfil y luego en `Configuración`.

2. En la sección `Acceso` de la barra lateral, haz clic en `Organizaciones`.

3. Junto a la organización, haga clic en `Settings`.

4. Si eres propietario de una organización, en la sección `Acceso` de la barra lateral, haz clic en `Facturación y planes`.

5. En `Administración de facturación`, junto a `Administradores de facturación`, haga clic en `Agregar`.

6. Escribe el nombre de usuario o la dirección de correo electrónico de la persona a la que quieres agregar y haz clic en `Enviar invitación`.

## Colaboradores

Es una persona que no es miembro de tu organización, pero tiene acceso a uno o más repositorios de ella. Cuando agregas un colaborador externo a un repositorio, también es necesario que lo agregues en cualquier bifurcación del repositorio al que le quieras dar acceso.

A menos que esté en un plan gratuito, agregar un colaborador externo a un repositorio privado usará una de sus licencias de pago. Las organizaciones que utilizan GitHub Enterprise Cloud pueden restringir la capacidad para invitar a colaboradores.

Los colaboradores externos no se pueden agregar a un equipo, la pertenencia al equipo está restringida a los miembros de la organización.

## Referencias

[GitHub docs](https://docs.github.com/en/organizations/managing-peoples-access-to-your-organization-with-roles/adding-a-billing-manager-to-your-organization)

[Microsoft Learn](https://learn.microsoft.com/en-us/training/modules/github-introduction-administration/2-what-is-github-administration)

[GitHub docs - Roles](https://docs.github.com/en/organizations/managing-peoples-access-to-your-organization-with-roles/roles-in-an-organization)

[GitHub docs - Roles II](https://docs.github.com/en/organizations/managing-user-access-to-your-organizations-repositories/managing-repository-roles/repository-roles-for-an-organization#repository-roles-for-organizations)

[GitHub docs - Roles III](https://docs.github.com/en/organizations/managing-peoples-access-to-your-organization-with-roles/roles-in-an-organization)

[GitHub docs - Levels](https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-user-account-settings/permission-levels-for-a-personal-account-repository)

[GitHub docs - Collaborators](https://docs.github.com/en/organizations/managing-access-to-your-organizations-repositories/adding-outside-collaborators-to-repositories-in-your-organization)

[GitHub docs - Permissions](https://docs.github.com/en/organizations/managing-user-access-to-your-organizations-repositories/managing-repository-roles/repository-roles-for-an-organization)
