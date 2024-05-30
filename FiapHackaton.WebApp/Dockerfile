
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build

WORKDIR /app

COPY . ./

COPY ["FiapHackaton.WebApp.csproj", "."]

RUN dotnet restore
COPY . ./
RUN dotnet publish "./FiapHackaton.WebApp.csproj" -c Release -o out

FROM nginx:1.23.0-alpine

WORKDIR /app
EXPOSE 8090


COPY nginx.conf /etc/nginx/nginx.conf
COPY --from=build /app/out/wwwroot /usr/share/nginx/html