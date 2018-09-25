FROM microsoft/dotnet:2.1.402-sdk AS build
LABEL maintainer="heisendumb"
WORKDIR API/

# Copy *.csproj 
COPY API ./

# With everything copied, its time to restore as distinct layers and build api
RUN dotnet restore \
    && dotnet publish -c Release -o out

# Runtime
FROM microsoft/dotnet:2.1-runtime
WORKDIR /api
COPY --from=build /API/APIContagem/out .
ENTRYPOINT ["dotnet", "APIContagem.dll"]