FROM adoptopenjdk/openjdk11 as builder
LABEL maintainer="Tomoya Sasaki"

WORKDIR /app
COPY ./gradle gradle
COPY ./src src
COPY build.gradle build.gradle
COPY gradlew gradlew
COPY settings.gradle settings.gradle
RUN ./gradlew build

FROM adoptopenjdk/openjdk11:alpine-slim	as runner
EXPOSE 8080
WORKDIR /app
COPY --from=builder /app/build/libs/demo-0.0.1-SNAPSHOT.jar /app/
CMD ["java", "-jar", "demo-0.0.1-SNAPSHOT.jar"]