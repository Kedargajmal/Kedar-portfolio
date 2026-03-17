# Stage 1: Build
FROM maven:3.8.5-openjdk-17 AS build
COPY . .
RUN mvn clean package -DskipTests

# Stage 2: Run
FROM openjdk:17.0.1-jdk-slim
COPY --from=build /target/*.jar demo.jar
EXPOSE 9090
ENTRYPOINT ["java","-jar","demo.jar"]