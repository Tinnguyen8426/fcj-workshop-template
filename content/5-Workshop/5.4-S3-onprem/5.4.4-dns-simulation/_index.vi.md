---
title : "Tự động Seed Database & Debugging APIs"
date : 2026-07-20
weight : 4
chapter : false
pre : " <b> 5.4.4. </b> "
---

#### 1. API Khởi tạo Dữ liệu Mẫu Async (`POST /products/reset-database`)

Phương thức `resetDatabase()` khởi chạy tiến trình seed 110 sản phẩm ngầm trong `Thread` riêng:

```java
@PostMapping(value = "/reset-database", produces = "text/plain; charset=UTF-8")
public ResponseEntity<String> resetDatabase() {
    new Thread(this::runSeedInBackground).start();
    return ResponseEntity.ok("✅ Đang xử lý: Dọn S3 bucket và seed 110 sản phẩm mẫu trong nền!");
}
```

Quy trình hoạt động ngầm:
1. `cleanS3Bucket()`: Liệt kê và xóa toàn bộ các đối tượng cũ trong S3 bucket `gearstore-data-images`.
2. Xóa sạch các item cũ trong bảng `GearStore_Products`.
3. Tải hơn 110 hình ảnh sản phẩm gaming gear thực tế (Laptop, PC GVN, VGA, CPU, RAM, Màn hình, Bàn phím, Chuột, Tai nghe) và lưu trực tiếp vào Amazon S3.
4. Ghi thông tin các thuộc tính sản phẩm vào DynamoDB.

#### 2. API Kiểm tra Cấu trúc Item Thô (`GET /products/{id}/debug`)

Cho phép kiểm tra dữ liệu đọc trực tiếp từ `DynamoDbClient.getItem()`:

```java
@GetMapping("/{id}/debug")
public ResponseEntity<?> debugRawItem(
        @PathVariable("id") String productId,
        @RequestParam(value = "type", defaultValue = "PRODUCT_INFO") String recordType) {
    var raw = productRepository.getRawItem(productId, recordType);
    return ResponseEntity.ok(raw);
}
```