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

            gh auth login


## Referencias

[GitHub Documentation](https://github.com/cli/cli#installation)