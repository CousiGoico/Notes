# Visibility

## Contenido

- [Introducción](#introducción)
  - [Convertir repositorio en privado](#convertir-repositorio-en-privado)
  - [Convertir un repositorio en interno](#convertir-un-repositorio-en-interno)
  - [Convertir un repositorio en público](#convertir-un-repositorio-en-público)
    - [Consecuencias de cambiar la visibilidad de un repositorio de público a privado o de interno a privado](#consecuencias-de-cambiar-la-visibilidad-de-un-repositorio-de-público-a-privado-o-de-interno-a-privado)
    - [Consecuencias de cambiar la visibilidad de un repositorio de privado a público o de interno a público](#consecuencias-de-cambiar-la-visibilidad-de-un-repositorio-de-privado-a-público-o-de-interno-a-público)
    - [Consecuencias de cambiar la visibilidad de un repositorio de privado a interno o de público a interno](#consecuencias-de-cambiar-la-visibilidad-de-un-repositorio-de-privado-a-interno-o-de-público-a-interno)
  - [Cambiar la visibilidad de un repositorio](#cambiar-la-visibilidad-de-un-repositorio)
- [Referencias](#referencias)

## Introducción

Los miembros de una empresa con usuarios administrados solo pueden configurar la visibilidad de los repositorios que pertenezcan a su cuenta personal como privados, y los repositorios de las organizaciones de su empresa solo pueden ser privados o internos.

> [!NOTE]
> Si no puedes cambiar la visibilidad de un repositorio, es posible que el propietario de la organización haya restringido la posibilidad de cambiar la visibilidad del repositorio solo a los propietarios de la organización.

### Convertir repositorio en privado

- GitHub desasociará las bifurcaciones (forks) públicas del repositorio público y las colocará en una red nueva. Las bifurcaciones públicas no se hacen privadas.

- Si cambias la visibilidad de un repositorio de interna a privada, GitHub eliminará las bifurcaciones que pertenezcan a cualquiera de los usuarios sin acceso al repositorio que recientemente se hizo privado. La visibilidad de las bifurcaciones también cambiará a privada.

- GitHub ya no incluirá el repositorio en el GitHub Archive Program.

- Características de GitHub Advanced Security, como code scanning, dejarán de funcionar a menos que el repositorio sea propiedad de una organización que tenga acceso a la característica en repositorios privados con una licencia de GitHub Advanced Security, GitHub Code Security o GitHub Secret Protection y suficientes puestos de reserva.

### Convertir un repositorio en interno

- Cualquier bifurcación del repositorio se mantendrá en la red del mismo y GitHub mantendrá la relación entre el repositorio raíz y la bifurcación.

### Convertir un repositorio en público

- GitHub se deslindará de las bifurcaciones privadas y las convertirá en repositorios privados independientes.

- Si vas a convertir tu repositorio privado en uno público como parte de un movimiento hacia la creación de un proyecto de código abierto, consulta las [Guías de código abierto](http://opensource.guide/) para obtener sugerencias y directrices útiles. También puedes realizar un curso gratuito sobre la administración de un proyecto de código abierto con [GitHub Skills](https://skills.github.com/). Una vez que tu repositorio es público, también puedes ver el perfil de la comunidad de tu repositorio para ver si tu proyecto cumple con las mejoras prácticas para los colaboradores de apoyo.

- El repositorio obtendrá acceso automático a las características de GitHub Advanced Security.

- El historial y los registros de acciones serán visibles para todos los usuarios. Si el repositorio tenía flujos de trabajo reutilizables o necesarios compartidos desde otro repositorio de la organización, la ruta de acceso del archivo de flujo de trabajo, incluido el nombre del repositorio, estará visible en los registros.

#### Consecuencias de cambiar la visibilidad de un repositorio de público a privado o de interno a privado

- Las estrellas y los monitores de este repositorio se borrarán permanentemente, lo que afectará a las clasificaciones del repositorio.

- Las reglas de alertas personalizadas de Dependabot se deshabilitarán a menos que GitHub Code Security esté habilitado para este repositorio. El gráfico de dependencias y las Dependabot alerts permanecerán habilitados con permiso para realizar análisis de solo lectura en este repositorio.

- Code scanning dejará de estar disponible a menos que Code Security esté habilitado para este repositorio.

- Las bifurcaciones actuales seguirán siendo públicas y se desasociarán de este repositorio.

#### Consecuencias de cambiar la visibilidad de un repositorio de privado a público o de interno a público

- El código será visible para todos los usuarios que puedan visitar GitHub.com.

- Cualquier persona puede bifurcar el repositorio.

- Todos los conjuntos de reglas de inserción se deshabilitarán.

- Los cambios se publicarán como actividad.

- El historial y los registros de acciones serán visibles para todos los usuarios.

- Las estrellas y los monitores de este repositorio se borrarán permanentemente.

#### Consecuencias de cambiar la visibilidad de un repositorio de privado a interno o de público a interno

- A todos los miembros de la empresa se les proporcionará acceso de lectura.

- Los colaboradores externos ya no se pueden agregar a bifurcaciones a menos que se agreguen a la raíz.

- Las estrellas y los monitores de este repositorio se borrarán permanentemente.

### Cambiar la visibilidad de un repositorio

1. En GitHub, navegue hasta la página principal del repositorio.

2. En el nombre del repositorio, haz clic en `Configuración`. Si no puedes ver la pestaña `Configuración`, selecciona el menú desplegable y, a continuación, haz clic en `Configuración`.

3. En la sección `Zona de peligro`, a la derecha de `Cambiar la visibilidad del repositorio`, haga clic en `Cambiar visibilidad`.

4. Selecciona una visibilidad.

5. Para verificar que estás cambiando la visibilidad del repositorio correcto, teclea el nombre del repositorio para el cual quieres cambiar la visibilidad.

6. Haz clic en `Lo entiendo, cambia la visibilidad del repositorio`.

## Referencias

[GitHub docs](https://docs.github.com/en/enterprise-cloud@latest/repositories/managing-your-repositorys-settings-and-features/managing-repository-settings/setting-repository-visibility)
