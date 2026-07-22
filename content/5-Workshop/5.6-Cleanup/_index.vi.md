---
title : "Kiểm thử API & Dọn dẹp tài nguyên Cloud"
date : 2026-07-20
weight : 6
chapter : false
pre : " <b> 5.6. </b> "
---

#### 1. Kiểm thử Endpoints Backend (cURL Test)

Thực hiện gọi các cURL command để kiểm tra API Gateway & Spring Boot Lambda:

1. **Lấy toàn bộ sản phẩm**:
   ```bash
   curl -X GET https://xxxxxx.execute-api.us-east-1.amazonaws.com/products
   ```
2. **Kích hoạt Async Seed Database**:
   ```bash
   curl -X POST https://xxxxxx.execute-api.us-east-1.amazonaws.com/products/reset-database
   ```
3. **Thử nghiệm Đăng ký Tài khoản**:
   ```bash
   curl -X POST https://xxxxxx.execute-api.us-east-1.amazonaws.com/auth/register \
     -H "Content-Type: application/json" \
     -d '{"username":"gamer1","password":"123","fullName":"Gamer Pro","email":"gamer@gmail.com"}'
   ```
4. **Thử nghiệm Đăng nhập**:
   ```bash
   curl -X POST https://xxxxxx.execute-api.us-east-1.amazonaws.com/auth/login \
     -H "Content-Type: application/json" \
     -d '{"username":"gamer1","password":"123"}'
   ```

#### 2. Dọn dẹp Tài nguyên Cloud (Teardown Sequence)

Xóa tài nguyên trên AWS để ngưng phát sinh chi phí:

1. **Xóa SAM Stack (Lambda & API Gateway)**:
   ```bash
   cd gearstore-backend
   sam delete --stack-name gearstore-backend-stack
   ```

2. **Dọn S3 Bucket `gearstore-data-images`**:
   - Mở **S3 Console** -> chọn `gearstore-data-images` -> chọn **Empty** -> chọn **Delete bucket**.

3. **Xóa Bảng DynamoDB**:
   - Mở **DynamoDB Console** -> chọn các bảng `GearStore_Products` và `GearStore_Users` -> chọn **Delete table**.