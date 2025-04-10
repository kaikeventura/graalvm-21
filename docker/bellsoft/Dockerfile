FROM gradle:8.4.0-jdk21 AS build
WORKDIR /app
COPY --chown=gradle:gradle .. .
RUN ./gradlew build -x test

FROM bellsoft/liberica-runtime-container:jre-21-cds-glibc
WORKDIR /app
COPY --from=build /app/build/libs/*.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]
