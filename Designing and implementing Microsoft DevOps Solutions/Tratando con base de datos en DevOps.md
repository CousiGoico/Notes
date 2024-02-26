# Tratando con base de datos en DevOps

## Gestionando el esquema de base de datos como código

ORM (**Object-relational mapper**) fue introducido para rellenar el desajuste entre la programación orientada a objectos y el esquema relacional de base de datos, que trabaja con tablas. Algunos ejemplos son NHibernate y Entity Framework.

Los ORMs proveen una capa de abstracción que permite el almacenamiento y recuperación de objetos desde la base de datos sin preocuparse de la estructura de la tabla. Para realizar el mapeo automatizado los ORMs a menudo tienen capacidades de compilación para desribir el esquema de base de datos, el modelo de objetos correspondiente y el mapa entre ellos en un lenguaje de marcado. Elllos pueden generar desde un modelo de objetos o una base de datos existente y el mapeo entre ellos, mediante convenciones, generados o pintados en un editor visual.

Para gestionar los cambios del esquema como código, hay dos enforques disponibles. El primero describe cada cambio en código (*basado en migraciones*); el otro describe sólo la última versión del esquema en código (*basado en el estado*). Ambos pueden confirar en heramientas de terceras partes para aplicar los cambios a la base de datos.

