FROM mcr.microsoft.com/dotnet/sdk:6.0-alpine AS build

WORKDIR /app

COPY Forecast.csproj .
RUN dotnet restore

COPY . .

RUN dotnet publish -c Release -o /app/publish

FROM mcr.microsoft.com/dotnet/aspnet:6.0-alpine

WORKDIR /app

COPY --from=build /app/publish .

EXPOSE 80

ENTRYPOINT ["dotnet", "Forecast.dll"]
