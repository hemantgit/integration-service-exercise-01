## Calling a REST service using Camel
This project shows an example of a route that calls a rest service using the Spring DSL. This particular example registers a new user into the backend system (training-server). Note that the route does not make any transformation or routing, just delegating the REST call from the Portal Server to the REST API.

## Prerequisites
You must have a CXP project configured in your machine before performing this exercise. If you do not have one, please follow the instructions on the following site: https://my.backbase.com/docs/how-to-guides/getting-your-first-launchpad-based-portal-set-up/

You must have the Training Server up and running. Here you can find the github page for the training-server project: https://github.com/Backbase/training-server

### Installation & Configuration

- Copy **integration-service-exercise-01** into the **services** folder of your project. You can use the git command to clone the project: ```git clone https://github.com/marciofk/integration-service-exercise-01.git```

- Include **integration-service-exercise-01** module to the build.  Open `services/pom.xml` and add **integration-service-exercise-01** in the `<modules>` section: 
	```xml
	    <modules>
	        ...	    
	        <module>integration-service-exercise-01</module>
	        ...
	    </modules>
	```	
	Re-compile **services** by executing `mvn clean install` in the **services** folder.
	
- Enable newly created module in the Portalserver application. In the `<dependencies>` section of `webapps/portalserver/pom.xml`, add the following dependency:

	```xml
	    <dependency>
	        <groupId>com.backbase.training</groupId>
	        <artifactId>integration-service-exercise-01</artifactId>
	        <version>1.0-SNAPSHOT</version>
	    </dependency>
	```

### Build & Run

- You must restart your portal server if the application is already running. 
- Test the route execution by using a REST client app (e.g. Postman)
- Example:

```javascript
POST http://localhost:7777/portalserver/services/rest/player/register
{
   "username" : "Edsger",
   "fullname" : "Edsger Dijkstra",
   "password" : "dijkstra123",
   "emailAddress" : "dijkstra@gmail.com",
   "birthDay" : "1930-05-11",
   "firstName" : "Edsger",
   "lastName" : "Dijkstra"
}	
``` 


 






