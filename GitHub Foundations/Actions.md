# GitHub Actions

## Contenido

- [Introducción](#introducción)
- [Eventos](#eventos)
- [Ejemplo](#ejemplo)
- [Referencias](#referencias)

## Introducción

Los GitHub Actions son flujos de trabajo de desarrollo de software que se guardan en tus repositorios como ficheros con extensión .yml. Puedes crear una gran variedad de flujos de trabajo, incluido CI/CD, totalmente personalizado.

Estos flujos de trabajo pueden ser ejecutados en tu máquina local o en GitHub.

### Plantillas

Las plantillas de flujo de trabajo son plantillas que le ayudan a crear flujos de trabajo de GitHub Actions propios para un repositorio. Según la tecnologia que uses en el repositorio, GitHub te ofrece una lista de plantillas para dicha tecnologia.

- Implementación (CD)
- Integración continua (CI)
- Automatización: Las plantillas de flujo de trabajo de automatización ofrecen soluciones para automatizar flujos de trabajo, como evaluar las solicitudes de incorporación de cambios (pull requests) y aplicar una etiqueta basada en las rutas modificadas en la solicitud de incorporación de cambios, o bien saludar a los usuarios que colaboran por primera vez en el repositorio.
- Escanear código
- Páginas

## Eventos

Los activadores de los flujos de trabajo son eventos que ocasionan que se ejecute un flujo de trabajo. Algunos eventos tienen tipos de actividad múltiple.

> [!NOTE]
> No todos los eventos de webhook activan flujos de trabajo.

- Eventos que ocurren en el repositorio de su flujo de trabajo
- Eventos que ocurren fuera de GitHub y desencadenan un repository_dispatch evento en GitHub
- Tiempos programados
- Manual

El proceso de la ejecución de un evento sería el siguiente:

1. Un evento ourre en su repositorio. El evento tiene un compromiso asociado SHA y Git ref.
2. GitHub busca en el directorio `.github/workflows` en la raíz de su repositiorio que estén presentes en la confirmación asociada SHA o Git ref del evento.
3. Se activa una ejecución de flujo de trabajo para cualquier flujo de trabajo que tenga `on:` valores que coinciden con el evento desencadenante. Algunos eventos también requieren que el archivo de flujo de trabajo esté presente en la rama predeterminada del repositorio para poder ejecutarse.

Cuando se ejecuta un flujo de trabajo, GitHub establece el GITHUB_SHA (compromiso SHA) y GITHUB_REF (Git ref) variables de entorno en el entorno del corredor.

Cuando usas el repositorio `GITHUB_TOKEN` para realizar tareas, eventos activados por el `GITHUB_TOKEN`, con la excepción de `workflow_dispatch` y repository_dispatch, no creará una nueva ejecución de flujo de trabajo. Esto le impide crear accidentalmente ejecuciones de flujo de trabajo recursivas.

## Elementos

- name: nombre del flujo de trabajo.
- on: información del ejecutor (en este tag no se indica)
  - {evento}: aquí se indica el evento (push, pull_request, ...)
    - {branches}: se indica la(s) rama(s) sobre las que al hacer el evento se dispará este flujo de trabajo.
  - schedule: información de la programación de ejecución de este flujo de trabajo (en este tag no se indica)
    - cron: se indica el cron en el que se desea ejecutar.
  - workflow_call: información del flujo de trabajo que invoca a este (en este tag no se indica)

- jobs: información de las tareas a realizar (en este tag no se indica)
  - {nombre_job}: nombre del flujo de trabajo
    - runs-on: en que OS se va a ejecutar (ubuntu-latest, windows-latest, ...)
    - steps: información de los pasos a ejecutar (en este tag no se indica)
      - name: nombre del paso.
        needs: nombre del flujo de trabajo que es requerido.
        run: sentencia a ejecutar.
        uses: ruta o nombre del flujo de trabajo que deseamos ejecutar en este punto.

## Ejemplo

        name: .NET Build and Deploy on PR to Azure Windows App Service

        on:
        pull_request:
            branches:
            - main  # Se activa en PRs que vayan a main

        jobs:
        build-and-deploy:
            runs-on: windows-latest  # Azure App Service de Windows, simulamos entorno similar

            steps:
            - name: Checkout repository
            uses: actions/checkout@v4

            - name: Setup .NET SDK
            uses: actions/setup-dotnet@v4
            with:
                dotnet-version: '8.0.x' # O la versión de .NET que uses, ej: 7.0.x, 6.0.x, etc.

            - name: Restore NuGet packages
            run: dotnet restore

            - name: Build the project
            run: dotnet build --configuration Release --no-restore

            - name: Publish the project
            run: dotnet publish --configuration Release --output ./publish --no-build

            - name: Deploy to Azure Web App (Windows)
            uses: azure/webapps-deploy@v3
            with:
                app-name: 'NOMBRE-DE-TU-APP'   # <-- Cambia aquí al nombre real del App Service
                slot-name: 'staging'            # <-- O 'production' si quieres desplegar directamente
                publish-profile: ${{ secrets.AZURE_PUBLISH_PROFILE }}
                package: './publish'

## Referencias

[GitHub docs - Actions events](https://docs.github.com/en/actions/writing-workflows/choosing-when-your-workflow-runs/events-that-trigger-workflows#about-events-that-trigger-workflows)

[GitHub docs - Actions](https://docs.github.com/en/actions/about-github-actions/about-continuous-integration-with-github-actions)

[GitHub docs - Built-in automations](https://docs.github.com/en/issues/planning-and-tracking-with-projects/automating-your-project/using-the-built-in-automations)

[GitHub docs - Configurar actions](https://docs.github.com/es/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository)

[GitHub docs - Workflows](https://docs.github.com/en/actions/writing-workflows/workflow-syntax-for-github-actions)