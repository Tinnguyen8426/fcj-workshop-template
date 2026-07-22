---
title : "Workshop Overview & Backend Architecture"
date : 2026-07-20 
weight : 1 
chapter : false
pre : " <b> 5.1. </b> "
---

#### Introduction to `GearStore Backend` Source Code

The `GearStore Backend` (`gearstore-backend`) project is a production-ready RESTful API built with key technologies:

- **Spring Boot 3.3.0 & Java 21**: Core application framework.
- **AWS Serverless Container**: `com.gearstore.backend.StreamLambdaHandler` implements `SpringBootLambdaContainerHandler` to route API Gateway HTTP requests directly to Spring DispatcherServlet without modifying existing REST controllers.
- **AWS SDK v2 (`dynamodb-enhanced`)**: Uses `StaticTableSchema` for exact mapping with DynamoDB tables `GearStore_Products` and `GearStore_Users`.
- **Amazon S3 Integration**: Supports direct multipart file uploads and automatic old image cleanup upon product update or deletion.

#### Package Structure (`com.gearstore.backend`)

```
gearstore-backend/src/main/java/com/gearstore/backend/
├── BackendApplication.java       # Spring Boot main entry point
├── StreamLambdaHandler.java      # RequestStreamHandler for AWS Lambda
├── config/
│   ├── DynamoDbConfig.java       # Beans for DynamoDbClient & DynamoDbEnhancedClient
│   └── WebConfig.java            # CORS configuration
├── entity/
│   ├── ProductEntity.java        # DynamoDbBean for GearStore_Products
│   └── UserEntity.java           # Model for GearStore_Users
├── repository/
│   ├── ProductRepository.java    # Data Access Layer for Products
│   └── UserRepository.java       # Data Access Layer for Users
└── controller/
    ├── AuthController.java       # APIs for login (/auth/login), register (/auth/register), user management
    └── ProductController.java    # APIs for products (/products), upload (/products/upload), seed DB (/products/reset-database)
```

#### System Architecture Diagram

![System Architecture Diagram](/images/5-Workshop/5.1-Workshop-overview/diagram1.png)

#### AWS Request Execution Flow

```
[ Client / Postman / Frontend ]
               │
               ▼  HTTP Request (GET/POST/PUT/DELETE)
    ┌──────────────────────┐
    │  Amazon API Gateway  │ (HttpApiV2 / REST Proxy)
    └──────────┬───────────┘
               │  Proxy Stream Event
               ▼
    ┌──────────────────────┐
    │  AWS Lambda Function │ Handler: com.gearstore.backend.StreamLambdaHandler
    └──────────┬───────────┘
               │
               ▼  Forward to Spring Boot DispatcherServlet
    ┌───────────────────────────┐
    │ ProductController / Auth  │
    └─────┬───────────────┬─────┘
          │               │
          ▼               ▼
┌──────────────────┐  ┌─────────────────────┐
│ Amazon DynamoDB  │  │      Amazon S3      │
│(GearStore_*)     │  │(gearstore-data-img) │
└──────────────────┘  └─────────────────────┘
```