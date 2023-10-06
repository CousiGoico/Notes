# Ruleset

## gh ruleset

Los conjuntos de reglas de repositorio son una forma de definir un conjunto de reglas que se aplican a un repositorio. Estos comandos le permiten ver información sobre ellos.

#### Argumentos

-R, --repo <[HOST/]OWNER/REPO>: selecciona otro repositorio usando el formato [HOST/]OWNER/REPO.

## gh ruleset check

#### Definición

Ver información sobre las reglas de GitHub que se aplican a una rama determinada.

Se mostrarán las reglas que se aplicarían a una sucursal con ese nombre.

El indicador --default se puede utilizar para ver las reglas que se aplican a la rama predeterminada del repositorio.

#### Sintaxis

            gh ruleset check [<branch>] [flags]

#### Argumentos

--default: comprueba las reglas de la rama por defecto.

-w, --web: abre las reglas en el navegador.

#### Ejemplos

            gh ruleset check

            gh ruleset check my-branch --repo owner/repo

            gh ruleset view 23 --repo owner/repo

## gh ruleset list

#### Definición

Enumera los conjuntos de reglas de GitHub para un repositorio u organización.

Su token de acceso debe tener el alcance admin:org para usar el indicador --org, que se puede otorgar ejecutando "gh auth refresco -s admin:org".

#### Sintaxis

            gh ruleset view 23 --repo owner/repo

#### Argumentos

-L, --limit <int>: número máximo de reglas a listar.

-o, --org <string>: organización a mostrar las reglas.

-p, --parents: incluir las reglas de los padres.

-w, --web: abre las reglas en el navegador.

#### Ejemplos

            gh ruleset list

            gh ruleset list --repo owner/repo --parents

            gh ruleset list --org org-name

## gh ruleset view

#### Definición

Ver información sobre un conjunto de reglas de GitHub.

Si no se proporciona ninguna identificación, se utilizará un mensaje interactivo para elegir el conjunto de reglas que desea ver.

#### Sintaxis

            gh ruleset view [<ruleset-id>] [flags]

#### Argumentos

-o, --org <string>: organización a mostrar las reglas.

-p, --parents: incluir las reglas de los padres.

-w, --web: abre las reglas en el navegador.

#### Ejemplos

            gh ruleset view

            gh ruleset view --no-parents

            gh ruleset view 43

            gh ruleset view 23 --repo owner/repo

            gh ruleset view 23 --org my-org