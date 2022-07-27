FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build-env
WORKDIR /app

RUN git clone https://github.com/cubomx/SocialNet-App.git

WORKDIR /app/SocialNet-App/API/

RUN cp appsettings.Development.json appsettings.json

# Use NuGet to restore dependencies, project-specifc tools
RUN dotnet restore

# Build databse
RUN dotnet tool install --global dotnet-ef --version 6.0.7
ENV PATH $PATH:/root/.dotnet/tools

RUN dotnet ef migrations add MyDB -o Data/Migrations
RUN dotnet ef database update 


RUN dotnet dev-certs https --trust


#Compiles the app, read dependencies and publish set of resulting
# files
RUN dotnet publish -c Release -o out

# Build runtime image
FROM mcr.microsoft.com/dotnet/aspnet:6.0
WORKDIR /app
COPY --from=build-env /app/SocialNet-App/API/out .
COPY --from=build-env /app/SocialNet-App/API/socialnet.db .
ENTRYPOINT ["dotnet", "API.dll"]