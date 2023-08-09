# Azure DevOps Configuration

Los recursos se configuran en los siguientes niveles:

+ Persona actual registrada
+ Equipo
+ Proyecto
+ Organización

Las opciones a configurar dependen del grupo de seguridad o rol administrativo.

## Configuración de usuario

Los colaboradores individuales podrán:
+ Establecer sus preferencias
+ Habilitar características en versión preliminar 
+ Administrar sus favoritos y notificaciones


## Rol de administrador de equipo y administración de equipos

Configuran los recursos del equipo, es decir, herramientas y paneles de Agile. Dichos usuarios deben ser administradores del equipo o administradores del proyecto en el que está dicho equipo.

#### Trabajo que realiza el administrador de equipo

+ Perfil de equipo
    + Agregar usuarios a un proyecto o equipo específico.
    + Agregar administradores de equipo.
+ Paneles
    + Niveles de trabajo pendiente.
    + Mostrar errores en los paneles de trabajo pendiente.
    + Establecer días laborables.
    + Configuración de rutas de acceso de área.
    + Selección de rutas de acceso de iteración activas (sprints).
    + Definición de plantillas de elementos de trabajo.
    + Creación de paneles.
    + Administrar permisos de panel.
+ Notificaciones
    + Administrar notificaciones a nivel de equipo.


`Cuando se crea un equipo se crea a su vez un panel. Los permisos predeterminados permiten a los miembros del equipo crear y editar paneles para su equipo.`





## Rol administrador de proyectos y administrador de proyectos

Configuran los recursos para un proyecto y administran permisos en el nivel de proyecto. También pueden configurar las opciones del equipo.

#### Trabajo que realiza el administrador de proyecto

+ General
    + Establecimiento de la descripción del proyecto.
    + Cambiar la visibilidad del proyecto (público o privado).
+ Servicios
    + Activar o desactivar un servicio (Boards, Repos, Pipelines, Test Plans, Artifacts).
+ Teams
    + Agregar otro equipo y miembros del equipo.
    + Agregar un administrador del equipo.
+ Seguridad
    + Agregar usuario a un proyecto.
    + Agregar un administrador del equipo.
    + Solicitar un aumento en los niveles de permisos.
    + Búsqueda de un administrador de proyectos.
    + Cambiar los permisos de nivel de proyecto.
    + Establecimiento de permisos de nivel de objeto.
    + Conceder o restringir permisos para seleccionar tareas.
    + Establecer permisos del panel.
    + Establecimiento de los permisos de Wiki.
    + Establecimiento de los permisos de comentarios.
    + Establecimiento de los permisos de compilación y versión.
+ Notificaciones
    + Administración de notificaciones de nivel de proyecto.
+ Enlaces de servicio
    + Configuración de enlaces de servicio.
+ Paneles
    + Establecimiento de permisos de panel predeterminados.
    + Definición de rutas de acceso de área.
    + Definir rutas de acceso de iteración o sprints.
+ Compilación y versión (grupos de agentes, versión)
    + Administración de colas de agentes y grupos de agentes.
    + Administrar conexiones de servicio.
    + Administración de grupos y grupos de implementación.
    + Establecer directivas de retención.
+ Repositorios, control de versiones de código
    + Creación de repositorios de Git adicionales.
    + Establecimiento de permisos de repositorios Git.
    + Establecimiento de permisos de repositorios de TFVC.
    + Administrar directivas de rama.
    + Agregar directivas de Check-In de Control de versiones de Team Foundation(TFVC).
+ Prueba
    + Establecer directivas de retención de pruebas.
    + Administración de permisos relacionados con pruebas en el nivel de proyecto.
    + Establecimiento de permisos de prueba de nivel de ruta de acceso de área.
+ Wiki
    + Creación de una wiki para el proyecto.
    + Publicación de un repositorio de Git en una wiki.
    + Administrar permisos LÉAME y Wiki.
+ Extensiones
    + Solicitud de una extensión de Marketplace.
+ Configuración del equipo
    + Administración y configuración de herramientas de equipo.
    + Administrar notificaciones.
+ Conexiones de GitHub
    + Conectar Azure Boards con GitHub.
    + Instalación y configuración de Azure Boards aplicación para GitHub.
    + Vinculación de confirmaciones, solicitudes de incorporación de cambios y problemas de GitHub a elementos de trabajo.
+ Conexiones de servicio
    + Administración de conexiones de servicio en Azure Pipelines


`Los colaboradores individuales y los administradores de proyectos pueden solicitar quese instale una extensión de Marketplace. Solo los miembros del grupo Administradoresde colecciones de proyectos pueden responder a estas solicitudes e instalar extensionesrealmente.`





## Rol administrador de colección de proyectos y administrador de colecciones de proyectos

Configuran recursos para todos los proyectos definidos para una organización o colección. Realizan todas las tareas para agregar proyectos, administrar proyectos yadministrar permisos para la colección, un proyecto, un equipo o un objeto.

#### Trabajo que realiza el administrador de colección de proyectos

+ Características en versión preliminar
    + Administración y habilitación de características en versión preliminar.
+ Información general
    + Agregar y administrar la información de la organización.
    + Configuración de la facturación.
+ Proyectos
    + Agregar y administrar proyectos.
    + Adición de usuarios a proyectos.
    + Guardar datos del proyecto.
+ Usuarios
    + Adición y administración de usuarios.
    + Adición de usuarios externos.
    + Quitar usuarios.
+ Facturación (toda la facturación se administra a través de Azure)
    + Configuración de la facturación.
    + Probar Azure Test Plans gratis.
    + Pago por usuario (básico).
    + Comprar trabajos paralelos.
    + Agregar un usuario para realizar compras.
+ Auditoria
    + Acceso, exportación y filtrado de registros de auditoria.
    + Crear flujo de auditoria.
+ Noticaciones globales
    + Administración de notificaciones de nivel de recopilación
+ Uso
    + Supervisión de uso
+ Extensiones
    + Instalación y administración de extensiones de Marketplace.
    + Aprobar extensiones.
    + Concesión de permisos para administrar extensiones.
    + Desinstalar o deshabilitar extensiones.
+ Seguridad: directivas
    + Administración de directivas de acceso a aplicaciones.
    + Adición de usuarios externos.
    + Deshabilitación de la directiva de solicitud de acceso.
    + Restricción de que los usuarios creen nuevas organizaciones con la directiva deAzure Active Directory.
    + Impedir que los administradores de equipos y proyectos inviten a nuevos usuarios.
    + Habilitar el acceso condicional o Multi-Factor Authentication.
+ Seguridad: permisos
    + Búsqueda del propietario de la organización.
    + Búsqueda de un administrador de colecciones de proyectos.
    + Agregar administradores, establecer permisos de nivel de organización.
    + Adición de grupos de Azure Active Directory.
    + Conectarse a Azure Active Directory.
    + Establecimiento de permisos para administrar extensiones.
    + Administrar el acceso condicional.
+ Paneles: proceso
    + Personalizar un proyecto.
    + Adición y administración de procesos.
+ Canalizaciones: Compilación y versión
    + Establecer directivas de retención.
    + Establecimiento de límites de recursos para canalizaciones.
    + Adición y administración de grupos de agentes.
    + Adición y administración de grupos de implementación.
+ Almacenamiento de artefactos
    + Eliminación y recuperación de paquetes en Azure Artifacts.
    + Consumo de almacenamiento de artefactos.