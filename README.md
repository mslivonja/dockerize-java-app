# dockerize-java-app
Dockerize Java app.

# Building Oracle JDK docker image

docker build -f Dockerfile-oracle-jdk8 -t oracle/oracle-jdk:8 .

# Testing the image

## Compiling the Java class
docker run --rm -v /docker/dockerize-java-app:/app -w /app --entrypoint "javac" oracle/oracle-jdk:8 Main.java

## Running Java app
docker run --rm -v /docker/dockerize-java-app:/app -w /app oracle/oracle-jdk:8 Main

# Building Maven image

$ docker build -f Dockerfile-mvn3 -t apache/mvn:3.3-jdk-8
