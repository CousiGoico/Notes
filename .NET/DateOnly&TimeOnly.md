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

Representa una hora del día sin fecha, cuyo valor va del 00:00:00.0000000 al 23:59:59.9999999. Antes de crearse esta estructura de datos, se solía usar **TimeSpan**.

#### Ventajas

- En un **TimeSpan** el rango superior puede superar los 29 000 años o tener valores negativos, cosa que no sucede con **TimeOnly**.

- Se puede establecer un valor fuera del día en el **TimeSpan** pero no en el **TimeOnly**.

- Si se usa **DateTime** para establecer una hora, se suele aplicar como día **DateTime.MinValue** y manipulando el valor puede hacer que lance una excepción del tipo **OutOfRange**.

- Con *TimeOnly* serializa menos datos.

#### Ejemplos

- Convertir **DateTime** a **DateOnly**

        var now = TimeOnly.FromDateTime(DateTime.Now);
        Console.WriteLine($"It is {now} right now");

        /* Este ejemplo produce el siguiente valor:
        * It is 2:01 PM right now
        */

- Agregar o restar tiempo

        var theTime = new TimeOnly(7, 23, 11);

        var hourLater = theTime.AddHours(1);
        var minutesBefore = theTime.AddMinutes(-12);
        var secondsAfter = theTime.Add(TimeSpan.FromSeconds(10));
        var daysLater = theTime.Add(new TimeSpan(hours: 21, minutes: 200, seconds: 83), out int wrappedDays);
        var daysBehind = theTime.AddHours(-222, out int wrappedDaysFromHours);

        Console.WriteLine($"Time: {theTime}");
        Console.WriteLine($" Hours later: {hourLater}");
        Console.WriteLine($" Minutes before: {minutesBefore}");
        Console.WriteLine($" Seconds after: {secondsAfter}");
        Console.WriteLine($" {daysLater} is the time, which is {wrappedDays} days later");
        Console.WriteLine($" {daysBehind} is the time, which is {wrappedDaysFromHours} days prior");

        /* Este ejemplo produce el siguiente valor:
        * Time: 7:23 AM
        *  Hours later: 8:23 AM
        *  Minutes before: 7:11 AM
        *  Seconds after: 7:23 AM
        *  7:44 AM is the time, which is 1 days later 
        *  1:23 AM is the time, which is -9 days prior
        */

- Analizar **TimeOnly** y darle formato

        var theTime = TimeOnly.ParseExact("5:00 pm", "h:mm tt", CultureInfo.InvariantCulture);  // Formato personalizado
        var theTime2 = TimeOnly.Parse("17:30:25", CultureInfo.InvariantCulture);

        Console.WriteLine(theTime.ToString("o", CultureInfo.InvariantCulture));     // Formato largo
        Console.WriteLine(theTime2.ToString("t", CultureInfo.InvariantCulture));    // Formato corto
        Console.WriteLine(theTime2.ToLongTimeString());

        /* Este ejemplo produce el siguiente valor:
        * 17:00:00.0000000
        * 17:30
        * 5:30:25 PM
        */

### Serializar DateOnly y TimeOnly

Con la versión .NET 7 y posteriores, se admite la serialización de estas estructuras de datos.

        sealed file record Appointment(
                Guid Id,
                string Description,
                DateOnly Date,
                TimeOnly StartTime,
                TimeOnly EndTime);

        Appointment originalAppointment = new(
                Id: Guid.NewGuid(),
                Description: "Take dog to veterinarian.",
                Date: new DateOnly(2002, 1, 13),
                StartTime: new TimeOnly(5,15),
                EndTime: new TimeOnly(5, 45));
        string serialized = JsonSerializer.Serialize(originalAppointment);

        Console.WriteLine($"Resulting JSON: {serialized}");

        Appointment deserializedAppointment = JsonSerializer.Deserialize<Appointment>(serialized)!;

        bool valuesAreTheSame = originalAppointment == deserializedAppointment;
        Console.WriteLine($"""Original record has the same values as the deserialized record: {valuesAreTheSame}""");

### Trabajar con TimeOnly y DateTime

**TimeOnly** puede crearse a partir de un **TimeSpan** y convertirse en ese valor. También puede utilizarse un **DateTim** para crear un **TimeOnly**.

        var theTime = TimeOnly.FromTimeSpan(new TimeSpan(23, 59, 59));
        var theTimeSpan = theTime.ToTimeSpan();

        Console.WriteLine($"Variable '{nameof(theTime)}' is {theTime}");
        Console.WriteLine($"Variable '{nameof(theTimeSpan)}' is {theTimeSpan}");

        /* Este ejemplo produce el siguiente valor:
        * Variable 'theTime' is 11:59 PM
        * Variable 'theTimeSpan' is 23:59:59
        */

Creación de un **DateTime** a través de un **TimeOnly**

        var theTime = new TimeOnly(11, 25, 46);   // 11:25 AM and 46 seconds
        var theDate = new DateOnly(2015, 10, 21); // October 21, 2015
        var theDateTime = theDate.ToDateTime(theTime);
        var reverseTime = TimeOnly.FromDateTime(theDateTime);

        Console.WriteLine($"Date only is {theDate}");
        Console.WriteLine($"Time only is {theTime}");
        Console.WriteLine();
        Console.WriteLine($"Combined to a DateTime type, the value is {theDateTime}");
        Console.WriteLine($"Converted back from DateTime, the time is {reverseTime}");

        /* Este ejemplo produce el siguiente valor:
        * Date only is 10/21/2015
        * Time only is 11:25 AM
        * 
        * Combined to a DateTime type, the value is 10/21/2015 11:25:46 AM
        * Converted back from DateTime, the time is 11:25 AM
        */

### Operadores aritméticos y comparación de TimeOnly

        var start = new TimeOnly(10, 12, 01); // 10:12:01 AM
        var end = new TimeOnly(14, 00, 53); // 02:00:53 PM

        var outside = start.AddMinutes(-3);
        var inside = start.AddMinutes(120);

        Console.WriteLine($"Time starts at {start} and ends at {end}");
        Console.WriteLine($" Is {outside} between the start and end? {outside.IsBetween(start, end)}");
        Console.WriteLine($" Is {inside} between the start and end? {inside.IsBetween(start, end)}");
        Console.WriteLine($" Is {start} less than {end}? {start < end}");
        Console.WriteLine($" Is {start} greater than {end}? {start > end}");
        Console.WriteLine($" Does {start} equal {end}? {start == end}");
        Console.WriteLine($" The time between {start} and {end} is {end - start}");

        /* Este ejemplo produce el siguiente valor:
        * Time starts at 10:12 AM and ends at 2:00 PM
        *  Is 10:09 AM between the start and end? False
        *  Is 12:12 PM between the start and end? True
        *  Is 10:12 AM less than 2:00 PM? True
        *  Is 10:12 AM greater than 2:00 PM? False
        *  Does 10:12 AM equal 2:00 PM? False
        *  The time between 10:12 AM and 2:00 PM is 03:48:52
        */

## Referencias

[Microsoft Learn](https://learn.microsoft.com/es-es/dotnet/standard/datetime/how-to-use-dateonly-timeonly#convert-datetime-to-dateonly)