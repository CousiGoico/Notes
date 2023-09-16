# Browse

## gh browse

#### Definición

Abre el repositorio indicado en el navegador.

#### Argumentos

-b, --branch <string>: rama seleccionada.

-c, --commit <string>: selecciona otro commit pasando el SHA.

-n, --no-browser: imprime la URL destino.

-p, --projects: proyectos a abrir.

-r, --releases: release a abrir.

-R, --repo <[HOST/]OWNER/REPO>: selecciona otro repositorio usando el formato [HOST/]OWNER/REPO.

-s, --settings: abre los ajustes del repositorio.

-w, --wiki: abre el wiki del repositorio.

#### Ejemplos

            gh browse

            gh browse 217 // Abre la incidecia o pull request 217

            gh browse 77507cd94ccafcf568f8560cfecde965fcfa63 // Commit

            gh browse --settings
