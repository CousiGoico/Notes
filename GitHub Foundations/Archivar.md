# Archivar

## Contenido

- [Introducción](#introducción)
  - [Acerca del GitHub Archive Program](#acerca-del-github-archive-program)
  - [Agregar una licencia de código abierto para aumentar la capacidad de archivado](#agregar-una-licencia-de-código-abierto-para-aumentar-la-capacidad-de-archivado)
- [Eliminar un repositorio](#eliminar-un-repositorio)
  - [Cómo eliminar un repositorio](#cómo-eliminar-un-repositorio)
- [Restaurar repositorio](#restaurar-repositorio)

- [Referencias](#referencias)

## Introducción

Puedes archivar el contenido y los datos de otras personas para su visualización y como referencia.

### Persistencias de repositorios públicos

GitHub intenta mantener disponibles tus repositorios públicos, a menos que los elimines. En algunos casos, hacemos que el contenido público no esté disponible:

- Recibimos un [aviso de eliminación de DMCA](https://docs.github.com/es/site-policy/content-removal-policies/dmca-takedown-policy) para el contenido de un repositorio.

- Determinamos que el contenido de un repositorio infringe las [Directrices de nuestra comunidad](https://docs.github.com/es/site-policy/github-terms/github-community-guidelines) o los [Términos del servicio](https://docs.github.com/es/site-policy/github-terms/github-terms-of-service).

### Acerca del GitHub Archive Program

Todos los repositorios públicos se incluyen en el GitHub Archive Program, una sociedad entre GitHub y organizaciones tales como Software Heritage Foundation e Internet Archive para garantizar la preservación a largo plazo del software de código abierto en el mundo.

Permite que los socios terceros archiven repositorios públicos utilizando la API pública. Estos socios archivan diferentes tipos de datos en frecuencias variables y hacen que éstos estén disponibles al público. El GitHub Archive Program también protege los datos constantemente al almacenar varias copias de ellos en formatos de datos y ubicaciones diversas.

### Agregar una licencia de código abierto para aumentar la capacidad de archivado

Bibliotecas e investigadores pueden requerir protecciones legales para crear archivos de contenido disponible públicamente. Si quieres que terceros tengan en cuenta tu trabajo en GitHub para el archivado, puedes agregar una [licencia de código abierto](https://docs.github.com/es/enterprise-cloud@latest/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/licensing-a-repository) a los proyectos. Una licencia de código abierto le brinda a los colaboradores permisos explícitos para copiar y distribuir el material en tu repositorio.

## Eliminar un repositorio

Puede eliminar un repositorio de la bifurcación si es propietario de la organización, el sí tiene permisos de administración para el repositorio de la bifurcación. Elimine un repositorio bifurcado en su repositorio ascendente.

Solo los miembros con privilegios de propietario para una organización o privilegios de administrador para un repositorio pueden eliminar un repositorio de organización, y una política de organización o empresa puede impedir que estos usuarios eliminen un repositorio.

Eliminar un repositorio público no eliminará ninguna bifurcación del repositorio.

> [!CAUTION]
>
> - Eliminar un repositorio será permanentemente eliminar archivos adjuntos de liberación y permisos de equipo. Esta acción no deshacer.
> - Eliminar un repositorio privado eliminará todas las bifurcaciones del repositorio.

Algunos repositorios eliminados se pueden restaurar dentro de los 90 días posteriores a la eliminación.

### Cómo eliminar un repositorio

1. En GitHub, navegue a la página principal del repositorio.

2. En el nombre de su repositorio, haga clic en `Configuración`. Si no puede ver la pestaña `Configuración`, seleccione el  menú desplegable, luego haga clic en `Configuración`.

3. En la página de configuración `General` (que se selecciona de forma predeterminada), desplácese hacia abajo hasta la sección `Zona de peligro` y haga clic en `Eliminar este repositorio`.

4. Haga clic `Quiero eliminar este repositorio`.

5. Lea las advertencias y haga clic en `He leído y entiendo estos efectos`.

6. Para verificar que está eliminando el repositorio correcto, en el cuadro de texto, escriba el nombre del repositorio que desea eliminar.

7. Haga clic `Eliminar este repositorio`.

## Restaurar repositorio

Un repositorio eliminado se puede restaurar en un plazo de 90 días, a menos que el repositorio haya sido parte de una red de bifurcaciones que actualmente no está vacía. Una red de bifurcaciones consiste en un repositorio padre, las bifurcaciones del repositorio y las bifurcaciones de las bifurcaciones del repositorio. Si tu repositorio forma parte de una red de bifurcaciones, no se puede restaurar a menos que se elimine cualquier otro repositorio de la red o que se haya separado de la red.

### Cómo restaurar un repositorio

1. En la esquina superior derecha de cualquier página en GitHub, haga clic en la fotografía de perfil y luego en `Configuración`.

2. En la sección `Código, planificación y automatización` de la barra lateral, haz clic en `Repositorios`.

3. En `Repositorios`, haga clic en `Repositorios eliminados`.

4. Junto al repositorio que quiera restaurar, haga clic en `Restore` (Restaurar).

5. Lee la advertencia y haz clic en Entiendo, `restaurar este repositorio`.

### Restaurar un repositorio que le pertenecía a una organización

1. En la esquina superior derecha de GitHub, selecciona la foto del perfil y haz clic en `Tus organizaciones`.

2. Junto a la organización, haga clic en `Settings`.

3. En la barra lateral de la izquierda, haga clic en `Deleted repositories`.

4. Junto al repositorio que quiera restaurar, haga clic en `Restore` (Restaurar).

5. Lee la advertencia y haz clic en `Entiendo, restaurar este repositorio`.

## Referencias

[GitHub - Docs](https://docs.github.com/es/enterprise-cloud@latest/repositories/archiving-a-github-repository/about-archiving-content-and-data-on-github#about-the-github-archive-program)

[GitHub Archive Program](https://archiveprogram.github.com/)

[GitHub - Docs - Eliminar repositorio](https://docs.github.com/es/repositories/creating-and-managing-repositories/deleting-a-repository)

[GitHub - Docs - Restaurar repositorio](https://docs.github.com/es/repositories/creating-and-managing-repositories/restoring-a-deleted-repository)