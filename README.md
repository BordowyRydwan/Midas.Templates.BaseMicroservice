# Base Microservice Template
It's a solution template for microservice with basic features. The template contains ASP.NET + EF Core solution with unit and integration tests.

Following instructions are for Debian-based systems - but on Windows machines it should be similar or even simpler. 

## Environment used
- JetBrains Rider
- SQL Server Express
- .NET 6

## Tech stack used
- ASP.NET Core 6
- Entity Framework Core 6
- AutoMapper
- nUnit, Moq

## Getting started

1. Install the latest [.NET 6 SDK](https://dotnet.microsoft.com/en-us/download/dotnet/6.0)
2. Install SQL Server Express instance
3. Clone this repository
4. Go through **Database configuration** section
5. Run `WebAPI` project

## Database configuration

### In-memory databases

Linux users will have to install the [SQL Server Express instance](https://docs.microsoft.com/en-us/sql/linux/quickstart-install-connect-ubuntu?view=sql-server-ver16). By default in this repository InMemory databases are turned off. 

To turn it on back again, edit `.json` files in `WebAPI` solution as follows:

```
"UseInMemoryDatabase": true
```

### Connection strings

You will also need to adjust a connection string. In order to do it, open the solution and edit connection string in `WebAPI/appsettings.*.json`.

### Migrations
Default command will look like following:

```
dotnet ef migrations add "SampleMigration" --project src\Infrastructure --startup-project src\WebAPI --output-dir Infrastructure\Migrations
```

Depending on the path where you're at, the command will look different.

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

