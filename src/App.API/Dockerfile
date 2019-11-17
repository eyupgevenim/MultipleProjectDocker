FROM mcr.microsoft.com/dotnet/core/aspnet:3.0-buster-slim AS base
WORKDIR /app
EXPOSE 80

FROM mcr.microsoft.com/dotnet/core/sdk:3.0-buster AS build
WORKDIR /src

# Keep the project list and command dotnet restore identical in all Dockfiles to maximize image cache utilization
COPY MultipleProjectDocker.sln .
COPY src/App.API/App.API.csproj src/App.API/
COPY src/App.Web/App.Web.csproj src/App.Web/

RUN dotnet restore MultipleProjectDocker.sln

COPY . .
WORKDIR /src/src/App.API
RUN dotnet publish --no-restore -c Release -o /app

FROM build AS publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "App.API.dll"]