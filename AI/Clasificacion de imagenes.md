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