---
title : "Các bước chuẩn bị & Cấu hình Maven"
date : 2026-07-20
weight : 2
chapter : false
pre : " <b> 5.2. </b> "
---

#### 1. Yêu cầu Môi trường Phát triển

Để biên dịch và triển khai mã nguồn **gearstore-backend**, môi trường máy tính cần cài đặt:

- **JDK 21**: Cấu hình trong `pom.xml` (`<java.version>21</java.version>`).
- **Apache Maven (3.9+)**: Sử dụng để biên dịch và đóng gói project.
- **AWS CLI (v2)**: Đã được cấu hình credential qua `aws configure`.
- **AWS SAM CLI**: Công cụ deploy Serverless template.

Kiểm tra thông số bằng các lệnh:
```bash
java -version
mvn -version
aws --version
sam --version
```

#### 2. Phân tích Phụ thuộc trong `pom.xml` (`gearstore-backend/pom.xml`)

File `pom.xml` tích hợp các thư viện quan trọng:

```xml
<dependencies>
    <!-- Spring Boot Web & Actuator -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>

    <!-- AWS SDK v2 cho DynamoDB Enhanced Client & S3 -->
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

    <!-- AWS Serverless Container Adapter cho Spring Boot 3 -->
    <dependency>
        <groupId>com.amazonaws.serverless</groupId>
        <artifactId>aws-serverless-java-container-springboot3</artifactId>
        <version>2.0.3</version>
    </dependency>
</dependencies>

<build>
    <plugins>
        <!-- Maven Shade Plugin đóng gói Fat-JAR cho AWS Lambda -->
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

#### 3. Phân tích `DynamoDbConfig.java`

Mã nguồn cấu hình tự động phân biệt giữa môi trường chạy Local và môi trường AWS Lambda:

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
        // Nếu có AccessKey (Chạy Local) -> Dùng Static Credentials
        // Nếu chạy trên Lambda (Không truyền AccessKey) -> Dùng DefaultCredentialsProvider (IAM Role)
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