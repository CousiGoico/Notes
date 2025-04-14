# GitHub

**Contenido**
* [Tipos de cuentas](#TiposCuentas)
    * [Cuenta de usuario](#CuentasUsuario)
        * [Cuentas personales](#CuentasPersonales)
        * [Cuentas de usuario administradas](#CuentasUsuarioAdministradas)
    * [Cuenta de organización](#CuentasOrganizacion)
        * [Roles de una organización](#RolesOrganizacion)
        * [Roles predefinidos de una organización](#RolesPredefinidosOrganizacion)
        * [Acerca de los roles en las organizaciones](#AcercaRolesOrganizacion)
            * [Propietarios](#Propietarios)
            * [Miembros](#Miembros)
            * [Moderadores](#Moderadores)
            * [Gerentes de facturación](#GerentesFacturacion)
            * [Administradores de seguridad](#AdministradoresSeguridad)
            * [GitHub App Administradores](#GitHubAppAdministradores)
            * [Colaboradores externos](#ColaboradoresExternos)
    * [Cuenta empresarial](#CuentasEmpresarial)
* [Fusión de múltiples cuentas personales](#FusionCuentas)
* [Crear y administrar repositorios](#CrearAdministrarRepositorios)
    * [Creación desde una plantilla](#CreacionDesdePlantilla)
        * [Acerca de las plantillas de repositorio](#AcercaPlantillasRepositorio)
        * [Crear un repositorio desde una plantilla](#CrearRepositorioDesdePlantilla)
        * [Crear plantilla desde repositorio](#CrearPlantillaDesdeRepositorio)
* [Personalizar panel](#PersonalizarPanel)

## Tipos de cuentas<a id="TiposCuentas"></a>

* Cuentas de usuario
* Cuentas de organización
* Cuentas empresariales

### Cuenta de usuario<a id="CuentasUsuario"></a>

Cada persona que usa GitHub inicia sesión en una cuenta de usuario. Su cuenta de usuario es su identidad en GitHub y tiene un nombre de usuario y perfil.

Su cuenta de usuario puede poseer recursos como repositorios, paquetes y proyectos. Cada vez que realiza alguna acción en GitHub, como crear un problema o revisar una solicitud de extracción, la acción se atribuye a su cuenta de usuario.

Puede crear cuentas (usuario de máquina) para automatizar la actividad en GitHub, como automatizar los flujos de trabajo de integración continua (CI)

Tipos de cuenta de usuario:

* Cuentas personales

* Cuentas de usuario administradas

#### Cuentas personales<a id="CuentasPersonales"></a>

Si se inscribió en su propia cuenta en GitHub.com, está utilizando una cuenta personal. Cada cuenta personal utiliza uno de los siguientes planes de pago:

* GitHub Free 

* GitHub Pro.

Todas las cuentas personales pueden poseer un número ilimitado de repositorios públicos y privados, con un número ilimitado de colaboradores en esos repositorios.

#### Cuentas de usuario administradas<a id="CuentasUsuarioAdministradas"></a>

Si una empresa creó su cuenta en GitHub Enterprise Cloud para usted, está utilizando una cuenta de usuario administrada.

* Algunos de los detalles y configuraciones de su cuenta son administrados por su empresa.
* Debe iniciar sesión en su cuenta de usuario administrada para acceder a organizaciones y repositorios propiedad de la empresa.
* Puede crear sus propios repositorios privados, pero no puede crear contenido público ni contribuir a repositorios fuera de la empresa.

### Cuenta de organización<a id="CuentasOrganizacion"></a>

Las organizaciones son cuentas compartidas donde un gran número de personas pueden colaborar en muchos proyectos a la vez.

Al igual que las cuentas de usuario, las organizaciones pueden poseer recursos como repositorios, paquetes y proyectos. Sin embargo, no puede iniciar sesión en una organización. En cambio, cada persona inicia sesión en su cuenta de usuario, y cualquier acción que la persona realice sobre los recursos de la organización se atribuye a su cuenta de usuario. Cada usuario puede ser miembro de múltiples organizaciones.

Los usuarios dentro de una organización pueden tener diferentes roles en la organización, que otorgan diferentes niveles de acceso a la organización y sus datos. Todos los miembros pueden colaborar entre sí en repositorios y proyectos, pero solo los propietarios de la organización y los gerentes de seguridad pueden administrar la configuración de la organización y controlar el acceso a los datos de la organización con funciones administrativas y de seguridad sofisticadas. 

#### Roles de una organización<a id="RolesOrganizacion"></a>

* Repositorio: brindan a los miembros de la organización, colaboradores 
externos y equipos de personas diferentes niveles de acceso a los repositorios.

* Equipo: son roles que otorgan permisos para administrar un equipo. Puede otorgar a cualquier miembro individual de un equipo el rol de mantenedor del equipo, lo que le da al miembro una serie de permisos administrativos sobre un equipo.

* Organización: son conjuntos de permisos que se pueden asignar a individuos o equipos para administrar una organización y los repositorios, equipos y configuraciones de la organización.

#### Roles predefinidos de una organización<a id="RolesPredefinidosOrganizacion"></a>

* Lectura todo-repositorio: Las subvenciones leen el acceso a todos los repositorios de la organización.

* Todo-repositorio escribir: Las subvenciones escriben acceso a todos los repositorios de la organización.

* Triaje todo-repositorio: Otorga acceso de triaje a todos los repositorios de la organización.

* Todo-repositorio mantener: Otorga acceso de mantenimiento a todos los repositorios de la organización.

* Admin todo-repositorio: Otorga acceso de administrador a todos los repositorios de la organización.

* CI/CD admin: Otorga acceso de administrador para administrar políticas de acciones, corredores, grupos de corredores, configuraciones de red de cómputo alojadas, secretos, variables y métricas de uso para una organización.

* Gerente de seguridad: Otorga la capacidad de administrar políticas de seguridad, alertas de seguridad y configuraciones de seguridad para una organización y todos sus repositorios.

#### Acerca de los roles en las organizaciones<a id="AcercaRolesOrganizacion"></a>

Puedes asignar a las personas diversos roles de nivel de organización para controlar el acceso de los miembros a esta y a sus recursos.

##### Propietarios<a id="Propietarios"></a>

Los propietarios de las organizaciones tienen acceso administrativo integral en tu organización. Este rol debe limitarse a dos personas, por lo mucho, en tu organización. 

##### Miembros<a id="Miembros"></a>

El rol no administrativo predeterminado para las personas en una organización. Los miembros de las organizaciones tienen varios permisos, incluyendo la capacidad de crear repositorios y proyectos.

##### Moderadores<a id="Moderadores"></a>

Además de miembros, pueden bloquear y desbloquear a colaboradores que no son miembros, establecer límites de interacción y ocultar comentarios en repositorios públicos que son propiedad de la organización.

##### Gerentes de facturación<a id="GerentesFacturacion"></a>

Son usuarios que pueden administrar los ajustes de facturación de tu organización, tales como la información de pago. Esta es una opción útil si los miembros de tu organización normalmente no tienen acceso a los recursos de facturación.

##### Administradores de seguridad<a id="AdministradoresSeguridad"></a>

Es un rol de nivel de organización que los propietarios de la organización pueden asignar a cualquier miembro o equipo de la organización. Cuando se aplica, concede permiso para ver las alertas de seguridad y administrar la configuración de las características de seguridad en toda la organización, así como permiso de lectura para todos los repositorios de la organización.

##### GitHub App administradores<a id="GitHubAppAdministradores"></a>

Permite que más usuarios administren los registros de GitHub App propiedad de una organización, un propietario puede otorgarles permisos de administrador de GitHub App. No concede a los usuarios acceso para instalar y desinstalar GitHub Apps en una organización. 

##### Colaboradores externos<a id="ColaboradoresExternos"></a>

Es una persona que tiene acceso a uno o más repositorios de la organización, pero no es explícitamente miembro de la organización, como ser, un consultor o empleado transitorio.

### Cuenta empresarial<a id="CuentasEmpresarial"></a>

Una cuenta empresarial permite la gestión centralizada de múltiples organizaciones.

Los administradores de la cuenta empresarial pueden:

* Ver y administrar la membresía empresarial
* Administrar facturación y uso
* Configure la seguridad, como el inicio de sesión único, las listas de permisos IP, las autoridades de certificación SSH y la autenticación de dos factores
* Auditoría de flujo y datos de eventos de Git
* Usar repositorios internos
* Acceda a características como GitHub Copilot Enterprise y los productos Advanced Security
* Hacer cumplir las políticas.

<a id="FusionCuentas"></a>
## Fusión de múltiples cuentas personales

Recomendamos usar solo una cuenta personal para administrar repositorios personales y profesionales.

* Los permisos de acceso a la organización y al repositorio no son transferibles entre cuentas. Si la cuenta que desea eliminar tiene un permiso de acceso existente, el propietario de una organización o el administrador del repositorio deberán invitar a la cuenta que desea conservar.

* Cualquier compromiso escrito con un GitHub-proporcionado noreply la dirección de correo electrónico no se puede transferir de una cuenta a otra. Si la cuenta que desea eliminar utilizó el Mantenga mi dirección de correo electrónico privada opción, no será posible transferir los commits escritos por la cuenta que está eliminando a la cuenta que desea conservar.

* Los problemas, las solicitudes de extracción y las discusiones no se atribuirán a la nueva cuenta.

* Los logros no se pueden transferir entre cuentas.

1. Transfiera cualquier repositorio desde la cuenta que desea eliminar hasta la cuenta que desea conservar. También se transfieren problemas, solicitudes de extracción y wikis. Verifique que los repositorios existan en la cuenta que desea conservar.
2. Actualizar las URL remotas en cualquier clón local de los repositorios que se movieron.
3. Para atribuir las confirmaciones anteriores a la nueva cuenta, agregue la dirección de correo electrónico que utilizó para crear las confirmaciones a la cuenta que mantiene. Para obtener más información, consulte ¿Por qué mis contribuciones no aparecen en mi perfil?
4. Eliminar la cuenta ya no quieres usar.


## Crear y aministrar repositorios<a id="CrearAdministrarRepositorios"></a>

### Creación desde una plantilla<a id="CreacionDesdePlantilla"></a>

Puedes generar un nuevo repositorio con la misma estructura de directorio y los mismos archivos que un repositorio existente.

#### Acerca de las plantillas de repositorio<a id="AcercaPlantillasRepositorio"></a>

Puede crear una plantilla a partir de un repositorio existente. Cualquier persona con acceso al repositorio de plantillas puede crear un nuevo repositorio basado en la plantilla con la misma estructura de directorios, ramas y archivos.

> [!TIP]
> También puedes crear un repositorio a partir de una plantilla con la GitHub CLI. Para más información, vea [`gh repo create`](https://cli.github.com/manual/gh_repo_create) en la documentación de GitHub CLI.

Puedes elegir incluir la estructura de directorio y archivos únicamente desde la rama predeterminada del repositorio plantilla o incluir todas las ramas. Las ramas que se creen a partir de una plantilla tienen historiales sin relación, lo cual significa que no puedes crear solicitudes de cambio ni hacer fusiones entre las ramas.

Crear un repositorio a partir de una plantilla es similar a bifurcar un repositorio, pero existen algunas diferencias importantes:

* Una nueva bifurcación incluye todo el historial de confirmaciones del repositorio padre, mientras que un repositorio creado a partir de una plantilla comienza con una única confirmación.
* Las confirmaciones en una bifurcación no aparecen en tu gráfico de contribuciones, mientras que las confirmaciones en un repositorio creado a partir de una plantilla sí se muestran en tu gráfico de contribuciones.
* Una bifurcación puede ser una forma temporaria de contribuir código a un proyecto existente, mientras que crear un repositorio a partir de una plantilla permite iniciar rápidamente un proyecto nuevo.

#### Crear un repositorio desde una plantilla <a id="CrearRepositorioDesdePlantilla"></a>

1. Navega hasta la página del repositorio.
2. Encima de la lista de archivos, haga click en **Use this template**.
3. Selecciona **Crear un repositorio nuevo**.
4. Usa el menú desplegable **Propietario** para seleccionar la cuenta que quieres que sea propietaria del repositorio.
5. Teclea el nombre de tu repositorio, y una descripción opcional.
6. Elige la visibiilidad del repositorio.
7. Seleccione **Include all branches** para incluir la estructura de directorios y archivos de todas las ramas.
8. Seleccione las aplicaciones del Marketplace que le gustaría usar en el repositorio.
9. Haga click en **Create repositoriy from template**.

#### Crear plantilla desde repositorio <a id="CrearPlantillaDesdeRepositorio"></a>

Cualquier persona con acceso al repositorio de plantillas puede crear un nuevo repositorio basado en la plantilla con la misma estructura de directorios, ramas y archivos.

Una vez que conviertas tu repositorio en una plantilla, cualquier usuario con acceso al repositorio podrá generar un nuevo repositorio con la misma estructura de directorio y los mismos archivos que la rama predeterminada.

> [!NOTE]
> El repositorio de plantillas no puede incluir archivos que se almacenen mediante Git LFS.

> [!NOTE]
> Puedes usar un repositorio de plantillas como el código inicial de una asignación en GitHub Classroom. [Crear una tarea desde un repositorio de plantilla](https://docs.github.com/es/education/manage-coursework-with-github-classroom/teach-with-github-classroom/create-an-assignment-from-a-template-repository)

1. Navegue hasta la página del repositorio.
2. En el nombre del repositorio, haz clic en  **Configuración**.
3. Seleccione **Template repository**

