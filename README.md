# Learning .NET Core and ASP.NET Core

Install [.NET Core](https://www.microsoft.com/net/core)

```sh
dotnet --version     // Installed version of .NET Core  (1+ versions for following CLI commands) 
dotnet new --help    // Available templates in .NET Core and ASP.NET Core applications
```

>Default templates include .NET Core applications: **console**, ASP.NET Core applications: **web, webapi**, testing and such.
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
----------
### JavaScript framework templates
For ease, we need templates with Angular, React in ASP.NET Core application. 
ASP.NET uses [JavaScriptServices](https://github.com/aspnet/JavaScriptServices) for this, which consists of  `Microsoft.AspNetCore.NodeServices`, `Microsoft.AspNetCore.SpaServices` and such...

#### Using nuget package: Microsoft.AspNetCore.SpaTemplates
```sh
dotnet new --install Microsoft.AspNetCore.SpaTemplates::*
dotnet new reactredux
dotnet restore     // May need to follow it with 'npm install' for some templates 
dotnet run
```
There are many more templates using Angular2, React... Use `dotnet new --help` to know newly added templates. [More Info](https://blogs.msdn.microsoft.com/webdev/2017/02/14/building-single-page-applications-on-asp-net-core-with-javascriptservices/)

#### Using yeomen generators: 
```sh
npm install -g yo generator-aspnetcore-spa
yo aspnetcore-spa // Choose from SPA templates: react, angular
dotnet run 
```
There are some other generators like `generator-aspnet` to help with development. It comes with sub commands to ease coding such as `yo aspnet:Class Person` [More Info](https://docs.microsoft.com/en-us/aspnet/core/client-side/yeoman)

----------
### .NET Core with Docker

-- To be completed --
