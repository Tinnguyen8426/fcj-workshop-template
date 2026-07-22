---
title : "Khởi tạo Bucket S3 gearstore-data-images & API Upload"
date : 2026-07-20
weight : 2
chapter : false
pre : " <b> 5.4.2. </b> "
---

#### Bước 1: Khởi tạo Amazon S3 Bucket `gearstore-data-images`

1. Truy cập **Amazon S3 Console** -> chọn **Create bucket**.
2. **Bucket name**: `gearstore-data-images`
3. **AWS Region**: `us-east-1`
4. Bỏ chọn **Block all public access** (cho phép đọc public hình ảnh sản phẩm).
5. Nhấp **Create bucket**.

#### Bước 2: Phân tích mã nguồn Upload trong `ProductController.java`

Phương thức `uploadProductImage` tiếp nhận file `MultipartFile`, lưu tạm và tải lên S3:

```java
@PostMapping("/upload")
public ResponseEntity<String> uploadProductImage(@RequestParam("file") MultipartFile file) {
    if (file.isEmpty()) return ResponseEntity.badRequest().body("File rỗng!");

    try {
        S3Client s3Client = S3Client.builder().region(Region.of(regionStr)).build();
        String fileName = System.currentTimeMillis() + "_" + file.getOriginalFilename();
        Path tempFile = Files.createTempFile("upload_", fileName);
        file.transferTo(tempFile.toFile());

        s3Client.putObject(
            PutObjectRequest.builder()
                .bucket("gearstore-data-images")
                .key(fileName)
                .contentType(file.getContentType())
                .acl(ObjectCannedACL.PUBLIC_READ)
                .build(),
            tempFile
        );

        Files.delete(tempFile);
        String s3Url = "https://gearstore-data-images.s3." + regionStr + ".amazonaws.com/" + fileName;
        return ResponseEntity.ok(s3Url);
    } catch (Exception e) {
        return ResponseEntity.status(500).body("Lỗi upload: " + e.getMessage());
    }
}
```