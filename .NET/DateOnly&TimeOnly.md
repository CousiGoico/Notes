# DateOnly and TimeOnly

## Introducción

Las estructuras de datos **DateOnly** y **TimeOnly** representan un dato de tipo fecha sin la hora o una hora del día sin especificar el día. Estas estructuras de datos están disponibles a partir de la versión 6 de .NET Core. 

### DateOnly

Representa una fecha sin hora, por lo que corresponde a un día completo. Se le puede establecer los valores del 01/01/0001 al 31/12/9999. En su constructor se le puede indicar el calendario a usar (aunque siempre se convertirá al gregoriano):

        var hebrewCalendar = new System.Globalization.HebrewCalendar();
        var theDate = new DateOnly(5776, 2, 8, hebrewCalendar); // 8 Cheshvan 5776

        Console.WriteLine(theDate);

        /* Este ejemplo produce el siguiente valor:
        * 10/21/2015
        */

#### Ventajas

* El valor de la fecha no puede ser modificada por la zona horaria, lo que si ocurría con el tipo de datos **DateTime**.

* Al serializar un valor de tipo **DateOnly** serializa menos datos que el tipo **DateTime**.

* Este valor coincide mejor con el tipo de base de datos **Date** de SqlServer.

#### Ejemplos

- Convertir DateTime a DateOnly

        var today = DateOnly.FromDateTime(DateTime.Now);
        Console.WriteLine($"Today is {today}");

        /* Este ejemplo produce el siguiente valor:
        * Today is 03/08/2024
        */

- Agregar o restar días, meses o años

        var theDate = new DateOnly(2015, 10, 21);

        var nextDay = theDate.AddDays(1);
        var previousDay = theDate.AddDays(-1);
        var decadeLater = theDate.AddYears(10);
        var lastMonth = theDate.AddMonths(-1);

        Console.WriteLine($"Date: {theDate}");
        Console.WriteLine($" Next day: {nextDay}");
        Console.WriteLine($" Previous day: {previousDay}");
        Console.WriteLine($" Decade later: {decadeLater}");
        Console.WriteLine($" Last month: {lastMonth}");

        /* Este ejemplo produce el siguiente valor:
        * Date: 10/21/2015
        *  Next day: 10/22/2015
        *  Previous day: 10/20/2015
        *  Decade later: 10/21/2025
        *  Last month: 9/21/2015
        */

- Analizar DateOnly y darle formato

        var theDate = DateOnly.ParseExact("21 Oct 2015", "dd MMM yyyy", CultureInfo.InvariantCulture);  // Formato personalizado
        var theDate2 = DateOnly.Parse("October 21, 2015", CultureInfo.InvariantCulture);

        Console.WriteLine(theDate.ToString("m", CultureInfo.InvariantCulture));     // Patrón mes día
        Console.WriteLine(theDate2.ToString("o", CultureInfo.InvariantCulture));    // Formato ISO 8601
        Console.WriteLine(theDate2.ToLongDateString());

        /* Este ejemplo produce el siguiente valor:
        * October 21
        * 2015-10-21
        * Wednesday, October 21, 2015
        */

- Comparar DateOnly

        var theDate = DateOnly.ParseExact("21 Oct 2015", "dd MMM yyyy", CultureInfo.InvariantCulture);  // Formato personalizado
        var theDate2 = DateOnly.Parse("October 21, 2015", CultureInfo.InvariantCulture);
        var dateLater = theDate.AddMonths(6);
        var dateBefore = theDate.AddDays(-10);

        Console.WriteLine($"Consider {theDate}...");
        Console.WriteLine($" Is '{nameof(theDate2)}' equal? {theDate == theDate2}");
        Console.WriteLine($" Is {dateLater} after? {dateLater > theDate} ");
        Console.WriteLine($" Is {dateLater} before? {dateLater < theDate} ");
        Console.WriteLine($" Is {dateBefore} after? {dateBefore > theDate} ");
        Console.WriteLine($" Is {dateBefore} before? {dateBefore < theDate} ");

        /* Este ejemplo produce el siguiente valor:
        * Consider 10/21/2015
        *  Is 'theDate2' equal? True
        *  Is 4/21/2016 after? True
        *  Is 4/21/2016 before? False
        *  Is 10/11/2015 after? False
        *  Is 10/11/2015 before? True
        */

### TimeOnly



## Referencias

[Microsoft Learn](https://learn.microsoft.com/es-es/dotnet/standard/datetime/how-to-use-dateonly-timeonly#convert-datetime-to-dateonly)