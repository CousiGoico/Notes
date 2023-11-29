# Supervisión del rendimiento de la aplicación

La instrumentación y supervisión de las aplicaciones le permitirá maximizar su disponibilidad y rendimiento.

## Exploración de Application Insights

Application Insights es una extensión de Azure Monitor y proporciona características de Supervisión de rendimiento de aplicaciones (también conocida como "APM"). Las herramientas de APM son útiles para supervisar aplicaciones de desarrollo, pruebas y producción de las siguientes maneras:

+ De manera proactiva comprende cómo funciona una aplicación.
+ De manera reactiva revisa los datos de ejecución de la aplicación para determinar la causa de un incidente.

Además de recopilar métricas y datos de telemetría de las aplicaciones, que describen las actividades y el estado de la aplicación, Application Insights también se puede usar para recopilar y almacenar datos de registro de seguimiento de aplicaciones.

El seguimiento del registro está asociado a otros datos de telemetría para proporcionar una vista detallada de la actividad. Agregar registro de seguimiento a las aplicaciones existentes solo requiere proporcionar un destino para los registros; rara vez es necesario cambiar la plataforma de registro.

### Información general de características de Application Insights

|Característica|Descripción|
|--------------|-----------|
|Live Metrics|Observe la actividad de la aplicación implementada en tiempo real sin ningún efecto en el entorno de host.|
|Disponibilidad|También se conoce como "Supervisión de transacciones sintéticas"; sondee los puntos de conexión externos de las aplicaciones para probar la disponibilidad general y la capacidad de respuesta a lo largo del tiempo.|
|Integración de GitHub o Azure DevOps|Cree elementos de trabajo de GitHub o Azure DevOps en el contexto de los datos de Application Insights.|
|Uso|Conozca qué características son populares para los usuarios y cómo estos interactúan con la aplicación y la usan.|
|Detección inteligente|Detección automática de errores y anomalías mediante análisis de telemetría proactivos.|
|Mapa de aplicación|Vista de arriba abajo de alto nivel de la arquitectura de la aplicación y referencias visuales de un vistazo al estado y la capacidad de respuesta de los componentes.|
|Seguimiento distribuido|Busque y visualice un flujo de un extremo a otro de una ejecución o transacción determinada.|

### Qué supervisa Application Insights

Application Insights recopila datos de telemetría de aplicación y métricas, que describen las actividades y el estado de la aplicación, así como datos de registro de seguimiento.

+ __Tasas de solicitud, tiempos de respuesta y tasas de error__ - Averigüe qué páginas que son las más conocidas, en qué momento del día y dónde están los usuarios. Vea qué páginas presentan mejor rendimiento. Si los tiempos de respuesta y las tasas de error aumentan cuando hay más solicitudes, quizás tiene un problema de recursos.
+ __Tasas de dependencia, tiempos de respuesta y tasa de error__ - Averigüe si los servicios externos le ralentizan.
+ __Excepciones__ - Analice las estadísticas agregadas o seleccione instancias concretas y profundice en el seguimiento de la pila y las solicitudes relacionadas. Se notifican tanto las excepciones de servidor como las de explorador.
+ __Vistas de página y rendimiento de carga__ - Notificados por los exploradores de los usuarios.
+ __Llamadas AJAX desde páginas web__ - Tasas, tiempos de respuesta y tasas de error.
+ __Número de usuarios y sesiones.__
+ __Contadores de rendimiento__ de las máquinas de servidor de Windows o Linux, como CPU, memoria y uso de la red.
+ __Diagnóstico de host__ de Docker o Azure.
+ __Registros de seguimiento de diagnóstico de la aplicación__ - De esta forma puede correlacionar eventos de seguimiento con las solicitudes.
+ __Métricas y eventos personalizados__ que usted mismo escribe en el código de cliente o servidor para realizar un seguimiento de eventos empresariales, como artículos vendidos o partidas ganadas.

### Introducción a Application Insights

Application Insights es uno de los muchos servicios hospedados en Microsoft Azure y los datos de telemetría se envían ahí para analizarlos y mostrarlos. El registro es gratuito y, si elige el plan de precios básico de Application Insights, no habrá cargo alguno hasta que la aplicación tenga un uso considerable.

Hay varias maneras de empezar a supervisar y analizar el rendimiento de las aplicaciones:

+ __En tiempo de ejecución__: instrumente la aplicación web en el servidor. Ideal para las aplicaciones ya implementadas. Evita toda actualización del código.
+ __En tiempo de desarrollo__: agregue Application Insights al código. Le permite personalizar la recopilación de telemetría y enviar más telemetría.
+ __Instrumente sus páginas web__ para la vista de la página, AJAX y otros datos de telemetría del lado cliente.
+ __Analice el uso de aplicaciones móviles__ mediante la integración con Visual Studio App Center.
+ __Pruebas de disponibilidad__: haga ping a su sitio web de manera regular desde nuestros servidores.

## Detección de métricas basadas en registros

Las métricas basadas en registros de Application Insights le permiten analizar el estado de las aplicaciones supervisadas, crear paneles eficaces y configurar alertas. Existen dos tipos de métricas:

+ __Las métricas basadas en registros__ subyacentes se traducen en consultas de Kusto de eventos almacenados. Se agregan previamente durante la recopilación, mejor rendimiento en la consulta. Son una mejor opción para paneles y alertas en tiempo real.
+ __Las métricas estándar__ se almacenan como series temporales previamente agregadas. Tienen más dimensiones, lo que las convierte en una mejor opción para el análisis de datos y los diagnósticos adhoc. 

### Métricas basadas en registros

Los desarrolladores pueden usar el SDK para enviar eventos manualmente o pueden usar la recopilación automática de eventos de la instrumentación automática. El servidor back-end de Application Insights almacena todos los eventos recopilados como registros y las hojas de Application Insights en Azure Portal actúan como herramienta de análisis y diagnóstico para visualizar los datos basados en eventos de los registros.

El uso de registros para conservar un conjunto completo de eventos puede aportar gran valor al análisis y el diagnóstico. Recopilar un conjunto completo de eventos puede resultar poco práctico (o incluso imposible) en el caso de aplicaciones que generan un gran volumen de telemetría. En aquellos casos en los que el volumen de eventos sea demasiado alto, Application Insights implementa varias técnicas de reducción del volumen de datos de telemetría, tales como muestreo y filtrado, que reducen el número de eventos recopilados y almacenados.

### Métricas agregadas previamente

Las métricas agregadas previamente no se almacenan como eventos individuales con muchas propiedades. Sino que se almacenan como series temporales previamente agregadas y solo con las dimensiones clave. Como consecuencia, las nuevas métricas son superiores en tiempo de consulta: la recuperación de datos es mucho más rápida y requiere menos capacidad de proceso. Esto hace posible nuevos escenarios, como alertas casi en tiempo real sobre las dimensiones de las métricas, paneles con más capacidad de respuesta y muchos más.

> __INFO: Las métricas basadas en registros y las métricas agregadas previamente coexisten en Application Insights. Para diferenciar las dos, en la experiencia de usuario de Application Insights, las métricas agregadas previamente ahora se llaman "métricas estándar (versión preliminar)", mientras que el nombre de las métricas tradicionales de eventos ha cambiado a "métricas basadas en registros".__

Los SDK más recientes agregan previamente las métricas durante la recopilación. Esto aplica a las métricas estándar enviadas de forma predeterminada y a las métricas personalizadas enviadas mediante GetMetric.

En el caso de los SDK que no implementan la agregación previa, el servidor back-end de Application Insights agrega los eventos recibidos por el punto de conexión de recopilación de eventos de Application Insights para rellenar las nuevas métricas.

## Instrumentación de una aplicación para supervisión

Application Insights se habilita mediante la instrumentación automática (agente) o agregando el SDK de Application Insights al código de la aplicación.

### Instrumentación automática

No requiere ninguna inversión de desarrollador y elimina la sobrecarga futura relacionada con la actualización del SDK. También es la única manera de instrumentar una aplicación en la que no tiene acceso al código fuente. Es el método de instrumentación perferido.

### Habilitación mediant los SDK e Application Insights

Solo debe instalar el SDK de Application Insights en las siguientes circunstancias:

+ Necesita eventos y métricas personalizados.
+ Necesita control sobre el flujo de telemetría.
+ La instrumentación automática no está disponible.

Para usar el SDK, instale un pequeño paquete de instrumentación en la aplicación y, a continuación, instrumente la aplicación web, los componentes en segundo plano y JavaScript en las páginas web. La instrumentación supervisa la aplicación y dirige los datos de telemetría a un recurso de Application Insights mediante un token único.

Los SDK de Application Insights para .NET, .NET Core, Java, Node.js y JavaScript admiten el seguimiento distribuido de forma nativa.

Puede realizar un seguimiento manual de cualquier tecnología con una llamada a TrackDependency en TelemetryClient.

### Habilitación mediante OpenCensus

OpenCensus es una distribución de bibliotecas de código abierto e independiente del proveedor que proporciona recopilación de métricas y seguimiento distribuido para los servicios. También permite a la comunidad de código abierto habilitar el seguimiento distribuido con tecnologías conocidas como Redis, Memcached o MongoDB.

## Selección de una prueba de disponibilidad

Después de haber implementado la aplicación o el sitio web, puede configurar pruebas periódicas para supervisar la disponibilidad y capacidad de respuesta.

Puede configurar pruebas de disponibilidad para cualquier punto de conexión HTTP o HTTPS que sea accesible desde la red pública de Internet. No hace falta realizar cambios en el sitio web que está probando. De hecho, ni siquiera es necesario que sea un sitio de su propiedad. Puede probar la disponibilidad de una API de REST de la que depende su servicio.

Existen tres tipos de pruebas de disponibilidad:

+ [Prueba de ping de URL (clásica)](https://learn.microsoft.com/es-es/azure/azure-monitor/app/monitor-web-app-availability): Validar si un punto de conexión responde y medir el rendimiento asociado a esa respuesta. También puede establecer criterios de éxito personalizados junto con características más avanzadas, como analizar solicitudes dependientes y permitir reintentos.

+ [Prueba estándar (versión preliminar)](https://learn.microsoft.com/es-es/azure/azure-monitor/app/availability-standard-tests): es similar a la prueba de ping de URL. Incluye la validez del certificado SSL, la comprobación proactiva de la duración, el verbo de solicitud HTTP (por ejemplo, `GET`, `HEAD` o `POST`), los encabezados personalizados y los datos personalizados asociados a la solicitud HTTP.

+ [Prueba TrackAvailability personalizada](https://learn.microsoft.com/es-es/azure/azure-monitor/app/availability-azure-functions): si decide crear una aplicación personalizada para ejecutar pruebas de disponibilidad, puede usar el método TrackAvailability() para enviar los resultados a Application Insights.

> __NOTA: La prueba de varios pasos es el cuarto tipo de prueba de disponibilidad, pero solo está disponible hasta Visual Studio 2019. La prueba TrackAvailability personalizada es la solución admitida a largo plazo para escenarios de prueba de autenticación o de varias solicitudes.__

> __IMPORTANTE: La prueba de ping de direcciones URL se basa en la infraestructura DNS de la red pública de Internet para resolver los nombres de dominio de los puntos de conexión probados. Si usa DNS privado, debe asegurarse de que los servidores de nombres de dominio públicos puedan resolver todos los nombres de dominio de la prueba. Cuando esto no sea posible, puede usar pruebas TrackAvailability personalizadas en su lugar.__

## Solución de pblemas de rendimiento de aplicaciones mediante el Mapa de aplicación

El mapa de aplicación le ayuda a detectar los cuellos de botella en el rendimiento o las zonas activas con error en todos los componentes de la aplicación distribuida. Cada nodo del mapa representa un componente de aplicación o sus dependencias, e incluye el KPI de mantenimiento y el estado de alerta.

+ Los componentes son diferentes de las dependencias externas "observadas", como SQL, Event Hubs y otras, a las que su equipo u organización no pueden acceder (código o telemetría).
+ Los componentes se ejecutan en cualquier número de instancias de rol, servidor o contenedor.
+ Los componentes pueden ser claves de instrumentación de Application Insights independientes o diferentes roles que informan a una única clave de instrumentación de Application Insights. La experiencia de mapa de vista preliminar muestra los componentes independientemente de cómo se configuren.

Puede ver la topología de aplicación completa a lo largo de varios niveles de componentes de aplicación relacionados. Los componentes podrían ser diferentes recursos de Application Insights o distintos roles de un único recurso.

Si todos los componentes son roles dentro de un único recurso de Application Insights, este paso de detección no es necesario. 

![](https://learn.microsoft.com/es-es/training/wwl-azure/monitor-app-performance/media/application-map.png)

Uno de los objetivos principales de la experiencia es poder visualizar topologías complejas con cientos de componentes. Haga clic en cada componente para ver información detallada relacionada e ir a la experiencia de evaluación de prioridades de rendimiento y errores de ese componente.

![](https://learn.microsoft.com/es-es/training/wwl-azure/monitor-app-performance/media/application-map-component.png)

El mapa de aplicación usa la propiedad nombre de rol en la nube para identificar los componentes en el mapa. Puede establecer o invalidar manualmente el nombre del rol en la nube y cambiar lo que se muestra en el Mapa de aplicación.

