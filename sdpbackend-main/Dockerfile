# Step 1: Build stage (Maven + JDK)
FROM maven:3.9.5-eclipse-temurin-21 AS build
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn clean package -DskipTests

# Step 2: Runtime stage (JRE only)
FROM eclipse-temurin:21-jre-alpine
WORKDIR /app
COPY --from=build /app/target/SDPProject-0.0.1-SNAPSHOT.jar app.jar
EXPOSE 8086
ENTRYPOINT ["java", "-jar", "app.jar"]
