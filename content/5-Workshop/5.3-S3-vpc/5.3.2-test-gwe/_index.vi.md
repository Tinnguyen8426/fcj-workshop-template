---
title : "Đóng gói & Triển khai Backend lên AWS Lambda"
date : 2026-07-20
weight : 2
chapter : false
pre : " <b> 5.3.2. </b> "
---

#### Bước 1: Biên dịch & Đóng gói Uber-JAR với Maven

Mở terminal trong thư mục `gearstore-backend` và thực hiện lệnh đóng gói:

```bash
cd gearstore-backend
mvn clean package
```

Thư viện `maven-shade-plugin` sẽ tạo ra file `target/backend-0.0.1-SNAPSHOT.jar` chứa đầy đủ Spring Boot 3 & AWS SDK dependencies.

#### Bước 2: Tạo File Cấu hình AWS SAM (`template.yaml`)

Tạo file `template.yaml` trong thư mục `gearstore-backend`:

```yaml
AWSTemplateFormatVersion: '2010-09-09'
Transform: AWS::Serverless-2016-10-31
Description: GearStore Backend Spring Boot 3 Lambda Function

Resources:
  GearStoreBackendFunction:
    Type: AWS::Serverless::Function
    Properties:
      CodeUri: target/backend-0.0.1-SNAPSHOT.jar
      Handler: com.gearstore.backend.StreamLambdaHandler::handleRequest
      Runtime: java21
      MemorySize: 1024
      Timeout: 30
      Environment:
        Variables:
          AWS_DYNAMODB_REGION: us-east-1
      Policies:
        - AmazonDynamoDBFullAccess
        - AmazonS3FullAccess
      Events:
        ProxyApi:
          Type: HttpApi
          Properties:
            Path: /{proxy+}
            Method: ANY

Outputs:
  ApiEndpoint:
    Description: "API Gateway Endpoint URL"
    Value: !Sub "https://${ServerlessHttpApi}.execute-api.${AWS::Region}.amazonaws.com"
```

#### Bước 3: Triển khai bằng AWS SAM CLI

Chạy các lệnh triển khai lên Cloud:

```bash
sam build
sam deploy --guided
```

Điền các thông tin:
- **Stack Name**: `gearstore-backend-stack`
- **AWS Region**: `us-east-1`
- **Confirm changes before deploy**: `N`
- **Allow SAM CLI IAM role creation**: `Y`

Sau khi hoàn tất, SAM CLI sẽ xuất ra URL API Gateway Endpoint:
`https://xxxxxx.execute-api.us-east-1.amazonaws.com`