# Planes para Copilot

## Contenido

- [¿Qué es?](#qué-es)
- [Planes](#planes)
- [Carácteristicas](#carácteristicas)
  - [Funiones de GitHub Copilot](#funiones-de-github-copilot)
    - [Finalización de código](#finalización-de-código)
    - [Copilot Chat](#copilot-chat)
    - [Copilot en el CLI](#copilot-en-el-cli)
    - [Revisión de código de GitHub Copilot](#revisión-de-código-de-github-copilot)
    - [Compatbilidad con lenguajes](#compatbilidad-con-lenguajes)
    - [Copilot en pull requests](#copilot-en-pull-requests)
    - [Copilot workspace (versión preliminar)](#copilot-workspace-versión-preliminar)
    - [Completar texto del copiloto (versión preliminar)](#completar-texto-del-copiloto-versión-preliminar)
    - [GitHub Copilot Extensions (versión preliminar)](#github-copilot-extensions-versión-preliminar)
    - [Modelos de GitHub (versión preliminar)](#modelos-de-github-versión-preliminar)
    - [Copilot Edits](#copilot-edits)
    - [Instrucciones personalizadas de Copilot](#instrucciones-personalizadas-de-copilot)
    - [Copilot in GitHub Desktop (versión preliminar)](#copilot-in-github-desktop-versión-preliminar)
    - [Bases de conocimiento Copilot (solo Copilot Enterprise)](#bases-de-conocimiento-copilot-solo-copilot-enterprise)
  - [Características de GitHub Copilot para administradores](#características-de-github-copilot-para-administradores)
    - [Administración de directivas](#administración-de-directivas)
    - [Administración de acceso](#administración-de-acceso)
    - [Datos de uso](#datos-de-uso)
    - [Archivos de exclusión](#archivos-de-exclusión)
- [Referencias](#referencias)

## ¿Qué es?

GitHub Copilot es un asistente de codificación de IA que te ayuda a escribir código más rápido y con menos esfuerzo.

## Planes

- **GitHub Copilot Free** está disponible para desarrolladores individuales que no tienen acceso a Copilot desde una organización o empresa.
- **GitHub Copilot Pro** incluye finalizaciones ilimitadas, acceso a modelos Premium en Copilot Chat, y una asignación mensual de solicitudes Premium.
- **GitHub Copilot Pro+** incluye una mayor asignación de solicitudes Premium y acceso total a todos los modelos disponibles en Copilot Chat.
- **GitHub Copilot Business** es para organizaciones con un plan GitHub Free o GitHub Team, o empresas en GitHub Enterprise Cloud. Este plan permite la administración centralizada y el control de directivas de Copilot para los miembros de la organización.
- **GitHub Copilot Enterprise** está para empresas que usan GitHub Enterprise Cloud. Incluye todas las características de Copilot Business, además de funcionalidades adicionales de nivel empresarial. Los propietarios de empresa pueden asignar Copilot Enterprise o Copilot Business a organizaciones individuales.

## Carácteristicas

### Funiones de GitHub Copilot

#### Finalización de código

Sugerencias de estilo autocompletar de Copilot en IDE compatibles (Visual Studio Code, Visual Studio, IDE de JetBrains, Azure Data Studio, Xcode, Vim/Neovim y Eclipse).

Si usas VS Code, también puedes usar sugerencias de edición siguientes, lo que predecirá la ubicación de la edición siguiente que probablemente hagas y sugerir una finalización para ella.

#### Copilot Chat

Una interfaz de chat que le permite formular preguntas relacionadas con la codificación. GitHub Copilot Chat está disponible en el sitio web de GitHub, en GitHub Mobile, en IDE compatibles (Visual Studio Code, Visual Studio, en IDE de JetBrains, el IDE de Eclipse y Xcode), y en Windows Terminal. Los usuarios también pueden usar capacidades con Copilot Chat.

#### Copilot en el CLI

Una interfaz tipo chat en el terminal, donde puede realizar preguntas sobre la línea de comandos. Puede pedir aCopilot que proporcione sugerencias de comandos o explicaciones sobre los comandos. Los usuarios también pueden integrar Copilot en Windows Terminal Canary.

#### Revisión de código de GitHub Copilot

Sugerencias de revisión de código generadas por IA para ayudarte a escribir mejor código. Revisión del código de Copilot en el sitio web GitHub es una característica premium, disponible con los planes Copilot Pro, Copilot Pro+, Copilot Business y Copilot Enterprise. Hay dos tipos de revisión del código de Copilot:

- **Revisión de la selección**: resalta la parte del código que quieras y pide una revisión inicial (solo disponible en VS Code)
- **Revisión de los cambios**: solicita una revisión más minuciosa de todos los cambios ( disponible en VS Code y el sitio web de GitHub)

> [!WARNING]
> No se garantiza que Copilot detecte todos los problemas o incidencias de una solicitud de cambios y, en ocasiones, cometerá errores. Valida siempre los comentarios de Copilot de forma minuciosa y complétalos con una revisión humana.

##### Compatbilidad con lenguajes

- C
- C#
- C++
- Go
- Java
- JavaScript
- Kotlin
- Markdown.
- Python
- Ruby
- Swift
- TypeScript

#### Copilot en pull requests

Resúmenes generados por IA de los cambios realizados en una solicitud de incorporación de cambios, a qué archivos afectan y en qué debe centrarse un revisor al realizar su revisión.

#### Copilot workspace (versión preliminar)

Un entorno habilitado para Copilot para perfeccionar las solicitudes de cambios, validar cambios e integrar sugerencias de revisores.

#### Completar texto del copiloto (versión preliminar)

Finalización de texto generado por IA para ayudarle a escribir descripciones de solicitudes de incorporación de cambios de forma rápida y precisa.

#### GitHub Copilot Extensions (versión preliminar)

GitHub Copilot Extensions son un tipo de GitHub App que integra la eficacia de las herramientas externas en GitHub Copilot Chat. Cualquier usuario puede desarrollar Copilot Extensions, para uso privado o público, y se puede compartir con otros usuarios a través de GitHub Marketplace.

#### Modelos de GitHub (versión preliminar)

Llevar el poder de los modelos de lenguaje grandes y pequeños líderes del sector a los usuarios directamente en GitHub.

#### Copilot Edits

Copilot Edits está disponible en Visual Studio Code y los IDE de JetBrains. Usa Copilot Edits para realizar cambios en varios archivos directamente desde una sola solicitud de Copilot Chat.

- **Modo de edición:** control más pormenorizado de las ediciones que propone Copilot. Puedes elegir los archivos en los que Copilot puede hacer cambios, proporcionar contexto a Copilot con cada iteración y decidir si aceptar o no las modificaciones sugeridas en cada caso.
- **Modo de agente:** cuando tengas una tarea específica en mente y quieras habilitar Copilot para editar de forma autónoma el código. determina en qué archivos hacer cambios, ofrece cambios de código y comandos de terminal para completar la tarea e itera para solucionar los problemas hasta que se complete la tarea original. El modo de agente solo está disponible en Visual Studio Code.

#### Instrucciones personalizadas de Copilot

Mejora las respuestas de Copilot Chat proporcionando detalles contextuales sobre tus preferencias, herramientas y requisitos.

#### Copilot in GitHub Desktop (versión preliminar)

Genera automáticamente mensajes de confirmación y descripciones con Copilot in GitHub Desktop en función de los cambios que realices en el proyecto.

#### Bases de conocimiento Copilot (solo Copilot Enterprise)

Cree y administre colecciones de documentación que se usarán como contexto para conversar con Copilot. Al formular una pregunta en Copilot Chat in GitHub o en VS Code, puedes especificar una base de conocimiento como contexto para la pregunta.

### Características de GitHub Copilot para administradores

#### Administración de directivas

Administre las directivas de GitHub Copilot en su organización o empresa.

#### Administración de acceso

Los propietarios de la empresa pueden especificar qué organizaciones de la empresa pueden utilizar Copilot, y los propietarios de la organización pueden especificar qué miembros de la organización pueden utilizar Copilot.

#### Datos de uso

Revise los registros de auditoría de Copilot de su organización para comprender qué acciones se han llevado a cabo y por qué usuarios.

#### Archivos de exclusión

Configure Copilot para ignorar ciertos archivos. Esto puede ser útil si tiene archivos que no desea que estén disponibles para Copilot.

## Referencias

[GitHub docs - Copilot business](https://docs.github.com/en/copilot/about-github-copilot/subscription-plans-for-github-copilot)
