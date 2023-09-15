# Instalación WinGet

## Definición

Instala la herramienta especificada. Tiene el alias __add__.

            winget install [[-q] \<query>] [\<options>]

## Argumentos u opciones

-q, --query: consulta para buscar aplicaciones.

-m, --manifest: se puede usar un fichero manifiesto (YAML) para ejecutar la instalación.

--id: filtra por el id de la aplicación.

--name: filtra por el nombre de la aplicación.

--moniker: filtra por el apodo de la aplicación.

-v, --version: filtra por versión.

-s, --source: especifica la fuente de la instalación.

--scope: permite especificar el ambito (usuario o máquina) de la instalación.

-a, --architecture: arquitectura a instalar.

-e, --exact: indica que el filtro de la consulta debe ser exacto, incluyendo case-sensitive.

-i, --interactive: la instalación se realizará en modo interactivo, por lo que el usuario visualizará el progreso de la instalación.

-h, --silent: instala en modo silencio, por lo que no se visualizará el progreso de la instalación.

--locale: configuración regional.

-o, --log: ruta en la que se escribirá el log de la instalación.

--custom: argumentos adicionales a enviar al instalador.

--override: una cadena que se pasará directamente al instalador.

-l, --location: localización de la instalación (si lo soporta).

--ignore-security-hash: ignorar la comprobación de hash (no recomenado).

--ignore-local-archive-mailware-scan: ignore el escaneo de malware como parte de la instalación.

--dependency-source: busca dependencias usando la fuente especificada.

--accept-package-agreements: acepta la licencia.

--accept-source-agreements: acepta la licencia de la fuente.

--no-upgrade: omite la actualización si ya existe una versión instalada.

--header: encabezado HTTP de origen REST de Windows-Package-Manager (opcional)

-r, --rename: renombra el fichero ejecutable.

--uninstall-previous: desinstala la versión previa durante la actualización.

--force: ejecuta el comando y continua con problemas no realizacionados con la seguridad.

-?, --help: obtiene información adicional sobre el comando.

--wait: solicita al usuario presionar cualquier tecla antes de finalizar.

--logs, --open-logs: abre la ubicación por defecto de los registros.

--verbose, --verbose-logs: anula los adjustes de registro y crea un registro detallado.

--disable-interactivity: desactiva las indicaciones interactivas.


## Ejemplos 

            winget install powertoys --version 0.15.2
            winget install --id Microsoft.PowerToys
            winget install --id Git.Git -e

## Referencias

[Microsoft Learn](https://learn.microsoft.com/en-us/windows/package-manager/winget/install)