---
title : "Create S3 Bucket gearstore-data-images & Upload API"
date : 2026-07-20
weight : 2
chapter : false
pre : " <b> 5.4.2. </b> "
---

#### Step 1: Create Amazon S3 Bucket `gearstore-data-images`

1. Open **Amazon S3 Console** -> click **Create bucket**.
2. **Bucket name**: `gearstore-data-images`
3. **AWS Region**: `us-east-1`
4. Uncheck **Block all public access** to enable public reads for product images.
5. Click **Create bucket**.

#### Step 2: Analyzing `ProductController.java` Upload Logic

The `uploadProductImage` endpoint receives a `MultipartFile` and uploads it to S3:

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