## ASP.NET Core Sample application

Sample application template for use with [Microclimate](https://microclimate-dev2ops.github.io)

### Table of Contents
* [Requirements](#requirements)
* [Project contents](#project-contents)
* [Run](#run)
* [Configuration](#configuration)
* [Service descriptions](#service-descriptions)
* [License](#license)
* [Generator](#generator)

#### Project contents
This application has been generated with the following capabilities and services, which are described in full in their respective sections below:

* [Embedded metrics collection](#embedded-metrics-dashboard)
* [Docker files](#docker-files)
* [Iterative Development](#iterative-development)

### Requirements
* [dotnet core 2.2+](https://dotnet.microsoft.com/download)

### Run
To build and run the application:
1. `dotnet build`
2. `dotnet run [PROJ_NAME_PLACEHOLDER]`

#### Docker
A description of the files related to Docker can be found in the [Docker files](#docker-files) setion. To build the docker image, run the following commands from the root directory of the project:
* `docker build -t [PROJ_NAME_PLACEHOLDER] .`
You may customize the names of these images by specifying a different value after the `-t` option.

To run the application:
```console
docker run -it -rm -p 8000:80 --name myapp [PROJ_NAME_PLACEHOLDER]
```
After the application starts, navigate to `http://localhost:8000` in your web browser. On Windows, you may need to navigate to the container via IP address. See [ASP.NET Core apps in Windows Containers](https://github.com/dotnet/dotnet-docker/blob/master/samples/aspnetapp/aspnetcore-docker-windows.md) for instructions on determining the IP address, using the value of `--name` that you used in `docker run`.

See [Hosting ASP.NET Core Images with Docker over HTTPS](https://github.com/dotnet/dotnet-docker/blob/master/samples/aspnetapp/aspnetcore-docker-https.md) to use HTTPS with this image.

#### Kubernetes
To deploy your application to your Kubernetes cluster, run `helm install --name myapp .` in the `/chart/[PROJ_NAME_PLACEHOLDER]` directory. You need to make sure you change the `repository` variable in your `chart/[PROJ_NAME_PLACEHOLDER]/values.yaml` file points to the docker image containing your runnable application.

### Configuration

### Service descriptions
#### Embedded metrics collector
This application uses the [AppMetrics package](https://github.com/AppMetrics/AppMetrics) to gather application and system metrics.

These metrics can be viewed in [Grafana dashboards](https://grafana.com/dashboards?search=app%20metrics). The dashboard displays various system and application metrics, including CPU, memory usage, HTTP response metrics and more.
#### Docker files
The application includes the following files for Docker support:
* `.dockerignore`
* `Dockerfile`

The `.dockerignore` file contains the files/directories that should not be included in the built docker image. By default this file contains the `Dockerfile` and `Dockerfile-tools`. It can be modified as required.

The `Dockerfile` defines the specification of the default docker image for running the application. This image can be used to run the application.

Details on how to build the docker images, compile and run the application within the docker image can be found in the [Run section](#run).

### License
All generated content is available for use and modification under the permissive MIT License (see `LICENSE` file), with the exception of AppMetrics which is licensed under an Apache-2.0 license (see `NOTICES.txt` file).

* [dotnet/core/sdk](https://hub.docker.com/_/microsoft-dotnet-core-sdk/): .NET Core SDK
* [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/): ASP.NET Core Runtime
* [dotnet/core/runtime](https://hub.docker.com/_/microsoft-dotnet-core-runtime/): .NET Core Runtime
* [dotnet/core/runtime-deps](https://hub.docker.com/_/microsoft-dotnet-core-runtime-deps/): .NET Core Runtime Dependencies
* [dotnet/core/samples](https://hub.docker.com/_/microsoft-dotnet-core-samples/): .NET Core Samples

# About .NET Core

[.NET Core](https://docs.microsoft.com/dotnet/core/) is a general purpose development platform maintained by Microsoft and the .NET community on [GitHub](https://github.com/dotnet/core). It is cross-platform, supporting Windows, macOS and Linux, and can be used in device, cloud, and embedded/IoT scenarios.

.NET has several capabilities that make development easier, including a utomatic memory management, (runtime) generic types, reflection, asynchrony, concurrency, and native interop. Millions of developers take advantage of these capabilities to efficiently build high-quality applications.

You can use C# to write .NET Core apps. C# is simple, powerful, type-safe, and object-oriented while retaining the expressiveness and elegance of C-style languages. Anyone familiar with C and similar languages will find it straightforward to write in C#.

[.NET Core](https://github.com/dotnet/core) is open source (MIT and Apache 2 licenses) and was contributed to the [.NET Foundation](http://dotnetfoundation.org) by Microsoft in 2014. It can be freely adopted by individuals and companies, including for personal, academic or commercial purposes. Multiple companies use .NET Core as part of apps, tools, new platforms and hosting services.
