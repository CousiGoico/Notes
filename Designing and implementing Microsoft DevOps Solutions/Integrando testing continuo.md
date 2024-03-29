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

Es dificil medir objetivamente la calidad del código escrito. Los desarrolladores a menudo tienen opiniones de lo que constituye un buen código, poniendo especial atención al resultado del código usado. Se trata de identificar métricas que pueden ayudar a proporcionar información sobre la calidad del código.

**Porcentaje de compilaciones de integración que fallan:** si el código no compila o pasa tests automáticos entonces esto es un undicador de que no tiene suficiente calidad. El resultado debe ser usado para cancelar un cambio de insuficiente calidad o que debe impactar en una funcionalidad del sistema antes de desplegarlo en la siguiente etapa o despliegue.

**El porcentaje del código cubierto por tests automáticos:** si una larga parte del código esta siendo testeado por tests unitarios, este incrementa la calidad del software.

**La tasa de fracaso del cambio:** este es el porcentaje  de despliegues de nuevas versiones del código que lidera problemas. El servidor web corre sin menmoria despues del despliegue de una nueva versión de la aplicación.

**El conjunto de trabajo sin planificar:** el conjunto de trabajo sin planificar que tiene que ser realizado en un periodod de tiempo puede ser una gran métrica de calidad. Si el trabajo no planificado incrementa, entonces esto debe ser porque la calidad va hacía abajo. Pueden ser incidencias en vivo, errores y parches.

**El número de defectos que son informados por usuarios:** si el número de errores resportados por los usuarios incrementa, esto puede ser signo que la calidad ha declinado. Puede ser otras razones para que el número incremente, como nuevo sistema operativo, un incremento en el número de usuarios, o cambiar las expectativas del usuario.

**El número de problemas conocidos:** inclusio si hay nuevos defectos que estan siendo reportados, si los defectos no son nunca corregidos y el número de incidencias conocidas se mantiene incrementando lentamente, entonces la calidad del software declina sobre el tiempo.

**El conjunto de deuda técnica:** es un termino usado para describir las consecuencias de sacrificar la calidad del software, en pocas palabras, entregar código rápido.

Testear es una actividad qeu es realizada para encontrar y reportar en la calidad del software. Los resultados de los tests pueden ser usados para permitir o cancelar un cambio progresivo de la siguiente etapa del despliegue.