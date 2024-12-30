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

