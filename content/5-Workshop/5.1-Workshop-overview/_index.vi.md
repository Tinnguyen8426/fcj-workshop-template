---
title : "Tổng quan Workshop & Kiến trúc Mã nguồn"
date : 2026-07-20 
weight : 1 
chapter : false
pre : " <b> 5.1. </b> "
---

#### Giới thiệu về Mã nguồn `GearStore Backend`

Dự án `GearStore Backend` (`gearstore-backend`) là hệ thống RESTful API được xây dựng với các thành phần kỹ thuật chính:

- **Spring Boot 3.3.0 & Java 21**: Framework chính xử lý logic nghiệp vụ.
- **AWS Serverless Container**: Class `com.gearstore.backend.StreamLambdaHandler` khởi tạo `SpringBootLambdaContainerHandler` giúp chuyển tiếp HTTP requests từ API Gateway vào Spring DispatcherServlet mà không làm thay đổi cấu trúc REST Controller.
- **AWS SDK v2 (`dynamodb-enhanced`)**: Sử dụng `StaticTableSchema` map chính xác cấu trúc dữ liệu với hai bảng DynamoDB `GearStore_Products` và `GearStore_Users`.
- **Amazon S3 Integration**: Upload trực tiếp file ảnh sản phẩm và hỗ trợ xóa tự động ảnh cũ khi cập nhật / xóa sản phẩm.

#### Cấu trúc Thư mục Mã nguồn (`com.gearstore.backend`)

```
gearstore-backend/src/main/java/com/gearstore/backend/
├── BackendApplication.java       # Spring Boot main entry point
├── StreamLambdaHandler.java      # RequestStreamHandler cho AWS Lambda
├── config/
│   ├── DynamoDbConfig.java       # Bean DynamoDbClient & DynamoDbEnhancedClient
│   └── WebConfig.java            # Cấu hình CORS
├── entity/
│   ├── ProductEntity.java        # DynamoDbBean cho GearStore_Products
│   └── UserEntity.java           # Model cho GearStore_Users
├── repository/
│   ├── ProductRepository.java    # Data Access Layer cho Bảng Sản phẩm
│   └── UserRepository.java       # Data Access Layer cho Bảng Người dùng
└── controller/
    ├── AuthController.java       # APIs đăng nhập (/auth/login), đăng ký (/auth/register), quản lý user
    └── ProductController.java    # APIs lấy sản phẩm (/products), upload ảnh (/products/upload), seed DB (/products/reset-database)
```

#### Sơ đồ Kiến trúc Hệ thống (System Architecture Diagram)

![Sơ đồ kiến trúc hệ thống](/images/5-Workshop/5.1-Workshop-overview/diagram1.png)

#### Luồng xử lý Request trên AWS

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
