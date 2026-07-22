---
title : "Prerequisites & Maven Setup"
date : 2026-07-20
weight : 2
chapter : false
pre : " <b> 5.2. </b> "
---

#### 1. Required Local Environment

To compile and deploy the **gearstore-backend** codebase, prepare your machine with:

- **JDK 21**: Configured in `pom.xml` (`<java.version>21</java.version>`).
- **Apache Maven (3.9+)**: Used for compiling and packaging the project.
- **AWS CLI (v2)**: Configured with credentials via `aws configure`.
- **AWS SAM CLI**: Tool for deploying the Serverless stack.

Verify versions in terminal:
```bash
java -version
mvn -version
aws --version
sam --version
```

#### 2. Key Dependencies in `pom.xml` (`gearstore-backend/pom.xml`)

The project `pom.xml` incorporates crucial SDKs:

```xml
<dependencies>
    <!-- Spring Boot Web & Actuator -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>

    <!-- AWS SDK v2 for DynamoDB Enhanced Client & S3 -->
    <dependency>
        <groupId>software.amazon.awssdk</groupId>
        <artifactId>dynamodb-enhanced</artifactId>
        <version>2.25.25</version>
    </dependency>
    <dependency>
        <groupId>software.amazon.awssdk</groupId>
        <artifactId>s3</artifactId>
        <version>2.25.25</version>
    </dependency>

    <!-- AWS Serverless Container Adapter for Spring Boot 3 -->
    <dependency>
        <groupId>com.amazonaws.serverless</groupId>
        <artifactId>aws-serverless-java-container-springboot3</artifactId>
        <version>2.0.3</version>
    </dependency>
</dependencies>

<build>
    <plugins>
        <!-- Maven Shade Plugin for packaging Uber-JAR for AWS Lambda -->
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-shade-plugin</artifactId>
            <version>3.5.1</version>
            <executions>
                <execution>
                    <phase>package</phase>
                    <goals><goal>shade</goal></goals>
                </execution>
            </executions>
        </plugin>
    </plugins>
</build>
```

#### 3. Analyzing `DynamoDbConfig.java`

The configuration automatically detects Local vs AWS Lambda execution:

```java
@Configuration
public class DynamoDbConfig {
    @Value("${aws.dynamodb.region}")
    private String region;

    @Value("${aws.dynamodb.accesskey:}")
    private String accessKey;

    @Value("${aws.dynamodb.secretkey:}")
    private String secretKey;

    @Bean
    public DynamoDbClient dynamoDbClient() {
        var builder = DynamoDbClient.builder().region(Region.of(region));
        if (StringUtils.hasText(accessKey) && StringUtils.hasText(secretKey)) {
            builder.credentialsProvider(StaticCredentialsProvider.create(
                AwsBasicCredentials.create(accessKey, secretKey)
            ));
        } else {
            builder.credentialsProvider(DefaultCredentialsProvider.create());
        }
        return builder.build();
    }
}
```