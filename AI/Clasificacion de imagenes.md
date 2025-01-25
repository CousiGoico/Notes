# Clasificación de imagenes

## Aprovisionar recursos de Azure para Custom Vision de Azure AI

El servicio **Custom Vision de Azure AI** le permite crear sus propios modelos de Computer Vision para la clasificación de imágenes o la detección de objetos.

La creación de una solución de Custom Vision de Azure AI implica dos tareas:

1. El uso de imágenes existentes (etiquetadas) para entrenar un modelo de Custom Vision de Azure AI.
2. La creación de una aplicación cliente que envíe nuevas imágenes al modelo para generar predicciones.

Para usar el servicio Custom Vision de Azure AI, debe aprovisionar dos tipos de recursos de Azure

* Un recurso de entrenamiento (que se usa para entrenar los modelos). Puede ser:
    * Recurso de servicios múltiples de Servicios de Azure AI.
    * Un recurso de Custom Vision de Azure AI (entrenamiento).
* Un recurso de predicción, usado por las aplicaciones cliente para obtener predicciones del modelo. Puede ser:
    * Recurso de servicios múltiples de Servicios de Azure AI.
    * Un recurso de Custom Vision de Azure AI (predicción).

Puede utilizar un recurso de Servicios de Azure AI multiservicio tanto para el entrenamiento como para la predicción, y puede mezclar y combinar tipos de recursos para entrenar un modelo que después publicará utilizando un recurso de (**Servicios de Azure AI multiservicio**). Si usa un recurso de varios servicios, la clave y el punto de conexión para el entrenamiento y la predicción serán los mismos

## Comprender la clasificación de imágenes

La *clasificación de imágenes* es una técnica de Computer Vision en la que se entrena un modelo para predecir una etiqueta de clase para una imagen en función de su contenido. Normalmente, la etiqueta de clase se relaciona con el asunto principal de la imagen.

Los modelos se pueden entrenar para la clasificación multiclase o clasificación multietiqueta.

## Entrenar un clasificador de imágenes

Para entrenar un modelo de clasificación de imágenes con el servicio Custom Vision de Azure AI, puede usar el portal de Custom Vision de Azure AI, la API de REST o el SDK de Custom Vision o una combinación de ambos enfoques.

En la mayoría de los casos, normalmente usará el portal de Custom Vision de Azure AI para entrenar el modelo.

El portal proporciona una interfaz gráfica que puede usar para hacer lo siguiente:

1. Crear un proyecto de clasificación de imágenes para el modelo y asociarlo a un recurso de entrenamiento.
2. Cargar imágenes, asignándoles etiquetas de clase.
3. Revisar y editar imágenes etiquetadas.
4. Entrenar y evaluar un modelo de clasificación.
5. Probar un modelo entrenado.
6. Publicar un modelo entrenado en un recurso de predicción.

La API de REST y los SDK permiten realizar las mismas tareas escribiendo código, lo que resulta útil si necesita automatizar el entrenamiento y la publicación de modelos como parte de un proceso DevOps.

