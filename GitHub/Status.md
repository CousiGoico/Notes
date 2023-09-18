# Status

## gh Status

#### Definición

Muestra información la siguiente información sobre GitHub:

+ Incidencias asignadas
+ Pull request asignados
+ Solicitudes de revisión
+ Menciones
+ Actividad del repositorio

#### Argumentos

-e, --exclude <strings>: lista de los repositorios a excluir en formato propietario/nombre.

-o, --org <string>: retorna el estado de la organización.

#### Ejemplos

            gh status -e cli/cli -e cli/go-gh
            
            gh status -o cli
