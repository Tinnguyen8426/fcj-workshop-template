---
title: "Week 5 Worklog"
date: 2026-06-01
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Week 5 Objectives:
* Study Module 4 covering OS-level Virtualization and Containerization technologies.
* Practice containerizing applications using Docker engine, utilizing `.dockerignore` files and layer caching strategies.
* Design Multi-stage build Dockerfiles separating compilation phases from runtime stages to shrink Java/Spring Boot container image sizes.
* Provision an Amazon Elastic Container Registry (ECR) repository, authenticate Docker CLI with ECR, and push container images to cloud storage.

### Tasks Carried Out This Week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Studied Module 4 containerization concepts, comparing Virtual Machine architectures (hypervisor-based) vs Docker Containers (shared OS kernel).<br>- Installed Docker Desktop and validated container management commands (`docker run`, `docker ps`, `docker images`). | 02/06/2026   | 02/06/2026      | <https://cloudjourney.awsstudygroup.com/docker-basics/> |
| 3   | - Researched standardized Dockerfile construction for Java/Spring Boot microservices.<br>- Analyzed layer caching impacts of `FROM`, `RUN`, `COPY`, `WORKDIR`, and `ENTRYPOINT` instructions on final image size. | 03/06/2026   | 03/06/2026      | <https://cloudjourney.awsstudygroup.com/dockerfile-best-practices/> |
| 4   | - Implemented Multi-stage Dockerfile builds: Stage 1 leveraged Maven JDK base image to compile source code into JAR; Stage 2 utilized minimal Alpine/Distroless JRE to run the artifact.<br>- Reduced final container image size from ~800MB down to ~200MB. | 04/06/2026   | 04/06/2026      | <https://cloudjourney.awsstudygroup.com/docker-multistage/> |
| 5   | - Provisioned a private repository on Amazon Elastic Container Registry (ECR).<br>- Executed `aws ecr get-login-password` to authenticate Docker CLI, applied `docker tag`, and pushed the image using `docker push` to Amazon ECR. | 05/06/2026   | 05/06/2026      | <https://cloudjourney.awsstudygroup.com/ecr-deployment/> |
| 6   | - Enabled ECR Image Scanning on Push to automatically scan container images for known CVE security vulnerabilities.<br>- Documented containerization guidelines and shared technical setup with team members. | 06/06/2026   | 06/06/2026      | Internal Team Document |

### Week 5 Achievements:
* Gained deep comprehension of containerization benefits over traditional virtual machines.
* Mastered Multi-stage Dockerfile packaging, successfully cutting Java/Spring Boot container image footprint by 75%.
* Established secure container deployment pipelines pushing verified images to Amazon ECR.