# Secret

Los secretos pueden estar establecidos a nivel de repositorio u organización para posteriormente usarlos en GitHub Actions. Los secretos de usuario, organización y repositorios pueden ser establecidos para usarlos en Codespaces. Los secretos de entorno pueden ser usados también en GitHub actions. 

## gh secret delete

#### Definición

Elimina un secreto en uno de los siguientes niveles:

+ repositorio (por defecto): disponible para Actions o Dependabot en un repositorio.

+ entorno: disponible para Actions en un entorno de despliegue en un repositorio.

+ organización: disponible para Actions o Dependabot or Codespaces con una organización.

+ usuario: disponbile para Codespaces para tu usuario.

#### Argumentos

-a, --app <string>: elimina el secreto de una aplicación especifica {actions|codespaces|dependabot}.

-e, --env <string>: elimina el secreto de un entorno.

-o, --org <string>: elimina el secreto de una organización

-u, --user: elimina un secreto para tu usuario.

-R, --repo <[HOST/]OWNER/REPO>: selecciona otro repositorio usando el formato [HOST/]OWNER/REPO.

#### Ejemplos

            gh delete secret xxx

## gh secret list

#### Definición

Lista los secretos de uno de los siguientes niveles:

+ repositorio (por defecto): disponible para Actions o Dependabot en un repositorio.

+ entorno: disponible para Actions en un entorno de despliegue en un repositorio.

+ organización: disponible para Actions o Dependabot or Codespaces con una organización.

+ usuario: disponbile para Codespaces para tu usuario.

#### Argumentos

-a, --app <string>: lista los secretos de una aplicación específica {actions|codespaces|dependabot}.

-e, --env <string>: lista los secretos de un entorno.

-o, --org <string>: lista los secretos de una organziación.

-u, --user: lista los secretos de tu usuario.

-R, --repo <[HOST/]OWNER/REPO>: selecciona otro repositorio usando el formato [HOST/]OWNER/REPO.

#### Ejemplos

        gh secret list

## gh secret set

#### Definición

Establece un valor para un secreto en uno de los siguientes niveles:

+ repositorio (por defecto): disponible para Actions o Dependabot en un repositorio.

+ entorno: disponible para Actions en un entorno de despliegue en un repositorio.

+ organización: disponible para Actions o Dependabot or Codespaces con una organización.

+ usuario: disponbile para Codespaces para tu usuario.

> **_NOTE:_**  Los secretos de organziación y usuario pueden ser opcionalmente restrictivos a un único repositorio. 

> **_NOTE:_**  Los valores secretos locales son encriptados antes de ser enviados a GitHub.

#### Argumentos

-a, --app <string>: establece la aplicación para un secreto {actions|codespaces|dependabot}.

-b, --body <string>: el valor del secreto.

-e, --env <environment>: establece secreto de entorno de despliegue.

-f, --env-file <file>: carga nombres y valores secretos desde un fichero dotenv-formatted.

--no-store: impirme la enciprtación (base64) almacenada en GitHub.

-o, --org <organization>: establece el secreto de una organización.

-r, --repos <repositories>: listado de repositorios que pueden acceder a los secretos de usuario u organización.

-u, --user: establece secreto para un usuario.

-v, --visibility <string>: establece la visibilidad de un secreto de organziación {all|private|selected}.

-R, --repo <[HOST/]OWNER/REPO>: selecciona otro repositorio usando el formato [HOST/]OWNER/REPO.

#### Ejemplos

            gh secret set MYSECRET

            gh secret set MYSECRET --body "$ENV_VALUE"

            gh secret set MYSECRET < myfile.txt