FROM maven:3.8.6-jdk-8-slim as mvn-build
WORKDIR /app/build
COPY ./src ./src
COPY pom.xml .
COPY .mvn .mvn
#COPY mvnw .
RUN mvn clean install -Dmaven.test.skip=true

FROM openjdk:8-jre-alpine
WORKDIR /app
COPY --from=mvn-build /app/build/target/*.jar ./spring-app.jar
CMD ["java", "-jar", "/app/spring-app.jar"]

