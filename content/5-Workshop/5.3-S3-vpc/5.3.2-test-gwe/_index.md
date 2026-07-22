---
title : "Package & Deploy Backend to AWS Lambda"
date : 2026-07-20
weight : 2
chapter : false
pre : " <b> 5.3.2. </b> "
---

#### Step 1: Build & Package Uber-JAR via Maven

Open terminal at `gearstore-backend` directory and run the build command:

```bash
cd gearstore-backend
mvn clean package
```

The `maven-shade-plugin` produces `target/backend-0.0.1-SNAPSHOT.jar` bundling Spring Boot 3 runtime & AWS SDK dependencies.

#### Step 2: Create AWS SAM Template (`template.yaml`)

Create `template.yaml` in `gearstore-backend`:

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

#### Step 3: Deploy via AWS SAM CLI

Execute deployment commands:

```bash
sam build
sam deploy --guided
```

Specify parameters:
- **Stack Name**: `gearstore-backend-stack`
- **AWS Region**: `us-east-1`
- **Confirm changes before deploy**: `N`
- **Allow SAM CLI IAM role creation**: `Y`

SAM CLI outputs the API Gateway Endpoint:
`https://xxxxxx.execute-api.us-east-1.amazonaws.com`
