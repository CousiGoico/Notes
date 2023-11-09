# Dotnet

## Dotnet sln

        dotnet new sln --name MySolution --use-program-main

        dotnet sln add {project}

## Dotnet build

        dotnet build 

## Dotnet clean

        dotnet clean

## dotnet new

### dotnet new console

        dotnet new console

## dotnet packages

### Add new package

        dotnet add package {package_name} --version {package_version}

## dotnet table

|Templates|Short name|Language|Tags|Introduced|
|---------|----------|--------|----|----------|
|Console application	|console|	[C#], F#, VB|	Common/Console|	1.0|
|Class library	|classlib	|[C#], F#, VB|	Common/Library|	1.0|
|WPF application	|wpf|	[C#], VB|	Common/WPF|	3.0 (5.0 for VB)|
|WPF class library	|wpflib|	[C#], VB|	Common/WPF|	3.0 (5.0 for VB)|
|WPF custom control library	|wpfcustomcontrollib|	[C#], VB|	Common/WPF|	3.0 (5.0 for VB)|
|WPF user control library	|wpfusercontrollib|	[C#], VB|	Common/WPF|	3.0 (5.0 for VB)|
|Windows Forms (WinForms) |application	winforms|	[C#], VB|	Common/WinForms|	3.0 (5.0 for VB)|
|Windows Forms (WinForms) |class library	winformslib|	[C#], VB|	Common/WinForms|	3.0 (5.0 for VB)|
|Worker service	|worker	|[C#]	|Common/Worker/Web	|3.0|
|Unit test project	|mstest	|[C#], F#, VB	|Test/MSTest|	1.0|
|NUnit 3 test project	|nunit|	[C#], F#, VB	|Test/NUnit	|2.1.400|
|NUnit 3 test item	|nunit-test|	[C#], F#, VB	|Test/NUnit	|2.2|
|xUnit test project	|xunit|	[C#], F#, VB	|Test/xUnit	|1.0|
|Razor component	|razorcomponent|	[C#]	|Web/ASP.NET|	3.0|
|Razor page	|page	|[C#]	|Web/ASP.NET	|2.0|
|MVC ViewImports	|viewimports|	[C#]	|Web/ASP.NET	|2.0|
|MVC ViewStart	|viewstart	|[C#]	|Web/ASP.NET|	2.0|
|Blazor server app	|blazorserver|	[C#]	|Web/Blazor|	3.0|
|Blazor WebAssembly app	|blazorwasm|	[C#]	|Web/Blazor/WebAssembly|	3.1.300|
|ASP.NET Core empty	|web|	[C#], F#	|Web/Empty|	1.0|
|ASP.NET Core web app (Model-View-Controller)	|mvc	|[C#], F#	|Web/MVC	|1.0|
|ASP.NET Core web app	|webapp, razor	|[C#]	|Web/MVC/Razor Pages	|2.2, 2.0|
|ASP.NET Core with Angular	|angular	|[C#]	|Web/MVC/SPA	|2.0|
|ASP.NET Core with React.js	|react	|[C#]	|Web/MVC/SPA	|2.0|
|ASP.NET Core with React.js and Redux	|reactredux	|[C#]	|Web/MVC/SPA	|2.0|
|Razor class library	|razorclasslib	|[C#]	|Web/Razor/Library/Razor Class Library	|2.1|
|ASP.NET Core web API	|webapi	|[C#], F#	|Web/WebAPI|	1.0|
|ASP.NET Core gRPC service	|grpc	|[C#]	|Web/gRPC|	3.0|
|dotnet gitignore file	|gitignore|		|Config|	3.0|
|global.json file	|globaljson|		|Config|	2.0|
|NuGet config	|nugetconfig|		|Config|	1.0|
|Dotnet local tool manifest file	|tool-manifest|		|Config|	3.0|
|Web config	|webconfig|		|Config|	1.0|
|Solution file	|sln|		|Solution|	1.0|
|Protocol buffer file	|proto	|	|Web/gRPC|	3.0|
|EditorConfig file	|editorconfig|		|Config|	6.0|