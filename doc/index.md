# Getting Started

Npgsql has an Entity Framework Core provider. It mostly behaves like a any other EFCore provider (e.g. SQL Server) - all the information in the [general EF Core docs](https://docs.microsoft.com/en-us/ef/core/index) applies. If you're just getting started with EF Core, those docs are the best place to start.

Development happens in the [Npgsql.EntityFrameworkCore.PostgreSQL](https://github.com/npgsql/Npgsql.EntityFrameworkCore.PostgreSQL) repository, all issues should be reported there.

## Using the Npgsql EF Core Provider

To use the Npgsql EF Core provider, simply add a dependency on `Npgsql.EntityFrameworkCore.PostgreSQL`. You can follow the instructions in the general [EF Core Getting Started docs](https://docs.microsoft.com/en-us/ef/core/get-started/).

Following is an example project.json using Npgsql EF Core:

```json
{
  "version": "1.0.0-*",
  "buildOptions": {
    "debugType": "portable",
    "emitEntryPoint": true
  },
  "dependencies": {
    "Npgsql.EntityFrameworkCore.PostgreSQL": "1.1.0",
    "Microsoft.EntityFrameworkCore.Design": {
      "version": "1.1.0",
      "type": "build"
    }
  },
  "frameworks": {
    "netcoreapp1.1": {
      "dependencies": {
        "Microsoft.NETCore.App": {
          "type": "platform",
          "version": "1.1.0"
        }
      }
    }
  },
  "tools": {
    "Microsoft.EntityFrameworkCore.Tools.DotNet": "1.1.0-preview4-final"
  }
}
```

## Using an Existing Database (Database-First)

The Npgsql EF Core provider also supports reverse-engineering a code model from an existing PostgreSQL database ("database-first"). To do so, add a dependency on Npgsql.EntityFrameworkCore.PostgreSQL.Design. Then, execute the following if you're using dotnet cli:

```bash
dotnet ef dbcontext scaffold "Host=localhost;Database=mydatabase;Username=myuser;Password=mypassword" Npgsql.EntityFrameworkCore.PostgreSQL
```

Or with Powershell:

```powershell
Scaffold-DbContext "Host=localhost;Database=mydatabase;Username=myuser;Password=mypassword" Npgsql.EntityFrameworkCore.PostgreSQL
```
