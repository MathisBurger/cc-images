FROM eclipse-temurin:21-jdk

# Install Maven
RUN apt-get update && \
    apt-get install -y maven && \
    apt-get clean

# Arbeitsverzeichnis festlegen
WORKDIR /app

COPY pom.xml .

RUN mvn clean install
RUN mvn dependency:go-offline

COPY settings.xml /root/.m2/settings.xml