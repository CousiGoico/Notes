# Markdown

## ¿Qué es Markdown?

Es un lenguaje de marcado que ofrece un enfoque sencillo para la edición de contenido al proteger a los creadores de contenido de la sobrecarga del HTML. Markdown ofrece un equilibrio perfecto entre la eficacia de HTML para la descripción del contenido y la facilidad de texto sin formato para editarlo.

### Enfatizar texto

Usar la cursiva en el texto es tan fácil como poner el texto de destino entre asteriscos (*) o guiones bajos (_) únicos. Solo tiene que asegurarse de que cierra las marcas de énfasis con el mismo carácter que ha usado para abrirlas.

        This is *italic* text.
        This is also _italic_ text.

Cree texto en negrita usando dos asteriscos (**) o dos guiones bajos (__).

        This is **bold** text.
        This is also __bold__ text.

Para usar un asterisco literal, anteponga un carácter de escape; en GFM, es una barra diagonal inversa (\\). Este ejemplo da como resultado que los guiones bajos y los asteriscos se muestren en la salida.

        \_This is all \*\*plain\*\* text\_.

### Declarar encabezados

En Markdown, esto se realiza a través del símbolo de almohadilla (#). Use una sola almohadilla por cada nivel de encabezado del 1 al 6.

        ###### This is H6 text

### Vínculo a imágenes y sitios

Los vínculos a sitios e imágenes usan una sintaxis parecida.

- Imagen:

        ![Link an image.](/learn/azure-devops/shared/media/mara.png)

- Vinculo:

        [Link to Microsoft Training](/training)

### Crear listas

Se pueden definir listas ordenadas o sin ordenar

* Las listas ordenadas comienzan con números.
* Las listas no desordenadas pueden usar asteriscos o guiones (-).

        1. First
        1. Second
        1. Third

        - First
            - Nested
        - Second
        - Third

### Compilación de tablas

Las tablas se pueden construir mediante una combinación de canalizaciones (|) para saltos de columna y guiones (-) para designar la fila anterior como encabezado.

        First|Second
        -|-
        1|2
        3|4

### Poner texto entre comillas

Puede crear citas en bloque con el carácter "mayor que" (>).

        > This is quoted text.

### Rellenar los huecos con HTML en línea

Si encuentra un escenario HTML que no es compatible con Markdown, puede utilizar ese HTML en línea.

        Here is a<br />line break

### Trabajo con código

Markdown proporciona un comportamiento predeterminado para trabajar con bloques de código en línea delimitados con el carácter de tilde aguda (`). Al decorar texto con este carácter, se representa como código.

        This is `code`.

Si tiene un segmento de código que ocupa varias líneas, se pueden usar tres tildes agudas (```) antes y después para crear un bloque de código con barrera.

        ```markdown
        var first = 1;
        var second = 2;
        var sum = first + second;
        ```

### Problemas de vínculos cruzados y solicitudes de extracción

GFM admite varios formatos de códigos cortos para facilitar la vinculación a problemas y solicitudes de extracción. La forma más fácil de hacerlo es usar el formato #ID, como #3602. GitHub ajusta automáticamente los vínculos más largos a este formato si lo pega.

|Tipo de referencia|Referencia sin formato|Vínculo corto|
|------------------|----------------------|-------------|
|Dirección URL de la solicitud de incorporación de cambios o el problema|https://github.com/desktop/desktop/pull/3602|[#3602](https://github.com/desktop/desktop/pull/3602)|
|`#` y número de la solicitud de incorporación de cambios o el problema|#3602|[#3602](https://github.com/desktop/desktop/pull/3602)|
|`GH-` y número de la solicitud de incorporación de cambios o el problema|GH-3602|[GH-3602](https://github.com/desktop/desktop/pull/3602)|
|`Username/Repository#` y número de la solicitud de incorporación de cambios o el problema|desktop/desktop#3602|[desktop/desktop#3602](https://github.com/desktop/desktop/pull/3602)|

### Vincular confirmaciones específicas

Puede vincular a una confirmación pegando su id. o simplemente usando su algoritmo hash seguro (SHA).

|Tipo de referencia|Referencia sin formato|Vínculo corto|
|------------------|----------------------|-------------|
|Dirección URL de confirmación|[https://github.com/desktop/desktop/commit/](https://github.com/desktop/desktop/commit/)||
|8304e9c271a5e5ab4fda797304cd7bcca7158c87|[8304e9c](https://github.com/desktop/desktop/commit/8304e9c271a5e5ab4fda797304cd7bcca7158c87)||
|SHA|8304e9c271a5e5ab4fda797304cd7bcca7158c87|[8304e9c](https://github.com/desktop/desktop/commit/8304e9c271a5e5ab4fda797304cd7bcca7158c87)|
|User@SHA|desktop@8304e9c271a5e5ab4fda797304cd7bcca7158c87|[desktop@8304e9c](https://github.com/desktop/desktop/commit/8304e9c271a5e5ab4fda797304cd7bcca7158c87)|
|Username/Repository@SHA|desktop/desktop@8304e9c271a5e5ab4fda797304cd7bcca7158c87|[desktop/desktop@8304e9c](https://github.com/desktop/desktop/commit/8304e9c271a5e5ab4fda797304cd7bcca7158c87)|

### Mencionar usuarios y equipos

Al escribir un símbolo `@` seguido de un nombre de usuario de GitHub, se envía una notificación a esa persona sobre el comentario. Esto se denomina "@mention", ya que se está mencionando al individuo. `@mention` también se puede usar para mencionar a los equipos de una organización.

        @githubteacher

### Seguir listas de tareas

Puede crear listas de tareas dentro de problemas o solicitudes de incorporación de cambios, para lo cual usará la sintaxis siguiente. Esto puede ser útil para llevar un seguimiento del progreso cuando se usa en el cuerpo de un problema o una solicitud de incorporación de cambios.

        - [x] First task
        - [x] Second task
        - [ ] Third task

### Comandos de barra diagonal

Con los comandos de barra diagonal puedes ahorrar tiempo, ya que se reduce la cantidad de escritura necesaria para crear código Markdown complejo.

Los comandos de barra diagonal se pueden usar en cualquier campo de descripción o comentario en problemas, solicitudes de incorporación de cambios o discusiones donde este tipo de comando se pueda usar.

|Comando|Descripción|
|-------|-----------|
|`/code`|Inserta un bloque de código Markdown. Tú eliges el lenguaje.|
|`/details`|Inserta un área de detalles contraíble. Tú eliges el título y el contenido.|
|`/saved-replies`|Inserta una respuesta guardada. Tú eliges una de las respuestas guardadas para tu cuenta de usuario. Si agrega %cursor% a su respuesta guardada, el comando de barra diagonal coloca el cursor en esa ubicación.|
|`table`|Inserta una tabla de Markdown. Tú eliges el número de columnas y filas.|
|`tasklist`|Inserta una lista de tareas. Este comando de barra diagonal sólo funciona en las descripciones de problemas.|
|`template`|Muestra todas las plantillas del repositorio. Tú eliges la plantilla que se va a insertar. Este comando de barra diagonal funciona para plantillas de incidencias y una plantilla de solicitud de extracción.|
