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