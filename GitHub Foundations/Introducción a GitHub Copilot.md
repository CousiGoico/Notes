# Introducción a GitHub Copilot

## GitHub Copilot, el programador de pares de IA

La adición de características de inteligencia artificial a las herramientas de desarrollo que usa y adora le ayuda a colaborar, desarrollar, probar y enviar sus productos de forma más rápida y eficaz que nunca. GitHub Copilot es un servicio que proporciona un programador de pares de IA que funciona con todos los lenguajes de programación populares.

GitHub y Microsoft encontraron que los desarrolladores experimentan un aumento significativo de la productividad cuando usan GitHub Copilot para trabajar en proyectos y tareas reales.

* El 46 % del nuevo código ahora escrito por IA
* La productividad general de los desarrolladores es un 55 % más rápida
* El 74 % de los desarrolladores se sienten más centrados en satisfacer el trabajo

Microsoft desarrolló GitHub Copilot en colaboración con OpenAI. GitHub Copilot cuenta con la tecnología del sistema OpenAI Codex. OpenAI Codex tiene un amplio conocimiento de cómo las personas usan código y es más capaz que GPT-3 en la generación de código. OpenAI Codex es más capaz, en parte, porque se entrenó en un conjunto de datos que incluía una mayor concentración de código fuente público.

GitHub Copilot está disponible como una extensión para VS Code, Visual Studio, Vim/Neovim y el conjunto de IDE de JetBrains.

### Características de GitHub Copilot

GitHub Copilot inició una nueva era de desarrollo de software como programador de pares de IA que mantiene a los desarrolladores en el flujo mediante comentarios y código autocompletar.

#### Copilot para chat

La interfaz de chat se centra en escenarios de desarrollador y se integra de forma nativa con VS Code y Visual Studio. Está profundamente incrustado en el IDE y reconoce qué código ha escrito un desarrollador y qué mensajes de error aparecen. Un desarrollador puede obtener análisis detallados y explicaciones de para qué están diseñados los bloques de código, generar pruebas unitarias e incluso obtener correcciones propuestas para errores.

#### Copilot para solicitudes de incorporación de cambios

El modelo GPT-4 de OpenAI agrega compatibilidad en GitHub Copilot para etiquetas con tecnología de IA en descripciones de solicitudes de incorporación de cambios a través de una aplicación de GitHub que los administradores de la organización y los propietarios de repositorios individuales pueden instalar. GitHub Copilot rellena automáticamente estas etiquetas en función del código cambiado. A continuación, los desarrolladores pueden revisar o modificar las descripciones sugeridas.

#### Copilot para la CLI

La interfaz de la línea de comandos (CLI) de GitHub Copilot puede componer comandos y bucles, y puede e iniciar marcas de find ocultas para satisfacer la consulta.

### Planes de suscripción

#### GitHub Copilot Business

Permite controlar quién puede usar GitHub Copilot en la empresa. Después de conceder acceso a una organización, sus administradores pueden conceder acceso a usuarios y equipos. Está abierto a todos los desarrolladores, equipos, organizaciones y empresas.

* Finalizaciones de código
* Chatear en IDE y dispositivos móviles
* Filtrado de vulnerabilidades de seguridad
* Referencia de código
* Filtrar para código público
* Indemnización de propiedad intelectual
* Seguridad, seguridad y privacidad de grado empresarial

#### GitHub Copilot Enterprise

Está disponible para organizaciones a través de GitHub Enterprise Cloud.

* Póngase en marcha rápidamente en el código base.
* Busque y compile documentación.
* Obtenga sugerencias basadas en código interno y privado.
* Revise rápidamente las solicitudes de incorporación de cambios.

Incluye todo en GitHub Copilot Business, además de una capa de personalización para organizaciones. Proporciona integración en GitHub como una interfaz de chat, por lo que los desarrolladores pueden hablar sobre su código base. También proporciona botones de acción en toda la plataforma. Puede indexar el código base de una organización para obtener una comprensión más profunda y para sugerencias más adaptadas. Ofrece acceso a la personalización de GitHub Copilot para ajustar los modelos privados para la finalización del código.

## Interacción con Copilot

### Sugerencias en línea

Las sugerencias insertadas son la forma más inmediata de asistencia de Copilot. A medida que escribe, Copilot analiza el código y el contexto para ofrecer finalizaciones de código en tiempo real. 

* Para aceptar una sugerencia, seleccione la tecla *Tab* o la tecla *>* (flecha derecha).
* Para rechazar una sugerencia, siga escribiendo o seleccione la tecla *Esc*.

Las sugerencias insertadas son especialmente útiles cuando se trabaja en tareas repetitivas o se necesita código reutilizable rápido.

        def calculate_average(numbers):
        # Start typing here and watch Copilot suggest the function body

### Paleta de comandos

La paleta de comandos proporciona acceso rápido a las diversas funciones de Copilot, para que pueda realizar tareas complejas solo con algunas pulsaciones de tecla.

1. Abra la paleta de comandos seleccionando Ctrl+Shift+P (Windows o Linux) o Cmd+Shift+P (Mac).
2. Escriba Copilot para ver los comandos disponibles.
3. Seleccione acciones como Explica esto o Genera pruebas unitarias para obtener ayuda.

### Chat de Copilot

Es una característica interactiva que le permite comunicarse con Copilot mediante lenguaje natural. Puede formular preguntas o solicitar fragmentos de código y Copilot proporciona respuestas en función de la entrada.

1. Abra el panel de chat de Copilot en el IDE.
2. Escriba preguntas o solicitudes en lenguaje natural y, a continuación, evalúe la respuesta de Copilot.

### Chat insertado

El chat en línea habilita conversaciones específicas del contexto con Copilot directamente en el editor de código. Puede usar esta característica para solicitar modificaciones de código o explicaciones sin cambiar de contexto.

1. Coloque el cursor donde quiera ayuda.
2. Use el método abreviado de teclado Ctrl+I (Windows o Linux) o Cmd+I (Mac) para abrir el chat en línea.
3. Formule preguntas o solicite cambios específicos de esa ubicación de código.

### Comentarios al código

Copilot usa el procesamiento de lenguaje natural para convertir comentarios en código. Puede describir la funcionalidad que desea en un comentario. Al seleccionar la tecla Enter, Copilot genera código en función de la descripción.

        # Function to reverse a string
        def reverse_string(s):
            # Copilot suggests the function body here

Con GitHub Copilot:

        // Function to reverse a string
        def reverse_string(s):
            return s[::-1]

### Sugerencias múltiples

Para fragmentos de código complejos, Copilot puede ofrecer varias alternativas.

1. Cuando Copilot ofrece una sugerencia, busque el icono de bombilla.
2. Seleccione el icono o use *Alt+]* (Windows/Linux) o *Option+]* (Mac) para recorrer alternativas.

### Explicaciones

Comprender el código existente es fundamental, especialmente en proyectos grandes. Puede usar la característica Explica esto para obtener explicaciones de fragmentos de código.

1. Seleccione un bloque de código.
2. Haga clic con el botón derecho en el bloque de código y seleccione Copilot: Explica esto en el menú contextual.
3. Lea la explicación que Copilot proporciona para el código seleccionado.

### Generación de pruebas automatizada

Las pruebas unitarias son esenciales para garantizar la calidad y confiabilidad del código. Copilot puede ahorrarle tiempo y esfuerzo mediante la generación de pruebas unitarias para sus funciones o clases.

1. Seleccione una función o clase.
2. Use la paleta de comandos para elegir Copilot: Genera pruebas unitarias.
3. Revise los casos de prueba que Copilot sugiere para el código.

La generación automatizada de pruebas le ayuda a mantener la integridad del código y a detectar errores al principio del proceso de desarrollo.

Tenga en cuenta que Copilot aprende del contexto. Mantener el código bien estructurado y comentado ayuda a Copilot a proporcionar asistencia más precisa y relevante. Cuanto más interactúe con Copilot, mejor se convierte en comprender el estilo y las preferencias de codificación.

## Instalación, configuración y solución de problemas de GitHub Copilot

### Registro en GitHub Copilot

Es preciso configurar una evaluación gratuita o una suscripción para tu cuenta. Seleccione la foto de perfil de GitHub y, a continuación, seleccione **Configuración**. Copilot está en el menú de la izquierda en Código, **planeamiento** y **automatización**. Posteriormente, debe instalar una extensión para su entorno preferido. GitHub Copilot admite GitHub.com (que no necesita ninguna extensión), VS Code, Visual Studio, los entornos de desarrollo integrado de JetBrains y Neovim como una extensión discreta.

### Configurar GitHub Copilot en VS Code

#### Agregar la extensión de VS Code para GitHub Copilot

1. En Visual Studio Marketplace, vaya a la página de la extensión de GitHub Copilot y seleccione Instalar.
2. Un cuadro de diálogo emergente le pide que abra VS Code. Seleccione Open (Abrir).
3. En VS Code, en la pestaña Extensión: GitHub Copilot, seleccione Instalar.
4. Si no autorizó previamente VS Code en su cuenta de GitHub, se le pedirá que inicie sesión en GitHub en VS Code. Seleccione Iniciar sesión en GitHub.

#### Habilitar o deshabilitar GitHub Copilot en VS Code

1. En el panel inferior de la ventana de VS Code, seleccione el icono de estado y, a continuación, seleccione Habilitar o Deshabilitar.

2. Al deshabilitar GitHub Copilot, VS Code pregunta si desea deshabilitar las finalizaciones globalmente o para el idioma del archivo que está editando actualmente.

* Para deshabilitar las finalizaciones de GitHub Copilot globalmente, seleccione Deshabilitar finalizaciones.
* Para deshabilitar las finalizaciones de GitHub Copilot para un idioma especificado, seleccione Deshabilitar finalizaciones para LANGUAGE.

#### Habilitación o deshabilitación de sugerencias insertadas en VS Code

1. En el menú Archivo, seleccione **Preferencias**>**Configuración**.
2. En el panel izquierdo de la pestaña Configuración, seleccione **Extensiones** y, después, seleccione **GitHub Copilot**.
3. En **Editor: Habilite las finalizaciones automáticas**, seleccione o borre la casilla para habilitar o deshabilitar sugerencias insertadas.

### Solucione problemas de GitHub Copilot en VS Code

En VS Code, los archivos de registro son útiles para diagnosticar problemas de conexión. La extensión GitHub Copilot almacena los archivos de registro en la ubicación de registro estándar para las extensiones de VS Code. Puede encontrar los archivos de registro abriendo la paleta de comandos y, después, escribiendo **Desarrollador: Abrir el archivo de registro o Desarrollador: Abrir la carpeta Registros de extensiones**.

Es posible que los errores no se registren en las ubicaciones normales. Si encuentra errores y nada está en los registros, puede intentar ver los registros del proceso que ejecuta VS Code y la extensión. Este proceso le permite ver los registros de Electron. Para encontrar estos registros, seleccione **Ayuda>Alternar Herramientas de desarrollo** en VS Code.

Las restricciones de red, los firewalls o el proxy pueden causar problemas al conectarse a GitHub Copilot. Si se produce un problema, siga estos pasos para abrir un nuevo editor con información pertinente que puede inspeccionar o compartir con el equipo de soporte técnico:

1. Abra la paleta de comandos de VS Code y, a continuación, haga lo siguiente:

* Para Mac, use Shift+Command+P.
* Para Windows o Linux, use Ctrl+Shift+P.

2. Escriba Diagnósticos y, a continuación, seleccione GitHub Copilot: Recopilar diagnósticos de la lista.