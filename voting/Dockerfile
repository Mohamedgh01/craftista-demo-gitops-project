# Stage 1: Build the Spring Boot application
FROM maven:3.9.4-eclipse-temurin-19-alpine AS build

WORKDIR /app

COPY . .

# Build the application (skip tests)
RUN mvn package -DskipTests

# Stage 2: Create a smaller image for production
FROM eclipse-temurin:19-jdk-alpine

WORKDIR /app

# Copy the JAR built in the previous stage
COPY --from=build /app/target/voting-0.0.1-SNAPSHOT.jar app.jar

EXPOSE 8080

CMD ["java", "-jar", "app.jar"]
