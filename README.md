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

#### Docker interactive session
```sh
docker run -it microsoft/dotnet:latest
dotnet new console -o myApp
cd myApp
dotnet restore
dotnet run
```
Here `-it` will begin interactive session where it will enter to docker container. Here **microsoft/dotnet:latest** is the dotnet image from [DockerHub: microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/). There are various options like *v1.0 or v1.1*, *runtime or sdk* & *debian or nanoserver*.  
Docker commands like `docker ps`, `docker stop`, `docker rm` used to manage docker containers.

#### Docker production image
```sh
dotnet new webapi -o dockerApp     // Create ASP.NET Core WebAPI application inside ./dockerApp
cd dockerApp
dotnet restore 
dotnet run                         // Test application using GET http://localhost:5000/api/values           
dotnet publish -c Release -o out   // Production .dll files added to ./out

docker build -t dockerapp .        // Build docker image from 'dockerfile'
docker run -it --rm dockerapp      // Run newly created docker container
```
Here *dotnet-docker/Dockerfile* contains dockerfile used above. Use of **microsoft/dotnet:runtime** because only *runtime* is needed for production. Default image with *SDK* used development. Other methods in [dotnet-docker](https://github.com/dotnet/dotnet-docker). 
<br/><br/>In *dotnet-docker/Dockerfile.nano* uses **microsoft/dotnet:1.1-runtime-nanoserver** which is dotnet windows container. Need to build with file flag as follows `docker build -t aspnetapp -f Dockerfile.nano .`. More [dotnet-docker-samples](https://github.com/dotnet/dotnet-docker-samples).
<br/><br/>In *dotnet-docker/Dockerfile-prebuild* applications is not published. Instead `dotnet restore` & `dotnet run` is done inside the container after copying all files. 
