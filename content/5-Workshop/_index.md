---
title: "Workshop"
date: 2026-07-20
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Deploying GearStore Backend on AWS Serverless Architecture

#### Overview

**GearStore Backend API** is an e-commerce server solution for tech accessories and gaming gear. Built with **Java 21** and **Spring Boot 3.3.0**, it incorporates `aws-serverless-java-container-springboot3` to run as a serverless container on **AWS Lambda** via **Amazon API Gateway**.

In this hands-on lab series, you will package and deploy the **gearstore-backend** codebase to AWS Cloud:

+ **SDK Integration & Configuration**: Integrate **AWS SDK v2** (`dynamodb-enhanced` & `s3`) and configure `DynamoDbConfig` to seamlessly switch between local credentials and AWS Lambda IAM Roles.
+ **NoSQL Storage with DynamoDB**: Set up two DynamoDB tables: `GearStore_Products` (PartitionKey: `ProductId`, SortKey: `RecordType`) and `GearStore_Users` (PartitionKey: `Username`).
+ **S3 Media Storage**: Upload and manage product images directly on **Amazon S3** (`gearstore-data-images`).
+ **Packaging & Deployment**: Package an Uber-JAR using `maven-shade-plugin` and deploy to **AWS Lambda** via `StreamLambdaHandler`.

#### Lab Contents

1. [Backend Source Code Architecture Overview](5.1-Workshop-overview/)
2. [Prerequisites & Maven Environment Configuration](5.2-Prerequiste/)
3. [Create DynamoDB Tables & Deploy Spring Boot 3 Lambda](5.3-S3-vpc/)
4. [Configure Amazon S3 & Auth / User Management APIs](5.4-S3-onprem/)
5. [Integrating Next.js Frontend with Backend APIs](5.5-Policy/)
6. [API Testing & Resource Cleanup](5.6-Cleanup/)