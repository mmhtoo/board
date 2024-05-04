FROM maven:3.9.6-amazoncorretto-17 as build
WORKDIR /app
COPY pom.xml .
RUN mvn dependency:go-offline
COPY src ./src
RUN mvn package -DskipTests -e

FROM openjdk:17
WORKDIR /app
COPY --from=build /app/target/board-api-0.0.1-SNAPSHOT.jar ./app.jar
CMD ["java", "-jar", "./app.jar"]