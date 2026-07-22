---
title : "API Testing & Cloud Resource Cleanup"
date : 2026-07-20
weight : 6
chapter : false
pre : " <b> 5.6. </b> "
---

#### 1. Testing Backend Endpoints (cURL Test)

Execute cURL commands to verify API Gateway & Spring Boot Lambda integration:

1. **Fetch All Products**:
   ```bash
   curl -X GET https://xxxxxx.execute-api.us-east-1.amazonaws.com/products
   ```
2. **Trigger Background Database Seeding**:
   ```bash
   curl -X POST https://xxxxxx.execute-api.us-east-1.amazonaws.com/products/reset-database
   ```
3. **Register New User**:
   ```bash
   curl -X POST https://xxxxxx.execute-api.us-east-1.amazonaws.com/auth/register \
     -H "Content-Type: application/json" \
     -d '{"username":"gamer1","password":"123","fullName":"Gamer Pro","email":"gamer@gmail.com"}'
   ```
4. **Login Verification**:
   ```bash
   curl -X POST https://xxxxxx.execute-api.us-east-1.amazonaws.com/auth/login \
     -H "Content-Type: application/json" \
     -d '{"username":"gamer1","password":"123"}'
   ```

#### 2. Teardown Sequence

Purge provisioned resources to avoid unwanted cloud charges:

1. **Delete SAM Stack (AWS Lambda & API Gateway)**:
   ```bash
   cd gearstore-backend
   sam delete --stack-name gearstore-backend-stack
   ```

2. **Purge S3 Bucket `gearstore-data-images`**:
   - Open **S3 Console** -> select `gearstore-data-images` -> click **Empty** -> click **Delete bucket**.

3. **Delete DynamoDB Tables**:
   - Open **DynamoDB Console** -> select tables `GearStore_Products` and `GearStore_Users` -> click **Delete table**.