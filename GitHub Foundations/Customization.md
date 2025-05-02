# Customization

## Contenido

- [Archivo de mantenimiento de la comunidad](#archivo-de-mantenimiento-de-la-comunidad)
  - [Tipos de archivo admitidos](#tipos-de-archivo-admitidos)
  - [Crear un repositorio para archivos predeterminados](#crear-un-repositorio-para-archivos-predeterminados)
- [Perfiles de comunidad](#perfiles-de-comunidad)
  - [Usar la lista de verificación del perfil de comunidad](#usar-la-lista-de-verificación-del-perfil-de-comunidad)
- [README](#readme)
  - [Acerca de los archivos README](#acerca-de-los-archivos-readme)
- [Código de conducta](#código-de-conducta)
  - [Agregar un código de conducta mediante una plantilla](#agregar-un-código-de-conducta-mediante-una-plantilla)
  - [Agregar un código de conducta manualmente](#agregar-un-código-de-conducta-manualmente)
- [Recursos de soporte](#recursos-de-soporte)
- [Licencia](#licencia)
  - [Incluir una licencia](#incluir-una-licencia)
- [Política de seguridad](#política-de-seguridad)
  - [Agregar una política de seguridad](#agregar-una-política-de-seguridad)
  - [Configurar tu dirección de correo electrónico de confirmación](#configurar-tu-dirección-de-correo-electrónico-de-confirmación)
    - [Configuración del e-mail de confirmación](#configuración-del-e-mail-de-confirmación)
    - [Configuración del e-mail de Git](#configuración-del-e-mail-de-git)
- [Maneras de hacer tu perfil más accesible](#maneras-de-hacer-tu-perfil-más-accesible)
- [Referencias](#referencias)

## Archivo de mantenimiento de la comunidad

Los archivos predeterminados de mantenimiento de la comunidad `CONTRIBUTING.md` constituyen un conjunto de archivos predefinidos que proporcionan instrucciones y plantillas para mantener un proyecto de código abierto correcto y colaborativo. Estos archivos te permiten automatizar y estandarizar varios aspectos del desarrollo y la interacción con la comunidad de tu proyecto, promoviendo la transparencia, los procedimientos recomendados y la colaboración.

Cualquiera que cree una propuesta o solicitud de cambios en un repositorio que no tenga su propio archivo `CONTRIBUTING.md` verá un enlace en el archivo `CONTRIBUTING.md` predeterminado del repositorio `.github`. Sin embargo, si un repositorio tiene archivos en una carpeta `.github/ISSUE_TEMPLATE` propia, incluidas las plantillas de incidencia o un archivo `_config.yml`, no se usará el contenido de la carpeta `.github/ISSUE_TEMPLATE` predeterminada. Esto permite a los mantenedores del repositorio invalidar los archivos predeterminados con plantillas o contenido específicos por repositorio.

> [!NOTE]
> Almacenar los archivos en el repositorio `.github` permite realizar cambios en los valores predeterminados en un solo lugar. Además, no aparecerán en el explorador de archivos ni en el historial de Git de los repositorios individuales, y no están incluidos en sus clones, paquetes ni descargas.

### Tipos de archivo admitidos

- CODE_OF_CONDUCT.md: define las normas estándar para participar en una comunidad.

- CONTRIBUTING.md: indica cómo las personas deben contribuir al proyecto.

- Formularios de categorías de discusión:  personalizan las plantillas que están disponibles para que los miembros de la comunidad las usen cuando abran nuevas discusiones en el repositorio.

- FUNDING.yml: muestra un botón de patrocinador en el repositorio para aumentar la visibilidad de las opciones de financiación del proyecto de código abierto.

- GOVERNANCE.md: permite a los usuarios saber cómo se gobierna el proyecto.

- Plantillas de problemas y de solicitudes de incorporación de cambios y config.yml: personalizan y normalizan la información que desea que los colaboradores incluyan cuando abran incidencias y solicitudes de cambios en el repositorio. Si una plantilla de problema establece una etiqueta, esa etiqueta debe crearse en el repositorio de `.github` y todos los repositorios en los que se usará la plantilla.

- SECURITY.md: proporciona instrucciones para informar de una vulnerabilidad de seguridad en el proyecto y una descripción con un hipervínculo al archivo.

- SUPPORT.md: permite a los usuarios conocer formas de obtener ayuda con el proyecto.

### Crear un repositorio para archivos predeterminados

1. En la esquina superior derecha de cualquier página, selecciona + y luego haz clic en `Nuevo repositorio`.

2. Usa el menú desplegable `Propietario` y selecciona la cuenta de la organización o personal para la que quieras crear archivos predeterminados.

3. En el campo `Nombre del repositorio`, escribe `.github`.

4. Opcionalmente, en el campo `Descripción`, teclea una descripción.

5. Asegúrate de que el estado del repositorio esté establecido en `Público`. Un repositorio de archivos predeterminados no puede ser privado.

6. Seleccione `Initialize this repository with a README` (Inicializar este repositorio con un archivo Léame).

7. Haga clic en `Create repository` (Crear repositorio).

8. En el repositorio, crea uno de los archivos admitidos de estado de la comunidad. Las plantillas de incidencia y su archivo de configuración deben estar en una carpeta denominada `.github/ISSUE_TEMPLATE`. Todos los demás archivos admitidos pueden estar en la raíz del repositorio, la carpeta `.github` o la carpeta `docs`.

## Perfiles de comunidad

Los mantenedores del repositorio pueden revisar el perfil de comunidad de sus repositorios públicos para saber cómo pueden ayudar a hacer crecer su comunidad y dar soporte a los colaboradores. Los colaboradores pueden ver el perfil de comunidad de un repositorio público para ver si quieren contribuir con el proyecto.

### Usar la lista de verificación del perfil de comunidad

Puede utilizar la lista de comprobación de las normas comunitarias para ver si su proyecto cumple las normas comunitarias recomendadas para ayudar a la gente a utilizar y contribuir a su proyecto. Si un proyecto no tiene uno de los archivos recomendados, puede hacer clic en el botón Agregar asociado para redactar y enviar un archivo.

Puedes crear una política de seguridad para dar instrucciones a las personas para reportar las vulnerabilidades de seguridad en tu proyecto.

Para que se muestren con una marca  en la lista de comprobación del perfil de la comunidad, las plantillas de incidencia deben estar en la carpeta `.github/ISSUE_TEMPLATE` y contener claves `name:` y `about:` válidas en el texto preliminar de TAML (en el caso de plantillas de incidencia definidas en archivos .md) o claves `name:` y `description:` válidas (en el caso de formularios de incidencia definidos en archivos `.yml`).

## README

### Acerca de los archivos README

Un archivo README en un repositorio suele usarse para comunicar información importante sobre tu proyecto. Un archivo LÉAME, junto con una licencia de repositorio, un archivo de cita, instrucciones de contribución y un código de conducta, comunica las expectativas de tu proyecto y te ayuda a administrar las contribuciones.

Un archivo README suele ser el primer elemento que verá un visitante cuando entre a tu repositorio. Los archivos README habitualmente incluyen información sobre:

- Qué hace el proyecto.
- Por qué el proyecto es útil.
- Cómo pueden comenzar los usuarios con el proyecto.
- Dónde pueden recibir ayuda los usuarios con tu proyecto
- Quién mantiene y contribuye con el proyecto.

Si creas un fichero README en el directorio `.github`, en la raíz o en el directorio `docs`, GitHub lo expondrá a los visitantes de tu repositorio. Si tienes más de un fichero readme se mostrarán en el siguiente orden:

1. directorio `.github`
2. directorio raíz del proyecto
3. directorio `docs`

Si agregas un archivo de README a la raíz de un repositorio público con el mismo nombre que tu nombre de usuario, dicho README aparecerá automáticamente en tu página de perfil.

## Código de conducta

Un código de conducta define las normas para participar en una comunidad. Describe los procedimientos para tratar problemas de tus proyectos entre los miembros de la comunidad.

Antes de adoptar un código de conducta para tu proyecto:

- Investiga códigos de conducta diferentes diseñados para proyectos de código abierto. Elije uno que refleje los estándares de tu comunidad.
- Considera cuidadosamente si estás dispuesto a hacerlo cumplir y puedes hacerlo.

Tu código de conducta estará disponible de cualquier forma, pero el "Código de conducta" solo se marcará como completo en el perfil comunitario de tu repositorio si utilizas una plantilla.

### Agregar un código de conducta mediante una plantilla

GitHub ofrece plantillas para códigos de conducta comunes a fin de ayudarte a agregar rápidamente un código de conducta para tu proyecto.

1. En GitHub, navegue hasta la página principal del repositorio.

2. Encima de la lista de archivos, selecciona el menú desplegable Add file  y, a continuación, haz clic en `Create new file`.

3. En el campo de nombre del archivo, escriba CODE_OF_CONDUCT.md.

4. Selecciona Elegir una plantilla de código de conducta.

5. En el lateral izquierdo de la página, selecciona un código de conducta para previsualizar y agregar a tu proyecto.

6. En el lateral derecho de la página, completa los campos para llenar el código de conducta seleccionado con la información adecuada.

7. Haga clic en Review and submit.

8. Revisa los contenidos del código de conducta que está en el área de texto.

9. Haz clic en Confirmar cambios... .

10. En el campo de "Mensaje de confirmación", escriba un mensaje de confirmación corto y significativo que describa la modificación que hizo en el archivo.

11. Debajo de los campos para el mensaje de confirmación, decide si deseas agregar tu confirmación a la rama actual o a una rama nueva.

12. Haz clic en Confirmar cambios o Proponer cambios.

### Agregar un código de conducta manualmente

1. En GitHub, navegue hasta la página principal del repositorio.

2. Encima de la lista de archivos, selecciona el menú desplegable Add file  y, a continuación, haz clic en `Create new file`.

3. En el campo de nombre, teclea el nombre y la extensión del archivo.

    - Para que el código de conducta se muestre como visible en el directorio raíz del repositorio, escriba CODE_OF_CONDUCT en el campo de nombre de archivo.
    - Para que el código de conducta sea visible en el directorio docs del repositorio, escriba docs/CODE_OF_CONDUCT.
    - Para que el código de conducta sea visible en el directorio .github del repositorio, escriba .github/CODE_OF_CONDUCT.

4. En el archivo nuevo, agrega tu código de conducta personalizado.

5. Haz clic en Confirmar cambios...

6. En el campo de "Mensaje de confirmación", escriba un mensaje de confirmación corto y significativo que describa la modificación que hizo en el archivo.

7. Debajo de los campos para el mensaje de confirmación, decide si deseas agregar tu confirmación a la rama actual o a una rama nueva.

8. Haz clic en Confirmar cambios o Proponer cambios.

## Recursos de soporte

Para dirigir a los usuarios a recursos de soporte técnico específicos, puede agregar un archivo `SUPPORT` a la carpeta raíz `docs` o `.github` del repositorio.

## Licencia

Si incluyes una licencia detectable en tu repositorio, las personas que visiten tu repositorio la verán en la parte superior de la página del repositorio. Las licencias de código abierto permiten que otras personas usen, cambien y distribuyan el proyecto en tu repositorio.

### Incluir una licencia

1. En GitHub, navegue hasta la página principal del repositorio.

2. Encima de la lista de archivos, selecciona el menú desplegable `Add file`  y, a continuación, haz clic en + `Create new file`.

3. En el campo de nombre de archivo, escribe `LICENSE` o `LICENSE.md` (todo en mayúsculas).

4. En el nombre de archivo, haz clic en `Elegir una plantilla de licencia`.

5. En el lateral izquierdo de la página, en `Agregar una licencia a tu proyecto`, revisa las licencias disponibles, luego selecciona una licencia de la lista.

6. Haga clic en `Review and submit`.

7. Haz clic en `Confirmar cambios...` .

8. En el campo de `Mensaje de confirmación`, escriba un mensaje de confirmación corto y significativo que describa la modificación que hizo en el archivo.

9. Debajo de los campos para el mensaje de confirmación, decide si deseas agregar tu confirmación a la rama actual o a una rama nueva.

10. Si tiene más de una dirección de correo electrónico asociada a la cuenta en , haga clic en el menú desplegable de la dirección de correo electrónico y seleccione la que se usará como dirección de correo electrónico del creador de Git.

11. Haz clic en `Confirmar cambios` o `Proponer cambios`.

## Política de seguridad

Si quieres proporcionar a otras personas instrucciones para notificar vulnerabilidades de seguridad en el proyecto, puedes agregar un archivo `SECURITY.md` a la raíz, a los documentos `docs` o la carpeta `.github` del repositorio.

Cuando alguien informa de una vulnerabilidad de seguridad en el proyecto, puede usar GitHub Security Advisories para divulgar, corregir y publicar información sobre esta.

### Agregar una política de seguridad

1. En GitHub, navegue hasta la página principal del repositorio.

2. En el nombre del repositorio, haz clic en  `Seguridad`. Si no puedes ver la pestaña `Seguridad`, selecciona el menú desplegable  y, a continuación, haz clic en `Seguridad`.

3. En la barra lateral izquierda, en `Informes`, haz clic en  `Política`.

4. Haga clic en `Iniciar configuración`.

5. En el nuevo archivo `SECURITY.md`, agregue información sobre las versiones admitidas del proyecto y cómo notificar una vulnerabilidad.

6. Haz clic en Confirmar cambios... .

7. En el campo de "Mensaje de confirmación", escriba un mensaje de confirmación corto y significativo que describa la modificación que hizo en el archivo.

8. Si tiene más de una dirección de correo electrónico asociada a la cuenta en , haga clic en el menú desplegable de la dirección de correo electrónico y seleccione la que se usará como dirección de correo electrónico del creador de Git.

9. Debajo de los campos para el mensaje de confirmación, decide si deseas agregar tu confirmación a la rama actual o a una rama nueva.

10. Haz clic en Confirmar cambios o Proponer cambios.

### Divulgar vulnerabilidad

Es un área donde la colaboración entre los reporteros de vulnerabilidades, como los investigadores de seguridad y los mantenedores de proyectos, es muy importante. Ambas partes deben trabajar juntas desde el momento en que se encuentra una vulnerabilidad de seguridad potencialmente dañina, hasta que se divulgue una vulnerabilidad al mundo, idealmente con un parche disponible.

El informe inicial de una vulnerabilidad se hace de forma privada, y los detalles completos solo se publican una vez que el mantenedor ha reconocido el problema, e idealmente hizo que las remediaciones o un parche estén disponibles, a veces con un retraso para permitir más tiempo para que se instalen los parches.

#### Mejores prácticas para reporteros de vulnerabilidad

Es una buena práctica reportar vulnerabilidades de forma privada a los mantenedores. Cuando sea posible, como reportero de vulnerabilidades, le recomendamos evitar:

- Divulgar la vulnerabilidad públicamente sin dar a los mantenedores la oportunidad de remediarla.
- Bypass de los mantenedores.
- Divulgar la vulnerabilidad antes de que esté disponible una versión fija del código.
- Esperando ser compensado por informar un problema, donde no existe un programa de recompensas públicas.

#### Mejores prácticas para mantenedores

Los mantenedores deben revelar vulnerabilidades de manera oportuna. Si hay una vulnerabilidad de seguridad en su repositorio, le recomendamos:

- Trate la vulnerabilidad como un problema de seguridad en lugar de un simple error, tanto en su respuesta como en su divulgación.

- Reconocer la recepción del informe de vulnerabilidad lo más rápido posible, incluso si no hay recursos inmediatos disponibles para la investigación. Esto envía el mensaje de que usted es rápido para responder y actuar, y establece un tono positivo para el resto de la interacción entre usted y el reportero de vulnerabilidad.

- Involucre al reportero de vulnerabilidades cuando verifique el impacto y la veracidad del informe. Es probable que el reportero de vulnerabilidad ya haya pasado tiempo considerando la vulnerabilidad en una variedad de escenarios, algunos de los cuales es posible que no se haya considerado a sí mismo.

- Remediar el problema de la manera que mejor le parezca, teniendo en cuenta cuidadosamente cualquier inquietud y consejo proporcionado por el reportero de vulnerabilidades. A menudo, el reportero de vulnerabilidad tendrá conocimiento de ciertos casos de esquina y derivaciones de remediación que son fáciles de perder sin un fondo de investigación de seguridad.

- Siempre reconozca al reportero de vulnerabilidades cuando acredite el descubrimiento.

- Trate de publicar una solución tan pronto como pueda.

- Asegúrese de que el ecosistema más amplio sea consciente del problema y su remediación cuando divulgue la vulnerabilidad. No es raro ver casos en los que se soluciona un problema de seguridad reconocido en la rama de desarrollo actual de un proyecto, pero el commit o la versión posterior no se marcan explícitamente como una solución o liberación de seguridad. Esto puede causar problemas con los consumidores intermedios.

### Configurar tu dirección de correo electrónico de confirmación

GitHub utiliza su dirección de correo electrónico de confirmaciones para asociar dichas confirmaciones con su cuenta de GitHub. Puedes elegir la dirección de correo electrónico que se asociará con las confirmaciones que subes desde la línea de comando y las operaciones de Git con base en la web que realizas.

> [!NOTE]
> Si quiere mantener la dirección de correo electrónico como privada, puede utilizar la dirección de correo electrónico noreply proporcionada por GitHub.

#### Configuración del e-mail de confirmación

1. En la esquina superior derecha de cualquier página en GitHub, haga clic en la fotografía de perfil y luego en `Configuración`.

2. En la sección `Acceso` de la barra lateral, haz clic en `Correos electrónicos`.

3. En `Agregar dirección de correo electrónico`, escribe tu dirección de correo electrónico y haz clic en `Agregar`.

4. Comprueba la dirección de correo electrónico.

5. En el menú desplegable `Dirección de correo electrónico principal`, selecciona la dirección que quieres asociar con tus operaciones de Git basadas en web.

#### Configuración del e-mail de Git

1. Abra Git Bash.

2. Configurar una dirección de correo electrónico en Git.

        git config --global user.email "YOUR_EMAIL"

3. Confirma que has establecido correctamente la dirección de correo electrónico en Git:

        $ git config --global user.email
        email@example.com

4. Agrega la dirección de correo electrónico a tu cuenta en GitHub, de modo que las confirmaciones se te atribuyan y aparezcan en el gráfico de contribuciones.

## Maneras de hacer tu perfil más accesible

<!--https://github.blog/developer-skills/github/5-tips-for-making-your-github-profile-page-accessible/-->

## Referencias

[GitHub docs](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository)

[OpenSurce - Code of conduct](https://opensource.guide/code-of-conduct/)

[OpenSurce - Building communities](https://opensource.guide/building-community/)

[GitHub security](https://docs.github.com/es/code-security/security-advisories/guidance-on-reporting-and-writing-information-about-vulnerabilities/about-coordinated-disclosure-of-security-vulnerabilities#about-reporting-and-disclosing-vulnerabilities-in-projects-on-github)

[OWASP](https://cheatsheetseries.owasp.org/cheatsheets/Vulnerability_Disclosure_Cheat_Sheet.html#commercial-and-open-source-software)

[GitHub - Blog](https://github.blog/developer-skills/github/5-tips-for-making-your-github-profile-page-accessible/)