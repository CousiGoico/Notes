# Análisis de imagenes

## Aprovisionar un recurso de Visión de Azure AI

El servicio Visión de Azure AI está diseñado para ayudarle a extraer información de las imágenes. Proporciona funcionalidad que puede usar para:

* Descripción y generación de etiquetas: determinación de un título adecuado para una imagen e identificar las "etiquetas" pertinentes que se pueden usar como palabras clave para indicar su asunto.
* Detección de objetos: detección de la presencia y ubicación de objetos específicos dentro de la imagen.
* Detección de caras: detección de la presencia, la ubicación y las características de las personas de la imagen.
* Análisis de metadatos, colores y tipos de imagen: determinación del formato y el tamaño de una imagen, su paleta de colores dominante y si contiene imágenes prediseñadas.
* Identificación de la categoría: identificación de una categorización adecuada para la imagen, y si contiene algún lugar de referencia conocido.
* Eliminación del fondo: detección del fondo de una imagen y salida de la imagen con el fondo transparente o una imagen mate alfa de escala de grises.
* Clasificación de moderación: determinación de si la imagen incluye contenido para adultos o violento.
* Reconocimiento óptico de caracteres: lectura del texto de la imagen.
* Generación de miniaturas inteligentes: identificación de la región de interés principal en la imagen para crear una versión más pequeña en "miniatura".

Puede aprovisionar Visión de Azure AI como un recurso de servicio único, o bien puede usar la API de Visión de Azure AI en un recurso de varios servicios de Servicios de Azure AI.

[Lectura de texto en imágenes y documentos con el servicio Visión de Azure AI](https://learn.microsoft.com/es-es/training/modules/read-text-images-documents-with-computer-vision-service/)

## Análisis de una imagen

Para analizar una imagen, puede usar el método REST de **Analyze Image** o el método equivalente en el SDK para su lenguaje de programación preferido, especificando las características visuales que quiere incluir en el análisis (y si selecciona categorías, si quiere incluir o no los detalles de celebridades o puntos de referencia). Este método devuelve un documento JSON que contiene la información solicitada.

> [!NOTE]
> La detección de celebridades requerirá obtener aprobación a través de una [directiva de acceso limitado](https://aka.ms/cog-services-limited-access). Puede obtener más información sobre la [agregación de esta directiva](https://azure.microsoft.com/blog/responsible-ai-investments-and-safeguards-for-facial-recognition/) a nuestro Estándar de inteligencia artificial responsable. El reconocimiento de celebridades se ve en algunas capturas de pantalla, pero no se incluye en el laboratorio.

        using Azure.AI.Vision.ImageAnalysis;

        ImageAnalysisClient client = new ImageAnalysisClient(
            Environment.GetEnvironmentVariable("ENDPOINT"),
            new AzureKeyCredential(Environment.GetEnvironmentVariable("KEY")));

        ImageAnalysisResult result = client.Analyze(
            new Uri("<url>"),
            VisualFeatures.Caption | VisualFeatures.Read,
            new ImageAnalysisOptions { GenderNeutralCaption = true });

Las características visuales disponibles se incluyen en la enumeración `VisualFeatures`:

* VisualFeatures.Tags: Identifica etiquetas sobre la imagen, incluidos los objetos, los paisajes, la configuración y las acciones
* VisualFeatures.Objects: Devuelve el rectángulo de selección de cada objeto detectado
* VisualFeatures.Caption: Genera una leyenda de la imagen en lenguaje natural
* VisualFeatures.DenseCaptions: Genera leyendas más detalladas para los objetos detectados
* VisualFeatures.People: Devuelve el rectángulo de selección para las personas detectadas
* VisualFeatures.SmartCrops: Devuelve el rectángulo de selección de la relación de aspecto especificada para el área de interés
* VisualFeatures.Read: Extrae texto legible

La especificación de las características visuales que desea analizar en la imagen determina qué información contendrá la respuesta. La mayoría de las respuestas contendrán un rectángulo de selección (si una ubicación de la imagen es razonable) o una puntuación de confianza (para características como etiquetas o subtítulos).

La respuesta JSON para el análisis de imágenes es similar a este ejemplo, en función de las características solicitadas:

        {
            "apim-request-id": "abcde-1234-5678-9012-f1g2h3i4j5k6",
            "modelVersion": "<version>",
            "denseCaptionsResult": {
                "values": [
                {
                    "text": "a house in the woods",
                    "confidence": 0.7055229544639587,
                    "boundingBox": {
                    "x": 0,
                    "y": 0,
                    "w": 640,
                    "h": 640
                    }
                },
                {
                    "text": "a trailer with a door and windows",
                    "confidence": 0.6675070524215698,
                    "boundingBox": {
                    "x": 214,
                    "y": 434,
                    "w": 154,
                    "h": 108
                    }
                }
                ]
            },
            "metadata": {
                "width": 640,
                "height": 640
            }
        }

