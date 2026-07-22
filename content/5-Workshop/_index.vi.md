---
title: "Workshop"
date: 2026-07-20
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Triển khai Hệ thống Thương mại Điện tử GearStore Backend trên AWS Serverless

#### Tổng quan

**GearStore Backend API** là giải pháp máy chủ thương mại điện tử chuyên cung cấp thiết bị công nghệ & gaming gear. Dự án được phát triển dựa trên **Java 21** và **Spring Boot 3.3.0**, tích hợp thư viện **AWS Serverless Java Container** (`aws-serverless-java-container-springboot3`) để vận hành dạng Serverless trên **AWS Lambda** thông qua **Amazon API Gateway**.

Trong chuỗi bài lab thực hành này, bạn sẽ thực hiện đóng gói và triển khai mã nguồn **gearstore-backend** lên AWS Cloud:

+ **Cấu hình & Tích hợp SDK**: Tích hợp **AWS SDK v2** (`software.amazon.awssdk:dynamodb-enhanced` & `s3`) và cấu hình `DynamoDbConfig` tự động chuyển đổi giữa credentials local và AWS Lambda IAM Role.
+ **Lưu trữ NoSQL với DynamoDB**: Thiết kế hai bảng DynamoDB `GearStore_Products` (PartitionKey: `ProductId`, SortKey: `RecordType`) và `GearStore_Users` (PartitionKey: `Username`).
+ **Quản lý Hình ảnh S3**: Upload và dọn dẹp hình ảnh sản phẩm trực tiếp trên **Amazon S3** (`gearstore-data-images`).
+ **Đóng gói & Deployment**: Sử dụng `maven-shade-plugin` đóng gói Uber-JAR và triển khai lên **AWS Lambda** với `StreamLambdaHandler`.

#### Nội dung bài lab

1. [Tổng quan Kiến trúc Mã nguồn Backend](5.1-Workshop-overview/)
2. [Các bước chuẩn bị môi trường & Cấu hình Maven](5.2-Prerequiste/)
3. [Tạo bảng DynamoDB & Triển khai Spring Boot 3 Lambda](5.3-S3-vpc/)
4. [Cấu hình Amazon S3 & APIs Xác thực / Người dùng](5.4-S3-onprem/)
5. [Kết nối Frontend Next.js với Backend APIs](5.5-Policy/)
6. [Kiểm thử API & Dọn dẹp tài nguyên Cloud](5.6-Cleanup/)