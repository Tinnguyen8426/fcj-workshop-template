---
title: "Proposal Document"
date: 2026-07-20
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# GearStore E-Commerce Platform  
## Unified AWS Serverless Solution for Gaming Gear E-Commerce Platform  

### 1. Executive Summary  
The **GearStore E-Commerce Platform** is designed as a modern online retail system specializing in gaming equipment and computer accessories (gaming gear), built on a cloud-native Serverless architecture. The platform addresses challenges related to high traffic spikes during flash sales, optimizes operational costs, and delivers a seamless real-time shopping experience. The system combines a **Java 21 / Spring Boot 3** backend deployed on **AWS Lambda**, a low-latency **Amazon DynamoDB** NoSQL database, **Amazon S3** for media asset storage, and secure authentication via **Amazon Cognito / JWT**. The web user interface is optimized for speed and SEO using **Next.js** hosted on **AWS Amplify**.

### 2. Problem Statement  
*Current Issues*  
Traditional monolithic e-commerce platforms often experience downtime or severe latency during flash sale events due to the inability to scale infrastructure rapidly. Maintaining dedicated 24/7 servers incurs high fixed operational costs, even during off-peak hours with low traffic. Additionally, managing a diverse catalog of gaming products (keyboards, mice, headsets, monitors) with dynamic attributes requires a highly responsive NoSQL database rather than traditional RDBMS.

*Solution*  
GearStore adopts a full-stack **AWS Serverless architecture**:
- **Backend API**: Developed using **Java 21 & Spring Boot 3**, integrated with `aws-serverless-java-container` to run seamlessly on **AWS Lambda** routed through **Amazon API Gateway**.
- **Database & Storage**: Utilizes **Amazon DynamoDB** (via AWS SDK v2 DynamoDB Enhanced Client) for millisecond-level retrieval of products, orders, and user profiles; **Amazon S3** manages high-resolution product images.
- **User Management & Security**: Integrates **Amazon Cognito** and JWT Authentication to ensure secure role-based access control between customers and administrators.
- **Frontend UI**: Built with **Next.js (React)** featuring a modern dark-mode gaming aesthetic, hosted on **AWS Amplify**.

*Benefits and Return on Investment (ROI)*  
- **Auto-scaling Capability**: Automatically scales up to handle thousands of concurrent requests during peak sale periods without manual infrastructure management.
- **Pay-as-you-go Cost Efficiency**: Leveraging Serverless pricing models (Lambda & DynamoDB On-Demand), baseline hosting costs remain extremely low when idle (approx. $0.50 – $1.20 USD/month for lab/testing environments).
- **Superior User Experience**: Page load times under 1 second and rapid API responsiveness thanks to Java 21 runtime optimizations and DynamoDB performance.

### 3. Solution Architecture  
The platform implements a multi-tier AWS Serverless architecture covering the end-to-end request processing pipeline.

*AWS Services Utilized*  
- **AWS Lambda**: Executes core Spring Boot 3 business logic (Auth, Product, Order, Inventory APIs).
- **Amazon API Gateway**: Acts as the HTTP entry point, routing requests to AWS Lambda.
- **Amazon DynamoDB**: Handles NoSQL data storage (Products, Categories, Users, Orders) with seamless scaling.
- **Amazon S3**: Object storage for high-resolution product media and static assets.
- **AWS Amplify**: Hosts the Next.js frontend application with continuous deployment via Git integration.
- **Amazon Cognito**: Manages user authentication, registration, and access token verification.

*Component Design*  
- **Client Tier**: Responsive Next.js application delivering product browsing, shopping cart functionality, checkout, and an Admin dashboard.
- **API & Authentication Tier**: API Gateway handles incoming traffic and validates JWT tokens issued by Amazon Cognito.
- **Business Logic Tier**: AWS Lambda invokes the Spring Boot 3 container (`StreamLambdaHandler`) to execute core e-commerce logic.
- **Data & Storage Tier**: DynamoDB processes real-time database queries; S3 handles image storage and delivery.

### 4. Technical Implementation  
*Implementation Phases*  
The project is organized into 4 primary phases:  
1. **Research & Architecture Design**: Analyze e-commerce requirements, design DynamoDB NoSQL single-table/multi-table schemas, and draft AWS Serverless architecture (Month 1).  
2. **Cost Estimation & Core Backend Setup**: Initialize Spring Boot 3 project (Java 21), integrate AWS SDK v2 (`dynamodb-enhanced`, `s3`), and configure Serverless Java Container wrappers (Months 1–2).  
3. **Frontend Development & AWS Integration**: Build Next.js user interfaces, integrate API Gateway endpoints, Cognito authentication, and S3 media uploads (Month 2).  
4. **Testing, Optimization & Deployment**: Test Lambda cold-start mitigation strategies, package application artifacts via Maven Shade Plugin, and deploy to AWS Amplify and AWS Lambda (Months 2–3).  

*Technical Specifications*  
- **Backend**: Java 21, Spring Boot 3.3.0, Lombok, Maven (`maven-shade-plugin`), AWS SDK v2 (`dynamodb-enhanced`, `s3`), AWS Serverless Java Container.
- **Frontend**: Next.js, React, Tailwind CSS / Vanilla CSS, Axios/Fetch API.
- **Cloud & DevOps**: AWS Lambda, API Gateway, DynamoDB, S3, Cognito, AWS Amplify, AWS SAM / CDK.

### 5. Roadmap & Milestones  
- **Pre-internship (Month 0)**: 1 month of requirement gathering and conceptual design of the GearStore platform.  
- **Internship (Months 1–3)**:  
    - **Month 1**: Learn AWS Cloud architecture and set up initial DynamoDB data models.  
    - **Month 2**: Develop Spring Boot 3 RESTful APIs (Auth, Products, Orders) and Next.js frontend pages.  
    - **Month 3**: Deploy to AWS Amplify and Lambda, conduct load/performance testing, and release for pilot usage.  
- **Post-Deployment**: Monitor system health via Amazon CloudWatch and explore future AI/ML product recommendation integrations.

### 6. Budget Estimation  

*Infrastructure Costs (Estimated via AWS Serverless Pay-as-you-go Pricing)*  
- **AWS Lambda**: ~$0.00 USD/month (Covered under AWS Free Tier for up to 1M requests/month).  
- **Amazon DynamoDB**: ~$0.25 USD/month (On-Demand read/write requests & storage).  
- **Amazon S3**: ~$0.10 USD/month (Product image storage & data transfer).  
- **Amazon API Gateway**: ~$0.05 USD/month (Estimated for 20,000–50,000 HTTP requests).  
- **AWS Amplify**: ~$0.35 USD/month (Hosting for Next.js frontend).  
- **Amazon Cognito**: $0.00 USD/month (Free for up to 50,000 Monthly Active Users).  

*Total Estimated Monthly Cost*: ~$0.75 USD/month (~$9.00 USD for 12 months)  
*ROI Period*: 3–6 months due to eliminating fixed EC2/dedicated server maintenance expenses.

### 7. Risk Assessment  
*Risk Matrix*  
- **AWS Lambda Cold-Start Latency**: Medium impact, medium probability (occurs during JVM initialization on cold invocations).  
- **Unexpected DynamoDB Write Cost Overruns**: Medium impact, low probability.  
- **Cloud Service Interruption**: High impact, very low probability.  

*Mitigation Strategies*  
- **Lambda Cold-Starts**: Leverage Java 21 runtime efficiency, keep dependencies minimal, and utilize Provisioned Concurrency if necessary.  
- **DynamoDB Costs**: Optimize Query Index usage (Global Secondary Indexes - GSI) and configure AWS Budget Alerts.  

### 8. Expected Outcomes  
- **Technical Improvements**: Successfully build a Cloud-Native Serverless E-Commerce platform capable of auto-scaling under peak traffic with Spring Boot 3 and Java 21.  
- **Long-term Value**: Provides a reusable, scalable serverless template adaptable to other retail environments, with future readiness for payment gateway integrations (VNPAY, Momo) and automated inventory management.