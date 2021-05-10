FROM gradle AS build
WORKDIR /home/gradle/project
COPY . .
RUN gradle build --scan


FROM openjdk:8-jdk-alpine
EXPOSE 8080
COPY --from=build /home/gradle/project/build/libs/*.jar /app.jar
ENTRYPOINT ["java","-jar","/app.jar"]