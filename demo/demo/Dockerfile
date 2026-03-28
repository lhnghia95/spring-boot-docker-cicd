# Stage 1: Build với Maven
FROM maven:3-eclipse-temurin-17-alpine AS build
WORKDIR /app

# Copy pom trước để cache dependency
COPY pom.xml .
RUN mvn dependency:go-offline -B

COPY src ./src
RUN mvn clean package -DskipTests -B

# Stage 2: Final image (nhẹ)
FROM eclipse-temurin:17-jdk-alpine
WORKDIR /app

# Copy jar từ stage build
COPY --from=build /app/target/*.jar app.jar

EXPOSE 8080

# Tối ưu JVM cho container
ENTRYPOINT ["java", \
    "-XX:+UseG1GC", \
    "-XX:MaxGCPauseMillis=100", \
    "-Xmx512m", \
    "-Xms256m", \
    "-jar", \
    "app.jar", \
    "--server.port=8080"]