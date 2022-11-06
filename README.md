# Base Microservice Template
It's a solution template for microservice with basic features. The template contains ASP.NET + EF Core solution with unit and integration tests. By default a database and the API are set to work in Docker containers.

Following instructions are for Debian-based systems - but on Windows machines it should be similar or even simpler. 

## Environment used
- JetBrains Rider
- SQL Server (inside container)
- Docker

## Tech stack used
- .NET 6
- ASP.NET Core 6
- Entity Framework Core 6
- AutoMapper
- nUnit, Moq

## Getting started

To run the solution in the easiest way, do the following:

1. Install the latest [.NET 6 SDK](https://dotnet.microsoft.com/en-us/download/dotnet/6.0)
2. Install Docker Engine
  ```
  apt install docker*
  ```
3. Clone this repository
4. Run `docker-compose build && docker-compose up` inside the root folder of the solution

## Database configuration
A database is containerised by using Docker. If you have to do something outside Docker (e.g. test something on local database or with in-memory database), you'll have to adjust connection strings.

In order to do it, open the solution and edit connection string in `WebAPI/appsettings.*.json` (where `*` means config that you would like to change).

### Migrations
Default command will look like following:

```
dotnet ef migrations add "SampleMigration" --project src\Infrastructure --startup-project src\WebAPI --output-dir Infrastructure\Migrations
```

Depending on the path where you're at, the command will look different.
Migrations are applied automatically just right after running up the solution, so you will not have to update it with `Update-Database`.

## In case of certification problems on Linux dev configs
1. Generate a custom self-signed certificate using [these instructions](https://stackoverflow.com/a/59702094/16231079)
2. To `appsettings.Development.json` add these lines:
```
"Kestrel": {
    "Certificates": {
        "Default": {
            "Path": "<your full path>/localhost.pfx",
            "Password": ""
        }
    }
}
```

All these instuctions are not needed in Windows where HTTPS configs are being set by default and for production configs because they are having another certificates that are not self-signed.

## Creating new project with template

### By command line

1. With command terminal go to this repository folder
2. To install a template run the following:
```
dotnet new --install .
```
3. Create a project
```
dotnet new base-microservice
```

### By JetBrains Rider IDE
1. Press **New Solution** button in the top right corner.
2. Press **More Templates** and then **Install Template**. Search for the directory of our template.
3. Click **Create**.

