---
title : "Overview of Amazon S3 Setup & Auth APIs"
date : 2026-07-20
weight : 1
chapter : false
pre : " <b> 5.4.1. </b> "
---

#### Amazon S3 Integration in `ProductController`

The backend application manages product media files via **Amazon S3**:
- Official Bucket Name: `gearstore-data-images` (configured in `ProductController.java`).
- **Automated Media Cleanup**: Updating product images (`PUT /products/{id}`) or deleting products (`DELETE /products/{id}`) automatically triggers `deleteS3Object(key)` to purge stale media files.
- **Asynchronous Seed Pipeline**: `POST /products/reset-database` runs a background thread that cleans up S3 and uploads 110+ high-res gaming equipment images directly to S3.

#### User Authentication APIs in `AuthController`

The `/auth` controller manages user records in DynamoDB table `GearStore_Users`:
- `POST /auth/login`: Authenticates user credentials and returns full user profile details.
- `POST /auth/register`: Registers a new account (default role `USER`).
- `GET /auth/users`: Fetches full user listing for the Admin Dashboard.
- `PUT /auth/users/update`: Updates user roles and contact details.
