FROM eclipse-temurin:21-jdk

# Install Maven
RUN apt-get update && \
    apt-get install -y maven && \
    apt install libx11-6 libxext6 libxrender1 libxtst6 libxi6 libgl1 xvfb libgtk-3-0 libgdk-pixbuf2.0-0 libpango-1.0-0 -y && \
    apt-get clean

# Arbeitsverzeichnis festlegen
WORKDIR /app

COPY pom.xml .

RUN mvn clean install
RUN mvn dependency:go-offline

COPY settings.xml /root/.m2/settings.xml