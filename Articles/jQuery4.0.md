# jQuery

## Introducción

[jQuery](https://blog.jquery.com/) es una librería de JavaScript, desarrollada en 2006 por *John Resig*, que permite realizar consultas de los elementos del DOM de una página web de manera más rápida y eficiente, permite realizar cambios en los atributos y estilos de varios elementos del DOM de una sola vez, tiene una capa de interacción AJAX que permite realizar llamadas a servidor, entre otras carácteristicas. 

## Librerias

La marca **jQuery** nos da acceso a otras librerias que nos permiten trabajar de una manera más sencilla y cómoda:

* **jQuery (v.3.7.1)**: librería base de JavaScript

* **jQuery UI (v.1.13.2)**: libreria de controles, interacciones, efectos, widgets y temas.

* **jQuery Mobile (v.1.4.5)**: sistema basado en HTMLpara crear alicaciones responsivas en todos los dispositivos.

* **QUnit (v.2.20.1)**: framework para testar el código.

## Versión 4.0

La compañía ha publicado un [articulo](https://blog.jquery.com/) en el blog de su página web indicando que van a sacar nueva versión, y que actualmente está en fase beta.

En dicho articulo destacan las nuevas carácteristicas que tendrá la versión, que son las siguientes:

### Adios a la compatibilidad con navegadores antiguos

Se eliminará la compatibilidad con las siguientes versiones de navegadores:

* Internet Explorer 10 o menor (seguirá siendo compatible con la versión 11 hasta que lancen la versión 5.0 de jQuery)

* Edge Legacy

* Safari (cuyo iOS sea 10 o menor)

* Firefox 64 o menor

### Eliminación de APIs obsoletas

Se ha prescindido de las siguientes APIs:

* jQuery.cssNumber
* jQuery.cssProps
* jQuery.isArray
* jQuery.parseJSON
* jQuery.nodeName
* jQuery.isFunction
* jQuery.isWindow
* jQuery.camelCase
* jQuery.type
* jQuery.now
* jQuery.isNumeric
* jQuery.trim
* jQuery.fx.interval

### Otras eliminaciones o cambios

#### Push y Sort

Se han eliminado los métodos *push* y *sort* para los arrays. Por ejemplo:

        $elems.push(element);

Pasa ahora a realizarse de la siguiente manera:

        [].push.call($elems, elem);

#### Orden eventos de foco

Se ha establecido un nuevo orden de los eventos de foco (en base a la especificación W3C), para que todos los navegadores modernos estén alineados:

1. blur
2. focusout
3. focus
4. focusin

#### FormData

Se ha agregado compatibilidad en jQuery.ajax con los datos binarios, incluido FormData. Anteriormente se convertian en cadena haciendo que el proceso pudiera fallar.

#### JSONP

Se ha eliminado la promoción automática de JSONP. Por defecto, cuando se ralizaba una llamada jQuery.ajax se devolvía en este formato. 

#### Módulos ES

Anteriormente jQuery se distribuia mediante [Node Package Manager](https://www.npmjs.com/) o [GitHub](https://github.com/), pero no se podía importar directamente como módulos sin [RequireJS](https://requirejs.org/). Ahora se está usando la herramienta [Rollup](https://rollupjs.org/) para empaquetar jQuery y distribuirlo como módulos ES. 

#### Tipos de confianza y CSP

Ahora se agrega compatibilidad con tipos de confianza, lo que garantiza que el HTML encapsulado en TrustedHTML se pueda usar como entrada para los métodos de manipulación de jQuery de una manera que no infrinja la directiva de política de seguridad de contenido.

        require-trusted-types-for

### Referencias

[jQuery](https://jquery.com/)

[jQuery GItHub](https://github.com/jquery/jquery)

[jQuery UI](https://jqueryui.com/)

[jQuery Mobile](https://jquerymobile.com/)

[QUnit](https://qunitjs.com/)

[RequireJS](https://requirejs.org/)

[Node Package Manager](https://www.npmjs.com/)

[GitHub](https://github.com/)

[Rollup](https://rollupjs.org/)

