# React JS

Es una biblioteca de JavaScript para construir interfaces de usuario, creada por meta (Jordan Walke) en 2011 y es de código abierto. Es declarativo y basado en componentes. Se puede ejecutar tanto en el cliente como en el servidor.

### Razones para usar React

1. Es el framework más demandado.
2. También se puede usar para React Native (app moviles). React Native for Windows + macOs te permite crear aplicaciones de escritorio. 
3. Mantenimiento asegurado. Comunidad grande.
4. Aprender React te ayudará a entener el resto de Frameworks.
5. Futuro prometedor. Las tendencias de npm muestran el incremento de React. 
6. API estable, no cambia mucho en las versiones. 
7. Comunidad gigante.

### Uso React JS

1. Importar librería

        import React from "https://esm.sh/react@18.2.0"
        import reactDOM from "https://esm.sh/react-dom@18.2.0/client"

2. Crear root

        const root = ReactDOM.createRoot(appDomElement);
        root.render('Hola React');

3. Crear y renderizar elemento 

        const button = React.createElement('button', { "data-id": 123 }, 'Me gusta');
        root.render(button);

> **_NOTE:_**  El método render sólo renderiza un elemento.

4. Crear un div que agrupe a varios botones y sea renderizado

        const div = React.createElement('div', null, [button, button2, button3]);
        root.render(div);

5. Se puede sustituir el div por un React Fragment.

        const div = React.createElement(React.Fragment, null, [button, button2, button3]);
        root.render(div);

### JSX