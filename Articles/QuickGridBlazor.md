# QuickGrid

## Introducción

QuickGrid es un nuevo componente Razor con el que podremos visualizar una grid de manera rápida. Este componente esta oficialmente soportado para la versión 8 de .NET. 

## Instalación

Para instalarlo en nuestro proyecto será necesario instalar el paquete nuget **Microsoft.AspNet.Componentes.QuickGrid** de una de las siguientes maneras:

- Añadiendo un paquete NuGet:

        dotnet add package Microsoft.AspNetCore.Components.QuickGrid

- Desde Visual Studio, abriendo el Gestor de Paquetes NuGet y buscando el siguiente paquete **Microsoft.AspNetCore.Components.QuickGrid**.

## Código

Para utilizar el componente, una vez instalado, será necesario usar el siguiente código de ejemplo:

        <QuickGrid Items="@cars">
            <PropertyColumn Property="@(p => p.Id)" Sortable="true" />
            <PropertyColumn Property="@(p => p.Brand)" Sortable="true" />
            <PropertyColumn Property="@(p => p.Model)" Sortable="true" />
            <PropertyColumn Property="@(p => p.Year)" Sortable="true" />
            <PropertyColumn Property="@(p => p.RegistrationDate)" Format="yyyy-MM-dd" Sortable="true" />
            <PropertyColumn Property="@(p => p.Colour)" Sortable="true" />
        </QuickGrid>

        @code {
            record Car(int Id, string Brand, string Model, int Year, DateOnly RegistrationDate, string Colour);

            IQueryable<Car> cars = new[]
            {
                new Car(1, "Mazda", "2", 2018, new DateOnly(1985, 3, 16), "Rojo"),
                new Car(2, "Mazda", "3", 2018, new DateOnly(1985, 3, 16), "Azul"),
                new Car(3, "Mazda", "5", 2017, new DateOnly(1985, 3, 16), "Blanco"),
                new Car(4, "Mazda", "6", 2016, new DateOnly(1985, 3, 16), "Negro"),
                new Car(5, "Mazda", "MX30", 2021, new DateOnly(1985, 3, 16), "Morado"),
                new Car(6, "Mazda", "CX3", 2019, new DateOnly(1985, 3, 16), "Verde"),
                new Car(7, "Mazda", "CX5", 2018, new DateOnly(1985, 3, 16), "Amarillo"),
                new Car(8, "Mazda", "CX30", 2020, new DateOnly(1985, 3, 16), "Marron"),
                new Car(9, "Mazda", "CX60", 2023, new DateOnly(1985, 3, 16), "Azul marino"),
                new Car(10, "Mazda", "MX5", 2019, new DateOnly(1985, 3, 16), "Gris"),
            }.AsQueryable();
        }

## Ejemplo

    

## Referencias

- [Microsoft Learn](https://learn.microsoft.com/es-es/aspnet/core/blazor/components/quickgrid?view=aspnetcore-8.0)

- [QuickGrid for Blazor](https://aspnet.github.io/quickgridsamples/getstarted)

- [GitHub](https://github.com/dotnet/aspnetcore/blob/main/src/Components/test/testassets/BasicTestApp/QuickGridTest/SampleQuickGridComponent.razor)