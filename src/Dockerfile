FROM mcr.microsoft.com/dotnet/core/sdk:2.2 AS build
WORKDIR /app

# copy csproj and restore as distinct layers
COPY *.sln .
COPY DemoApp/*.csproj ./DemoApp/
RUN dotnet restore

# copy everything else and build app
COPY DemoApp/. ./DemoApp/
WORKDIR /app/DemoApp
RUN dotnet publish -c Release -o out


FROM mcr.microsoft.com/dotnet/core/aspnet:2.2 AS runtime
WORKDIR /app
# ENV ASPNETCORE_ENVIRONMENT Development
COPY --from=build /app/DemoApp/out ./
ENTRYPOINT ["dotnet", "DemoApp.dll"]