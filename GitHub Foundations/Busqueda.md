# Busqueda en GitHub

## Contenido

- [Introducción](#introducción)
- [Calificadores](#calificadores)
  - [Is](#is)
- [Búsquedas](#búsquedas)
  - [Búsquedas básicas](#búsquedas-básicas)
  - [Búsqueda de repositorios](#búsqueda-de-repositorios)
  - [Búsqueda de código](#búsqueda-de-código)
  - [Búsqueda de incidencias](#búsqueda-de-incidencias)
  - [Búsqueda de usuarios](#búsqueda-de-usuarios)
- [Referencias](#referencias)

## Introducción

Dentro de la plataforma de GitHub existe un buscador. Existen algunos trucos para encontrar de manera mas sencilla lo que buscamos dentro de GitHub.

## Calificadores

- Repositorio: `repo:`
- Organización: `org:`
- Usuario: `user:`
- Lenguaje: `language:`
- Ruta (puede usarse expresiones regulares): `path:`
- Contenido: `content:`
- Símbolos: `symbol:`

### Is

Para filtrar por las propiedades de un repositorio, puedes usar el calificador `is:`:

- `archived`: repositorios archivados.
- `fork`: repositorios bifurcados.
- `vendored`: contenido detectado como delegado a proveedores.
- `generated`: contenido detectado como generado.

        path:/^MIT.txt$/ is:archived

        log4j NOT is:fork

## Búsquedas

### Búsquedas básicas

Si buscas por un texto en concreto, te filtrará aquellos ficheros que tengan ese {texto}:

        {texto}

Si el texto en cuestión tiene espacios lo puedes rodear por comillas dobles:

        "{texto}"

El carácter de escape es la barra inclinada (`\`):

        "\"{texto}\""

Puedes realizar operaciones booleanas para tu búsqueda:

        jquery OR javascript

Encontrar repositorios con más de n estrellas:

        cat stars:>{n}

Obtener todos los rempositorios de un usuario:

        user:{usuario}

Buscar por {localización}:

        location:{localización}

Encontrar todas las instancias de unión en el código con la extensión {extensión}:

        join extension:{extensión}

Excluir resultados que contengan {text}

        NOT {text}

### Búsqueda de repositorios

Filtrado por la fecha en la que se hizo commit en el repositorio remoto:

        pushed:>2015-31-01

Obtener repositorios por el número de forks:

        forks:<200

Encontrar repositorios en base a su tamaño (entre 1024 y 2048 kb):

        size:1024.2048

Obtención de los repositorios que tienen forks de gitx:

        gitx fork:true

Obtención de los repositorios que tienen sólo forks de gitx:

        gitx fork:only

### Búsqueda de código

Encuentre todas las instancias de {texto} en el código del repositorio {usuario}/{repositorio}.

        {texto} repo:{usuario}/{repositorio}

Obtiene las referencias de para {texto} en todos los repositorios publicos del usuario {usuario}:

        {texto} user:{usuario}

Búsqueda de {texto} en ficheros que coincida con el filtro de tamaño {tamaño} (kb):

        {texto} size:>{tamaño}

Encontrar las instancias de {texto} en una carpeta indicada {ruta}:

        {texto} path:{ruta}

Buscar reemplazar en el código fuente de forks:

        replace fork:true

### Búsqueda de incidencias

Búsqueda por aquellas incidencias que están abiertas:

        is:open

Incidencias que tienen un {número} de comentarios:

        comments:>{numero}

Encontrar incidencias con una {etiqueta}:

        label:{etiqueta}

Buscar incidencias escritas por {usuario}:

        author:{usuario}

Incidencias en las que se mencione a {usuario}:

        mentions:{usuario}

Búsqueda de aquellas incidencias asignadas a {usuario}:

        assignee: {usuario}

Por {fecha de creación} (yyyy-mm-dd):

        created:>{fecha de creación}

Por {fecha de modificación} (yyyy-mm-dd):

        updated:<{fecha de modificación}

### Búsqueda de usuarios

Búsqueda por {nombre completo}:

        fullname:{nombre completo}

Encontrar usuarios de una {localización}:

        location:{localización}

Con un {número} determinado de seguidores:

        followers:>{número}

Encontrar usuarios con un rango {número1}..{número2} de seguidores:

        followers:{número1}..{número2}

Usuarios con un {número} determinado de repositorios:

        repos:>{número}

## Referencias

- [FreeCodeCamp](https://www.freecodecamp.org/espanol/news/consejos-de-busqueda-en-github-como-buscar-problemas-repositorios-y-mas-de-manera-efectiva-en-github/)

- [GiHub](https://github.com/search?q=&type=Repositories&ref=advsearch&l=&l=)

- [GitHub docs](https://docs.github.com/es/search-github/github-code-search/understanding-github-code-search-syntax)