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

