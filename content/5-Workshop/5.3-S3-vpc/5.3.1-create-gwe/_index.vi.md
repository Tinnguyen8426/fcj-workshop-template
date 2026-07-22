---
title : "Tạo Bảng DynamoDB GearStore_Products & GearStore_Users"
date : 2026-07-20
weight : 1
chapter : false
pre : " <b> 5.3.1. </b> "
---

#### Bước 1: Tạo bảng `GearStore_Products`

Bảng `GearStore_Products` được ánh xạ bằng `StaticTableSchema` trong `ProductRepository.java`:

1. Truy cập **AWS Management Console** -> **DynamoDB** -> chọn **Create table**.
2. Thiết lập thông số:
   - **Table name**: `GearStore_Products`
   - **Partition key**: `ProductId` (String)
   - **Sort key**: `RecordType` (String)
   - **Table class**: DynamoDB Standard
   - **Capacity mode**: **On-Demand** (Tối ưu chi phí).
3. Nhấp **Create table**.

Các trường dữ liệu được lưu trữ trong bảng:
- `ProductId`: Mã sản phẩm (ví dụ: `LAP001`, `KEY001`, `MSL001`).
- `RecordType`: Phân loại bản ghi (ví dụ: `PRODUCT_INFO`).
- `Name`: Tên hiển thị sản phẩm.
- `Price`: Giá sản phẩm (Double).
- `ImageUrl`: Link hình ảnh lưu trữ trên S3 (`gearstore-data-images`).
- `Attributes`: Map các thuộc tính linh hoạt (Hãng, CPU, RAM, VGA...).

#### Bước 2: Tạo bảng `GearStore_Users`

Bảng `GearStore_Users` được ánh xạ trong `UserRepository.java`:

1. Nhấp **Create table**.
2. Thiết lập thông số:
   - **Table name**: `GearStore_Users`
   - **Partition key**: `Username` (String)
   - **Capacity mode**: **On-Demand**.
3. Nhấp **Create table**.

Các trường dữ liệu:
- `Username`: Tên đăng nhập (Partition Key).
- `Password`: Mật khẩu tài khoản.
- `FullName`: Họ và tên người dùng.
- `Role`: Quyền truy cập (`ADMIN` hoặc `USER`).
- `Email`, `Phone`, `Address`: Thông tin liên hệ.
