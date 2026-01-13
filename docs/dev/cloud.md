# Table of Contents
- [Table of Contents](#table-of-contents)
- [Running Spring Boot in production](#running-spring-boot-in-production)
  - [Dependencies](#dependencies)
  - [Spring Boot](#spring-boot)
    - [Environment specific profiles](#environment-specific-profiles)
    - [Spring Profiles](#spring-profiles)
    - [Spring Boot Actuator](#spring-boot-actuator)
    - [Packaging](#packaging)
    - [@ControllerAdvice](#controlleradvice)

# Running Spring Boot in production

> You don't need to deploy the code into a container. Just stand up the engine. 
> It is just a library at that point. It is all about reducing that surface area. 
> Josh Long, Spring Developer

## Dependencies
```bash
curl -s "https://get.sdkman.io" | bash
sdk list java
sdk install java 8.0.462-amzn 
brew install docker
brew install virtualbox
brew install virtualbox-extension-pack
brew install vagrant
brew install git
```

## Spring Boot
```bash
./gradlew clean build
java -jar build/libs/SampleApplication-0.0.1-SNAPSHOT.jar
```

### Environment specific profiles
Our applications must be environment configurable for lifecycle development processes in development, user testing and production deployment.

```Java
@Controller
public class MainController {

    @Autowired
    private Environment env;

    @GetMapping({"/", "/index"})
    public String welcomePage(Model model){
        model.addAttribute("environments", env.getActiveProfiles());

        return "index";
    }
}
```
```bash
./gradlew clean build
java -jar -Dspring.profiles.active=dev build/libs/SampleApplication-0.0.1-SNAPSHOT.jar
java -jar -Dspring.profiles.active=prod build/libs/SampleApplication-0.0.1-SNAPSHOT.jar
```

### Spring Profiles
It's the first step to keep our application configurations externalized and configurable.
* application.properties
* application-dev.properties
* application-qa.properties
* application-prod.properties

We can access to resources and servers configured throug beans that might include:
* Database servers
* Message queues
* Microservices

Spring Boot offers the app profile that can be used and applied to different beans to support this use case.
* Profile(dev)
* Profile(qa)
* Profile(prod)

```Java
package com.mdrsolutions.springbootprod.configuration;
import org.springframework.boot.context.properties.ConfigurationProperties;

@ConfigurationProperties("spring.datasource")
public class DBConfiguration {
    private String driverClassName;
private String url;
    private String userName;
    private String password;

    // getters and setters
}
```

**application-dev.properties**
```
spring.h2.console.enabled=true
spring.h2.console.path=/h2
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.url=jdbc:h2:mem:db
spring.datasource.userName=sa
spring.datasource.password=sa
```

**application-qa.properties**
```
spring.datasource.url=jdbc:mysql://localhost:3306/qaDB
spring.datasource.userName=root
spring.datasource.password=root123
spring.datasource.driverClassName=com.mysql.cj.jdbc.Driver
spring.jpa.hibernate.ddl-auto=update
spring.jpa.properties.hibernate.dialect = org.hibernate.dialect.MySQL5Dialect
```

**application-prod.properties**
```
spring.datasource.url=jdbc:mysql://localhost:3306/prodDB
spring.datasource.userName=root
spring.datasource.password=root123
spring.datasource.driverClassName=com.mysql.cj.jdbc.Driver
spring.jpa.hibernate.ddl-auto=update
spring.jpa.properties.hibernate.dialect = org.hibernate.dialect.MySQL5Dialect
```
The next step is to register the configuration by profile.

```java
package com.mdrsolutions.springbootprod.configuration;

import org.springframework.boot.context.properties.EnableConfigurationProperties;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.context.annotation.Profile;

@Configuration
@EnableConfigurationProperties(DBConfiguration.class)
public class DBConnectionConfiguration {
    private final DBConfiguration dbConfiguration;

    public DBConnectionConfiguration(DBConfiguration dbConfiguration) {
        this.dbConfiguration = dbConfiguration;
    }

    @Profile("dev")
    @Bean
    public String devDBConnection(){
        System.out.println("DB Connection for DEV");
        System.out.println(dbConfiguration.getUrl());
        System.out.println(dbConfiguration.getDriverClassName());
        System.out.println(dbConfiguration.getUserName());
        System.out.println(dbConfiguration.getPassword());
        return "DB Connection for DEV";
    }

    @Profile("qa")
    @Bean
    public String qaDBConnection(){
        System.out.println("DB Connection for QA");
        System.out.println(dbConfiguration.getUrl());
        System.out.println(dbConfiguration.getDriverClassName());
        System.out.println(dbConfiguration.getUserName());
        System.out.println(dbConfiguration.getPassword());
        return "DB Connection for QA";
    }

    @Profile("prod")
    @Bean
    public String prodDBConnection(){
        System.out.println("DB Connection for PROD");
        System.out.println(dbConfiguration.getUrl());
        System.out.println(dbConfiguration.getDriverClassName());
        System.out.println(dbConfiguration.getUserName());
        System.out.println(dbConfiguration.getPassword());
        return "DB Connection for PROD";
    }
}
```
```bash
./gradlew clean build
java -jar -Dspring.profiles.active=dev build/libs/SpringBootProdApplication-0.0.1-SNAPSHOT.jar
java -jar -Dspring.profiles.active=qa build/libs/SpringBootProdApplication-0.0.1-SNAPSHOT.jar
java -jar -Dspring.profiles.active=prod build/libs/SpringBootProdApplication-0.0.1-SNAPSHOT.jar
```
### Spring Boot Actuator
It allows to monitor a health endpoints, management over HTTP or JMX, control loggers and much more.

**build.gradle**
```gradle
dependencies {
    ...
	implementation 'org.springframework.boot:spring-boot-starter-actuator'
    ...
}
```

```bash
./gradlew clean build
java -jar -Dspring.profiles.active=prod build/libs/SpringBootProdApplication-0.0.1-SNAPSHOT.jar
```

[http://localhost:8080/actuator/health](http://localhost:8080/actuator/health)
```
{"status":"UP"}
```

**application.properties**
```java
management.server.port=9001
server.port=9000
management.endpoint.health.show-details=always
management.endpoints.web.exposure.include=health,info,metrics,loggers

#info
info.application.name=SpringBootProduction
info.application.description=A Demo for Spring Boot in Production!
info.application.author.name=Michael Rodgers
info.application.author.bio=Independent Software Engineer and all around good guy
```

```bash
./gradlew clean build
java -jar -Dspring.profiles.active=prod build/libs/SpringBootProdApplication-0.0.1-SNAPSHOT.jar
```

[http://localhost:9001/actuator/health](http://localhost:9001/actuator/health)
```json
{
  "status": "UP",
  "components": {
    "dataWebServiceApi": {
      "status": "UP",
      "details": {
        "Data Web Service API": "Up"
      }
    },
    "diskSpace": {
      "status": "UP",
      "details": {
        "total": 250790436864,
        "free": 70818664448,
        "threshold": 10485760,
        "exists": true
      }
    },
    "ping": {
      "status": "UP"
    }
  }
}
```

[http://localhost:9001/actuator/info](http://localhost:9001/actuator/info)
```json
{
  "application": {
    "name": "SpringBootProduction",
    "description": "A Demo for Spring Boot in Production!",
    "author": {
      "name": "Michael Rodgers",
      "bio": "Independent Software Engineer and all around good guy"
    }
  }
}
```

### Packaging

> You don't need to deploy the code into a container. Just stand up the engine. 
> It is just a library at that point. It is all about reducing that surface area. 

Josh Long, Spring Developer


### @ControllerAdvice
aaa