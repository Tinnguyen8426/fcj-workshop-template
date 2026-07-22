---
title : "Automated Database Seeding & Debugging APIs"
date : 2026-07-20
weight : 4
chapter : false
pre : " <b> 5.4.4. </b> "
---

#### 1. Asynchronous Database Seeding API (`POST /products/reset-database`)

The `resetDatabase()` method launches an asynchronous background thread seeding 110+ items:

```java
@PostMapping(value = "/reset-database", produces = "text/plain; charset=UTF-8")
public ResponseEntity<String> resetDatabase() {
    new Thread(this::runSeedInBackground).start();
    return ResponseEntity.ok("✅ Processing: Cleaning S3 bucket & seeding 110 items in background!");
}
```

Background Seed Workflow:
1. `cleanS3Bucket()`: Lists and deletes all legacy objects in S3 bucket `gearstore-data-images`.
2. Purges existing items from table `GearStore_Products`.
3. Downloads 110+ real gaming gear images (Laptop, GVN PC, VGA, CPU, RAM, Monitors, Keyboards, Mice, Headsets) and uploads them directly to S3.
4. Inserts product metadata and attribute maps into DynamoDB.

#### 2. Raw Item Debugging API (`GET /products/{id}/debug`)

Allows inspecting the low-level item map returned by `DynamoDbClient.getItem()`:

```java
@GetMapping("/{id}/debug")
public ResponseEntity<?> debugRawItem(
        @PathVariable("id") String productId,
        @RequestParam(value = "type", defaultValue = "PRODUCT_INFO") String recordType) {
    var raw = productRepository.getRawItem(productId, recordType);
    return ResponseEntity.ok(raw);
}
```