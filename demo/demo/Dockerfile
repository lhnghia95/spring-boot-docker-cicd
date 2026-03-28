FROM eclipse-temurin:17-jdk-alpine
COPY --from=build /app/target/*.jar app.jar

EXPOSE 8080

# Tối ưu JVM cho container
ENTRYPOINT ["java", \
  "-XX:+UseG1GC", \
  "-XX:MaxGCPauseMillis=100", \
  "-Xmx512m", \
  "-Xms256m", \
  "-jar", \
  "/app.jar", \
  "--server.port=8080"]