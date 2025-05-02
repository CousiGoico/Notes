# Wikis

## Contenido

- [Introduccción](#introducción)
  - [Agregar o eliminar páginas wiki](#agregar-o-eliminar-páginas-wiki)
  - [Editar páginas Wiki](#editar-páginas-wiki)
  - [Wiki localmente](#wiki-localmente)
  - [Acerca de los nombres de archivo wiki](#acerca-de-los-nombres-de-archivo-wiki)
  - [Crear un pie de página o barra lateral para tu wiki](#crear-un-pie-de-página-o-barra-lateral-para-tu-wiki)
    - [Crear una carpeta](#crear-una-carpeta)
    - [Crear una barra lateral](#crear-una-barra-lateral)
    - [Crear un pie de página o barra lateral de manera local](#crear-un-pie-de-página-o-barra-lateral-de-manera-local)
  - [Buscar wikis](#buscar-wikis)
- [Referencias](#referencias)

## Introducción

Cada repositorio de GitHub viene equipado con una sección para hospedar documentación, denominada wiki. Puedes usar la wiki de tu repositorio para compartir contenido en forma completa acerca de tu proyecto, como por ejemplo cómo usarlo, cómo lo diseñaste o sus principios básicos. Un archivo README rápidamente dice lo que puede hacer tu proyecto, mientras que puedes usar una wiki para proporcionar documentación adicional.

Si creas una wiki en un repositorio público, estará disponible para el público. Si creas una wiki en un repositorio privado, solo los usuarios que tengan acceso al repositorio podrán acceder a la wiki.

> [!NOTE]
> Los motores de búsqueda solo indexan wikis con 500 o más estrellas que configures para evitar la edición pública. Si necesitas que los motores de búsqueda indexen el contenido, puedes usar GitHub Pages en un repositorio público.
> [!NOTE]
> Por motivos de rendimiento, las wikis tienen un límite temporal de 5000 archivos totales, independientemente del tipo de archivo. Si supera este límite, es posible que algunas páginas no sean accesibles para los usuarios. Si necesita una wiki más grande, se recomienda utilizar GitHub Pages.
> [!IMPORTANT]
> Esta carácteristica no esta disponible en los repositorios privados de las cuentas free.

### Agregar o eliminar páginas wiki

1. En GitHub, navegue hasta la página principal del repositorio.

2. En el nombre del repositorio, haga clic en `Wiki`.

3. En la esquina superior derecha de la página, haga clic en Nueva página.

4. Opcionalmente, para escribir en otro formato diferente a Markdown, usa el menú desplegable `Modo de edición` para elegir un formato diferente.

5. Usa el editor de texto para agregar el contenido de tu página.

6. En el campo `Editar mensaje`, escribe un mensaje de confirmación que describa el nuevo archivo que vas a agregar.

7. Para confirmar los cambios en la wiki, haga clic en Guardar página.

### Editar páginas Wiki

1. En GitHub, navegue hasta la página principal del repositorio.

2. En el nombre del repositorio, haga clic en `Wiki`.

3. Desplázate hasta la página que deseas cambiar con la ayuda de la barra lateral wiki de la derecha. En la esquina superior derecha de la página, haga clic en `Editar`.

4. Usa el editor de texto para modificar el contenido de la página.

5. En el campo `Editar mensaje`, escribe un mensaje de confirmación que describa el nuevo archivo que vas a agregar.

6. Para confirmar los cambios en la wiki, haga clic en `Guardar página`.

### Wiki localmente

Las wikis son parte de los repositorios Gift, de manera que puedes hacer cambios localmente y subirlos a tu repositorio mediante un flujo de trabajo de Git.

Cada wiki brinda una manera sencilla de clonar sus contenidos en tu computadora. Una vez que hayas creado una página inicial en GitHub, puedes clonar el repositorio en el equipo con la dirección URL proporcionada:

        $ git clone https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.wiki.git
        # Clones the wiki locally

### Acerca de los nombres de archivo wiki

El nombre de archivo determina el título de tu página wiki, y la extensión del archivo determina cómo se presenta el contenido wiki.

Los wikis usan [nuestra biblioteca de marcado de código abierto](https://github.com/github/markup) para convertir el marcado y determina qué convertidor va a usar la extensión de un archivo.

No use los siguientes caracteres en los títulos de la página de la wiki: `\ / : * ? " < > |`.

### Crear un pie de página o barra lateral para tu wiki

Puedes agregar una barra lateral o un pie de página personalizados a tu wiki para dar a los lectores más información contextual.

#### Crear una carpeta

1. En GitHub, navegue hasta la página principal del repositorio.

2. En el nombre del repositorio, haga clic en `Wiki`.

3. En la parte inferior de la página, haga clic en `Add a custom footer` (Agregar un pie de página personalizado).

4. Usa el editor de texto para escribir el contenido que deseas que tenga tu pie de página.

5. En el campo `Editar mensaje`, escribe un mensaje de confirmación que describa el pie de página que vas a agregar.

6. Para confirmar los cambios en la wiki, haga clic en `Save Page` (Guardar página).

#### Crear una barra lateral

1. En GitHub, navegue hasta la página principal del repositorio.

2. En el nombre del repositorio, haga clic en `Wiki`.

3. Haga clic en `Agregar una barra lateral personalizada` en el lado derecho de la página.

4. Usa el editor de texto para agregar el contenido de tu página.

5. En el campo `Editar mensaje`, escribe un mensaje de confirmación que describa el pie de página que vas a agregar.

6. Para confirmar los cambios en la wiki, haga clic en `Save Page` (Guardar página).

#### Crear un pie de página o barra lateral de manera local

Si crea un archivo denominado `_Footer.<extension>` o `_Sidebar.<extension>`, los usaremos para rellenar el pie de página y la barra lateral de la wiki, respectivamente. Al igual que cualquier otra página wiki, la extensión que elijas para estos archivos determina cómo los representaremos.

## Buscar wikis

Puedes buscar wikis globalmente a través de todos los GitHub, o buscar wikis dentro de un repositorio u organización particular.

|Calificador|Ejemplo|
|-----------|-------|
|`user:USERNAME`|`user:defunkt` busca páginas wiki de repositorios propiedad de @defunkt.|
|`org:ORGNAME`|`org:github` busca wikis en repositorios propiedad de la organización de GitHub.|
|`repo:USERNAME/REPOSITORY`|`repo:defunkt/gibberish` busca páginas wiki del repositorio "gibberish" de @defunkt.|
|`in:title`|`usage in:title` busca títulos de páginas wiki con la palabra "usage".|
|`in:body`|`installation in:body` busca páginas wiki con la palabra "installation" en el texto del cuerpo principal.|
|`updated:YYYY-MM-DD`|`usage updated:>2016-01-01` busca páginas wiki con la palabra "usage" que se actualizaron por última vez después del 01-01-2016.|

## Referencias

[GitHub - docs](https://docs.github.com/es/communities/documenting-your-project-with-wikis/about-wikis)

[GitHub - docs](https://docs.github.com/es/search-github/searching-on-github/searching-wikis)

[GitHub - docs](https://docs.github.com/es/search-github/getting-started-with-searching-on-github/understanding-the-search-syntax)