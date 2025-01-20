# Creación y consumo de los servicios Azure AI

Servicios de Azure AI:

* Visión de Azure AI: análisis de contenido en imágenes y vídeos.
* Lenguaje de Azure AI: crear aplicaciones con funcionalidades de comprensión del lenguaje natural líderes del sector.
* Voz de Azure AI: conversión de voz a texto, texto a voz, traducción y reconocimiento del hablante.
* Inteligencia de documentos de Azure AI: una solución de reconocimiento óptico de caracteres (OCR) que puede extraer el significado semántico de formularios como facturas, recibos, etc.
* Búsqueda de Azure AI: una solución de búsqueda de escalado en la nube que usa servicios de inteligencia artificial para extraer información de datos y documentos.
* Azure OpenAI: un servicio de Azure que proporciona acceso a las funcionalidades de OpenAI GPT-4.

## Aprovisionamiento de un recurso de servicios de Azure AI

Los servicios de Azure AI incluyen una amplia gama de funcionalidades de inteligencia artificial que puede usar en sus aplicaciones. Para usar cualquiera de los servicios de Azure AI, debe crear los recursos adecuados en una suscripción de Azure para definir un punto de conexión en el que se pueda consumir el servicio, proporcionar claves de acceso para el acceso autenticado y administrar la facturación del uso del servicio por parte de la aplicación.

### Opciones de los recursos de Azure

#### Recurso de varios servicios

Puede aprovisionar un recurso de Servicios de AI que admita varios servicios de IA diferentes. Este enfoque le permite administrar un único conjunto de credenciales de acceso para consumir varios servicios en un único punto de conexión y con un único punto de facturación para el uso de todos los servicios.

#### Recurso de un único servicio

Cada servicio de Servicios de AI se puede aprovisionar individualmente. Este enfoque le permite usar puntos de conexión independientes para cada servicio y administrar las credenciales de acceso para cada servicio de forma independiente. También permite administrar la facturación por separado para cada servicio.

Los recursos de un solo servicio ofrecen un nivel gratuito, lo que los convierte en una buena opción para probar un servicio antes de usarlo en una aplicación de producción.

### Recursos de entrenamiento y predicción

Aunque la mayoría de los servicios de IA se pueden usar a través de un único recurso de Azure, algunos ofrecen (o requieren) recursos independientes para el entrenamiento y la predicción de modelos. Esto le permite administrar la facturación para el entrenamiento de modelos personalizados de forma separada del consumo de modelos por parte de las aplicaciones, y en la mayoría de los casos le permite utilizar un recurso específico del servicio dedicado para entrenar un modelo, pero un recurso genérico de servicios de IA para que el modelo esté disponible para las aplicaciones con fines de inferencia.