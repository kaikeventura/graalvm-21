FROM gradle:jdk21-graal AS build
WORKDIR /app
COPY --chown=gradle:gradle . .
RUN ./gradlew build -x test

FROM ghcr.io/graalvm/jdk-community:21
WORKDIR /app
COPY --from=build /app/build/libs/*.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]
