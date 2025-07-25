# Stage 1: Build the application
FROM maven:3.9.4-eclipse-temurin-17 AS build
WORKDIR /app

# Copy all files and build
COPY pom.xml .
COPY src ./src
RUN mvn clean package -DskipTests

# Stage 2: Create minimal runtime image
FROM eclipse-temurin:17-jre-alpine
WORKDIR /app

# Copy the JAR from the build stage
COPY --from=build /app/target/demo-0.0.1-SNAPSHOT.jar app.jar

# Run the application
ENTRYPOINT ["java", "-jar", "app.jar"]
