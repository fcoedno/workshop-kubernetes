FROM gradle:jdk11 as builder
COPY --chown=gradle:gradle . /home/gradle/src
WORKDIR /home/gradle/src
RUN ./gradlew clean && \
    ./gradlew build

FROM openjdk:11.0.2-jre-stretch
COPY --from=builder /home/gradle/src/build/libs/*.jar /home/helloworld.jar
ENTRYPOINT ["/usr/bin/java", "-jar", "/home/helloworld.jar"]
