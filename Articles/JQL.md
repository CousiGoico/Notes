# JQL

## Indice

1. [Introducción](#Introduction)
2. [Estructura](#Structure)
3. [JQL Functions](#JQL Functions)
    1. [approved()](#approved())
    2. [approver()](#approver())
    3. [breached()()](#breached())
    1. [approved()](#approved())
4. [Referencias](#Referencias)

### Introducción

JQL (Jira Query Language) es la forma más potente y flexible de realizar busquedas en el sistema JIRA.

### Estructura

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
|approver(user,user)|Campos personalizados del tipo Approval|=|~ , != , !~ , > , >= , < , <=  IS , IS NOT , IN , NOT IN , WAS, WAS IN, WAS NOT, WAS NOT IN , CHANGED|approvals = approved() `(Encuentra todas las solicitudes que han sido aprobadas)`|


#### breached()


### Referencias

[Excentia](https://www.excentia.es/jql-la-forma-de-buscar-en-jira#:~:text=JQL%20son%20las%20siglas%20de,proyectos%20%C3%A1giles%20y%20usuarios%20empresariales.)

[Jira Support](https://support.atlassian.com/jira-software-cloud/docs/jql-functions/)