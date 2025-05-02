# GitHub codespaces

## Contenido

- [Sobre el ciclo de vida de un codespace](#sobre-el-ciclo-de-vida-de-un-codespace)
    - [Crear un codespace](#crear-un-codespace)
        - [Facturación cuentas gratuitas o pro](#facturación-cuentas-gratuitas-o-pro)
        - [Precios por el uso de pago](#precios-por-el-uso-de-pago)
        - [Administrar límite de gasto cuenta personal](#administrar-límite-de-gasto-cuenta-personal)
        - [Administrar límite de gasto organización](#administrar-límite-de-gasto-organización)
    - [Timeout](#timeout)
    - [Recompilar un codespace](#recompilar-un-codespace)
    - [Parar un codespace](#parar-un-codespace)
    - [Eliminar un codespace](#eliminar-un-codespace)
    - [Perdida de conexión con un codespace](#perdida-de-conexión-con-un-codespace)
    - [Publicar codespace a través de una plantilla](#publicar-codespace-a-través-de-una-plantilla)
        - [Codespace a través de una plantilla de GitHub](#codespace-a-través-de-una-plantilla-de-github)
        - [Codespace a través de una plantilla](#codespace-a-través-de-una-plantilla)
    - [Configuraciones del codespace](#configuraciones-del-codespace)
        - [Configuración del período de tiempo de espera predeterminado](#configuración-del-período-de-tiempo-de-espera-predeterminado)
        - [Visualización del uso de GitHub Codespaces](#visualización-del-uso-de-github-codespaces)
        - [DevContainer.json](#devcontainerjson)

## Sobre el ciclo de vida de un codespace

El ciclo de vida de un codespace comienza cuando crea un codespace y termina cuando lo elimina. Puede desconectarse y volver a conectarse a un codespace activo sin afectar sus procesos en ejecución. Puede detener y reiniciar un codespace sin perder los cambios que ha realizado en su proyecto.

### Crear un codespace

Hay límites en el número de espacios de códigos que puede crear y el número de espacios de códigos que puede ejecutar al mismo tiempo. Si alcanza el número máximo de espacios de código e intenta crear otro, se muestra un mensaje que le indica que debe eliminar un codespace existente antes de poder crear uno nuevo. Si se elimina su codespace, su trabajo también se eliminará.

#### Facturación cuentas gratuitas o pro

|Plan de cuenta|Almacenamiento al mes|Horas dnúcleo al mes|
|--------------|---------------------|--------------------|
|GitHub Free para cuentas personaes|15 GB al mes|120|
|GitHub Pro|20 GB al mes|180|

Recibirás una notificación por correo electrónico o por el IDE cuando hayas usado el 75 %, el 90 % y el 100 % de las cuotas incluidas. Cuando se llegue al 100% y no haya ningún límite de gasto configurado, se bloqueará el uso.

#### Precios por el uso de pago

|Componente|Tipo de máquina|Unidad de medida|Multiplicador de uso incluido|Precio|
|----------|--------------------------------|-----------------------------|------|
|Procesos de codespace|2 núcleos|1 hora|2|$0.18|
|Procesos de codespace|4 núcleos|1 hora|4|$0.36|
|Procesos de codespace|8 núcleos|1 hora|8|$0.72|
|Procesos de codespace|16 núcleos|1 hora|16|$1.44|
|Procesos de codespace|32 núcleos|1 hora|32|$2.88|
|Almacenamiento de codespaces|Storage|1 GB-mes|N/A|$0.07|

Incurrirá en cargos por el tiempo de proceso, mientras esté activa, y por la cantidad de espacio en disco que ocupe el codespace, mientras exista.

GitHub Codespaces se factura en dólares estadounidenses (USD) mensualmente.

#### Administrar límite de gasto cuenta personal

1. En la esquina superior derecha de cualquier página en GitHub, haga clic en la fotografía de perfil y luego en `Configuración`.

2. En la sección `Acceso` de la barra lateral, haz clic en `Facturación y planes` y luego en Límites de gasto.

3. En la parte superior de la página, en `Información de pago`, haz clic en `Administrar límite de gasto`.

4. En `Codespaces`, selecciona `Limitar gasto` y escribe un límite de gasto o selecciona `Gasto ilimitado`.

5. Dependiendo de la opción que hayas elegido, haz clic en `Actualizar límite` o `Actualizar a ilimitado`.

#### Administrar límite de gasto organización

1. En la esquina superior derecha de cualquier página en GitHub, haga clic en la fotografía de perfil y luego en `Configuración`.

2. En la sección `Acceso` de la barra lateral, haz clic en `Organizaciones`.

3. Junto a la organización, haga clic en `Settings`.

4. Si eres propietario de una organización, en la sección `Acceso` de la barra lateral, haz clic en `Facturación y planes`.

5. En la parte superior de la página, en `Información de pago`, haz clic en `Administrar límite de gasto`.

6. En `Codespaces`, selecciona Limitar gasto y escribe un límite de gasto o selecciona Gasto ilimitado.

7. Dependiendo de la opción que hayas elegido, haz clic en `Actualizar límite` o `Actualizar a ilimitado`.

### Timeout

Si cierras el codespace sin interacción o si cierras sin pararlo, el codespace lanzará un timeout después de 30 minutos de inactividad (este dato es personalizable).

### Recompilar un codespace

Puedes recompilar un codespace para mplemtnar cambios en la configuración de tu codespace. Cuando recompilas reusarás imagenes de tu caché para acelerar la compilación, aunque también puedes limpiar la caché antes de compilar.

> [!NOTE]
> Los cambios hechos fuera del directorio /workspaces se perderán al hacer un compilado.

### Parar un codespace

Cuando paras un codespace, los procesos ejecutados son parados, los cambios guardados seguirán disponibles y el historico del terminal es preservado, pero el contenido de la ventana del terminal no es preservado.

> [!IMPORTANT]
> Si no paras el codespace, el coste sigue aumentando.

### Eliminar un codespace

SI intentas eliminar un codespace cuando tienes cambios pendientes de hacer push, el editor te notificará que debes hacer push antes de eliminar el codespace.

Los codespaces que estan parados durante 30 días de inactividad, serán eliminados (aunque se puede personalizar este dato).

Eliminar un codespace no reduce la factura actual, que se acumula durante cada ciclo de facturación mensual.

Si un usuario es borrado de una organización o repositori, también se borrará su codespace.

### Perdida de conexión con un codespace

Los cambios sin commit serán guardados. Puedes usar el fichero `decontainer.json` con la extensión [`DevContainers`](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) para compilar y adjuntar un contanedor local a tu repositorio.

## Publicar codespace a través de una plantilla

### Codespace a través de una plantilla de GitHub

1. En la esquina superior izquierda de GitHub, seleccione el menu y haga clic en **Codespaces** para acceder a la página de `Sus codespaces` en github.com/codespaces.

2. Para ver la lista completa de plantillas, en `Explorar plantillas de inicio rápido`, haz clic en Ver todo.

3. Opcionalmente, para ver el repositorio de plantilla que contiene los archivos de una plantilla, haz clic en el nombre de la plantilla.

4. En el nombre de la plantilla que deseas iniciar, haz clic en Usar esta plantilla.

### Codespace a través de una plantilla

1. En GitHub, navegue hasta la página principal del repositorio.

2. Haz clic en `Usar esta plantilla` y luego en `Abrir en un codespace`.

## Configuraciones del codespace

### Configuración del período de tiempo de espera predeterminado

1. En la esquina superior derecha de cualquier página en GitHub, haga clic en la fotografía de perfil y luego en `Configuración`.

2. En la sección `Código, planificación y automatización` de la barra lateral, haz clic en `Codespaces`.

3. En `Período de retención predeterminado`, escribe el número de días para los que deseas que se conserven los codespaces, de forma predeterminada, una vez detenidos.

4. Haga clic en `Save(Guardar)`.

### Visualización del uso de GitHub Codespaces

1. En la esquina superior derecha de cualquier página en GitHub, haga clic en la fotografía de perfil y luego en `Configuración`.

2. En la sección `Acceso` de la barra lateral, haz clic en  Facturación y planes y luego en Planes y uso.

3. En `Codespaces`, puedes ver cuántas horas del uso de núcleo del proceso de GitHub Codespaces y los GB-meses de almacenamiento que has usado hasta ahora en el mes de facturación actual.

4. Opcionalmente, haz clic en `Horas de uso y Almacenamiento` para ver más detalles.

5. Opcionalmente, junto a `Uso este mes`, haz clic en `Obtener informe de uso` para recibir un correo electrónico que contenga un vínculo para descargar un informe CSV de uso de almacenamiento de GitHub Actions, GitHub Packages y GitHub Codespaces. El correo electrónico se envía a la dirección de correo electrónico principal de la cuenta. Puedes elegir si el informe debe abarcar los últimos 7, 30, 90 o 180 días.

![Codespace billing](..\Images\CodespaceBilling.png)

### DevContainer.json

        {
            "name": "My Dev Container",
            "image": "mcr.microsoft.com/vscode/devcontainers/javascript-node:18", // or use "build"
            "build": {
                "dockerfile": "Dockerfile",
                "context": ".",
                "args": {
                "VAR_NAME": "value"
                }
            },
            "settings": {
                "terminal.integrated.shell.linux": "/bin/bash"
            },
            "extensions": [
                "dbaeumer.vscode-eslint",
                "esbenp.prettier-vscode"
            ],
            "postCreateCommand": "npm install",
            "remoteUser": "node",
            "forwardPorts": [3000, 9229],
            "mounts": [
                "source=${localWorkspaceFolder}/data,target=/workspace/data,type=bind"
            ],
            "features": {
                "ghcr.io/devcontainers/features/docker-in-docker:1": {}
            },
            "runArgs": ["--cap-add=SYS_PTRACE", "--security-opt", "seccomp=unconfined"]
        }


<!--TODO-->

![Lifecycle of codespace](..\Images\codespace-lifecycle.png)