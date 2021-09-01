
<p align="center">
	<img width="70" height="70" src="spd.jpg" alt="Spring boot">
  <h1 align="center">Build Spring boot application with Docker</h1>
</p>


[![Platform](https://img.shields.io/badge/Java-11%2B-red)](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html)
[![Framework](https://img.shields.io/badge/Spring%20Boot-2.5.4-green)](https://spring.io/projects/spring-boot)
[![License](https://img.shields.io/badge/License-MIT-green)](https://github.com/VishnuViswam/spring-boot-docker-basic/blob/main/LICENSE)

## About Project
 This is a simple spring boot application with the basic details of docker implementation.


## Repository contains

* Spring boot application source code.
* Docker file.

## How it works using docker container
* Create a simple spring boot application. 
* Create a docker file under parent directory.
* Paste the following code in the docker file.

```
FROM openjdk:11-jre
VOLUME /tmp
ADD target/springBootDocker-1.0.0.jar springBootDocker.jar
ENTRYPOINT ["java","-jar","/springBootDocker.jar"]
```
**FROM openjdk:11-jre** <br>
Here we are creating a docker image of openJre 11. And it will act as the parent image of our application.<br><br>
**VOLUME /tmp**<br>
This line is for allocating a folder to install our application. Because when we are executing our application tomcat needs space to create a work folder.<br><br>
**ADD target/springBootDocker-1.0.0.jar springBootDocker.jar**<br>
By this line, we are just specifying the path of the executable jar file and assign it to the "springBootDocker.jar" named file.<br><br>
**ENTRYPOINT ["java","-jar","/springBootDocker.jar"]**<br>
Here we are mentioning the comment that used to run the jar file in through the cmd.<br><br>

* Go to the spring boot application root directory open the cmd and create jar file using following command
  ```mvn clean install```
  ### Docker Commands
* Execute the following docker command to create the docker image.<br>
  ```docker build -t <imagename> .```
  * Here "-t" is used for mention the tag of container. 
  * Our docker file is present in the same directory where we are executing this command. That is why we mentioned a dot at last of to commend
* To list the created docker images please use the following command. And make sure that our docker image is in the list.<br>
  ```docker image ls```
* Now it is time to run the docker image. Use the following command to run the docker image.<br> 
  ```docker run -p8080:8080 <imagename>```
  * Here java application will be running inside the docket container , so we need to expose the application running port to outside the container. "-p8080:8080" is the command which expose the port to outside the docket container.
### Thanks :)
