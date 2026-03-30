# Stage 1: Use Maven for building
FROM maven:3.9.6-eclipse-temurin-21 as build
WORKDIR /app
COPY ./discoverserver ./discoverserver
WORKDIR /app/discoverserver
RUN mvn clean package -DskipTests

# Staage 2: use OpenJDK for running
FROM eclipse-temurin:21-jre-jammy
WORKDIR /app
COPY --from=build /app/discoverserver/target/*.jar discoverserver.jar
EXPOSE 8761
ENTRYPOINT ["java","-jar","discoverserver.jar"]
