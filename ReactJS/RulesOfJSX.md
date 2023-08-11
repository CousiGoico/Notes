# Reglas del JSX

1. __Retorna un elemento raíz__

Para devolver multiples elementos de un componente, envuelvelos en un tag. Puedes usar el tag `<div>` o el tag `<>` (Fragment).

        <>
            <h1>Hedy Lamarr's Todos</h1>
            <img 
                src="https://i.imgur.com/yXOvdOSs.jpg" 
                alt="Hedy Lamarr" 
                class="photo"
            >
            <ul>
                ...
            </ul>
        </>

2. __Cierra todos los tags__

JSX requiere que los tags sean explicitamente cerrados. Las etiquetas como `<img>` que no tienen etiquetas de cierre, se deben establecer como `<img />`.

        <>
            <img 
                src="https://i.imgur.com/yXOvdOSs.jpg" 
                alt="Hedy Lamarr" 
                class="photo"
            />
            <ul>
                <li>Invent new traffic lights</li>
                <li>Rehearse a movie scene</li>
                <li>Improve the spectrum technology</li>
            </ul>
        </>

3. __Usa camelCase__

JSX se convierte en JavaScript y los atributos escritos se convierten en claves de objetos JavaScript. En sus propios componentes, querrá leer los atributos como variables. Pero JavaScript tiene limitaciones en losombres de variables, ya que no pueden contener guiones ni ser palabras reservadas como `class` (en su lugar debes usar className).  Es el motivo por el que atributos en React están escritos en camelCase. 

        <img 
            src="https://i.imgur.com/yXOvdOSs.jpg" 
            alt="Hedy Lamarr" 
            className="photo"
        />

`Por razones historicas, aria-* y data-* están escritos en HTML con guiones.`


### Conversor de HTML a JSX

Existe un conversor gratuito de HTML a JSX en la siguiente [web](https://transform.tools/html-to-jsx).