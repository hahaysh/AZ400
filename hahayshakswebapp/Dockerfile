FROM mcr.microsoft.com/dotnet/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:3.1 AS build
WORKDIR /src
COPY ["hahayshakswebapp.csproj", ""]
RUN dotnet restore "./hahayshakswebapp.csproj"
COPY . .
WORKDIR "/src/."
RUN dotnet build "hahayshakswebapp.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "hahayshakswebapp.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "hahayshakswebapp.dll"]
