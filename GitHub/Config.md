# Configuration

## gh config

Muestra o cambia los ajustes de configuración de gh.

Configuraciones actuales:

+ git_protocol: el protocolo a utilizar para las operaciones de inserción y clonación de git (predeterminado: "https").

+ editor: el programa de edición de texto que se utilizará para crear texto.

+ prompt: alternar mensajes interactivos en la terminal (predeterminado: "habilitado").

+ pager: el programa de terminal pager para enviar salida estándar.

+ http_unix_socket: la ruta a un socket Unix a través del cual realizar una conexión HTTP.

+ browser: el navegador web que se utilizará para abrir URL.

## gh config clear-cache

#### Definición

Limpia la cache cli.

#### Sintaxis

            gh config clear-cache

#### Argumentos

#### Ejemplos

            gh config clear-cache

## gh config get

#### Definición

Imprime el valor de una clave de configuración.

#### Sintaxis

            gh config get <key> [flags]

#### Argumentos

-h, --host <string>: obtiene el ajuste por hosting.

#### Ejemplos

            gh config get git_protocol

## gh config list

#### Definición

Imprime una lista de claves-valor de configuración.

#### Sintaxis

            gh config list [flags]

#### Argumentos

-h, --host <string>: lista los ajustes de un hosting.

#### Ejemplos

            gh config list

## gh config set

#### Definición

Actualiza la configuración con el valor de una clave.

#### Sintaxis

            gh config set <key> <value> [flags]

#### Argumentos

-h, --host <string>: establece el ajuste por hosting.

#### Ejemplos

            gh config set editor vim
            gh config set editor "code --wait"
            gh config set git_protocol ssh --host github.com
            gh config set prompt disabled