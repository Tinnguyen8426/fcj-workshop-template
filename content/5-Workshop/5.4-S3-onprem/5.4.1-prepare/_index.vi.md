---
title : "Tổng quan Cấu hình Amazon S3 & APIs Xác thực"
date : 2026-07-20
weight : 1
chapter : false
pre : " <b> 5.4.1. </b> "
---

#### Giới thiệu về Tích hợp Amazon S3 trong `ProductController`

Ứng dụng backend xử lý hình ảnh sản phẩm trực tiếp thông qua **Amazon S3**:
- Bucket Name chính thức: `gearstore-data-images` (đã khai báo trong `ProductController.java`).
- **Tự động hóa quản lý file**: Khi cập nhật hình ảnh sản phẩm (`PUT /products/{id}`) hoặc xóa sản phẩm (`DELETE /products/{id}`), hệ thống sẽ tự động gọi phương thức `deleteS3Object(key)` để xóa hình ảnh cũ trên S3 bucket.
- **Hỗ trợ Seed Database ngầm**: API `POST /products/reset-database` chạy tiến trình ngầm tự động dọn dẹp S3 và tải hơn 110 hình ảnh sản phẩm gaming gear thực tế (Unsplash) lên S3.

#### Giới thiệu về APIs Xác thực Người dùng trong `AuthController`

Controller `/auth` quản lý tập trung thông tin tài khoản trên DynamoDB table `GearStore_Users`:
- `POST /auth/login`: Xác thực thông tin đăng nhập và trả về profile người dùng (bảo mật ẩn mật khẩu).
- `POST /auth/register`: Đăng ký tài khoản người dùng mới (mặc định role `USER`).
- `GET /auth/users`: Lấy danh sách người dùng cho trang Quản trị.
- `PUT /auth/users/update`: Cập nhật thông tin phân quyền và chi tiết người dùng.
