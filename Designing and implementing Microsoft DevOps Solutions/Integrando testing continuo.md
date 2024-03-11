# Integrando testing continuo

## Definiendo calidad

Uno de los primeros objetivos de DevOps es incrementar el flujo de valor del usuario final. Para hacer despliegues más frecuentes, dos cosas son importantes: automatización y calidad. 

Es el momento de empezar a medir la calidad de los cambios. Esto permite abortar cambios que no tienen la suficente calidad.

En software, alta calidada es más caro y/o toma más tiempo. Es una compensación entre el número de caracteristicas que puedes desplegar y la calidad que puede ser garantizada.

Es importante que primero establezcas como medir la calidad del software. Un enfoque común para monitorizar la calidad del software es reunir una o más métricas. Creando graficos de esas métricas sobre el tiepo provee ideas de como la calidad del software ha ido evolucionando.

### Métricas de calidad

Las métricas son un significado de capturar algo que es medido como un número. Las métricas a menudo son usadas para representar una calidad particular que puedes ser duro para cuantificarlo. La calidad  de una pieza de software puede ser muy duro de describirla.

Es importante para realizar esas métricas que sean una buena herramienta pero deben ser siempre usadas con precaución. Puede haber más factores que influyan en la calidad del software que las métricas que se miden. Si bien esto podría mostrar los números deseados en los informes, no necesariamente significa que la calidad del software esté mejorando realmente.

Registrar la velocidad del sprint para que el equipo vea si se vuelve más eficiente con el tiempo suena efectivo; Si el tamaño del equipo varía de un sprint a otro, entonces la métrica podría ser inútil ya que la asistencia influye en la velocidad cada semana. La métrica puede ser fácilmente falsificada si un equipo acuerda multiplicar todas las estimaciones por un número aleatorio en cada sprint.