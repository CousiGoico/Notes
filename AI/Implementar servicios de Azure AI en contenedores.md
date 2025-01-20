# Implementar servicios de Azure AI en contenedores

Los contenedores permiten hospedar servicios de Azure AI de forma local o en Azure. La implementación de servicios de Azure AI en un contenedor local también reduce la latencia entre el servicio y los datos locales, lo que puede mejorar el rendimiento.

## Comprender los contenedores

Al implementar un servicio de software, debe hospedarse en un entorno que proporciona el hardware, el sistema operativo y los componentes de runtime de los que depende el servicio.

Servicios de Azure AI se proporciona como un servicio en la nube, en el que el software del servicio se hospeda en un centro de datos de Azure que proporciona los servicios en tiempo de ejecución, el sistema operativo y el hardware subyacentes. Sin embargo, también puede implementar algunos servicios de Azure AI en un contenedor, que encapsula los componentes de runtime necesarios y que, a su vez, se implementa en un host de contenedor que proporciona el sistema operativo y el hardware subyacentes.

### ¿Qué es un contenedor?

Un contenedor consta de una aplicación o servicio y los componentes de runtime necesarios para ejecutarlo, a la vez que abstrae el sistema operativo y el hardware subyacentes. Ventajas significativas:

* Los contenedores son portables entre hosts, que pueden ejecutar sistemas operativos diferentes o usar hardware diferente, lo que facilita el traslado de una aplicación y todas sus dependencias.
* Un único host de contenedor puede admitir varios contenedores aislados, cada uno con su propia configuración específica de runtime, lo que facilita la consolidación de varias aplicaciones que tienen requisitos de configuración diferentes.

Un contenedor se encapsula en una imagen de contenedor que define el software y la configuración que debe admitir. Las imágenes se pueden almacenar en un registro central, como Docker Hub, o bien puede mantener un conjunto de imágenes en su propio registro.

### Implementación de contenedores

Para usar un contenedor, normalmente se extrae la imagen de contenedor de un registro y se implementa en un host de contenedor, especificando los valores de configuración necesarios. El host de contenedor puede estar en la nube, en una red privada o en el equipo local. Por ejemplo:

* Un servidor de Docker*.
* Una instancia de Azure Container (ACI).
* Un clúster de Azure Kubernetes Service (AKS).

*Docker es una solución de código abierto para el desarrollo y la administración de contenedores que incluye un motor de servidor que puede usar para hospedar contenedores. Hay versiones del servidor de Docker para sistemas operativos comunes, incluidos Microsoft Windows y Linux*.

## Uso de los contenedores de los servicios de Azure AI

Hay imágenes de contenedor para los servicios de Azure AI en Microsoft Container Registry que puede usar para implementar un servicio de contenedor que encapsula una API de servicio individual de los servicios de Azure AI.

Para implementar y usar un contenedor de servicios de Azure AI, deben producirse las tres actividades siguientes:

1. La imagen de contenedor de la API específica de servicios de Azure AI que quiere usar se descarga e implementa en un host de contenedor, como un servidor de Docker local, una instancia de Azure Container (ACI) o Azure Kubernetes Service (AKS).
2. Las aplicaciones cliente envían datos al punto de conexión proporcionado por el servicio contenedorizado y recuperan los resultados tal como lo harían desde un recurso en la nube de servicios de Azure AI en Azure.
3. Periódicamente, las métricas de uso del servicio contenedorizado se envían a un recurso de servicios de Azure AI en Azure con el fin de calcular la facturación del servicio.

Incluso cuando se usa un contenedor, debe aprovisionar un recurso de servicios de Azure AI en Azure con fines de facturación. Las aplicaciones cliente envían sus solicitudes al servicio contenedorizado, lo que significa que los datos potencialmente confidenciales no se envían al punto de conexión de servicios de Azure AI en Azure, pero el contenedor debe poder conectarse al recurso de servicios de Azure AI en Azure periódicamente para enviar las métricas de uso para la facturación.

### Imágenes de contenedor de servicios de Azure AI

Cada contenedor proporciona un subconjunto de funcionalidades de servicios de Azure AI. La detección de idioma, la traducción y el análisis de sentimiento se encuentran en imágenes de contenedor independientes. 

#### Contenedores de idioma

Para el servicio de Lenguaje de Azure AI, las características principales se asignan a imágenes independientes:

|Característica|Imagen|
|--------------|------|
|Extracción de frases clave|mcr.microsoft.com/azure-cognitive-services/textanalytics/keyphrase|
|Detección de idiomas|mcr.microsoft.com/azure-cognitive-services/textanalytics/language|
|Análisis de sentimiento|mcr.microsoft.com/azure-cognitive-services/textanalytics/sentiment|
|Reconocimiento de entidades con nombre|mcr.microsoft.com/product/azure-cognitive-services/textanalytics/language/about|
|Text Analytics for Health|mcr.microsoft.com/product/azure-cognitive-services/textanalytics/healthcare/about|
|Traductor|mcr.microsoft.com/product/azure-cognitive-services/translator/text-translation/about|
|Resumen|mcr.microsoft.com/azure-cognitive-services/textanalytics/summarization|

> [!NOTE]
> El Análisis de sentimiento admite otros idiomas mediante la sustitución de en en la imagen por el código de idioma correcto.

#### Contenedores de Speech

|Característica|Imagen|
|--------------|------|
|Conversión de voz en texto|mcr.microsoft.com/product/azure-cognitive-services/speechservices/speech-to-text/about|
|Conversión de voz en texto personalizada|mcr.microsoft.com/product/azure-cognitive-services/speechservices/custom-speech-to-text/about|
|Texto a voz neuronal|mcr.microsoft.com/product/azure-cognitive-services/speechservices/neural-text-to-speech/about|
|Detección de idioma de Voz|mcr.microsoft.com/product/azure-cognitive-services/speechservices/language-detection/about|

#### Contenedores de Vision

|Característica|Imagen|
|--------------|------|
|Lectura de OCR|mcr.microsoft.com/product/azure-cognitive-services/vision/read/about|
|Análisis espacial|mcr.microsoft.com/product/azure-cognitive-services/vision/spatial-analysis/about|

Puede usar el comando pull de Docker para descargar imágenes de contenedores con el fin de trabajar con ellas directamente desde su máquina. Algunos de los contenedores están en un estado de versión preliminar pública "controlada" y debe solicitar explícitamente acceso para usarlos. De lo contrario, los contenedores estarán disponibles para que cualquier usuario pueda usarlos con su implementación de servicios de Azure AI.

### Configuración del contenedor de servicios de Azure AI

Al implementar una imagen de contenedor de servicios de Azure AI en un host, debe especificar tres ajustes.

|Configuración|Descripción|
|-------------|-----------|
|ApiKey|Clave de servicios de Azure AI implementado. Se usa para la facturación.|
|Facturación|URI del punto de conexión de servicios de Azure AI implementado. Se usa para la facturación.|
|CLUF|Valor de aceptación para indicar que acepta la licencia para el contenedor.|

### Consumo de servicios de Azure AI desde un contenedor

Una vez que el contenedor de servicios de Azure AI se ha implementado, las aplicaciones consumen del punto de conexión de los servicios de Azure AI contenedorizados en lugar de utilizar el punto de conexión predeterminado de Azure. La aplicación cliente debe configurarse con el punto de conexión adecuado para el contenedor, pero no es necesario proporcionar una clave de suscripción para autenticarse. Puede implementar su propia solución de autenticación y aplicar restricciones de seguridad de red según corresponda para su escenario de aplicación específico.