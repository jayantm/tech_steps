# Application Boiler Plate

## PHP based

* Laravel app

## Java based

### Jersey 2
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
	<name>restex Maven Webapp</name>
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
* Add Package
  * Add package path com.test.restex or package path com/test/rest, under src/main/java
* Add Application code
  * Add new File Application.java into package (src/main/java/com/test/restex/Application.java)
```java
package com.test.restex;

import org.glassfish.jersey.server.ResourceConfig;

public class Application extends ResourceConfig {

	public Application() {
		packages(this.getClass().getPackage().getName());
	}
}

```
* Add Sample Rest API code (src/main/java/com/test/restex/HelloWS.java)
```java
package com.test.restex;

import javax.ws.rs.GET;
import javax.ws.rs.Path;
import javax.ws.rs.PathParam;
import javax.ws.rs.Produces;
import javax.ws.rs.core.MediaType;
import javax.ws.rs.core.Response;

@Path("/hello")
public class HelloWS {

	private Response sayHello(String name) {
		return Response.ok("Hello "+name).build();
	}

	@GET
	@Path("/text/{name}")
	@Produces(MediaType.TEXT_PLAIN)
	public String world(@PathParam("name") String name) {
		return sayHello(name).toString();
	}

	@GET
	@Path("/xml/{name}")
	@Produces(MediaType.APPLICATION_XML)
	public Response xmlWorld(@PathParam("name") String name) {
		return sayHello(name);
	}

	@GET
	@Path("/json/{name}")
	@Produces(MediaType.APPLICATION_JSON)
	public Response jsonWorld(@PathParam("name") String name) {
		return sayHello(name);
	}
}
```
* Update web.xml
```xml
<web-app xmlns="http://java.sun.com/xml/ns/javaee" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://java.sun.com/xml/ns/javaee 
          http://java.sun.com/xml/ns/javaee/web-app_3_0.xsd"
	version="3.0">

	<display-name>Servlet 3.0 Web Application</display-name>

	<servlet>
		<servlet-name>restex</servlet-name>
		<servlet-class>org.glassfish.jersey.servlet.ServletContainer</servlet-class>
		<init-param>
			<param-name>javax.ws.rs.Application</param-name>
			<param-value>com.test.restex.Application</param-value>
		</init-param>
	</servlet>
	<servlet-mapping>
		<servlet-name>restex</servlet-name>
		<url-pattern>/api/*</url-pattern>
	</servlet-mapping>
</web-app>
```
* Build/Compile
```sh
$ mvn clean install
$ mvn package
$ cp restex.war apache-tomcat/webapps
```
* Run/Debug
```sh
$ mvn tomcat:run
$ mvnDebug tomcat:run
```
#### Normal

## NodeJS based

* Express
