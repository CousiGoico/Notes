# Tratando con base de datos en DevOps

## Gestionando el esquema de base de datos como código

ORM (**Object-relational mapper**) fue introducido para rellenar el desajuste entre la programación orientada a objectos y el esquema relacional de base de datos, que trabaja con tablas. Algunos ejemplos son NHibernate y Entity Framework.

Los ORMs proveen una capa de abstracción que permite el almacenamiento y recuperación de objetos desde la base de datos sin preocuparse de la estructura de la tabla. Para realizar el mapeo automatizado los ORMs a menudo tienen capacidades de compilación para desribir el esquema de base de datos, el modelo de objetos correspondiente y el mapa entre ellos en un lenguaje de marcado. Elllos pueden generar desde un modelo de objetos o una base de datos existente y el mapeo entre ellos, mediante convenciones, generados o pintados en un editor visual.

Para gestionar los cambios del esquema como código, hay dos enforques disponibles. El primero describe cada cambio en código (*basado en migraciones*); el otro describe sólo la última versión del esquema en código (*basado en el estado*). Ambos pueden confirar en heramientas de terceras partes para aplicar los cambios a la base de datos.

### Migrations

El primer enfoque es basado en mantener un ordenado conjunto de cambios que tienene que ser aplicados en la base de datos. Las **migraciones** pueden ser generadsas por herramientas tales como Microsoft Entity Framework o Redgate SQL Change Automation, o ellos pueden ser escritos a mano.

Las herramientas pueden automaticamente generar el script de la migración basada en la comparación del actual esquema y del nuevo esquema en el control de versiones. A esto se le llama **scaffolding**. Los scripts generdos por las herramientas no siempre son perfectos, y ellos tiene que ser mejorados aplicando el cónocimiento que el programador tiene.

![Figure9.1](Figure9.1.png)

Las etiquetas **m1** a la **m4** describen los cambios incrementales. Para modificar la base de datos a la última versión, la última migración aplicada es determinante y todas las migraciones posteriores que son añadadidas una después de otra.

Cuando edistas las migaciones a mano debes mantener en mente:

* La migración debe ser ordenada. Ddscriben las sentencias SQL que necesita ser ejecutadas en orden. La siguiente migración puede ser iniciada sólo cuando esta estapa este completada.

* Debe migrar no sólo el esquema también los datos. Esto puede significar que varias etapaas son necesarias entre migraciaciones.

* Indices extra y restricciones deben ser aplicadas no sólo en la base de producción. Asegurar que los indices y las restricciones son aplicadas en el mismo orden y no pueden bloquear migraciones existiendo sólo en proudcción.

* La migración debe ser realizada idempotente. El retorno de la última migración es una gran manera de asegurarse que está totalmente aplicada.

Una desventaja de este enfoque es el estricto orden requerido que es impuesto en la generación y aplicación de migraciones generadas. Esto hace duro la integración de este enfoque en el dessarrollo del workflow que dependende duramente del uso de ramas.

Las migraciones creadas en diferentes ramas que son mergeadas juntas sólo la última debe romper el orden de las migraciones o, peor aún mergear una separación en la ruta de la migración. La única manera de que el error pueda ser corregido es realizarlo en varias etapas:

1. Eliminar todas las migracaciones a partir de la nueva.

2. Aplicar todas las otras migraciones a labase de datos que no tiene nuevas migraciones aplicadas.

3. Generar nueva migración para las otras migraciones.

Una ventaja de este enfoque es que cada individual esquema puede ser desplegado contra la base de datos en la misma manera. Ello ejecutará aún una por una en un predecible orden y en la misma manera en el que ellos corrieron contra el entorno de etests, incluso si ellos son aplicados uno por uno.

### Estado final

A diferencia del enfoque de gestionar cambios del esquema, este no mantiene la traza de los cambios individuales, sólo almacena la última versión del esquema en el control de versiones. Herramientas externas como Microsoft VIsual Studio y Redgate's SQL Data Compare son usadas para comparar el actual esquema en el control de versiones con el actual esquema de base de datos, generando scrips de migración y aplicandolos cuando se ejecuta. Los scripts de migración no estan almacenados y son de un único uso.

A diferencia de escribir migraciones, no es factible eejcutar tareas a mano. Mientras tracenando la nueva versión del esquema a mano en el control de versiones puede ser gestionado, el mismo no es factible por el enfoque estado final. Generando scripts de migración mientras se compara lel esquema existente y el nuevo esquema y aplicando las migraciones solo puede ser hecho usando herramientas, tales como Redgate SQL Source Control y SQL Server Data Tools.

![Figure9.2](Figure9.2.png)

El esquema de la base de datos actual y la descripción de la base de datos deseada son comparadas para generar una mejora y directamente aplicar un script para hacer los camos necesarios para que el esquema actual sea el mismo que el esquema deseado.

Una ventaja de este enfoque es que no genera una serie de scripts que deben ser ejecutados en un orden especifico. Este enfoque combina fácilmente con ramas de esquemas donde los cambios son integrados más lentamente cada vez. También remueve la necesidada de escribir migraciones a mano para escenarios simples, tales como añadir o eliminar una columna, tabla o indice. 

La desventaja de este enfoque es que hace difícil gestionar los cambios que necesita las operaciones de datos. Desde las herramientas solo haces cumplir el nuevo esquema, esto dirige los datos perdidos y no hay intervención.

Una posible manaera de intervenir para evitar estar añadiendo scripts pre-despliegue y post-despliegue en el paquete de esquema, es que en el script de pre-despliegue se guadarse los datos en una tabla temporal. Después de aplicar el nuevo esquema los datos son compiados desde la tabla temporal a su nueva localización en el script post-despliegue.

## Aplicando cambios en el esquema de la base de datos

Cuando aplicas cambios al esquema de la base de datos, existen dos métodos para hacerlo. Cambios que pueden ser aplicados prioritariamente para desplegar en la nueva versión de la aplicación, o por el código proprio de la aplicación.

### Mejorando como parte de la release

El primer enfoque para aplicar cambios en la base de datos como parte de una release. Cuando esto es el caso, la herramienta que es la responsable de leer y ejecutar el script de migracion es invocada usando una tarea en la pipeline. 

Puede ser realizado usando un script personalizado en PowerShell o otro lenguaje de scripting. Esto es propenso a generar errores, y con cada cambio de la herramienta es un riesgo que los scripts necesiten ser modificados. La mayoría de las herramientas basadas en migraciones, como las tareas de Azure Pipelines que están disponibles para iniciar la migración desde la liberación (release).

Otra variación es separar entre las fases de la aplicación compilación y la liberación (release). Los scripts migración son exportados como un artefacto compilado separado, desde el código fuente o después de ejecutar una herramienta que genera el script SQL necesario. Este arttefacto es entonces descargado contra la fase de la libración (release) dde es aplicado para la baes de datos usando una tarea de Azure Pipelines para ejecutar SQL.

### Mejorando como parte del código de la aplicación

En cambio aplicando los cambios de esquema desde la pipeline de liberación (release), puede también ser aplicada por la aplicación propia. Algunos de los ORMs, con migraciones soportan la construcción, teniendo la capacidad automática de detectar si el esquema de la bse de datos coincide con la última migración. Si no, automáticamente migra el esquema a la última versión. 

La versión del framework no soporta migraciones automáticas. En Entity Framework Core, con una simple linea del código de la aplicación puede ser usada para iniciar una mejora en el tiempo que es conveniente desde la perspectiva de la aplicación.

        using (var context = new MyContext(...))
        {
            context.Database.Migrate();
        }

La ventaja de este enfoque es que es muy simple para habilitarlo. La desventaja es que más ORMs que soportan esto forzaran el bloqueo en la base de datos, parando todas las transacciones mientras las migraciones se ejecuten. 

Este enfoque es normalmente usado paramigraciones basadas en enfoques. El enfoque que usaun enfoque end-state requiere una herramienta externa de tercera parte que es usada para generar el script de migración necesario y aplicarlo. Esto es normalmente realizado por la pipeline de libración (release) y no envuelve la propia aplicación.

### Añadiendo un proceso

Es importante pensar sobre como y caundo los cambios de esquema en la base de datos o la aplicación que usa el esquema son aplicados. Como el despliegue del esquema y el código despliega son programados, siempre será un periodo donde uno de los siguientes es verdadero:

* El código de lan ueva aplicación esta lista de ejecutarse mientras el esquema no es aplicado todavía o está en le proceso de ser aplicado.

* El código de la aplicación antigua esta actualmente ejecutandose, mientras el esquema esta actualmente aplicado o esta en el proceso de ser aplicado.

* El código de la aplicación no esta ejecutandose, mientras el esquema esta siendo aplicado.

La tercera situación es altamente indeseable. Esto es verdadero en general, pero espeicialmente cuando practicas DevOps. Si los cambios son enviados a menudo y durante el horario laboral, no es aceptable deshabilitar la aplcación para cada cambio de esquema.

Para prevenir teniendo que deshabilitar la aplicación mientras el esquema es aplicado, uno de los siguientes requerimientos debe reunirse:

* El esquema es retro-compatible de tal manera que la vieja versión de la aplicación puede ejecutar sin errores contra la base de datos donde el esquema tiene los cambios aplicados o seran aplicados.

* La nueva aplicacón es retro-compatible de tal manera que si puede ejecutarse contra ambas la vieja y la nueva versión el esquema. 

Reuniendo el primero de esas condiciones aseguras qeu la vieja aplicacón puede continuar ejecutando mientras el esquema es siendo aplicado. Reuniendo el segundo de las condiciones aseguras que la nueva versión puede ser desplegada primero y una vez que este completada, la base de datos puede ser actaulizada con el código ejecutandose. La razón es que el esquema a menudos soporta los cambios de código. 

Esto significa quel siguiente es un proceso seguro para desplegar cambios de esquema sin deshabilitar la aplicación:

1. Creas una nueva base de datos.
2. Aplicas los cambios de la base de datos.
3. Verificas que los cambios han sido aplicados o abortas la pipeline de despliegue.
4. Desplieguas la nueva aplicación.

Esto es imporante para realizar que este proceso asuma los fallos para adelante. Esto significa que si se produce una incidnecia con el despliegue del esquema, serán reueltos antes de continuar con el despliegue. 

La condición de retro-compatiblidad para un cambio de esquema puede en algunos momentos ser imposible. El cambio puede a menudo ser dividido en dos cambios que juntos tienen el mismo resultado finl, mientras ambos reunen la condición de retro-compatiblidad.

1. Genera una migración que añade una nueva columna a la tabla de base de datos, almacenado la distancia en metros.
2. Añade el código de la aplicación que lee de la antigua columna pero es que escribe en ambas columnas.
3. Despliega esos cambios en producción.
4. Añade una nueva migración que migra los datos de la vieja columna a la nueva para todos los caso donde la nueva columna no esta aún rellan, pero la columna antigua si.
5. Modifica el código de la aplicación para que lea de la nueva columna.
6. Despliega los cambios de la aplicación en producción.
7. Añade uan nueva migración que elimina la columna antigua.

## Sin esquema

Completamente diferente enfoque para la gestión del esquema de base de datos es dejar de tener esquema de base de datos. Esto puede ser hechousando una base de datos sin esuqema o de documentos. La base de datos más conocida de este tipo es **Azure Cosmos DB**. Esas bases de datos pueden almacenar documentos de diferentes formas. Estas bases de datos no usan el termino *table*, pero en estas bases de datos se conocen como contenedores o colecciones.

Pueden almacenar documentos con un esuqema diferente en la misma colección, cambios de esquema existentes desde un punto de vista de base de datos. Para ver como gestionar esto, la mejor manera de diferenciar es entre almacenar objetos en la base de datos y leerlos de vuelta.

