FROM mcr.microsoft.com/dotnet/core/aspnet:2.2 AS base
WORKDIR /app
EXPOSE 80

FROM mcr.microsoft.com/dotnet/core/sdk:2.2 AS build
WORKDIR /src
COPY ["ErhardtEnterprises.SteeltoeExample.csproj", "."]
RUN dotnet restore "ErhardtEnterprises.SteeltoeExample.csproj"
COPY . .
RUN dotnet build "ErhardtEnterprises.SteeltoeExample.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "ErhardtEnterprises.SteeltoeExample.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "ErhardtEnterprises.SteeltoeExample.dll"]
