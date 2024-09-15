# Fundamentos RESTFul


## Verbos HTTP

Usa correctamente cada uno de los verbos HTTP.

- GET: solicitud de recursos.
- POST: creación de nuevos recursos.
- PUT: actualización de recursos en su totalidad.
- PATCH: actualiza parcialmente un recurso.
- DELETE: Elimina un recurso.

## Códigos HTTP

- 1XX: respuestas informativas.
- 2XX: peticiones correctas.
- 3XX: redirecciones.
- 4XX: errores de cliente.
- 5XX: errores de servidor.

## Versionado del servicio

Es importante mantener un versionado de tu API, de tal manera, que tenga las siguientes cualidades:

- Retrocompatibilidad: de esta manera, alguien que este usando una versión antigua de tu API no se le rompera.

- Evolución y desarrollo: permite que el equipo de desarrollo avance o evolucione la API sin tener que modificar algo existente. 

- Deprecado: puedes indicar de una manera oficial y sencilla que un método se volvió antiguo e innecesario.

## Rutas

En las rutas deben usarse sustantivos y nombres en plural y en minúscula. No se deben usar verbos que determinen la acción, ya que eso lo hace el verbo. 

Incorrecto

        POST https://api.es/v1/createStudent

Correcto

        POST https://api.es/v1/students

## Filtrado y paginación

Las buenas prácticas indican que tanto para el filtrado como para la paginación hay que usar las cadenas de consulta (QueryStrings).

        GET https://api.es/students?first_name=Javier&sort=first_name&order=desc&offset=50&limit=50

## Patronces de urls

- Todos los recursos

        GET /students

- Recurso específico

        GET /students/{id}

- Obtener los recursos en base a un nivel superior

        GET /teachers/{id}/students

- Crear un nuevo recurso de nivel inferior

        POST /teachers/{id}/students

- Actualizar un recurso de nivel inferior

        PUT /teachers/{id}/students/{id_student}

- Eliminar un recurso de nivel inferior

        DELETE /teachers/{id}/students/{id_student}

## Seguridad

- Limites: se debe establecer límites de llamadas a la API.

- Puertas de enlace: se podrán usar puertas de enlace para realizar contoles de tráfico y analisis.

- HTTPS: conexión segura y cifrada.

- Autenticación y autorización: implementación de un nivel de seguridad para autenticar y autorizar la llamada.



## Referencias

[Medium](https://medium.com/@diego.coder/introducci%C3%B3n-a-las-apis-rest-6b3ad900acc9)