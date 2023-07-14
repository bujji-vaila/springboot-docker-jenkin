Spring Boot app with Docker

prerequisite: Dcoker must installed  and running.

step1 : write sping boot app using spring initializer(dependency modules, Spring web)

Step 2:Add one endpoint

        @RestController
		@RequestMapping("/")
		@SpringBootApplication
		public class DemoDocker1Application {

			public static void main(String[] args) {
				SpringApplication.run(DemoDocker1Application.class, args);
			}
			
			@GetMapping
			public String greetings() {
				return "hello welcome to docker demo";
			}

		}
   
Step 3: create Dockerfile at root folder

        FROM openjdk:8
		EXPOSE 8080
		ADD target/springboot-docker-jenkin.jar springboot-docker-jenkin.jar
		ENTRYPOINT [ "java", "-jar","springboot-docker-jenkin.jar" ]

		
Step 4. build the docker image file below below command[Go to application rrot folder where docker file located]
  
        docker build -t spring-boot-docker-demo-01.jar

Step 5. run the container by below command
   
   docker run -p 9090:8080 spring-boot-docker-demo-01.jar
   
Step 6:  hit the browser url http://localhost:9090   

