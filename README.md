# Learning .NET Core and ASP.NET Core

Install [.NET Core](https://www.microsoft.com/net/core)

```sh
dotnet --version     // Installed version of .NET Core  (1+ versions for following CLI commands) 
dotnet new --help    // Available templates in .NET Core and ASP.NET Core applications
```

>Default templates include .NET Core applications: **console**, ASP.NET Core applications: **web, mvc**, unit testing and such.
Flags like **--framework netcoreapp1.1** could be used to set ASP.NET Core version to 1.1 instead of default 1.0.


#### .NET Core console application
```sh
dotnet new console   // This is console application.
dotnet restore
dotnet run 
```

#### ASP.NET Core web application
```sh
dotnet new web      // This is empty web application. 'dotnet new mvc' also available. 
dotnet restore
dotnet run 
```
