# Stage 1: Build using Maven and JDK 21
FROM maven:3.9.6-eclipse-temurin-21 AS build
COPY . .
RUN mvn clean package -DskipTests

# Stage 2: Run using JDK 21
FROM eclipse-temurin:21-jdk-jammy
COPY --from=build /target/*.jar demo.jar
EXPOSE 9090
ENTRYPOINT ["java","-jar","demo.jar","--server.port=9090"]