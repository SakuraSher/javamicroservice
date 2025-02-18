FROM maven:3.8.6-amazoncorretto-17 AS build
WORKDIR /app
COPY ./pom.xml ./
COPY ./src /app/src

RUN mvn clean package -DskipTests

FROM  eclipse-temurin:17-alpine

WORKDIR /home/app

COPY --from=build /app/target/config-server-*.jar  app.jar

EXPOSE 8080

CMD ["java","-jar","/app/app.jar"]
