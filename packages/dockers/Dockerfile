# Use the official .NET SDK image to build the application
FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build

FROM node:18 

# Set the working directory
WORKDIR /app

# Copy the project files
COPY . ./

# Restore dependencies
RUN dotnet restore

# Build the application
RUN dotnet publish -c Release -o /out

# Use the runtime image to run the application
FROM mcr.microsoft.com/dotnet/runtime:7.0

# Set the working directory
WORKDIR /app

# Copy the published output from the build stage
COPY --from=build /out .

# Set the entry point to run the application
ENTRYPOINT ["dotnet", "YourApp.dll"]