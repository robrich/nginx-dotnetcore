FROM microsoft/aspnetcore-build:2.0 as build

WORKDIR /app

COPY DynamicContent.csproj .
RUN dotnet restore

COPY . .
RUN dotnet build -c Release
RUN dotnet publish -c Release -o dist


FROM microsoft/aspnetcore:2.0

WORKDIR /app

COPY --from=build /app/dist .

ENV ASPNETCORE_URLS http://+:5000
EXPOSE 5000

CMD ["dotnet", "DynamicContent.dll"]
