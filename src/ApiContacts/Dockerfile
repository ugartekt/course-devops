FROM mcr.microsoft.com/dotnet/sdk:10.0 AS build 
WORKDIR /src
COPY ApiContacts.csproj .
RUN dotnet restore
COPY . .

RUN dotnet build "ApiContacts.csproj" -c Release -o /app/build

RUN dotnet publish -c release -o /app

FROM mcr.microsoft.com/dotnet/aspnet:10.0
WORKDIR /app
COPY --from=build /app .
ENTRYPOINT ["dotnet", "ApiContacts.dll"]

#Ejecuta los comandos:

#docker build -t aminespinoza/apicontacts .

#docker run -it --rm --name apicontacts -p 8080:8080 ugarte/apicontacts