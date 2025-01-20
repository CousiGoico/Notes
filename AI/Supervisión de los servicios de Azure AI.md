# Supervisión de los servicios de Azure AI

## Supervisión del costo

Una de las principales ventajas de usar servicios en la nube es que puede obtener rentabilidad al pagar por los servicios únicamente a medida que los usa. Algunos recursos de los servicios de Azure AI ofrecen un nivel gratuito con restricciones de uso, que resulta útil para trabajos de desarrollo y pruebas, así como uno o varios niveles de pago que generan cargos por las transacciones. La tarifa de facturación específica depende del tipo de recurso.

### Planificación de costes de los servicios de inteligencia artificial

Para estimar los costes de los servicios de inteligencia artificial con la calculadora de precios, cree un nuevo presupuesto y seleccione servicios de Azure AI en la categoría IA y Machine Learning. A continuación, seleccione la API de servicio de inteligencia artificial específica que tiene previsto usar (por ejemplo, Text Analytics de Azure AI), la región donde planea aprovisionarla y el plan de tarifa de la instancia que planea usar, y rellene las métricas de uso previstas y la opción de soporte técnico. Para crear un presupuesto que incluya varias API de servicios de inteligencia artificial, agregue más productos de los servicios de Azure AI al presupuesto.

### Visualización de costes de los servicios de inteligencia artificial

Al igual que ocurre con otros recursos de Azure, puede ver los detalles de los costes acumulados por los recursos de los servicios de inteligencia artificial en Azure Portal.

Para ver los costes de los servicios de inteligencia artificial, inicie sesión en Azure Portal y seleccione su suscripción. A continuación, seleccione la pestaña Análisis de costos para visualizar los costes generales de la suscripción. Para visualizar únicamente los costos de los servicios de inteligencia artificial, agregue un filtro que restrinja los datos para reflejar los recursos con un nombre de servicio de Servicios de Azure AI.

> [!NOTE]
> Para obtener más información, consulte [Planeamiento y administración de los costes de los servicios de Azure AI](https://learn.microsoft.com/es-es/azure/ai-services/plan-manage-costs) en la documentación de los servicios de inteligencia artificial.

## Creación de alertas

Microsoft Azure proporciona funcionalidad de alertas para los recursos mediante la creación de reglas de alertas. Las reglas de alertas se usan para configurar notificaciones y alertas para los recursos en función de eventos o umbrales de métricas. Estas alertas garantizarán que el equipo apropiado sepa cuándo surge un problema.

### Reglas de alertas

Para crear una regla de alertas para un recurso de los servicios de Azure AI, seleccione el recurso en Azure Portal y, en la ficha Alertas, agregue una nueva regla de alertas. Para definir la regla de alertas, debe especificar lo siguiente:

* Ámbito de la regla de alertas, es decir, el recurso que desea supervisar.
* Condición en la que se desencadena la alerta. El desencadenador específico de la alerta se basa en un tipo de señal, que puede ser Registro de actividad (entrada en el registro de actividad creado por una acción realizada en el recurso, como regenerar sus claves de suscripción) o Métrica (umbral de una métrica, como el número de errores superior a 10 en una hora).
* Acciones opcionales, como enviar un correo electrónico a un administrador para notificarle la alerta o ejecutar una aplicación lógica de Azure para solucionar el problema automáticamente.
* Detalles de la regla de alertas, como un nombre para la regla y el grupo de recursos en el que se debe definir.

> [!TIP]
> [Información general sobre las alertas en Microsoft Azure](https://learn.microsoft.com/es-es/azure/azure-monitor/alerts/alerts-overview)

## Visualización de métricas

Azure Monitor recopila métricas de los recursos de Azure a intervalos regulares para que pueda realizar un seguimiento de los indicadores de uso, estado y rendimiento de los recursos. Las métricas específicas recopiladas dependen del recurso de Azure. En el caso de los servicios de Azure AI, Azure Monitor recopila métricas relacionadas con las solicitudes de punto de conexión, los datos enviados y devueltos, los errores y otras medidas útiles.

### Visualización de métricas en Azure Portal

Para ver las métricas de un recurso concreto en Azure Portal, seleccione el recurso y vea su página Métricas. En esta página, puede agregar métricas específicas del recurso a los gráficos. De forma predeterminada, se crea un gráfico vacío y puede agregar más gráficos según sea necesario.

Puede agregar varias métricas a un gráfico y elegir agregaciones y tipos de gráfico adecuados. Cuando esté satisfecho con el gráfico, puede compartirlo exportándolo a Excel o copiando un vínculo a él. También puede clonarlo para crear un duplicado en la página Métricas, quizá como punto de partida para un nuevo gráfico que muestre las mismas métricas de una manera diferente.

### Adición de métricas a un panel

Puede crear paneles que consten de varias visualizaciones de diferentes recursos de su entorno de Azure para ayudarlo a obtener una vista general del estado y el rendimiento de sus recursos de Azure.

Para crear un panel, seleccione Panel en el menú de Azure Portal (puede que la vista predeterminada ya esté establecida en un panel en lugar de en la página principal del portal). Desde ahí, puede agregar hasta 100 paneles con nombre para encapsular vistas de aspectos específicos de los servicios de Azure de los que desee realizar un seguimiento.

Puede agregar una gran variedad de iconos y otras visualizaciones a un panel y, cuando vea las métricas de un recurso específico en un gráfico, como ya hemos explicado, puede agregar el gráfico a un panel nuevo o que ya estuviera creado. En la siguiente imagen, se han agregado a un panel dos gráficos que muestran las métricas de un recurso de servicios de IA.

## Administrar registros de diagnóstico

El registro de diagnóstico permite capturar datos operativos muy completos de un recurso de los servicios de Azure AI que se pueden usar para analizar el uso de los servicios y solucionar problemas.

### Creación de recursos para el almacenamiento de registros de diagnóstico

Para capturar registros de diagnóstico de un recurso de los servicios de Azure AI, se necesita un destino para los datos de registro. En determinados casos, puede usar Azure Event Hubs como destino para los datos de registro. Azure Event Hubs le permite reenviar los datos a una solución de telemetría personalizada y conectarse directamente a algunas soluciones de terceros. Sin embargo, en la mayoría de los casos usará uno (o ambos) de los siguientes tipos de recursos dentro de la suscripción de Azure:

* Azure Log Analytics: servicio que permite consultar y visualizar datos de registro en Azure Portal.
* Azure Storage: almacén de datos basado en la nube que se puede usar para almacenar los archivos de registro (que se pueden exportar para analizarlos en otras herramientas según sea necesario).

Debe crear estos recursos antes de configurar el registro de diagnóstico para el recurso de los servicios de Azure AI. Si tiene previsto archivar los datos de registro en Azure Storage, cree la cuenta de Azure Storage en la misma región que la del recurso de los servicios de Azure AI.

### Configuración de diagnóstico

Una vez establecidos los destinos para los datos de registro, puede definir la configuración de diagnóstico para el recurso de los servicios de Azure AI. La configuración de diagnóstico se define en la página Configuración de diagnóstico de la hoja del recurso de los servicios de Azure AI en Azure Portal. Al agregar la configuración de diagnóstico, debe especificar lo siguiente:

* Nombre para la configuración de diagnóstico.
* Categorías de los datos de eventos de registro que desea capturar.
* Detalles de los destinos en los que desea almacenar los datos de registro.

### Visualización de datos de registro en Azure Log Analytics

El flujo de datos de diagnóstico hacia los destinos puede tardar una hora o más en comenzar, pero, una vez capturados los datos, puede verlos en el recurso de Azure Log Analytics mediante la ejecución de consultas.

> [!TIP]
> [Habilitación del registro de diagnóstico para los servicios de Azure AI](https://learn.microsoft.com/es-es/azure/ai-services/diagnostic-logging)