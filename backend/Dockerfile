FROM maven:3.8-openjdk-11 as mvn-cache
WORKDIR /backend
COPY pom.xml .
RUN mvn dependency:go-offline
COPY src/ /backend/src/
RUN mvn clean compile -DskipTests=true package

FROM openjdk:11-jdk as run-image
WORKDIR /
COPY --from=mvn-cache /backend/target/backend-0.0.1-SNAPSHOT.jar /backend/target/backend-0.0.1-SNAPSHOT.jar
EXPOSE 8080
CMD java -jar /backend/target/backend-0.0.1-SNAPSHOT.jar