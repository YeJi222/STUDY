## [ 2023.01.26.목 ]
- Swagger 세팅
    - application.properties
        
        ```java
        server.port = 9090
        spring.mvc.pathmatch.matching-strategy=ant_path_matcher
        ```
        
    - SwaggerConfiguration.java
        
        ```java
        package studio.thinkground.AroundHubSpringBoot.config;
        
        import org.springframework.context.annotation.Bean;
        import org.springframework.context.annotation.Configuration;
        import org.springframework.http.HttpHeaders;
        import springfox.documentation.builders.ApiInfoBuilder;
        import springfox.documentation.builders.ParameterBuilder;
        import springfox.documentation.builders.PathSelectors;
        import springfox.documentation.builders.RequestHandlerSelectors;
        import springfox.documentation.schema.ModelRef;
        import springfox.documentation.service.ApiInfo;
        import springfox.documentation.service.Parameter;
        import springfox.documentation.spi.DocumentationType;
        import springfox.documentation.spring.web.plugins.Docket;
        import springfox.documentation.swagger2.annotations.EnableSwagger2;
        
        import java.util.ArrayList;
        import java.util.List;
        
        /**
         * @package : studio.thinkground.aroundhub.config
         * @name : SwaggerConfiguration.java
         * @date : 2022-01-28 오후 4:34
         * @author : Flature
         * @version : 1.0.0
         **/
        @Configuration
        public class SwaggerConfiguration {
        
            private static final String API_NAME = "Programmers Spring Boot Application";
            private static final String API_VERSION = "1.0.0";
            private static final String API_DESCRIPTION = "프로그래머스 스프링 부트 애플리케이션입니다.";
        
            // 접속 경로 : http://localhost:8080/swagger-ui/
            @Bean
            public Docket api() {
                Parameter parameterBuilder = (Parameter) new ParameterBuilder()
                        .name(HttpHeaders.AUTHORIZATION)
                        .description("Access Tocken")
                        .modelRef(new ModelRef("string"))
                        .parameterType("header")
                        .required(false)
                        .build();
        
                List<Parameter> globalParameters = new ArrayList<>();
                globalParameters.add(parameterBuilder);
        
                return new Docket(DocumentationType.SWAGGER_2)
                        .globalOperationParameters(globalParameters)
                        .apiInfo(apiInfo())
                        .select()
                        .apis(RequestHandlerSelectors.basePackage("studio.thinkground.AroundHubSpringBoot"))
                        .paths(PathSelectors.any())
                        .build();
            }
        
            public ApiInfo apiInfo() {
                return new ApiInfoBuilder()
                        .title(API_NAME)
                        .version(API_VERSION)
                        .description(API_DESCRIPTION)
                        .build();
            }
        }
        ```
        
    - AroundHubSpringBootApplication.java
        
        ```java
        package studio.thinkground.AroundHubSpringBoot;
        
        import org.springframework.boot.SpringApplication;
        import org.springframework.boot.autoconfigure.EnableAutoConfiguration;
        import org.springframework.boot.autoconfigure.SpringBootApplication;
        import org.springframework.boot.autoconfigure.jdbc.DataSourceAutoConfiguration;
        
        @SpringBootApplication
        @EnableAutoConfiguration(exclude={DataSourceAutoConfiguration.class})
        public class AroundHubSpringBootApplication {
        	public static void main(String[] args) {
        		SpringApplication.run(AroundHubSpringBootApplication.class, args);
        	}
        }
        ```
        
    - pom.xml

        ```xml
        <?xml version="1.0" encoding="UTF-8"?>
        <project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
          xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
          <modelVersion>4.0.0</modelVersion>
          <parent>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-parent</artifactId>
            <version>3.0.2</version> <!-- initial setting : 3.0.2 -->
            <relativePath/> <!-- lookup parent from repository -->
          </parent>

          <groupId>studio.thinkground</groupId>
          <artifactId>AroundHub</artifactId>
          <version>1.0.0</version>
          <packaging>jar</packaging>

          <name>AroundHubSpringBoot</name>
          <url>https://thinkground.studio</url> <!-- option -->
          <description>Demo project for Spring Boot</description>

          <properties>
            <java.version>17</java.version> <!-- initial setting : 17 -->
          </properties>

          <dependencies>
            <dependency>
              <groupId>org.springframework.boot</groupId>
              <artifactId>spring-boot-starter-web</artifactId>
            </dependency>

            <dependency>
              <groupId>org.springframework.boot</groupId>
              <artifactId>spring-boot-configuration-processor</artifactId>
              <optional>true</optional>
            </dependency>

            <!-- lombok : method를 만들지 않고 annotation으로 기능들을 대체할 수 있음 -->
            <dependency>
              <groupId>org.projectlombok</groupId>
              <artifactId>lombok</artifactId>
              <optional>true</optional>
            </dependency>

            <dependency>
              <groupId>org.springframework.boot</groupId>
              <artifactId>spring-boot-starter-test</artifactId>
              <scope>test</scope>
            </dependency>

            <dependency>
              <groupId>io.springfox</groupId>
              <artifactId>springfox-boot-starter</artifactId>
              <version>3.0.0</version>
            </dependency>

            <dependency>
              <groupId>io.springfox</groupId>
              <artifactId>springfox-swagger-ui</artifactId>
              <version>3.0.0</version>
            </dependency>

            <dependency>
              <groupId>org.springframework</groupId>
              <artifactId>spring-web</artifactId>
              <version>6.0.3</version>
            </dependency>
          </dependencies>

          <build>
            <plugins>
              <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
                <configuration>
                  <excludes>
                    <exclude>
                      <groupId>org.projectlombok</groupId>
                      <artifactId>lombok</artifactId>
                    </exclude>
                  </excludes>
                </configuration>
              </plugin>
            </plugins>
          </build>

        </project>
        ```
