# Tratando con base de datos en DevOps

## Gestionando el esquema de base de datos como código

ORM (**Object-relational mapper**) fue introducido para rellenar el desajuste entre la programación orientada a objectos y el esquema relacional de base de datos, que trabaja con tablas. Algunos ejemplos son NHibernate y Entity Framework.

Los ORMs proveen una capa de abstracción que permite el almacenamiento y recuperación de objetos desde la base de datos sin preocuparse de la estructura de la tabla. Para realizar el mapeo automatizado los ORMs a menudo tienen capacidades de compilación para desribir el esquema de base de datos, el modelo de objetos correspondiente y el mapa entre ellos en un lenguaje de marcado. Elllos pueden generar desde un modelo de objetos o una base de datos existente y el mapeo entre ellos, mediante convenciones, generados o pintados en un editor visual.

Para gestionar los cambios del esquema como código, hay dos enforques disponibles. El primero describe cada cambio en código (*basado en migraciones*); el otro describe sólo la última versión del esquema en código (*basado en el estado*). Ambos pueden confirar en heramientas de terceras partes para aplicar los cambios a la base de datos.

### Migrations

El primer enfoque es basado en mantener un ordenado conjunto de cambios que tienene que ser aplicados en la base de datos. Las **migraciones** pueden ser generadsas por herramientas tales como Microsoft Entity Framework o Redgate SQL Change Automation, o ellos pueden ser escritos a mano.

Las herramientas pueden automaticamente generar el script de la migración basada en la comparación del actual esquema y del nuevo esquema en el control de versiones. A esto se le llama **scaffolding**. Los scripts generdos por las herramientas no siempre son perfectos, y ellos tiene que ser mejorados aplicando el cónocimiento que el programador tiene.

![Figure9.1](Figure9.1.png){width="800" height="600" style="display: block; margin: 0 auto"}

Las etiquetas **m1** a la **m4** describen los cambios incrementales. Para modificar la base de datos a la última versión, la última migración aplicada es determinante y todas las migraciones posteriores que son añadadidas una después de otra.

Cuando edistas las migaciones a mano debes mantener en mente:

* La migración debe ser ordenada. Ddscriben las sentencias SQL que necesita ser ejecutadas en orden. La siguiente migración puede ser iniciada sólo cuando esta estapa este completada.

* Debe migrar no sólo el esquema también los datos. Esto puede significar que varias etapaas son necesarias entre migraciaciones.

* Indices extra y restricciones deben ser aplicadas no sólo en la base de producción. Asegurar que los indices y las restricciones son aplicadas en el mismo orden y no pueden bloquear migraciones existiendo sólo en proudcción.

* La migración debe ser realizada idempotente. El retorno de la última migración es una gran manera de asegurarse que está totalmente aplicada.

