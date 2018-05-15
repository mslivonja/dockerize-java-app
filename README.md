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

## Creating sample project using quickstart artifact

Sample application is built in interactive mode. Artifact requires following information to complete:
GroupId, ArtifactId, version, and App name.

$ docker run -it --rm -v /docker/dockerize-java-app:/app -w /app apache/mvn:3.3-jdk-8 archetype:generate -DarchetypeGroupId=org.apache.maven.archetypes -DarchetypeArtifactId=maven-archetype-quickstart -DarchetypeVersion=1.3

## Building sample project using maven

$ docker run --rm -v /docker/dockerize-java-app/app:/app -w /app apache/mvn:3.3-jdk-8 clean package

## Running sample project using maven

$ docker run --rm -v /docker/dockerize-java-app/app:/app -w /app apache/mvn:3.3-jdk-8 exec:java -Dexec.mainClass="com.ericsson.oss.App"