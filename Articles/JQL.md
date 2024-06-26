# JQL

## Indice

1. [Introducción](#Introduction)
2. [Estructura](#Structure)
3. [JQL Functions](#JQL-Functions)
    1. [approved()](#approved())
    2. [approver()](#approver())
    3. [breached()()](#breached())
    4. [cascadeOption()](#cascadeOption())
    5. [cascadeOption()](#cascadeOption())
    6. [choiceOption()](#choiceOption())
    7. [closedSprints()](#closedSprints())
    8. [completed()](#completed())
    9. [componentsLeadByUser()](#componentsLeadByUser())
    10. [componentsLeadByUser()](#componentsLeadByUser())
    11. [currentLogin()](#currentLogin())
    12. [currentUser()](###currentUser())
4. [Referencias](#Referencias)

## Introducción

JQL (Jira Query Language) es la forma más potente y flexible de realizar busquedas en el sistema JIRA.

## Estructura

- **Campo**: propiedades del propio JIRA, tales como, tipo de tarjeta, código de tarjeta, fecha de creación, ...

- **Operador**: son las operaciones que puedes realizar con las propiedaes, igual (=), menor que (<), mayor que (>), contiene (in), ...

- **Valor**: es el dato con en que estas realizando la operación.

- **Palabra clave**: palabras reservadas, tales como, Empty, And, Or, ...

### JQL Functions

#### approved()

Busca en las solicitudes que requieren aprobación y están aprobadas. 

> [!IMPORTANT]
> Sólo aplicable a sitios con suscripción Jira Service Management

|Sintaxis|Campos soportados|Operadores soportados|Operadores no soportados|Ejemplos|
|--------|-----------------|---------------------|------------------------|--------|
|approved()|Campos personalizados del tipo Approval|=|~ , != , !~ , > , >= , < , <=  IS , IS NOT , IN , NOT IN , WAS, WAS IN, WAS NOT, WAS NOT IN , CHANGED|approvals = approved() `(Encuentra todas las solicitudes que han sido aprobadas)`|



#### approver()

Busca aquellas solicitudes que necesitan ser aprobadas por un usuario. 

> [!IMPORTANT]
> Sólo aplicable a sitios con suscripción Jira Service Management

|Sintaxis|Campos soportados|Operadores soportados|Operadores no soportados|Ejemplos|
|--------|-----------------|---------------------|------------------------|--------|
|approver(user,user)|Campos personalizados del tipo Approval|=|~ , != , !~ , > , >= , < , <=  IS , IS NOT , IN , NOT IN , WAS, WAS IN, WAS NOT, WAS NOT IN , CHANGED|approvals = approved(user) `(Encuentra todas las solicitudes que han sido aprobadas por user)`|


#### breached()

Devuelve aqeullas incidencias cuyo SLA no se ha cumplido.

> [!IMPORTANT]
> Sólo aplicable a sitios con suscripción Jira Service Management

|Sintaxis|Campos soportados|Operadores soportados|Operadores no soportados|Ejemplos|
|--------|-----------------|---------------------|------------------------|--------|
|breached()|SLA|= , !=|~ , !~ , > , >= , < , <= IS , IS NOT , WAS , WAS IN , WAS NOT , WAS NOT IN , CHANGED|"Time to First Response" = breached() `(Encuentra todas las incidencias donde Time to First Response fue incumplido)`|


#### cascadeOption()

Devuelve aqeullas incidencias con valores seleccionados en un campo de selección en cascada. El parámetro parentOption coincide con el primer nivel de opciones en el campo de selección en cascada. El parámetro childOption coincide con el segundo nivel de opciones en el campo de selección en cascada y es opcional. La palabra clave "ninguno" se puede utilizar para buscar problemas en los que una o ambas opciones no tienen valor.


|Sintaxis|Campos soportados|Operadores soportados|Operadores no soportados|Ejemplos|
|--------|-----------------|---------------------|------------------------|--------|
|cascadeOption(parentOption) / cascadeOption(parentOption,childOption)|Campos personalizados de tipo selección en cascada|IN , NOT IN|= , != , ~ , !~ , > , >= , < , <= IS , IS NOT, WAS , WAS IN , WAS NOT , WAS NOT IN , CHANGED|location in cascadeOption("USA","New York") `(Encuentra todas las incidencias donde Location es USA para el primer nivel y New York para el segundo nivel)`|


#### choiceOption()

Proporciona el ID de una opción en un campo personalizado desplegable o de opción múltiple. Requiere al menos un argumento. Para múltiples argumentos, devuelve el ID de cada uno. Los argumentos deben ser valores de opción válidos.

|Sintaxis|Campos soportados|Operadores soportados|Operadores no soportados|Ejemplos|
|--------|-----------------|---------------------|------------------------|--------|
|choiceOption(ValueOption) / choiceOption(ValueOption1,ValueOption2,ValueOption3)|Campos personalizado desplegable o de opción múltiple|IN , NOT IN|= , != , ~ , !~ , > , >= , < , <= IS , IS NOT, WAS , WAS IN , WAS NOT , WAS NOT IN , CHANGED|"productVersion[Select List (multiple choices)]" in choiceOption(123) `(Busqueda valores de opción numérica)`|


#### closedSprints()

Busca incidencias que están en sprints completados.

> [!NOTE]
> Es posible que una incidencia pertenezca tanto a un Sprint completado como a un Sprint incompleto. Véase también openSprints().

|Sintaxis|Campos soportados|Operadores soportados|Operadores no soportados|Ejemplos|
|--------|-----------------|---------------------|------------------------|--------|
|closedSprints()|Sprint|IN , NOT IN|= , != , ~ , !~ , > , >= , < , <= IS , IS NOT, WAS , WAS IN , WAS NOT , WAS NOT IN , CHANGED|sprint in closedSprints() `(Busqueda todas las incidencias que están asignadas a sprints completados)`|


#### completed()

Busca incidencias que están en sprints completados con SLA.

> [!IMPORTANT]
> Sólo aplicable a sitios con suscripción Jira Service Management

|Sintaxis|Campos soportados|Operadores soportados|Operadores no soportados|Ejemplos|
|--------|-----------------|---------------------|------------------------|--------|
|completed()|SLA|=, !=|~ , !~ , > , >= , < , <= IS , IS NOT , WAS , WAS IN , WAS NOT , WAS NOT IN , CHANGED|"Time to First Response" = completed() `(Busqueda todas las incidencias que Time to first Reponse ha sido completado)`|


#### componentsLeadByUser()

Busca componentes dirigidos por el usuario.

> [!NOTE]
> Si no estas logado en Jira, un usuario debe ser especificado.

|Sintaxis|Campos soportados|Operadores soportados|Operadores no soportados|Ejemplos|
|--------|-----------------|---------------------|------------------------|--------|
|componentsLeadByUser() / componentsLeadByUser(username)|Component|IN , NOT IN|= , != , ~ , !~ , > , >= , < , <= IS , IS NOT, WAS , WAS IN , WAS NOT , WAS NOT IN , CHANGED|component in componentsLeadByUser() AND status = Open `(Busqueda todas los componentes que están liderados por el usuario y estén abiertos)`|

#### currentLogin()

Realiza busquedas basadas en el tiempo que el usuario inicio sesión.

|Sintaxis|Campos soportados|Operadores soportados|Operadores no soportados|Ejemplos|
|--------|-----------------|---------------------|------------------------|--------|
|currentLogin()|Created, Due, Resolved, Updated, custom fields of type Date/Time|= , != , > , >= , < , <= WAS* , WAS IN* , WAS NOT* , WAS NOT IN* , CHANGED* * Only in predicate|~ , !~ IS , IS NOT , IN , NOT IN|created > currentLogin() `(Busca incidencias que han sido creados durante la sesión actual)`|

### currentUser()

Realiza busquedas basadas en el usuario logado.

> [!NOTE]
> Sólo puede ser usado cuando estas logado.

|Sintaxis|Campos soportados|Operadores soportados|Operadores no soportados|Ejemplos|
|--------|-----------------|---------------------|------------------------|--------|
|currentUser()|Assignee, Reporter, Voter, Watcher, Creator, custom fields of type User|= , !=|~ , !~ , > , >= , < , <= IS , IS NOT , IN , NOT IN , WAS , WAS IN , WAS NOT , WAS NOT IN , CHANGED|reporter = currentUser() AND (assignee != currentUser() OR assignee is EMPTY) `(Busca incidencias que han sido reportados por el usuario actual y que el asignado sera diferente que el usuario actual o vacío)`|


### customerDetail()

Realiza busquedas basadas en los clientes.

> [!NOTE]
> Sólo aplicable a sitios con suscripción Jira Service Management

|Sintaxis|Campos soportados|Operadores soportados|Operadores no soportados|Ejemplos|
|--------|-----------------|---------------------|------------------------|--------|
|customerDetail()|Assignee, Reporter, Voter, Watcher, custom fields of type User|IN , NOT IN|= , != , ~ , !~ , > , >= , < , <= IS , IS NOT , WAS , WAS IN , WAS NOT IN, WAS NOT , CHANGED|reporter in customerDetail("Region", "APAC") `(Busca incidencias reportadas por clientes en la región APAC)`|



## Referencias

[Excentia](https://www.excentia.es/jql-la-forma-de-buscar-en-jira#:~:text=JQL%20son%20las%20siglas%20de,proyectos%20%C3%A1giles%20y%20usuarios%20empresariales.)

[Jira Support](https://support.atlassian.com/jira-software-cloud/docs/jql-functions/)