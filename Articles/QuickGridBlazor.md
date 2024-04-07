# QuickGrid

## Introducción

QuickGrid es un componente Razor con el que podremos visualizar una grid de manera rápida. Este componente esta oficialmente soportado para la versión 8 de .NET. 

## Instalación

Para instalarlo en nuestro proyecto será necesario instalar el paquete nuget **Microsoft.AspNet.Componentes.QuickGrid** de una de las siguientes maneras:

- Añadiendo un paquete NuGet:

        dotnet add package Microsoft.AspNetCore.Components.QuickGrid

- Desde Visual Studio, abriendo el Gestor de Paquetes NuGet y buscando el siguiente paquete **Microsoft.AspNetCore.Components.QuickGrid**.

## Código

Para utilizar el componente, una vez instalado, será necesario usar el siguiente código de ejemplo:

        <QuickGrid Items="@people">
            <PropertyColumn Property="@(p => p.PersonId)" Sortable="true" />
            <PropertyColumn Property="@(p => p.Name)" Sortable="true" />
            <PropertyColumn Property="@(p => p.BirthDate)" Format="yyyy-MM-dd" Sortable="true" />
        </QuickGrid>

        @code {
            record Person(int PersonId, string Name, DateOnly BirthDate);

            IQueryable<Person> people = new[]
            {
                new Person(10895, "Jean Martin", new DateOnly(1985, 3, 16)),
                new Person(10944, "António Langa", new DateOnly(1991, 12, 1)),
                new Person(11203, "Julie Smith", new DateOnly(1958, 10, 10)),
                new Person(11205, "Nur Sari", new DateOnly(1922, 4, 27)),
                new Person(11898, "Jose Hernandez", new DateOnly(2011, 5, 3)),
                new Person(12130, "Kenji Sato", new DateOnly(2004, 1, 9)),
            }.AsQueryable();
        }

### Parámetros de las columnas

* **Title**: título de la columna.

* **Class**: clase de CSS para esa columna.

* **Align**: alineamiento de la columna (left/center/right).

* **HeaderTemplate**: plantilla para la cabecera.

* **ColumnOptions**: fragmento de Razor como ventana emergente al pulsar sobre las opciones de la columna.

* **Sortable**: indicar si la columna será ordenable.

* **IsDefaultSortColumn**: indica si esta será la columna ordenada por defecto.

* **InitialSortDirection**: indica la dirección de ordenación inicial.

* **PlaceholderTemplate**git : fragmento de Razor que aparecerá cuando se esté cargando la grid. 

## Referencias

- [Microsoft Learn](https://learn.microsoft.com/es-es/aspnet/core/blazor/components/quickgrid?view=aspnetcore-8.0)

- [QuickGrid for Blazor](https://aspnet.github.io/quickgridsamples/getstarted)

- [GitHub](https://github.com/dotnet/aspnetcore/blob/main/src/Components/test/testassets/BasicTestApp/QuickGridTest/SampleQuickGridComponent.razor)