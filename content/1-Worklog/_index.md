---
title: "Worklog"
date: 2026-05-04
weight: 1
chapter: false
pre: " <b> 1. </b> "
---

This chapter records the full work progress, theoretical research topics, hands-on cloud labs, and the complete engineering journey of packaging and optimizing a Spring Boot 3 web application onto AWS Lambda serverless infrastructure throughout the 12 internship weeks in the FCAJ program.

The worklog content is detailed week by week as follows:

**Week 1:** [FCAJ orientation, setting up AWS CLI environment, configuring IAM profiles, and establishing cost alerts via AWS Budgets](1.1-week1/)

**Week 2:** [In-depth study of IAM authorization architecture, IAM Policy JSON structures (Rules, ARNs, Conditions), and IAM Execution Roles for Serverless Compute](1.2-week2/)

**Week 3:** [Researching Serverless Architecture, Function-as-a-Service (FaaS) fundamentals on AWS Lambda, Event Triggers, and Memory/Timeout resource tuning](1.3-week3/)

**Week 4:** [Analyzing Lambda Execution Environment Lifecycle, JVM Cold Start latency mechanics, and mitigation strategies for Java serverless applications](1.4-week4/)

**Week 5:** [Studying OS-level virtualization & containerization, writing multi-stage Dockerfiles for Spring Boot, and pushing container images to Amazon ECR](1.5-week5/)

**Week 6:** [Analyzing open-source AWS Serverless Java Container framework, Request/Response mapping mechanisms from Web Frameworks to AWS Lambda](1.6-week6/)

**Week 7:** [Practicing build automation with Maven, library aggregation via maven-shade-plugin, and security signature filtering](1.7-week7/)

**Week 8:** [Initializing Spring Boot 3 core architecture for the GearStore backend, establishing Maven Monorepo structure and dependency management](1.8-week8/)

**Week 9:** [Integrating aws-serverless-java-container-springboot3 dependency into pom.xml and bypassing traditional embedded Tomcat overhead](1.9-week9/)

**Week 10:** [Implementing StreamLambdaHandler.java entry point, processing binary request streams, decoding payloads, and routing to Spring Boot](1.10-week10/)

**Week 11:** [Configuring advanced maven-shade-plugin transformers/filters and building an optimized Shaded Uber JAR (backend-0.0.1-SNAPSHOT.jar)](1.11-week11/)

**Week 12:** [Deploying JAR artifact onto AWS Lambda console, fine-tuning memory allocations, analyzing CloudWatch execution metrics, and final acceptance](1.12-week12/)
