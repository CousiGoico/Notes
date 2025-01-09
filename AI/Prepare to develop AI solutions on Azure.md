# Prepare to develop AI solutions on Azure

## Definir la inteligencia artificial

La inteligencia artificial es como un software que presenta una o varias funcionalidades "humanas".

|Capacidad|Descripción|
|---------|-----------|
|Percepción visual|Capacidad de usar funcionalidades de Computer Vision para aceptar, interpretar y procesar la entrada de imágenes, secuencias de vídeo y cámaras en directo.|
|Análisis de texto y conversación|Capacidad de usar el procesamiento de lenguaje natural (NLP) no solo para "leer", sino también para generar respuestas realistas y extraer el significado semántico del texto.|
|Voz|Capacidad de reconocer la voz como entrada y sintetizar la salida hablada. La combinación de funcionalidades de voz junto con la capacidad de aplicar análisis de NLP de texto permite una forma de interacción de proceso humano que se conoce como IA conversacional, en la que los usuarios pueden interactuar con agentes de inteligencia artificial (normalmente denominados bots) de la misma manera que harían con otra persona.|
|Toma de decisiones|Capacidad de usar la experiencia pasada y las correlaciones aprendidas para evaluar situaciones y tomar las medidas adecuadas. Por ejemplo, el reconocimiento de anomalías en las lecturas del sensor y la adopción de medidas automatizadas para evitar errores o daños en el sistema.|

## Comprender los términos relacionados con la inteligencia artificial

### Ciencia de datos

Es un campo insertivo que se centra en el procesamiento y el análisis de datos; aplicar técnicas estadísticas para descubrir y visualizar relaciones y patrones en los datos, y definir modelos experimentales que ayudan a explorar esos patrones.

### Machine Learning

Los científicos de datos suelen trabajar con modelos de aprendizaje automático. El aprendizaje automático trata el entrenamiento y la validación de modelos predictivos. Normalmente, un científico de datos prepara los datos y, a continuación, los usa para entrenar un modelo basado en un algoritmo que aprovecha las relaciones entre las características de los datos para predecir valores para etiquetas desconocidas.

### Inteligencia artificial

La inteligencia artificial (IA) describe el software que emula una o varias características de la inteligencia humana. El aprendizaje automático es un enfoque destacado que se usa para crear software de inteligencia artificial. El conocimiento de la ciencia de datos puede admitir una comprensión de la inteligencia artificial.

## Comprender las consideraciones de los ingenieros de IA

Los ingenieros de software pueden aplicar sus conocimientos sobre programación, pruebas, trabajo con sistemas de control de código fuente y empaquetado de aplicaciones para la implementación, sin tener que convertirse en científicos de datos o expertos en aprendizaje automático.

### Entrenamiento e inferencia de modelos

Muchos sistemas de inteligencia artificial se basan en modelos predictivos que deben entrenarse con datos de ejemplo. El proceso de entrenamiento analiza los datos y determina las relaciones entre las características de los datos (los valores de datos que generalmente estarán presentes en las nuevas observaciones) y la etiqueta (el valor para cuya predicción se entrena el modelo).

Una vez entrenado el modelo, puede enviar nuevos datos que incluyan valores de características conocidos y hacer que el modelo prediga la etiqueta más probable. El uso del modelo para realizar predicciones se conoce como inferencia.

### Puntuaciones de probabilidad y confianza

Un modelo de Machine Learning bien entrenado puede ser preciso, pero ningún modelo predictivo es infalible. Las predicciones realizadas por los modelos de Machine Learning se basan en la probabilidad y, aunque los ingenieros de software no requieren una comprensión matemática profunda de la teoría de la probabilidad, es importante comprender que las predicciones reflejan una probabilidad estadística, no una verdad absoluta. En la mayoría de los casos, las predicciones tienen una puntuación de confianza asociada que refleja la probabilidad de realización de la predicción. Los desarrolladores de software deben usar los valores de puntuación de confianza para evaluar las predicciones y aplicar los umbrales adecuados para optimizar la confiabilidad de las aplicaciones y mitigar el riesgo de predicciones que se pueden realizar en función de las probabilidades marginales.

### Ética e inteligencia artificial responsables

Es importante tener en cuenta el impacto de su software en los usuarios y en la sociedad en general, incluyendo consideraciones éticas sobre su uso. Cuando la aplicación está imbuida de inteligencia artificial, estas consideraciones son especialmente importantes debido a la naturaleza del funcionamiento de los sistemas de inteligencia artificial y de cómo informan sobre las decisiones; a menudo se basan en modelos probabilísticos, que a su vez dependen de los datos con los que se entrenaron.

La posibilidad de daños a individuos o grupos a través de predicciones incorrectas o un uso incorrecto de las funcionalidades de inteligencia artificial es una problema importante, y los ingenieros de software que compilan soluciones habilitadas para inteligencia artificial deben aplicar la consideración adecuada para mitigar los riesgos y garantizar la equidad, la confiabilidad y la protección adecuada frente a daños o discriminación.

## Comprender las consideraciones para una IA responsable

### Imparcialidad

Los sistemas de IA deberían tratar a todas las personas de manera equitativa. La equidad de los sistemas de aprendizaje automático es un área muy activa de investigación en curso y existen algunas soluciones de software para evaluar, cuantificar y mitigar la parcialidad en los modelos de Machine Learning.  Tenga en cuenta la equidad desde el principio del proceso de desarrollo de aplicaciones, revisando cuidadosamente los datos de entrenamiento para asegurarse de que sean representativos de todas las personas a las que afecten potencialmente y evaluando el rendimiento predictivo de las subsecciones de la población de usuarios a lo largo del ciclo de vida de desarrollo.

### Confiabilidad y seguridad

Los sistemas de inteligencia artificial deben funcionar de manera confiable y segura. El desarrollo de aplicaciones de software basadas en inteligencia artificial debe someterse a rigurosos procesos de prueba y administración de implementaciones para garantizar que funcionen de la forma esperada antes de su lanzamiento. Los ingenieros de software deben tener en cuenta la naturaleza probabilística de los modelos de Machine Learning y aplicar los umbrales adecuados al evaluar las puntuaciones de confianza de las predicciones.

### Privacidad y seguridad

Los sistemas de inteligencia artificial deben ser seguros y respetar la privacidad. Los modelos de Machine Learning en los que se basan los sistemas de inteligencia artificial dependen de grandes volúmenes de datos, que pueden contener datos personales que deben mantenerse privados. Incluso después de entrenar los modelos y de que el sistema pase a producción, usan nuevos datos para hacer predicciones o tomar medidas relacionadas con preocupaciones relativas a la privacidad o la seguridad, por lo que se deberán aplicar las salvaguardias necesarias para proteger los datos y el contenido de los clientes.

### Inclusión

Los sistemas de inteligencia artificial deben empoderar a todos e involucrar a las personas. La inteligencia artificial debería aportar beneficios a todos los sectores de la sociedad, independientemente de su capacidad física, género, orientación sexual, origen étnico u otros factores.

### Transparencia

Los sistemas de inteligencia artificial deben ser comprensibles. Los usuarios deben ser plenamente conscientes del propósito del sistema, su funcionamiento y las limitaciones que se pueden esperar.

Cuando una aplicación de inteligencia artificial se basa en datos personales, como un sistema de reconocimiento facial que toma imágenes de personas para reconocerlas, debe dejar claro al usuario cómo se usan y conservan sus datos, y quién tiene acceso a ellos.

### Responsabilidad

Las personas deberían ser responsables de los sistemas de inteligencia artificial. Aunque muchos sistemas de inteligencia artificial parecen funcionar de forma autónoma, en última instancia, es responsabilidad de los desarrolladores que entrenaron y validaron los modelos que usan, y definieron la lógica que basa las decisiones en predicciones del modelo con el fin de garantizar que el sistema global cumpla los requisitos sobre responsabilidad. Para ayudar a cumplir este objetivo, los diseñadores y desarrolladores de soluciones basadas en IA deben trabajar dentro de un marco de gobernanza y principios de organización que garanticen que la solución cumpla con los estándares éticos y legales claramente definidos.

## Comprender las funcionalidades de Azure Machine Learning

Microsoft Azure proporciona el servicio Azure Machine Learning: una plataforma basada en la nube para ejecutar experimentos a gran escala para entrenar modelos predictivos a partir de datos y publicar los modelos entrenados como servicios.

Azure Machine Learning proporciona las siguientes características y funcionalidades:

|Característica|Funcionalidad|
|--------------|-------------|
|ML automatizado|Esta característica permite a los no expertos crear con rapidez un modelo de Machine Learning efectivo a partir de datos.|
|Diseñador de Azure Machine Learning|Una interfaz gráfica que permite el desarrollo sin código de soluciones de aprendizaje automático.|
|Administración de datos y procesos|Almacenamiento de datos basado en la nube y recursos de procesos que los científicos de datos profesionales pueden usar para ejecutar código de experimentos de datos a escala.|
|Canalizaciones|Los científicos de datos, ingenieros de software y profesionales de operaciones de TI pueden definir canalizaciones para organizar las tareas de entrenamiento, implementación y administración de modelos.|

Los científicos de datos pueden usar Azure Machine Learning a lo largo de todo el ciclo de vida de aprendizaje automático para:

* Ingerir y preparar los datos.
* Ejecutar experimentos para explorar datos y entrenar modelos predictivos.
* Implementar y administrar modelos entrenados como servicios web.

Los ingenieros de software pueden interactuar con Azure Machine Learning de las siguientes maneras:

* Usando el diseñador de Azure Machine Learning o ML automatizado para entrenar modelos de Machine Learning e implementarlos como servicios que se pueden integrar en aplicaciones habilitadas para inteligencia artificial.
* Colaboración con científicos de datos para implementar modelos basados en marcos comunes como Scikit-Learn, PyTorch y TensorFlow como servicios web y consumirlos en aplicaciones.
* Usando SDK de Azure Machine Learning o scripts de interfaz de la línea de comandos (CLI) para orquestar procesos DevOps que administran el control de versiones, la implementación y pruebas de modelos de Machine Learning como parte de una solución de entrega de aplicaciones general.

