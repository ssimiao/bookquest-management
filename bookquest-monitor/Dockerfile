FROM gradle:jdk17-alpine AS build
COPY --chown=gradle:gradle . /home/gradle/src
WORKDIR /home/gradle/src
RUN gradle build --no-daemon

FROM ibm-semeru-runtimes:open-17.0.5_8-jre
COPY --from=build /home/gradle/src/build/libs/bookquest-monitor-0.0.1.jar app.jar
EXPOSE 8080
ENTRYPOINT java -jar -Duser.timezone="America/Sao_Paulo" app.jar
