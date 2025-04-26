
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