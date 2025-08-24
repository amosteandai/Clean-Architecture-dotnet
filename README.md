# Clean-Architecture-dotnet
Build .NET 9 APIs in Clean Architecture, user Identity system and Azure deployment using CI/CD

dotnet new webapi -n Restaurants.API --no-openapi -controllers
dotnet new sln -n Restaurants
dotnet sln add ./Restaurants.API

dotnet new classlib -n Restaurants.Domain
dotnet sln add ./Restaurants.Domain

dotnet new classlib -n Restaurants.Application
dotnet sln add ./Restaurants.Application

dotnet add ./Restaurants.Application/Restaurants.Application.csproj reference ./Restaurants.Domain/Restaurants.Domain.csproj
dotnet add ./Restaurants.API/Restaurants.API.csproj reference ./Restaurants.Application/Restaurants.Application.csproj

dotnet new classlib -n Restaurants.Infrastructure
dotnet sln add ./Restaurants.Infrastructure

dotnet add ./Restaurants.Infrastructure/Restaurants.Infrastructure.csproj reference ./Restaurants.Application/Restaurants.Application.csproj
dotnet add ./Restaurants.API/Restaurants.API.csproj reference ./Restaurants.Infrastructure/Restaurants.Infrastructure.csproj



PM> add-migration Init -Project Restuarants.Infrastructure -StartupProject Restaurants.API
