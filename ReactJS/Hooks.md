# REACT JS 

## HOOKS

Los [hooks](https://es.react.dev/reference/react) son funcionalidades integradas en __REACT JS__ que te ayudan y te facilitan el desarrollo de la aplicación. 

#### __HOOK DE ESTADO__

Permite almacenar la información de la entrada de un usuario en memoria. Un caso de uso sería el almacenamiento de la información del usuario que ha iniciado sesión, o el identificador de un elemento seleccionado en un listado.

+ __useState__: administra una variable de estado que puedes actualizar directamente.
+ __useReducer__: administra una variable de estado cuya actualización se gestiona mediante una función reductora.

        function ImageGallery() {
            const [index, setIndex] = useState(0);
        // ...


#### __HOOK DE CONTEXTO__

Permite compartir información a los componentes hijos sin la necesidad de pasar dicha información como props. Un ejemplo de uso de este hook sería compartir el tema de la aplicación o la configuración del usuario entre los diferentes componentes hijos.

+ __useContext__: lee y se suscribe a un contexto.

        function Button() {
            const theme = useContext(ThemeContext);
        // ...

#### __HOOK DE REFS__

Mantiene informacion que no es usada para renderizar. Son útiles cuando necesitas trabajar con sistemas distintos de React, como las APIs integradas del navegador. El id de un timeout sería un ejemplo de dato para almacenar en este tipo de hook.

`Este tipo de hook no vuelve a renderizar tu componente. En el caso del uso del hook de estado si se renderiza el componente.`

+ __useRef__: administra una referencia, como por ejemplo un nodo del DOM.
+ __useImperativeHandle__: permite personalizar la *ref* expuesta por tu componente. Esto rara vez se usa.

        function Form() {
            const inputRef = useRef(null);
        // ...

#### __HOOK DE EFECTO__

Se usa para conectarse y sincronizarse con sistemas externos (red, DOM del navegador, animaciones, widgets, ...). 

`No uses este tipo de hooks para guiar el flujo de datos de tu aplicación.`

+ __useEffect__: permite a un componente conectarse con un sistema externo.
+ __useLayoutEffect__: (variación poco usado de useEffect) se activa antes de que el navegador vuelva a pintar la pantalla. Se suelen hacer cálculos de maquetación (layout).
+ __useInsertionEffect__: (variación poco usado de useEffect) se activ antes de que React haga cambios en el DOM. Aquí las bibliotecas pueden insertar CSS dinámico. 

        function ChatRoom({ roomId }) {
            useEffect(() => {
                const connection = createConnection(roomId);
                connection.connect();
                return () => connection.disconnect();
            }, [roomId]);
        // ...

#### __HOOK DE RENDIMIENTO__

Permite realizar un renderizado cacheado si los datos no han sido cambiado desde el renderizado anterior. Puedes separar las actualizaciones del renderizado haciendo que actualizaciones bloqueantes sean síncronas para mejorar el rendimiento. 

+ __useMemo__: permite guardar en caché los resultados de un cálculo costoso.
+ __useCallback__: permite guardar en caché una función definida antes de pasarl a un componente optimizado.
+ __useTransition__: marca una transición de estado como no bloqueante para permitir que otras actualizaciones la interrumpan.
+ __UseDeferredValue__: aplaza la actualización de una parte no crítica de la interfaz de usuairo y deja que otras partes se actualizen primero.

        function TodoList({ todos, tab, theme }) {
            const visibleTodos = useMemo(() => filterTodos(todos, tab), [todos, tab]);
            // ...
        }

#### __OTROS HOOKS__

Otros hooks interesantes de conocer.

+ __useDebugValue__: personaliza la etiqueta en las Herramientas de Desarrollo de React muestra para el Hook personalizado.
+ __useId__: permite que un componente se asocie a un ID único. Normalmente se asocia a las APIs de accesibilidad.
+ __useSyncExternalStore__: suscribe un componente a un almacenamiento externo. 