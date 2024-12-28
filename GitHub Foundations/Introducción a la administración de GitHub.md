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