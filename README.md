# Docker Class Exercise

## Create your first Docker Image

### Step 1: Hello Docker World

1. In terminal, run the following command to clone the example:

```sh
git clone https://github.com/spring-guides/gs-spring-boot-docker.git
```

2. Next, in terminal, go to the folder: `gs-spring-boot-docker/complete`.

```sh
cd gs-spring-boot-docker/complete
```

3. Examine the following files within the folder:
    - gs-spring-boot-docker/complete/src/main/java/hello/***Application.java***
    - gs-spring-boot-docker/complete/***Dockerfile***

3. In terminal, use the following command line to run the application:

```sh
./mvnw install && java -jar target/spring-boot-docker-complete-0.0.1-SNAPSHOT.jar
```
 
**Note:** For gradle applications, run it with the command: `./gradlew build && java -jar build/libs/complete-0.0.1-SNAPSHOT.jar`

4. Go to [localhost:8080](http://localhost:8080) to see your "Hello Docker World" message.

### Step 2: Containerize It

1. To containerize the example application, update the ***Dockerfile*** for the Spring Boot project:


```dockerfile
FROM maven:3.9.8-eclipse-temurin-21
ARG JAR_FILE=target/*.jar
COPY ${JAR_FILE} app.jar
ENTRYPOINT ["java","-jar","app.jar"]
```

2. Next, to build the image, replace **`<your-docker-account-name>`** with your own Docker account name (repeat this for all other instances below) before running the following command line in the terminal: 
    
```sh
docker build -t <your-docker-account-name>/spring-boot-docker-complete .
```

**Note:** For those building on gradle, run the command: `docker build --build-arg JAR_FILE=build/libs/\*.jar -t your-docker-account-name/spring-boot-docker-complete .`

3. To run the image in a container, run the following command:

```sh
docker run -p 8080:8080 -t <your-docker-account-name>/spring-boot-docker-complete
```

4. Check out your Docker World Application at [localhost:8080](http://localhost:8080).

Congratulations! You’ve just created a Docker container for a Spring Boot app!


**Tip:** The prefix **`<your-docker-account-name>`** represents your repository name - which you may assign when creating an account on [Docker Hub](https://hub.docker.com). Prepending your repository name to your Docker image (e.g. ***`your-docker-account-name/docker-image-name`***) is a good practice, especially when you plan to push the image to a Docker Registry (e.g. Docker Hub, AWS ECR, GCR, etc).


