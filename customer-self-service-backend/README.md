# Lakeside Mutual : Customer Self-Service Backend

The Customer Self-Service backend provides an HTTP resource API for the Customer Self-Service frontend and the Policy Management frontend.

## IDE 

To view and edit the source code, we recommend the official Eclipse-based IDE [Spring Tool Suite](https://spring.io/tools/sts) (STS). Other IDEs might work as well, but this application has only been tested with STS.

## Installation

The Customer Self-Service backend is a [Spring Boot](https://projects.spring.io/spring-boot/) application and its dependencies are managed with [Apache Maven](https://maven.apache.org/). To get started, install Java and Maven:

1. Install JDK 8 or above (see [Java SE Development Kit 8 Downloads](http://www.oracle.com/technetwork/pt/java/javase/downloads/jdk8-downloads-2133151.html) for installation instructions)
2. Install Maven (see [https://maven.apache.org](https://maven.apache.org) for installation instructions). Note that most IDEs, such as the Spring Tool Suite, already contain a bundled copy of Maven. If this project is only built and launched from within the IDE, this step can be skipped.

## Launch Application

In order to launch the Customer Self-Service backend, you can run the command `mvn spring-boot:run`. When startup is completed, the output should look like this:

```
2018-05-07 14:21:13.011  INFO 12773 --- [  restartedMain] c.l.customerselfservice.DataLoader              : DataLoader has successfully imported all application dummy data, the application is now ready.
``` 

Alternatively, you can download and install the Spring Tool Suite: <!-- Above we say that we recommend STS as IDE, partial contradiction? -->

1. Install Spring Tool Suite (you can download the IDE from [https://spring.io/tools/sts](https://spring.io/tools/sts))
2. Start Spring Tool Suite and create a new workspace or open an existing one
3. Import the project:<br>
      1. Go to File -> Import -> Maven -> Existing Maven Projects
      2. Select the `LakesideMutual` repository as the root directory
      3. Enable the check mark for the `customer-self-service-backend` project
      4. Click *Finish* to import the project
4. Right-click on the project and select Run As -> Spring Boot App to start the application

By default, the Spring Boot application starts on port 8080. If this port is already used by a different application, you can change it in the 
`src/main/resources/application.properties` file.

Warnings about a `java.net.ConnectException: Connection refused` can safely be ignored. See the [FAQ](../FAQ.md#im-getting-a-connection-refused-connect-exception-on-startup) for details.

## Springfox
[Springfox](https://github.com/springfox/springfox) is an automated JSON API documentation tool for APIs built with Spring. To access the Springfox
documentation for the Customer Self-Service backend, go to the Swagger Web UI available at [http://localhost:8080/swagger-ui.html](http://localhost:8080/swagger-ui.html). The native Swagger file is available at [http://localhost:8080/v2/api-docs](http://localhost:8080/v2/api-docs).

## Testing
To run the automated tests for the Customer Self-Service backend, right-click on the project in the Spring Tool 
Suite and then click on `Run As -> JUnit Test`. The test classes are located in the `src/test/java` folder.

## Enabling Persistence
By default, the database will be re-created when the application is started and any changes that were made are lost. This is configured in `src/main/resources/application.properties` by the following setting:

```
spring.jpa.hibernate.ddl-auto=create-drop
```
If you want to persist your changes across restarts, change the setting to:
```
spring.jpa.hibernate.ddl-auto=update
```

## Spring Boot Admin
The application is configured to connect to the Spring Boot Admin on startup. See the [README](../spring-boot-admin/README.md#how-it-works) to learn more.