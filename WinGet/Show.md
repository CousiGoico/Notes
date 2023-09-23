# Show command

## Definición

Muestra detalles de una especifica aplicaicon, incluyendo detalles de su fuente. Muestra los metadatos que fueron enviados con la aplicación.

## Alias

+ view

## Uso

            winget show [[-q] \<query>] [\<options>]

## Argumentos u opciones

-q, --query: consulta usada para buscar una aplicación.

-m, --manifest: ruta del manifiesto de la aplicación para instalar.

--id: filtra los resultados por id.

--name: filtra los resultados por nombre.

--moniker: filtra los resultados por el apodo de la aplicación.

-v, --version: usa la versión especificada. Por defecto, es la última versión.

-s, --source: busca la aplicación en un origen concreto.

-e, --exact: busca una aplicación usando su macheo exacto.

--scope: selecciona el ámbito de instalación (usuario o máquina).

-a, --architecture: selecciona la arquitectura de instalación.

--locale: configuración regional a usar.

--versions: muetra las versiones disponbiles de la aplicación.

--header: encabezado HTTP de origen REST de Windows-Package-Manager.

--accept-source-agreements: usado para aceptar la licencia de acuerdos.

-?, --help: muestra la ayuda del comando.

--wait: indicaciones al usuario para que presione una tecla para salir.

--logs, --open-logs: abre la localización por defecto de logs.

--verbose, --verbose-logs: usado para sobreescribir los ajustes de login y crear logs detallados.

--disable-interactivity: desabilita las indicaciones interactivas. 

## Metadata

|Valor|Descripción|
|-----|-----------|
|Version|Versión de la aplicación|
|Publisher|Publicador de la aplicación|
|Moniker|Alias de la aplicación|
|Description|Descripción de la aplicación|
|Homepage|Página inicial de la aplicación|
|Licence|Licencia de la aplicación|
|LicenceUrl|Url del fichero de licencia de la aplicación|

## Detalles instaladores

|Valor|Descripción|
|-----|-----------|
|Type|El tipo de instalador|
|Download Url| Url del instalador|
|Locale|Idioma del instalador|
|SHA256|Código SHA256 de la aplicación|

## Ejemplos 

            winget show --name Microsoft

            winget show --id Postman.Postman

## Referencias

[Microsoft Learn](https://learn.microsoft.com/en-us/windows/package-manager/winget/show )
