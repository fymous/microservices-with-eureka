# microservices-with-eureka

3 microservices and a eureka server.

Microservice 1: movie-catalog-service - calls ratings-data-service and then calls movie-info-service.  #port 8081

Microservice 2: ratings-data-service #port 8083

Microservice 3: movie-info-service #port 8082

Microservice 4: discovery-server with Eureka # default port 8761.

Eureka is used for service discovery and also for client side load balacing.
Provides few annotation like.. @LoadBalanced

Microservice 4 acts as a eureka server and other first 3 microservies are eureka client.

ref1.

For eureka client use below data.

<dependency>
	<groupId>org.springframework.cloud</groupId>
	<artifactId>spring-cloud-starter-netflix-eureka-client</artifactId>
</dependency>
    
&

@EnableEurekaClient in main class.

ref2.

For eureka server use below data.

<dependency>
	<groupId>org.springframework.cloud</groupId>
	<artifactId>spring-cloud-starter-netflix-eureka-server</artifactId>
</dependency>
    
&

@EnableEurekaServer.

Ideally, we have to specify eureka server information in properties file of each eureka client so they register themselves.
But in this case since each microservice is running in same environment and eureka server is running in default port of 8761,
all microservice register automatically with above data only(ref1 and ref2).

Communication:
I am using RestTempate for communication between microservices.
In future RestTemplate will be deprecated with WebClient(Reactive async). So watch out for the same.
https://docs.spring.io/spring/docs/current/javadoc-api/org/springframework/web/client/RestTemplate.html



    
