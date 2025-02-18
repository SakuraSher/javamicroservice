FROM  maven:3.8.6-amazoncorretto-17 AS build

WORKDIR /app

COPY pom.xml .

COPY src ./src

RUN mvn clean package -DskipTests

FROM openjdk:17-oracle

WORKDIR /home/app

COPY --from=build /app/target/auth-service-*.jar /app/app.jar

CMD ["java", "-jar", "/app/app.jar"]
#just adding a comment to 