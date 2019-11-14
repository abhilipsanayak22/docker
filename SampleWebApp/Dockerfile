
# build phase
FROM mcr.microsoft.com/dotnet/core/sdk:latest AS build
WORKDIR /src
COPY ["SampleWebApp.csproj", "./"]
RUN dotnet restore
COPY . .
RUN dotnet build -c Release -o /bin
RUN dotnet publish -c Release -o /publish

# Stage 2
FROM mcr.microsoft.com/dotnet/core/aspnet:latest AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
COPY --from=build /publish .
ENTRYPOINT ["dotnet", "SampleWebApp.dll"]


