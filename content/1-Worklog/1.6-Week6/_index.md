---
title: "Week 6 Worklog"
date: 2026-06-08
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Week 6 Objectives:
* Study open-source documentation for the AWS Serverless Java Container project (`aws-serverless-java-container`).
* Understand request/response data mapping mechanisms between traditional Java Web Frameworks (Spring Boot) and AWS Lambda execution environments.
* Explore Adapter Pattern implementations converting `AwsProxyRequest` / `AwsProxyResponse` JSON events into standard Java Servlet API `HttpServletRequest` / `HttpServletResponse` objects.
* Evaluate architectural approaches for running Spring Boot applications on Lambda without refactoring existing Controller classes or business logic.

### Tasks Carried Out This Week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Researched the open-source `aws-serverless-java-container` GitHub repository and AWS integration guides.<br>- Analyzed the core engineering challenge: How Spring Boot applications designed for web servers (Tomcat/Jetty) process events in AWS Lambda. | 09/06/2026   | 09/06/2026      | <https://cloudjourney.awsstudygroup.com/aws-serverless-java-container/> |
| 3   | - Studied Adapter Pattern design within `aws-serverless-java-container`.<br>- Examined how adapters receive raw `AwsProxyRequest` events from API Gateway and instantiate mock `AwsProxyHttpServletRequest` objects complying with Servlet specs. | 10/06/2026   | 10/06/2026      | <https://cloudjourney.awsstudygroup.com/aws-serverless-java-container/> |
| 4   | - Investigated response processing pipelines: After Spring Boot Controllers yield responses, the adapter intercepts `HttpServletResponse` and wraps it into binary `AwsProxyResponse` payloads for API Gateway. | 11/06/2026   | 11/06/2026      | <https://cloudjourney.awsstudygroup.com/aws-serverless-java-container/> |
| 5   | - Evaluated trade-offs of launching full Spring Boot Application Contexts inside Lambda Execution Environments vs writing granular micro-functions.<br>- Assessed benefits of retaining RESTful Controllers, Security Filter Chains, and Dependency Injection. | 12/06/2026   | 12/06/2026      | <https://cloudjourney.awsstudygroup.com/serverless-springboot-architecture/> |
| 6   | - Constructed end-to-end Request/Response Sequence Diagrams from API Gateway through the Adapter layer to Spring Boot Controllers.<br>- Presented research findings to project advisors and team members. | 13/06/2026   | 13/06/2026      | Internal Team Document |

### Week 6 Achievements:
* Comprehensive architectural understanding of the AWS Serverless Java Container framework.
* Mastery over Adapter Pattern mechanics translating AWS Lambda JSON events into standard Java Servlet APIs.
* Defined the target migration architecture enabling Spring Boot 3 applications to run seamlessly on AWS Lambda while preserving existing Controllers.