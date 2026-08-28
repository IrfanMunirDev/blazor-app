# Standard Enterprise Service Template Architecture

Whenever a new service or project is requested, it MUST follow this exact multi-project structure and naming convention:

## Required Projects & Layers
1. `{ProjectName}.API` - ASP.NET Core web host and controllers.
2. `{ProjectName}.Data` - Data access implementations and repositories.
3. `{ProjectName}.Database` - Database scripts and configurations.
4. `{ProjectName}.DataModels` - Domain entities and data transfer objects.
5. `{ProjectName}.Services` - Core business logic layer.
6. `{ProjectName}.Migrations` - EF Core migration history.
7. `{ProjectName}.Utils` - Shared utilities and extension methods.
8. `{ProjectName}.FuntionalTests` - End-to-end and functional test suites.
9. `{ProjectName}.UnitTests` - Isolated unit tests.

## Standard Configuration Files Required
- `.dockerignore`
- `.gitignore`
- `Dockerfile`
- Solution file (`{ProjectName}.sln`) linking all projects correctly.