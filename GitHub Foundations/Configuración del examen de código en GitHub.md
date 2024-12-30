# Configuración del examen de código en GitHub

## ¿Qué es el examen de código?

El examen de código usa CodeQL para analizar el código de un repositorio GitHub en busca de vulnerabilidades de seguridad y errores de codificación. El examen de código está disponible para todos los repositorios públicos y para repositorios privados propiedad de organizaciones que tienen habilitado GitHub Advanced Security. Si el examen de código detecta una posible vulnerabilidad o error en el código, GitHub muestra una alerta en la pestaña Security (Seguridad) del repositorio. Después de corregir el código que desencadenó la alerta, GitHub cierra la alerta.

Puede usar el análisis de código para buscar, evaluar y priorizar las correcciones de los problemas existentes en el código. El análisis de código también evita que los desarrolladores generen nuevos problemas. Puede programar exámenes para determinados días y horas, o desencadenar exámenes cuando se produce un evento específico en el repositorio, como un envío de cambios.

### Acerca del examen de código con CodeQL

CodeQL es el motor de análisis de código desarrollado por GitHub para automatizar las comprobaciones de seguridad. Puede analizar el código mediante CodeQL y mostrar los resultados como alertas de examen de código. Hay tres maneras principales de configurar el análisis de CodeQL para el examen de código:

* Use la configuración predeterminada para configurar rápidamente el análisis de CodeQL para el análisis de código en el repositorio. La configuración predeterminada controla la elección de los lenguajes para analizar, el conjunto de consultas que se va a ejecutar y los eventos que desencadenan exámenes con la opción de configurar manualmente los lenguajes y los conjuntos de consultas. Esta opción de configuración ejecuta el examen del código como una Acción de GitHub.
* Use la configuración avanzada para agregar el flujo de trabajo de CodeQL directamente al repositorio. Añadir el flujo de trabajo de CodeQL directamente en su repositorio genera un archivo de flujo de trabajo personalizable, que usa [**github/codeql-action**](https://github.com/github/codeql-action/) para ejecutar la CLI de CodeQL como una Acción de GitHub.
* Ejecute la CLI de CodeQL directamente en un sistema de CI externo y cargue los resultados en GitHub.

CodeQL trata el código como datos, lo que le permite detectar posibles vulnerabilidades en el código con más confianza en comparación con los analizadores estáticos tradicionales. Se genera una base de datos de CodeQL para representar el código base y, a continuación, se ejecutan consultas de CodeQL en esa base de datos para identificar problemas en el código base. Los resultados de las consultas se muestran como alertas de examen de código en GitHub cuando se usa CodeQL con el examen de código.

CodeQL admite lenguajes compilados e interpretados, y puede detectar vulnerabilidades y errores en el código escrito en los siguientes lenguajes compatibles:

* C o C++
* C#
* Go
* Java/Kotlin
* JavaScript/TypeScript
* Python
* Ruby
* Swift

### Habilitación de CodeQL en el repositorio con el programa de instalación predeterminado

Si tiene permisos de escritura en un repositorio, puede configurar el examen de código para ese repositorio.

Siga estos pasos para configurar el examen de código mediante el flujo de trabajo de Acciones de GitHub para CodeQL:

1. Ir a la página principal del repositorio.
2. Debajo del nombre del repositorio, seleccione **Seguridad**.
3. Seleccione **Configurar examen de código**. Si esta opción no está disponible, pida al propietario de la organización o al administrador del repositorio que habilite GitHub Advanced Security.
4. En el menú desplegable **Configurar**, seleccione **Predeterminado**.
5. Revise las opciones predeterminadas. Si es necesario, seleccione el botón Editar en la esquina inferior izquierda de la nueva ventana para personalizar cómo se ejecuta CodeQL. Los desencadenadores de *on:pull_request* y *on:push* son los predeterminados para el examen de códigos y cada uno de ellos es útil para fines distintos. Aprenderá más sobre estos desencadenadores en la unidad Configuración del examen de código.
6. Seleccione **Habilitar CodeQL** una vez que esté listo para activar el examen de código.

### Acerca de la facturación de Acciones

El examen de código usa Acciones de GitHub y cada ejecución de un flujo de trabajo de examen de código consume minutos para Acciones de GitHub. El uso de las Acciones de GitHub es gratuito tanto para los repositorios públicos como para los ejecutores autohospedados. En el caso de los repositorios privados, cada cuenta de GitHub recibe un número determinado de minutos y almacenamiento gratis, según el producto usado con la cuenta. Cualquier uso que supere las cantidades incluidas se controla mediante límites de gasto. Si es un cliente al que se le factura mensualmente, su cuenta tendrá un límite de gasto predeterminado de 0 dólares estadounidenses (USD), lo que impide usar minutos o almacenamiento adicionales para repositorios privados más allá de las cantidades incluidas en su cuenta. Si paga su cuenta mediante factura, la cuenta tendrá un límite de gasto predeterminado ilimitado. Los minutos se restablecen cada mes, mientras que el uso del almacenamiento no.

## Habilitación del examen de código con herramientas de terceros

En lugar de ejecutar el examen de código en GitHub, puede realizar análisis en otro lugar y, después, cargar los resultados. Las alertas de examen de código que se ejecutan externamente se muestran de la misma manera que las que se ejecutan en GitHub. Puede cargar archivos de formato de intercambio de resultados de análisis estáticos (SARIF) generados fuera de GitHub o con Acciones de GitHub para ver alertas de examen de código de herramientas de terceros en el repositorio.

### Acerca de las cargas de archivos SARIF para el examen de código

GitHub crea alertas de examen de código en un repositorio mediante información de archivos SARIF. Puede generar archivos SARIF con muchas herramientas de prueba de seguridad de análisis estáticos, incluido CodeQL. Los resultados deben usar la versión 2.1.0 de SARIF.

Puede cargar los resultados mediante la API de examen de código, la CLI de CodeQL o Acciones de GitHub. El mejor método de carga dependerá de cómo haya generado el archivo SARIF.

### Code Scanning API

La API de análisis del código le permite recuperar información sobre las alertas del análisis del código, los análisis, las bases de datos y la configuración de configuración predeterminada de un repositorio. Además, puede actualizar las alertas de análisis del código y la configuración predeterminada. Puede usar los puntos de conexión para crear informes automatizados para las alertas de examen código en una organización o cargar los resultados del análisis generados mediante herramientas de examen de código sin conexión.

Puede acceder a la API de GitHub a través de HTTPS desde **https://api.github.com**. Todos los datos se envían y reciben como JSON. La API usa tipos de medios personalizados para permitir que los consumidores elijan el formato de los datos que desean recibir. Los tipos de medios son específicos de los recursos, lo que les permite cambiar de forma independiente y admitir formatos que otros recursos no admiten.

Hay un tipo de medio personalizado admitido para la API de REST de examen de código, *application/sarif+json*.

Puede usar este tipo de medio con solicitudes GET enviadas al punto de conexión */analyses/{analysis_id}*. Cuando se usa este tipo de medio con esta operación, la respuesta incluye un subconjunto de los datos reales que se cargaron para el análisis especificado, en lugar del resumen del análisis que se devuelve cuando se usa el tipo de medio predeterminado. La respuesta también incluye datos adicionales, como las propiedades *github/alertNumber* y *github/alertUrl*. El formato de los datos es SARIF, versión 2.1.0.

        curl -L \
        -H "Accept: application/vnd.github+json" \
        -H "Authorization: Bearer <YOUR-TOKEN>" \
        -H "X-GitHub-Api-Version: 2022-11-28" \
        https://api.github.com/orgs/ORG/code-scanning/alerts

### CLI de CodeQL

La CLI de CodeQL es un producto independiente que puede usar para analizar código. Su propósito principal es generar una representación de base de datos de un código base, una base de datos de CodeQL. Una vez que la base de datos esté lista, puede consultarla de manera interactiva, o bien ejecutar un conjunto de consultas para generar un conjunto de resultados en formato SARIF y cargar los resultados en GitHub.com. El uso de la CLI de CodeQL es gratuito en repositorios públicos que se mantienen en GitHub.com, y se puede usar en repositorios privados que son propiedad de clientes con una licencia de Advanced Security. Descargue la agrupación de CodeQL de [https://github.com/github/codeql-action/releases](https://github.com/github/codeql-action/releases).

* Producto de la CLI de CodeQL
* Una versión compatible de las consultas y bibliotecas de https://github.com/github/codeql
* Versiones precompiladas de todas las consultas incluidas en la agrupación

Siempre debe usar la agrupación de CodeQL, porque esto garantiza la compatibilidad y también proporciona un rendimiento mucho mayor que una descarga independiente de la CLI de CodeQL y la restauración de las consultas de CodeQL.

### Análisis de examen de código con Acciones de GitHub

Para usar Acciones de GitHub para cargar un archivo SARIF de terceros en un repositorio, necesitará un flujo de trabajo de Acciones de GitHub. Un flujo de trabajo de Acciones de GitHub es un proceso automatizado, integrado por uno o varios trabajos, configurado como un archivo *.yml*. Los flujos de trabajo se almacenan en el directorio *.github/workflows* del repositorio.

El flujo de trabajo usa la acción *upload-sarif*, que forma parte del repositorio *github/codeql-action*. Este flujo de trabajo incluye parámetros de entrada que puede usar para configurar la carga. El parámetro de entrada principal es *sarif-file*, que configura el archivo o directorio de los archivos SARIF que se van a cargar. La ruta de acceso del directorio o archivo es relativa a la raíz del repositorio. La acción *upload-sarif* se puede configurar para ejecutarse cuando se producen los eventos *push* y *scheduled*.

        name: 'Code Scanning : Upload SARIF'
        description: 'Upload the analysis results'
        author: 'GitHub'
        inputs:
        sarif_file:
            description: |
            The SARIF file or directory of SARIF files to be uploaded to GitHub code scanning.
            See https://docs.github.com/en/code-security/code-scanning/integrating-with-code-scanning/
            uploading-a-sarif-file-to-github#uploading-a-code-scanning-analysis-with-github-actions
            for information on the maximum number of results and maximum file size supported by code scanning.
            required: false
            default: '../results'
        checkout_path:
            description: "The path at which the analyzed repository was checked out. 
            Used to relativize any absolute paths in the uploaded SARIF file."
            required: false
            default: ${{ github.workspace }}
        token:
            default: ${{ github.token }}
        matrix:
            default: ${{ toJson(matrix) }}
        category:
            description: String used by Code Scanning for matching the analyses
            required: false
        wait-for-processing:
            description: If true, the Action will wait for the uploaded SARIF to be processed before completing.
            required: true
            default: "false"
        runs:
        using: 'node12'
        main: '../lib/upload-sarif-action.js'

Cada vez que se cargan los resultados de un nuevo examen de código, los resultados se procesan y se agregan alertas al repositorio. GitHub usa propiedades del archivo SARIF para mostrar alertas. Los archivos SARIF creados por el flujo de trabajo de análisis de CodeQL incluyen estos datos de huella digital en el campo *partialFingerprints*. Si carga un archivo SARIF con la acción *upload-sarif* y faltan estos datos, GitHub intenta rellenar el campo *partialFingerprints* a partir de los archivo de código fuente.

Si el archivo SARIF no incluye *partialFingerprints*, la acción *upload-sarif* calculará el campo *partialFingerprints* automáticamente e intentará evitar alertas duplicadas. GitHub puede crear solo *partialFingerprints* cuando el repositorio contiene el archivo SARIF y el código fuente usado en el análisis estático. 

La carga de SARIF admite un máximo de 5000 resultados por carga. Los resultados que superen este límite se omiten. Si una herramienta genera demasiados resultados, debe actualizar la configuración para centrarse en los resultados de las reglas o consultas más importantes. Para cada carga, la carga de SARIF admite un tamaño máximo de 10 MB para el archivo SARIF comprimido con gzip. Se rechazarán las cargas que superen este límite. Si el archivo SARIF es demasiado grande porque contiene demasiados resultados, debe actualizar la configuración para centrarse en los resultados de las reglas o consultas más importantes.

### Carga de los archivos SARIF generados fuera del repositorio

También puede crear un flujo de trabajo que cargue archivos SARIF después de confirmarlos en el repositorio. Esto resulta útil cuando el archivo SARIF se genera como un artefacto fuera del repositorio.

        name: "Upload SARIF"

        // Run workflow each time code is pushed to your repository and on a schedule. 
        //The scheduled workflow runs every Thursday at 15:45 UTC.

        on:
        push:
        schedule:
            - cron: '45 15 * * 4'

        jobs:
        build:
            runs-on: ubuntu-latest
            permissions:
            security-events: write
        steps:
            # This step checks out a copy of your repository.
            - name: Checkout repository
            uses: actions/checkout@v2
            - name: Upload SARIF file
            uses: github/codeql-action/upload-sarif@v1
            with:
                # Path to SARIF file relative to the root of the repository
                sarif_file: results.sarif

### Carga de archivos SARIF generados como parte de un flujo de trabajo de CI

Si genera el archivo SARIF de terceros como parte de un flujo de trabajo de integración continua (CI), puede agregar la acción *upload-sarif* como un paso después de ejecutar las pruebas de CI. Si aún no tiene un flujo de trabajo de CI, puede crear uno mediante un flujo de trabajo de inicio en el repositorio *https://github.com/actions/starter-workflows*.

        ```
        name: "ESLint analysis"

        // Run workflow each time code is pushed to your repository and on a schedule.
        // The scheduled workflow runs every Wednesday at 15:45 UTC.
        on:
        push:
        schedule:
            - cron: '45 15 * * 3'

        jobs:
        build:
            runs-on: ubuntu-latest
            permissions:
            security-events: write
            steps:
            - uses: actions/checkout@v2
            - name: Run npm install
                run: npm install
            // Runs the ESlint code analysis
            - name: Run ESLint
                // eslint exits 1 if it finds anything to report
                run: node_modules/.bin/eslint build docs lib script spec-main -f node_modules/@microsoft/eslint-formatter-sarif/sarif.js -o results.sarif || true
            // Uploads results.sarif to GitHub repository using the upload-sarif action
            - uses: github/codeql-action/upload-sarif@v1
                with:
                // Path to SARIF file relative to the root of the repository
                sarif_file: results.sarif
        ```