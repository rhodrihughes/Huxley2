
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build-env
WORKDIR /app


COPY *.csproj ./
RUN dotnet restore


COPY . ./
RUN dotnet publish -c Release -o out --no-restore


FROM mcr.microsoft.com/dotnet/runtime:8.0-alpine
WORKDIR /app

COPY --from=build-env /app/out .

ENTRYPOINT ["dotnet", "Huxley2.dll"]
