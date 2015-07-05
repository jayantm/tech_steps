# Application Boiler Plate

## PHP based

* Laravel app

## Java based

### Jersey
#### Maven
* Create a maven application project
  * Command line 
```mvn archetype:generate -DgroupId=com.test -DartifactId=restex -DarchetypeArtifactId=maven-archetype-webapp -DinteractiveMode=false```
  * IDE Eclipse/IntelliJ/Netbeans
    * New Maven Project
    * Archetype: maven-archetype-webapp
    * GroupId: com.test
    * ArtifactId: restex
* Folder Structure
* Update Web Descriptor File (web.xml)
```xml
<web-app xmlns="http://java.sun.com/xml/ns/javaee"
   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
   xsi:schemaLocation="http://java.sun.com/xml/ns/javaee 
   http://java.sun.com/xml/ns/javaee/web-app_3_0.xsd"
   version="3.0">
   <display-name>Servlet 3.0 Web Application</display-name>
</web-app>
```
* Add Dependency (pom.xml)
```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<groupId>com.test</groupId>
	<artifactId>restex</artifactId>
	<packaging>war</packaging>
	<version>0.0.1</version>
	<name>topup Maven Webapp</name>
	<url>http://maven.apache.org</url>
	<dependencies>
		<dependency>
			<groupId>org.glassfish.jersey.containers</groupId>
			<artifactId>jersey-container-servlet</artifactId>
			<version>2.14</version>
		</dependency>
	</dependencies>
	<build>
		<finalName>restex</finalName>
	</build>
</project>
```
#### Normal

## NodeJS based

* Express
