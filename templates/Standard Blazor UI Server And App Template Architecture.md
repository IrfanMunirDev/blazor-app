# Standard Blazor UI Template Architecture

Whenever a new Blazor frontend presentation layer is requested, it MUST follow this multi-project structure and naming convention:

## Required Projects & Layers
1. `{ProjectName}.App` - Razor Class Library housing layouts (`MainLayout.razor`), global navigation (`NavMenu.razor`), and routable Blazor feature pages.
2. `{ProjectName}.Server` - ASP.NET Core web host project responsible for booting the application, handling runtime configurations, and referencing the App layer.

## Standard Configuration Files Required
- Solution file (`{ProjectName}.UI.sln`) linking the Server host and App library projects correctly.
- Project reference configuration where `{ProjectName}.Server` references `{ProjectName}.App`.