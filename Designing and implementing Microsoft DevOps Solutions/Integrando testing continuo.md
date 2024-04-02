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

### Deuda técnica

La deuda técnica es un termino que describe el coste futuro de sacrificar la calidad del código for algo diferente. El término deuda implica que se debe algo (tiempo, calidad, atención o trabajo) a la solución. Mientas la deuda no sea saldada, tienes que pagar en la forma de que todos los trabajos se relanticen un poco.

La deuda técnica puede tomar varias formas:

* Código que no esta cubierto por algún tests unitario donde los cambios para la implementación de dicho código no puede sr verificado usando tests originales que son usados para crearlos. 

* Código que no está escrito que se explique por si mismo usando variables y nombres de métodos significiativos.

* Código que no adhiere los principios de código como **KISS**, **YAGNI**, **DRY** y/o **SOLID**.

* Clases que son demasiado complejas por que tienen demasiadas variables y métodos.

* Métodos que son demasiado complejos porque tienen demasiados elementos.

* Clases o nombres de espacios que tienen dependencias circulares en diferentes partes de la aplicación.

* Clases que no adhieren el diseño arquitectónico de la aplicación.

Son varias formas de deuda te´cnica, y puede ser un desafio a supervisar. Existen algunas herramientas disponibles que pueden medir la deuda técnia en el código automaticamente e informarlo.

Mientas la deuda ténica es a menudo considerada cosa mala, hay buenas razones para crear deuda técnica a proposito. Es importante, gestionar la altura de la deuda y asegurar que se puede pagar los interses y que la deuda quede saldada.

Mientas la primera versión es usada para validar las proposiciones del negocio y atraer fondos, los desarrolladores pueden saldar la deuda reimplementando o refactorizando la aplicación.

Otra razón debe ser la oportunidad de mercado o un importante evento de negocio que ha sido planificado meses en anterioridad. Tomando algo de deuda técnica para llegar a los objetivos y entregar en tiempo puede valer la pena.

Sin embargo, nunca pagando la deuda y sólo tomando más deuda, incrementará la deuda en el tiempo que un desarrollador necesita para hacer un cambio. Si esto empieza a ocurrir es inevitable que en algún punto los cambios no valgan la pena realizarlos, debido a que el coste siempre superará los beneficios. 

## Entendiendo los tipos de tests

En el desarrollo tradicional de software, los tests son a menudo ejecutados cuando el desarrollo fue completado, la aplicación fue declarada *dev-done*, las carácteristicas fueron congeladas o en situaciones similares. Después de declarar el desarrollo está realizado, el testeo fue realizado y a menudo un largo periodo de ir y venir entre el testeo y la corrección de incidencias, se realiza el desplieuge. El resultado fue que a menudo algunas incidencias fueron encontradas después del despliegue.

*Shifting left* es un principio de pruebas que establece que las pruebas automatizadas deben realizarse en una etapa más temprana del proceso de desarollo. Si todas las actividades envueltas con el desarrollo son dibujadas en una línea desde el comienzo hasta la liberación, entonces *shifting left* indica acercar las actividades de prueba automatizadas al comienzo.

Para hacer esto, se reconoce una amplia selección de diferentes tipos de pruebas.

* **Pruebas funcionales**: son usadas para probar si la funcionalidad deseada es actualmente realizada por la aplicación.

* **Pruebas no funcionales**: son usadas para verificar si otras propiedades deseadas de la aplicación se realizan y que las propiedades no deseadas no están presentes. 

