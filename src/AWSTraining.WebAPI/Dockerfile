FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src

COPY AWSTraining.sln ./

COPY src/AWSTraining.WebAPI/*.csproj src/AWSTraining.WebAPI/
# if you have more projects, add:
# COPY src/SharedLibrary/*.csproj src/SharedLibrary/
# COPY src/AnotherApi/*.csproj src/AnotherApi/

RUN dotnet restore

COPY . .

WORKDIR /src/src/AWSTraining.WebAPI
RUN dotnet publish -c Release -o /app/publish

FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS runtime
WORKDIR /app
COPY --from=build /app/publish .

ENV ASPNETCORE_URLS=http://+:80
EXPOSE 80
ENTRYPOINT ["dotnet", "AWSTraining.WebAPI.dll"]
