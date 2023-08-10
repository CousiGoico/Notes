# Componentes integrados en React JS

## `<Fragment>`

#### __Referencia__

Te permite agrupar varios nodos JSX juntos. La etiqueta JSX vacía `<></>` es la abreviatura de `<Fragment></Fragment>`. Los Fragmentos son útiles porque la agrupación de elementos con un Fragmento no tiene efecto en el diseño o los estilos, al contrario de cómo sería si envolvieras los elementos dentro de cualquier otro contenedor tal como un elemento del DOM.

#### __Props__

+ key: el atributo key puede ser usado de manera opcional en el componente Fragment.

#### __Advertencias__

+ Si quisieras pasarle una key a un Fragmento, no podrias usar la sintaxis `<>...</>`. Tendrias que importar explícitamente Fragment desde 'react' y renderizar `<Fragment key={yourKey}>...</Fragment>`.
+ React no reinicia el estado cuando renderizas desde un `<><Child /></>` a un `[<Child />]` y viceversa, o cuando renderizas desde un `<><Child /></>` a un `<Child />` y viceversa. Ten en cuenta de que esto sólo funciona a un nivel de profundidad: por ejemplo, ir desde un `<><><Child /></></>` a un `<Child />` reinicia el estado.

#### __Ejemplo__

        function CloseDialog() {
            const buttons = (
                <>
                <OKButton />
                <CancelButton />
                </>
            );
            return (
                <AlertDialog buttons={buttons}>
                Are you sure you want to leave this page?
                </AlertDialog>
            );
        }   

## `<Profiler>`

#### __Referencia__

Mide el rendimiento de la renerización de un árbol de React de manera 
programática. Envuelve un árbol de componentes en un `<Profiler` para medir su rendimiento de renderizado.

#### __Props__

+ id: string que identifica que parte de la interfaz de usuario estás midiendo.
+ onRender: un callback onRender que React llama cada vez que los componenentes dentro del árbol perfilado se actualizan. Recibe información sobre lo que se renderizó y cuánto tiempo llevó.
    + id: id del profiler que se entregó. Esto permite identificar que parte del árbol se entregó si estás usando varios perfiles.
    + phase: ("mount", "update", "nested-update") indica si el árbol acaba de ser montado por primera vez o se ha vuelto a renderizar debo a un cambio en las props, el estado o los hooks. 
    + actualDuration: milisegundos que tardó en rendrzar.Este valor debería diminuir después del montaje inicial, ya que los descendientes sólo se renderizarán si cambian sus propiedades.
    + baseDuration: milisegundos que estima cuánto tiempo tarda en volver a renderizar. Se suman las duraciones del renderizado de cada componente del árbol. Compara `actualDuration` con este valor para ver si la momorización está funcionando.
    + startTime: marca de tiempo desde que React empezó a renderizar.
    + endTime: tiempo final de la renderización.


            function onRender(id, phase, actualDuration, baseDuration, startTime, commitTime) {
                // Agregar o registrar tiempos de procesamiento...
            }

#### __Advertencias__

+ Agrega cierta sobrecarga adicional, por lo que en el entorno de producción está deshabiitado por defecto.

#### __Ejemplo__

        <App>
            <Profiler id="Sidebar" onRender={onRender}>
                <Sidebar />
            </Profiler>
            <Profiler id="Content" onRender={onRender}>
                <Content>
                <Profiler id="Editor" onRender={onRender}>
                    <Editor />
                </Profiler>
                <Preview />
                </Content>
            </Profiler>
        </App>

## `<Suspense>`

#### __Referencia__

Muestra un sustituto mientras los componentes hijos se están cargando.

#### __Ejemplo__

## `<ScriptMode>`

#### __Referencia__

Permite controles adicionales solo para el desarrollo que te ayudan a encontrar errores anticipadamente. 

#### __Ejemplo__