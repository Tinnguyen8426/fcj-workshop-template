---
title: "Week 8 Worklog"
date: 2026-06-22
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Week 8 Objectives:
* Initialize core Spring Boot 3 architecture (Java 17/21 runtime, Jakarta EE 10 specs) serving as the core backend engine for the GearStore e-commerce platform.
* Establish standardized Maven project directory structures following Layered Architecture principles (separating Controller, Service, Repository, DTO, and Entity packages).
* Synchronize dependency versions across Spring Web, Spring Data JPA, Hibernate, Validation, and Jackson libraries via Maven `<dependencyManagement>` inside `pom.xml`.
* Assign tasks, establish backend coding standards, and align Git Workflow conventions across team members.

### Tasks Carried Out This Week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Initialized Spring Boot 3 project via Spring Initializr using Java 17 runtime and core modules: Spring Web, Spring Data JPA, PostgreSQL Driver, Validation, and Lombok.<br>- Analyzed Spring Boot 3 updates leveraging Jakarta EE 10 specs (`jakarta.persistence.*`, `jakarta.validation.*`). | 23/06/2026   | 23/06/2026      | <https://cloudjourney.awsstudygroup.com/springboot3-setup/> |
| 3   | - Designed GearStore directory structure following Clean / Layered Architecture standards.<br>- Created core packages: `com.gearstore.controller`, `com.gearstore.service`, `com.gearstore.repository`, `com.gearstore.entity`, `com.gearstore.dto`. | 24/06/2026   | 24/06/2026      | <https://cloudjourney.awsstudygroup.com/springboot3-architecture/> |
| 4   | - Constructed central `pom.xml` build configuration, enforcing standardized dependency versions.<br>- Guaranteed team alignment on Spring Boot 3.2.x, Jakarta Servlet API 6.0, and Jackson Databind versions to eliminate binary conflicts. | 25/06/2026   | 25/06/2026      | <https://cloudjourney.awsstudygroup.com/springboot3-setup/> |
| 5   | - Implemented sample RESTful Controllers (`ProductController`, `CategoryController`) utilizing `@RestController`, `@RequestMapping`, `@GetMapping`, `@PostMapping` annotations.<br>- Verified local execution on Tomcat port `8080` using Swagger UI / Postman. | 26/06/2026   | 26/06/2026      | <https://cloudjourney.awsstudygroup.com/springboot3-rest-api/> |
| 6   | - Pushed baseline codebase to shared team Git repository, establishing branch strategies (`main`, `develop`, `feature/*`).<br>- Conducted Code Review guidelines sync and held Week 8 progress meeting with team members. | 27/06/2026   | 27/06/2026      | Internal Team Document |

### Week 8 Achievements:
* Successfully bootstrapped core Spring Boot 3 backend application for the GearStore system on Java 17 runtime and Jakarta EE 10.
* Standardized project package structure following professional, scalable Layered Architecture patterns.
* Fully synchronized Maven build files (`pom.xml`) and dependency matrices across all team developers.
* Implemented and validated foundational RESTful API endpoints running locally.