# TODO

# We use .NET Core SDK version 3.1 for the build.

# Run restore.sh and then build.sh - you'll need to make
# the files executable first with chmod +x <filename>.

# Build output is in the folder:
#  /out

# The app should run using a .NET Core ASP.NET 3.1 image, with a minimal OS.
 
# We need to set four environment variables - 
# DOTNET_VERSION and APP_VERSION
# Widgetario__ProductsApi__Url set to "http://products-api/products"
# Widgetario__StockApi__Url set to "http://stock-api:8080/stock"

# The startup command needs to run the DLL  from the build:
#  dotnet Widgetario.Web.dll

#
FROM mcr.microsoft.com/dotnet/core/sdk:3.1-alpine as builder
WORKDIR /src
COPY . .

RUN chmod +x restore.sh && ./restore.sh
RUN chmod +x build.sh && ./build.sh

#
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1-alpine
WORKDIR /app
COPY --from=builder /out/ .

ENV DOTNET_VERSION="3.1" \
APP_VERSION="1.0.0" \
Widgetario__ProductsApi__Url="http://products-api/products" \
Widgetario__StockApi__Url="http://stock-api:8080/stock"

CMD [ "dotnet", "Widgetario.Web.dll" ]
