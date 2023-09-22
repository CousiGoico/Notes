# Alias

Los alias se pueden usar para crear atajos para comandos gh o para componer múltiples comandos.

## gh alias delete

#### Definición

Elimina el alias.

#### Sintaxis

        gh alias delete {<alias> | --all} [flags]

#### Argumentos

-- all: elimina todos los alias.

#### Ejemplos

        gh alias delete --all

## gh alias import

#### Definición

Importa alias desde un fichero YAML. Los alias deben ser definidos como un mapa en el YAML, donde las claves representan los alias y los valores representan las expansiones.

        bugs: issue list --label=bug
        igrep: '!gh issue list --label="$1" | grep "$2"'
        features: |-
            issue list
            --label=enhancement

Utilice "-" para leer alias (en formato YAML) desde la entrada estándar.

> **_NOTA_**: El resultado del comando gh "alias list" se puede utilizar para generar un archivo YAML que contenga sus alias, que puede utilizar para importarlos de una máquina a otra. Ejecute "gh help alias list" para obtener más información.

#### Sintaxis

gh alias import [<filename> | -] [flags]

#### Argumentos

--clobber: sobeescribe un alias existente del mismo nombre.

#### Ejemplos

        gh alias import aliases.yml

## gh alias list

#### Definición

Muestra todos los alias configurados para su uso.

#### Sintaxis

        gh alias list

#### Argumentos

#### Ejemplos

        gh alias list

## gh alias set

#### Definición

Define una palabra que será expandida a un comando gh cuando se invoque.

La expansion debe especificar argumentos adicionales y flags. Si la expansion incluye marcadores como "$1", argumentos extra deben seguir al alias para ser insertados apropiadamente. 

Utilice "-" como argumento de expansión para leer la cadena de expansión de la entrada estándar.

Si la expansión comienza con "!" o si se proporcionó "--shell", la expansión es una expresión de shell que se evaluará a través del intérprete "sh" cuando se invoque el alias. Esto permite encadenar múltiples comandos mediante canalización y redirección.

#### Sintaxis

        gh alias set <alias> <expansion> [flags]

#### Argumentos

--clober: sobreescribe el alias con el mismo nombre.

-s, --shell: define un alias para ser pasado mediante el interprete shell.

#### Ejemplos

        gh alias set pv 'pr view' // gh pv -w 123

        gh alias set bugs 'issue list --label=bugs' // gh bugs

        gh alias set homework 'issue list --assignee @me' // gh homework