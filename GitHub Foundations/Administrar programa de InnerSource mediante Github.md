# Administrar programa de InnerSource mediante Github

## Cómo administrar un programa de InnerSource eficaz

### ¿Qué es Inner Source?

Cualquier persona puede usar, modificar y compartir software de código abierto libremente. InnerSource es un procedimiento que consiste en aplicar patrones de código abierto a proyectos con un público limitado.

#### Ventajas de InnerSource

Fomenta la transparencia. El acceso al código fuente de los proyectos de otras empresas puede ayudar a los desarrolladores a ser más productivos a la hora de trabajar en sus propios proyectos. El acceso a problemas de equipos, solicitudes de incorporación de cambios y planes de proyecto también les proporciona mejores datos para entender la velocidad y la dirección del proyecto.

Reduce la fricción. En un programa InnerSource, tienen un canal a través del cual pueden proponer los cambios que necesitan. Si esos cambios no se pueden combinar por cualquier motivo, el equipo de consumo tiene la opción de bifurcar el proyecto para satisfacer sus necesidades.

Etandariza procedimientos. La compilación de un programa de InnerSource es una excelente oportunidad para adoptar convenciones estándar que se pueden usar en todos los equipos de desarrollo, aunque no sigan los mismos procedimientos. 

### Configuración de un programa de InnerSource en GitHub

#### Configuración de los permisos y la visibilidad del repositorio

Puede configurar repositorios de GitHub con tres niveles de visibilidad.

* Repositorios públicos, visibles para cualquiera. Use esta visibilidad para los proyectos que son verdaderamente de código abierto y que ofrecen acceso a usuarios de dentro y fuera de la organización.
* Repositorios internos, solo visibles para los miembros de la organización que los posee. Use esta visibilidad para proyectos de InnerSource.
* Repositorios privados, solo visibles para el propietario y los equipos o usuarios que este agrega. Use esta visibilidad para los proyectos a los que solo deben tener acceso usuarios y grupos específicos.

Configurar permisos por usuario o equipo.

* Nivel de lectura se recomienda para colaboradores que no trabajan en el código, pero que quieren ver el proyecto o hablar sobre él.
* Nivel de evaluación de prioridades se recomienda para colaboradores que necesitan administrar de forma proactiva problemas y solicitudes de incorporación de cambios sin acceso de escritura.
* Nivel de escritura se recomienda para colaboradores que insertan cambios activamente en el proyecto.
* Nivel de mantenimiento se recomienda para jefes de proyecto que necesitan administrar el repositorio sin acceder a acciones confidenciales o destructivas.
* Nivel de administración se recomienda para usuarios que necesitan acceso total al proyecto, incluidas acciones confidenciales y destructivas como, por ejemplo, administrar la seguridad o eliminar un repositorio.

#### Crear repositorios detectables

A medida que un programa de InnerSource crece, es plausible que el número de repositorios escale verticalmente de forma considerable. Se recomienda a los equipos pensar qué hacer para que otros usuarios puedan buscar sus repositorios y trabajar con ellos con más facilidad.

* Usar un nombre de repositorio descriptivo, como `warehouse-api` o `supply-chain-web`.
* Incluir una descripción concisa. Una frase o dos deben bastar para que los usuarios potenciales sepan si el proyecto puede ajustarse a sus necesidades.
* [Conceda una licencia al repositorio](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/licensing-a-repository) para que los clientes sepan cómo pueden usar, cambiar y distribuir el software.
* Incluir un archivo `README.md` en el repositorio. GitHub usa este archivo como página de aterrizaje cuando los usuarios visitan el repositorio.

#### Incorporación de un archivo LÉAME

Un archivo LÉAME comunica las expectativas del proyecto y le ayuda a administrar las contribuciones.

* Articular el propósito y la visión del proyecto para que los consumidores potenciales entiendan si se ajusta a sus necesidades.
* Ofrecer ayudas visuales, como capturas de pantalla o ejemplos de código, para ilustrar el proyecto en acción.
* Incluir vínculos a una versión de demostración o de producción de la aplicación para su revisión;
* Establecer las expectativas en cuanto a requisitos previos y procedimientos de implementación.
* Incluir referencias a los proyectos de los que usted dependa. Estas referencias son una buena manera de promover el trabajo de los demás;
* Utilizar Markdown para guiar a los lectores por un contenido con el formato correcto.

Si coloca el archivo Léame en el directorio raíz del repositorio o en el directorio `.github` o `docs` oculto, GitHub reconoce y expone automáticamente el archivo Léame a los visitantes del repositorio. Si un repositorio contiene más de un archivo README, el archivo que se muestra se elige de las ubicaciones en el siguiente orden: el directorio `.github`, luego el directorio raíz del repositorio y finalmente el directorio `docs`.

[Ejemplos de archivos LEAME](https://github.com/matiassingers/awesome-readme)

#### Administración de proyectos en GitHub

La afluencia de usuarios y contribuciones puede requerir mucho trabajo de administración. En función del proyecto, es posible que se necesite una cantidad considerable de trabajo solo para administrar las expectativas de los participantes en el mismo.

Para abordar este problema de forma proactiva, GitHub busca un archivo `CONTRIBUTING.md` en la raíz (`/docs` o `/.github`) de un repositorio. Use este archivo para explicar la directiva de contribución del proyecto. Los detalles exactos pueden variar, pero es una buena idea permitir que los posibles colaboradores sepan qué convenciones sigue el proyecto.

Si existe un archivo CONTRIBUTING.md, GitHub presenta un vínculo a él cuando los usuarios crean incidencias o solicitudes de incorporación de cambios para animarles a seguirlo.

[Ejemplos de archivo CONTRIBUTING.md](https://github.com/mntnr/awesome-contributing)

> [!TIP]
> Puede considerar la posibilidad de [agregar un archivo CODEOWNERS](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-code-owners) al repositorio para definir los usuarios o los equipos responsables de revisar las modificaciones de código.

#### Creación de plantillas de incidencias y de solicitud de incorporación de cambios

GitHub admite plantillas de inicio para nuevos problemas y solicitudes de incorporación de cambios. Use estas plantillas para proporcionar el texto de descripción inicial de un problema o una solicitud de incorporación de cambios recién creados.

Si el proyecto tiene .github/ISSUE_TEMPLATE.md, cada vez que un usuario inicia el proceso de creación de una incidencia, ve este contenido. En vez de tener que hacer referencia constantemente a los detalles obligatorios de un archivo CONTRIBUTING.md, puede rellenar la incidencia como formulario mediante el texto de la plantilla.

[Plantillas fantásticas de problemas y de solicitudes de incorporación de cambios de GitHub](https://github.com/devspace/awesome-github-templates)

#### Definición de los flujos de trabajo

En el caso de los proyectos que alientan las contribuciones externas, asegúrese de especificar qué flujo de trabajo sigue el proyecto. El flujo de trabajo debe incluir detalles sobre dónde y cómo se deben usar las ramas para errores y características. También debe incluir cómo se deben abrir las solicitudes de cambios y cualquier otro detalle que los usuarios externos al equipo del repositorio deben saber antes de insertar código. 

[El flujo de GitHub](https://guides.github.com/introduction/flow/)

Debe comunicar una estrategia para administrar versiones e implementaciones. Estas partes del flujo de trabajo afectan a la bifurcación y combinación cotidianas, por lo que es importante comunicárselas a los colaboradores.

[Estrategia de bifurcación de Git](https://learn.microsoft.com/es-es/azure/devops/repos/git/git-branching-guidance)

#### Medición del éxito de un programa

Cualquier equipo que se aventure en InnerSource debe pensar en los tipos de métricas que quiere seguir para medir el éxito de su programa. Considere la posibilidad de agregar métricas que muestren cómo mejoró la participación externa la calidad del proyecto. 

Las métricas son difíciles, especialmente cuando se trata de medir el valor y el impacto de las contribuciones individuales y colectivas. Si se usan mal, las métricas pueden dañar la cultura corporativa, los procesos existentes y perjudicar la opinión colectiva sobre la organización o el equipo directivo. Al pensar en la medición de la adopción de InnerSource, tenga en cuenta las siguientes instrucciones sobre las métricas:

* Mida el proceso, no los resultados
    * Tiempo de respuesta de revisión de código
    * Tamaño de las solicitudes de incorporación de cambios
    * Trabajo en curso
    * Plazo de apertura
* Mida en objetivos y no en valores absolutos
* Mida equipos y no personas
    * Número de colaboradores únicos en un proyecto
    * Número de proyectos que reutilizan código
    * Número de @mentions entre equipos