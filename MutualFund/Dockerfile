#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/aspnet:5.0 AS build-env
WORKDIR /app
#copy
#FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
#WORKDIR /src
#COPY ["DailySharePriceMS/DailySharePriceMS.csproj", "DailySharePriceMS/"]
#RUN dotnet restore "DailySharePriceMS/DailySharePriceMS.csproj"
#COPY . .
#WORKDIR "/src/DailySharePriceMS"
#RUN dotnet build "DailySharePriceMS.csproj" -c Release -o /app/build
COPY * .csproj ./
RUN dotnet restore
#FF
COPY . ./
#DD
RUN dotnet publish -c Release -o out
#DD
FROM mcr.microsoft.com/dotnet/sdk:5.0
WORKDIR /app
COPY --from=build-env /app/out .
ENTRYPOINT ["dotnet", "DailySharePriceMS.dll"]

