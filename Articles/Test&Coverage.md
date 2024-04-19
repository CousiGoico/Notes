# Tests and coverage

## Introduccion

En nuestro día a día necesitamos que nuestros proyectos sean fiables. Para que sean eficaces se crean tests que demuestren la solidez de la arquitectura y del código que programamos, y para medir los tests está la cobertura que indica el % del código que esta cubierto por los tests. 

### Frameworks de testing

En C# conozco tres frameworks de testing (seguramente haya más):

* [MSTest](https://learn.microsoft.com/es-es/dotnet/core/testing/unit-testing-with-mstest): MSTest es el marco de pruebas de Microsoft para todos los lenguajes .NET. Es extensible y funciona con la CLI de .NET y Visual Studio

* [NUnit](https://nunit.org/): NUnit es un marco de pruebas unitarias para todos los lenguajes .Net. Inicialmente portada desde JUnit, la versión de producción actual, la versión 3, ha sido completamente reescrita con muchas características nuevas y soporte para una amplia gama de plataformas .NET.

* [xUnit](https://xunit.net/): xUnit.net es una herramienta de prueba unitaria gratuita, de código abierto y centrada en la comunidad para .NET Framework. Escrito por el inventor original de NUnit v2, xUnit.net es la última tecnología para pruebas unitarias de C#, F#, VB.NET y otros lenguajes .NET. xUnit.net funciona con ReSharper, CodeRush, TestDriven.NET y Xamarin. Es parte de la Fundación .NET y opera según su código de conducta. Tiene licencia Apache 2 (una licencia aprobada por OSI).

#### Creación de un test



### Herramientas de cobertura de código

* Recopiladores de datos: supervisan la ejecución de pruebas y recopilan información, en diversos formatos de salida como XML y JSON, sobre las series de pruebas. 

* Generadores de pruebas: usan los datos recopilados de las series de pruebas para generar informes, a menudo como HTML con estilo.

.NET incluye un recopilador de datos de cobertura de código integrado, llamado **dotnet-coverage**, que genera un archivo .coverage binario que se puede usar para generar informes. El archivo binario no es legible por el usuario y debe convertirse a un formato legible para poder usarse a fin de generar informes.

> [!TRIP]
> [dotnet-coverage](https://learn.microsoft.com/es-es/dotnet/core/additional-tools/dotnet-coverage) es una herramienta multiplataforma que se puede usar para convertir el archivo de resultados de pruebas de cobertura binaria a un formato legible por el usuario.

#### Coverlet

**Coverlet** es una alternativa de código abierto al recopilador integrado. Genera resultados de prueba como archivos XML de Cobertura legibles por usuarios, que luego se pueden usar para generar informes en HTML. A fin de usar Coverlet para la cobertura de código, un proyecto de prueba unitaria existente debe tener las dependencias de paquete [coverlet.msbuild](https://www.nuget.org/packages/coverlet.msbuild).

#### Generador de informes

Puedes crear informe con los datos recopilados mediante la herramienta [ReportGenerator](https://github.com/danielpalme/ReportGenerator), instalandola con el siguiente comando:

        dotnet tool install -g dotnet-reportgenerator-globaltool

El informe resultante tendría el siguiente aspecto:

![test-report](images/test-report.png)

## Referencias

- [Microsoft learn - Testing](https://learn.microsoft.com/es-es/dotnet/core/testing/)
- [NUnit](https://nunit.org/)
- [xUnit](https://xunit.net/)
- [Nuget Coverlet](https://www.nuget.org/packages/coverlet.msbuild)
- [GitHub Coverlet](https://github.com/coverlet-coverage/coverlet)

