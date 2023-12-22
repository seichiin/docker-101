# TODO

# We use Maven version 3.6.3 for the build, with JDK 11.

# Run restore.sh and then build.sh - you'll need to make
# the files executable first with chmod +x <filename>.

# Build output is a single JAR file:
#  /usr/src/api/target/products-api-0.1.0.jar

# The app should run on OpenJDK 11.0.12, it can use a minimal OS. 

# We need to set two environment variables - 
# JRE_VERSION and APP_VERSION. 

# The startup command needs to run the JAR file from the build:
#  java -jar products-api-0.1.0.jar

#
FROM maven:3.6.3-jdk-11 as builder
WORKDIR /usr/src/api
COPY . .

RUN chmod +x restore.sh && ./restore.sh
RUN chmod +x build.sh  && ./build.sh

#
FROM openjdk:11.0.12-jre-slim-buster
WORKDIR /app
COPY --from=builder /usr/src/api/target/products-api-0.1.0.jar .

ENV JRE_VERSION="11.0.12"
ENV APP_VERSION="0.4.0"

EXPOSE 80

ENTRYPOINT ["java", "-jar", "/app/products-api-0.1.0.jar"]
