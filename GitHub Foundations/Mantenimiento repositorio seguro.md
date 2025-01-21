# Mantenimiento de un repositorio seguro mediante procedimientos recomendados de GitHub

## Cómo mantener un repositorio de GitHub seguro

### Importancia de una estrategia de desarrollo segura

La seguridad de las aplicaciones es importante. Los servicios de noticias suelen contar historias sobre vulneraciones en los sistemas de empresas y datos de clientes y empresariales privados robados.

Hay determinados aspectos que se deben tener en cuenta a la hora de planear una estrategia de desarrollo segura. Está claro que tenemos que proteger la información para que no se revele a personas que no deberían tener acceso a ella, pero lo que es más importante, tenemos que asegurarnos de que la información solo se modifique o destruya cuando sea apropiado.

Debemos asegurarnos de autenticar correctamente a quién obtiene acceso a los datos y de que tiene los permisos correctos para hacerlo. Es necesario poder encontrar evidencias si algo salió mal por medio de registros o datos históricos o de archivo.

Estas son tres cosas que se deben tener en cuenta en la compilación e implantación:

* **Hay un problema de conocimiento general**: Muchos desarrolladores y otros miembros del personal dan por hecho que entienden la seguridad, pero no es así. La ciberseguridad es una disciplina en continua evolución. Un programa de educación y aprendizaje continuo es fundamental.

* **El código debe crearse de forma correcta y segura**: Debemos asegurarnos de que el código se crea correctamente y de que implementa de forma segura las características necesarias. También hay que asegurarse de que las características se diseñen pensando en la seguridad.

* **Las aplicaciones deben cumplir las reglas y la normativa**: Debemos asegurarnos de que el código cumpla con las normas y regulaciones necesarias. Hay que probar la compatibilidad al compilar el código y, a continuación, volver a probar periódicamente, incluso después de la implementación.

### Seguridad en todos los pasos

El desarrollo seguro debe formar parte de cada fase del ciclo de vida de desarrollo de software.

Para que los equipos sean responsables de lo que desarrollan, es necesario aplicar a los procesos el **principio de desplazamiento a la izquierda** o completarse antes, en el ciclo de vida de desarrollo. Al desplazar los pasos de una puerta final en tiempo de implementación a un paso anterior, se producen menos errores y los desarrolladores pueden avanzar más rápidamente.

Si se tiene en cuenta el tiempo de reelaboración, la incorporación de la seguridad a los procedimientos de DevOps al comienzo del proceso de desarrollo ayuda a los equipos de desarrollo a detectar antes los problemas. Detectar los problemas más pronto puede realmente reducir el tiempo total que se tarda en desarrollar software de calidad.

El desplazamiento a la izquierda es un cambio de proceso, pero no es un solo control o una herramienta específica. Se trata de hacer que toda la seguridad esté más centrada en el desarrollador y proporcionar a este comentarios de seguridad donde estén.

### Características de la pestaña Seguridad

Pestaña seguridad: 

1. En GitHub.com, vaya a la página principal del repositorio.

2. En el nombre del repositorio, seleccione Seguridad.

En la pestaña Seguridad, puede agregar características al flujo de trabajo de GitHub para ayudar a evitar vulnerabilidades en el repositorio y el código base. Estas características son las siguientes:

* **Directivas de seguridad** que permiten especificar cómo notificar una vulnerabilidad de seguridad en el proyecto agregando un archivo `SECURITY.md` al repositorio.
* **Alertas de Dependabot** que le notifican cuando GitHub detecta que el repositorio usa una dependencia vulnerable o malware.
* **Avisos de seguridad** que puede usar para analizar, corregir y publicar información sobre vulnerabilidades de seguridad en el repositorio de forma privada.
* **Examen de código** que le ayuda a encontrar, evaluar y corregir vulnerabilidades y errores en el código.

> [!TIP]
> [Características de seguridad de GitHub](https://docs.github.com/code-security/getting-started/github-security-features)

> [!NOTE]
> Los avisos de alertas de Dependabot para malware están actualmente en versión beta y están sujetos a cambios. Solo los avisos revisados por GitHub desencadenarán alertas de Dependabot.

### Comunicación de una directiva de seguridad con SECURITY.md

Las ventajas de la comunidad de GitHub son considerables, pero también conllevan posibles riesgos. La más importante es la revelación responsable de la información que podría dar lugar a vulnerabilidades de seguridad antes de que se pudieran solucionar los errores subyacentes. Los desarrolladores que intentan comunicar o abordar problemas de seguridad buscan un archivo SECURITY.md en la raíz de un repositorio para revelar de forma responsable sus inquietudes. Al proporcionar instrucciones en este archivo, se acelera la resolución de estos problemas críticos.

> [!TIP]
> [Agregar una política de seguridad a tu repositorio](https://docs.github.com/code-security/getting-started/adding-a-security-policy-to-your-repository)

### Avisos de seguridad de GitHub

Los avisos de seguridad de GitHub permiten a los mantenedores de repositorios analizar y corregir de forma privada una vulnerabilidad de seguridad en un proyecto. Después de que los mantenedores de repositorios colaboren en una corrección, pueden publicar el aviso de seguridad para revelar públicamente la vulnerabilidad de seguridad a la comunidad del proyecto. Al publicar avisos de seguridad, los mantenedores de repositorios facilitan a su comunidad la actualización de dependencias de paquetes y la investigación de las consecuencias de las vulnerabilidades de seguridad. GitHub almacena los avisos publicados en la lista Vulnerabilidades y exposiciones comunes (CVE). Esta lista se usa para notificar automáticamente a los repositorios afectados que usen software que tenga una vulnerabilidad listada.

> [!TIP]
> [Acerca de los avisos de seguridad del repositorio](https://docs.github.com/code-security/security-advisories/working-with-repository-security-advisories/about-repository-security-advisories)

### Mantenimiento de los archivos confidenciales fuera del repositorio con .gitignore

Es fácil para los desarrolladores pasar por alto archivos incluidos en una confirmación. A veces, estos archivos pasados por alto son benignos, como los archivos de compilación intermedios. Una técnica que ayuda a evitar este riesgo consiste en compilar y mantener archivos `.gitignore`. Estos archivos indican a las herramientas cliente, como la utilidad de línea de comandos git, que omitan las rutas de acceso y los patrones al agregar archivos para una confirmación.

Ejemplo de `.gitignore`.

        # User-specific files - Ignore all files ending in ".suo"
        *.suo

        # Mono auto generated files - Ignore all files starting with "mono_crash."
        mono_crash.*

        # Build results - Ignore all files in these folders found at any folder depth
        [Dd]ebug/
        [Rr]elease/
        x64/
        x86/

        # Root config folder - Ignore this directory at the root due to leading slash
        # Removing the slash would ignore "config" directories at all depths 
        /config

        # Ignore intermediate JS build files produced during TypeScript build at any 
        # folder depth under /Web/TypeScript. This won't ignore JS files elsewhere. 
        /Web/TypeScript/**/*.js

El repositorio podría incluir varios archivos .gitignore. La configuración se hereda de los directorios principales, y los campos de invalidación de los nuevos archivos .gitignore tienen prioridad sobre la configuración principal de sus carpetas y subcarpetas. Supone un esfuerzo importante mantener el archivo .gitignore raíz, aunque agregar un archivo .gitignore a un directorio del proyecto puede ser útil si ese proyecto tiene requisitos específicos que son más fáciles de mantener independientemente del principal, como archivos que no se deben omitir.

> [!TIP]
> [Ignorar archivos](https://docs.github.com/get-started/getting-started-with-git/ignoring-files)

### Eliminación de datos confidenciales de un repositorio

Aunque los archivos .gitignore pueden ser útiles para ayudar a los colaboradores a evitar la que se comprometan datos confidenciales, solo es una sugerencia firme. Los desarrolladores se lo pueden saltar para agregar archivos si están lo suficientemente motivados y, a veces, hay archivos que se podrían colar porque no cumplen la configuración del archivo .gitignore. Los participantes en el proyecto deben estar siempre atentos a las confirmaciones que contengan datos que no deberían incluirse en el repositorio ni en su historial.

> [!TIP]
> [Eliminar datos confidenciales de un repositorio](https://docs.github.com/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository)

### Reglas de protección de ramas

Cree una [regla de protección de rama](https://docs.github.com/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/managing-a-branch-protection-rule) para aplicar determinados flujos de trabajo a una o varias ramas.

Use los flujos de trabajo que protegen la rama para:

* Ejecución de una compilación para comprobar que se pueden compilar los cambios de código
* Ejecutar un linter para comprobar si hay errores tipográficos y se cumplen las convenciones de codificación internas
* Ejecutar pruebas automatizadas para comprobar los cambios de comportamiento del código
* Etcétera.

### Adición de un archivo CODEOWNERS

Al agregar un archivo [CODEOWNERS](https://docs.github.com/github/creating-cloning-and-archiving-repositories/creating-a-repository-on-github/about-code-owners#codeowners-syntax) al repositorio, puede asignar miembros individuales del equipo o equipos completos como propietarios del código a las rutas del repositorio. A continuación, se solicita a estos propietarios de código que hagan revisiones de solicitudes de cambios sobre los cambios realizados en los archivos de una ruta de acceso para la que están configurados.

        # Changes to files with the js extensions need to be reviewed by the js-owner user/group:
        *.js    @js-owner

        # Changes to files in the builds folder need to be reviewed by the octocat user/group:
        /build/ @octocat

Puede crear el archivo CODEOWNERS en la raíz del repositorio o en la carpeta `docs` o `.github`.

## Seguridad automatizada

### Detectar y corregir dependencias obsoletas con vulnerabilidades de seguridad

Todos los proyectos hoy en día tienen dependencias en paquetes externos. Estar atento a estos paquetes y su estado de vulnerabilidad puede llevar mucho tiempo, especialmente porque cada dependencia podría tener sus propias dependencias, lo que dificulta su seguimiento y mantenimiento. Afortunadamente, GitHub proporciona características que reducen esta carga de trabajo.

#### Gráficos de dependencias de repositorios

Una característica predeterminada que incluyen todos los repositorios son los gráficos de dependencias. GitHub examina los manifiestos de paquete comunes, como `package.json`, `requirements.txt` y otros. Estos gráficos permiten a los propietarios de proyectos realizar un seguimiento recurrente de todas las dependencias en las que se basa su proyecto.

> [!TIP]
> [Acerca del gráfico de dependencias](https://docs.github.com/code-security/supply-chain-security/understanding-your-software-supply-chain/about-the-dependency-graph)

#### Alertas de Dependabot

GitHub proporciona [alertas de Dependabot](https://docs.github.com/code-security/dependabot/dependabot-alerts/about-dependabot-alerts#dependabot-alerts-for-vulnerable-dependencies) que vigilan los gráficos de dependencias automáticamente. Comparan las versiones de destino con las versiones de listas de vulnerabilidades conocidas. Cuando se detecta un riesgo, se alerta al proyecto. La entrada para el análisis procede de [avisos de seguridad de GitHub](https://docs.github.com/code-security/security-advisories/working-with-repository-security-advisories/about-repository-security-advisories#dependabot-alerts-for-published-security-advisories).

#### Actualizaciones de dependencias automatizadas con Dependabot

Una alerta de dependencia puede llevar a un colaborador del proyecto a cambiar la referencia de paquete infractor a la versión recomendada y a crear una solicitud de incorporación de cambios para validación. Dependabot hace precisamente eso. Examina las alertas de dependencia y crea solicitudes de incorporación de cambios para que un colaborador pueda validar la actualización y combinar la solicitud.

> [!TIP]
> [Configuración de actualizaciones de seguridad de Dependabot](https://docs.github.com/code-security/dependabot/dependabot-security-updates/configuring-dependabot-security-updates)

#### Análisis automatizado del código

Puede usar el análisis de código para analizar y detectar errores y vulnerabilidades de seguridad en el código de un repositorio de GitHub. Se puede usar para buscar, evaluar y clasificar por orden de prioridad las correcciones de problemas existentes o posibles vulnerabilidades de seguridad. También resulta útil para impedir que los desarrolladores introduzcan nuevos problemas de seguridad en el código.

Otra ventaja del análisis de código es su capacidad para usar CodeQL. CodeQL sirve para consultar código como datos, lo que le permite crear consultas personalizadas, o bien usar consultas mantenidas por la comunidad de código abierto. El análisis de código le ofrece libertad para personalizar y mantener la forma en que se examina el código del repositorio.

Puede habilitar alertas y flujos de trabajo de análisis de código en la pestaña de seguridad de un repositorio de GitHub.

> [!TIP]
> [Análisis de código y CodeQL](https://docs.github.com/code-security/code-scanning/introduction-to-code-scanning/about-code-scanning#about-code-scanning)

#### Análisis de secretos

Otra característica de análisis automatizada en un repositorio de GitHub es el análisis de secretos. Este análisis se realiza para impedir el uso de comportamientos fraudulentos y para proteger la integridad de los datos confidenciales. De forma predeterminada, el análisis de secretos se produce en repositorios públicos, y se puede habilitar en repositorios privados por los administradores del repositorio o los propietarios de la organización.

Cuando el examen de secretos detecta un conjunto de credenciales, GitHub notifica al proveedor de servicios que ha emitido el secreto. El proveedor de servicios valida la credencial. A continuación, decide si se debería revocar el secreto, emitir un nuevo secreto o ponerse en contacto directamente con usted. La acción depende de los riesgos asociados para usted o el proveedor de servicios.

> [!TIP]
> [Análisis de secretos para repositorios públicos y privados](https://docs.github.com/code-security/secret-scanning/about-secret-scanning)

