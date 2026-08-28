# syntax=docker/dockerfile:1

# ---------------------------------------------------------------------------
# Build stage: restore & publish ServiceFlow.Server (with ServiceFlow.App)
# ---------------------------------------------------------------------------
FROM mcr.microsoft.com/dotnet/sdk:10.0 AS build
WORKDIR /src

# Copy solution and project files for layer-friendly restore of the
# split architecture (Server host + referenced App Razor Class Library).
COPY ["ServiceFlow.UI.sln", "./"]
COPY ["src/ServiceFlow.App/ServiceFlow.App.csproj", "src/ServiceFlow.App/"]
COPY ["src/ServiceFlow.Server/ServiceFlow.Server.csproj", "src/ServiceFlow.Server/"]

RUN dotnet restore "src/ServiceFlow.Server/ServiceFlow.Server.csproj"

# Copy remaining sources and publish the Server host in Release mode.
COPY ["src/ServiceFlow.App/", "src/ServiceFlow.App/"]
COPY ["src/ServiceFlow.Server/", "src/ServiceFlow.Server/"]

RUN dotnet publish "src/ServiceFlow.Server/ServiceFlow.Server.csproj" \
    -c Release \
    -o /app/publish \
    --no-restore

# ---------------------------------------------------------------------------
# Runtime stage: slim ASP.NET Core runtime
# ---------------------------------------------------------------------------
FROM mcr.microsoft.com/dotnet/aspnet:10.0 AS final
WORKDIR /app

ENV ASPNETCORE_URLS=http://+:8080
EXPOSE 80
EXPOSE 8080

COPY --from=build /app/publish .

ENTRYPOINT ["dotnet", "ServiceFlow.Server.dll"]