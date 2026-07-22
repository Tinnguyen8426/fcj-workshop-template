---
title: "Week 9 Worklog"
date: 2026-06-29
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Week 9 Objectives:
* Integrate the `aws-serverless-java-container-springboot3` dependency wrapper into the GearStore project `pom.xml`.
* Exclude embedded web server containers (`spring-boot-starter-tomcat`) from build packaging, transitioning to a Serverless Asynchronous In-Memory HTTP Adapter execution model.
* Establish internal network request conversion pipelines mapping incoming cloud HTTP requests directly into RAM buffers.
* Verify framework compatibility between Spring Boot 3.x Application Contexts and AWS Serverless Container wrappers.

### Tasks Carried Out This Week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Added `com.amazonaws.serverless:aws-serverless-java-container-springboot3` dependency into project `pom.xml`.<br>- Verified version compatibility against Spring Boot 3.2.x and Jakarta Servlet API 6.0 specifications. | 30/06/2026   | 30/06/2026      | <https://cloudjourney.awsstudygroup.com/aws-serverless-java-container-integration/> |
| 3   | - Configured `<exclusions>` tags inside `spring-boot-starter-web` to strip out embedded `spring-boot-starter-tomcat`.<br>- Analyzed technical benefits: Saving ~30-50MB RAM footprint and accelerating serverless container startup. | 01/07/2026   | 01/07/2026      | <https://cloudjourney.awsstudygroup.com/aws-serverless-java-container-integration/> |
| 4   | - Researched internal mechanics of `AwsProxyHttpServletRequestReader` and `AwsProxyHttpServletResponseWriter` streaming binary data via memory buffers.<br>- Benchmarked in-memory request processing speeds vs local TCP HTTP sockets. | 02/07/2026   | 02/07/2026      | <https://cloudjourney.awsstudygroup.com/aws-serverless-java-container-integration/> |
| 5   | - Configured Spring Profiles (`@Profile("lambda")`) enabling the application to toggle seamlessly between Serverless Lambda runtime and standard Embedded Web Server mode during local dev. | 03/07/2026   | 03/07/2026      | <https://cloudjourney.awsstudygroup.com/springboot3-profiles/> |
| 6   | - Executed compilation checks via `mvn clean compile`, resolving minor transitive dependency version conflicts.<br>- Reported wrapper integration progress to team members and updated project technical specs. | 04/07/2026   | 04/07/2026      | Internal Team Document |

### Week 9 Achievements:
* Successfully integrated `aws-serverless-java-container-springboot3` into the GearStore Maven build configuration.
* Fully stripped out embedded Tomcat web server overhead, drastically reducing memory consumption and speeding up Application Context initialization.
* Established an efficient in-memory adapter infrastructure, preparing the codebase for main entry point handler implementation in Week 10.