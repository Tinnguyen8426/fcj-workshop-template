---
title : "Create DynamoDB Tables GearStore_Products & GearStore_Users"
date : 2026-07-20
weight : 1
chapter : false
pre : " <b> 5.3.1. </b> "
---

#### Step 1: Create `GearStore_Products` Table

The table schema is mapped via `StaticTableSchema` in `ProductRepository.java`:

1. Open **AWS Management Console** -> navigate to **DynamoDB** -> click **Create table**.
2. Configure attributes:
   - **Table name**: `GearStore_Products`
   - **Partition key**: `ProductId` (String)
   - **Sort key**: `RecordType` (String)
   - **Table class**: DynamoDB Standard
   - **Capacity mode**: **On-Demand**.
3. Click **Create table**.

Attributes stored per item:
- `ProductId`: Unique Product identifier (e.g., `LAP001`, `KEY001`).
- `RecordType`: Record classification (`PRODUCT_INFO`).
- `Name`: Product title.
- `Price`: Product price (Double).
- `ImageUrl`: S3 object URL (`gearstore-data-images`).
- `Attributes`: Dynamic specifications map (Brand, CPU, RAM, VGA...).

#### Step 2: Create `GearStore_Users` Table

The user schema is defined in `UserRepository.java`:

1. Click **Create table**.
2. Settings:
   - **Table name**: `GearStore_Users`
   - **Partition key**: `Username` (String)
   - **Capacity mode**: **On-Demand**.
3. Click **Create table**.

Stored user attributes:
- `Username`: Partition Key.
- `Password`: User password string.
- `FullName`: Full name.
- `Role`: Access role (`ADMIN` or `USER`).
- `Email`, `Phone`, `Address`: Contact details.