Prompt: Scaffold Docker Build for Split Architecture
Please generate a production-ready Dockerfile and .dockerignore for the ServiceFlow application.

Requirements:

Use the official .NET 10 SDK image for the build stage.

Use the official .NET 10 ASP.NET Core runtime image for the final stage.

Account for the multi-project architecture: restore and build both the ServiceFlow.Server host and its referenced ServiceFlow.App project.

Publish the ServiceFlow.Server project in Release mode.

Expose standard web ports (80/8080).

Place the generated files in the root src directory.