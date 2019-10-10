# escape=`
FROM microsoft/dotnet:2.2.104-sdk-alpine3.8 as builder

WORKDIR /src
COPY SignupApiCore/SignupApiCore.csproj .
RUN dotnet restore

COPY SignupApiCore/ .
RUN dotnet publish

# app image
FROM microsoft/dotnet:2.2.2-aspnetcore-runtime-alpine3.8

CMD ["dotnet", "SignupApiCore.dll"]

WORKDIR /dotnetapp
COPY --from=builder /src/bin/Debug/netcoreapp2.2/publish .