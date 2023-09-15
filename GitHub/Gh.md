# GitHub Commands

## Instalación

### Windows

GitHub commands está disponible su instalación mediante WinGet, scoop, Chocolatey, Conda y como MSI descargable. 

#### WinGet

            winget install --id GitHub.cli
            winget upgrade --id GitHub.cli

#### Scoop

            scoop install gh
            scoop update gh

#### Chocolatey

            choco install gh
            choco upgrade gh

### Mac & Linux

#### Homebrew

            brew install gh
            brew upgrade gh

#### MacPorts

            sudo port install gh
            sudo port selfupdate && sudo port upgrade gh

#### Conda

            conda install gh --channel conda-forge
            conda update gh --channel conda-forge

#### Spack

            spack install gh
            spack uninstall gh && spack install gh

## Autenticación

### gh auth login

#### Definición

La autenticación por defecto es mediante la web. Después de autenticarte un token será almacenado internamente. 

#### Argumentos

-p, --git-protocol <string>: ssh o https.

-h, --hostname <string>: nombre del host de GitHub

--insecure-storage: guarda las credenciales en texto plano

-s, --scopes:<strings>: ambitos de la consulta de autenticación

-w, --web: abre el navegador para autenticarte

--with-token: lee el token de la entrada estandar.

#### Ejemplos

            gh auth login
            gh auth login --with-token < mytoken.txt
            gh auth login --hostname enterprise.interval

### gh auth logout

#### Definición

Cierra la sesión de autenticación.

#### Argumentos

-h, --hostname <string>: nombre del host de GitHub

#### Ejemplos

            gh auth logout
            gh auth logout --hostname enterprise.internal

### gh auth refresh

#### Definición

Ampliar o corregir los alcances de los permisos para las credenciales almacenadas.

#### Argumentos

-h, --hostname <string>: nombre del host de GitHub

--insecure-storage: guarda las credenciales en texto plano

-r, --remove-scopes <strings>: elimina los ambitos de autenticación

--reset-scopes: resetea ls ambitos de autenticación al mínimo

-s, --scopes:<strings>: ambitos de la consulta de autenticación

#### Ejemplos

            gh auth refresh
            gh auth refresh --scopes write:org,read:public_key
            gh auth refresh --remove-scopes delete_repo
            gh auth refresh --reset-scopes

### gh auth setup-git

#### Definición

Este comando configura git para usar la CLI de GitHub como asistente de credenciales. De forma predeterminada, la CLI de GitHub se configurará como asistente de credenciales para todos los hosts autenticados. [Más información](https://git-scm.com/docs/gitcredentials)

#### Argumentos

-h, --hostname <string>: nombre del host de GitHub

#### Ejemplos

            gh auth setup-git
            gh auth setup-git --hostname enterprise.internal

### gh auth status

#### Definición

Verifica y muestra información sobre el estado de la autenticación.

#### Argumentos

-h, --hostname <string>: comprueba el hostname especifico

-t, --show-token: muestra el token de autenticación

#### Ejemplos

            gh auth status
            gh auth status --show-token

### gh auth token

#### Definición

Muestra el token de autenticación.

#### Argumentos

-h, --hostname <string>: nombre del host en GitHub

#### Ejemplos

            gh auth token

## Referencias

[GitHub Documentation](https://github.com/cli/cli#installation)