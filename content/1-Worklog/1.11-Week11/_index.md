---
title: "Week 11 Worklog"
date: 2026-07-13
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Week 11 Objectives:
* Fine-tune `maven-shade-plugin` configuration details in `pom.xml` to optimize output artifact sizes for the GearStore project.
* Strip out unused transitive dependencies, testing libraries (`junit`, `mockito`), and redundant logging frameworks.
* Execute packaging builds compiling the entire system into a single Shaded Uber JAR named `backend-0.0.1-SNAPSHOT.jar`.
* Ensure ultra-compact JAR sizes to minimize artifact download latency and decompression times during AWS Lambda Cold Starts.

### Tasks Carried Out This Week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Audited complete Maven dependency trees using `mvn dependency:tree`, identifying non-essential runtime libraries.<br>- Applied `<scope>test</scope>` tags and `<exclusions>` rules to strip unwanted dependencies from executable JARs. | 14/07/2026   | 14/07/2026      | <https://cloudjourney.awsstudygroup.com/maven-dependency-optimization/> |
| 3   | - Configured detailed `<configuration>` blocks for `maven-shade-plugin` in `pom.xml`.<br>- Added `<createUnshadedJar>false</createUnshadedJar>` rules and fine-tuned `<artifactSet>` filters to include essential libraries only. | 15/07/2026   | 15/07/2026      | <https://cloudjourney.awsstudygroup.com/maven-shade-advanced/> |
| 4   | - Added specialized Resource Transformers: `ManifestResourceTransformer` (specifying Handler Entry Point metadata) and `ServicesResourceTransformer` (aggregating `META-INF/services/*` files for SPI discovery). | 16/07/2026   | 16/07/2026      | <https://cloudjourney.awsstudygroup.com/maven-shade-advanced/> |
| 5   | - Executed compilation builds via `mvn clean package -DskipTests`, monitoring class shading compression steps.<br>- Inspected target artifact size `target/backend-0.0.1-SNAPSHOT.jar`: Reduced size from ~110 MB down to ~35 MB. | 17/07/2026   | 17/07/2026      | <https://cloudjourney.awsstudygroup.com/maven-shade-advanced/> |
| 6   | - Inspected compiled contents using `jar -tf target/backend-0.0.1-SNAPSHOT.jar`, confirming `StreamLambdaHandler.class` resides at the correct root package path.<br>- Delivered verified JAR artifact to team for cloud deployment. | 18/07/2026   | 18/07/2026      | Internal Team Document |

### Week 11 Achievements:
* Mastered production-grade `maven-shade-plugin` optimization configurations for Java Serverless workloads.
* Stripped 100% of non-essential dependencies, trimming total artifact file size by 68% down to ~35 MB.
* Successfully built executable Shaded Uber JAR (`backend-0.0.1-SNAPSHOT.jar`), ready for optimal Cold Start cloud deployments.