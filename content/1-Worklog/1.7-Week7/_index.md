---
title: "Week 7 Worklog"
date: 2026-06-15
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Week 7 Objectives:
* Practice build automation and packaging workflows using Apache Maven.
* Deeply analyze `maven-shade-plugin` mechanics in aggregating and compressing compiled source code alongside transitive dependencies into a single executable Uber/Fat JAR.
* Resolve Spring configuration file collisions (`META-INF/spring.handlers`, `META-INF/spring.schemas`, `META-INF/spring.factories`) using Maven Resource Transformers.
* Exclude third-party security signature files (`*.SF`, `*.DSA`, `*.RSA`) from dependency JARs to prevent `Invalid signature file digest` errors during cloud execution.

### Tasks Carried Out This Week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Studied Maven Build Lifecycle documentation (distinguishing `clean`, `compile`, `test`, `package`, `verify`, and `install` phases).<br>- Compared differences between Standard JARs (thin) and Fat/Uber JARs containing embedded dependencies. | 16/06/2026   | 16/06/2026      | <https://cloudjourney.awsstudygroup.com/maven-packaging-basics/> |
| 3   | - Configured `maven-shade-plugin` inside `pom.xml`, binding execution goal `shade` to the `package` build phase.<br>- Inspected generated Shaded JAR artifacts, verifying the presence of all required runtime class files. | 17/06/2026   | 17/06/2026      | <https://cloudjourney.awsstudygroup.com/maven-shade-plugin-guide/> |
| 4   | - Researched Resource Transformers in `maven-shade-plugin`.<br>- Configured `AppendingTransformer` for `META-INF/spring.handlers`, `META-INF/spring.schemas`, and `META-INF/spring.factories` to aggregate Spring bean definitions across dependencies. | 18/06/2026   | 18/06/2026      | <https://cloudjourney.awsstudygroup.com/maven-shade-plugin-guide/> |
| 5   | - Configured plugin `<filters>` to strip third-party digital security signature files (`META-INF/*.SF`, `META-INF/*.DSA`, `META-INF/*.RSA`).<br>- Completely eliminated potential `SecurityException: Invalid signature file digest` runtime failures on AWS Lambda. | 19/06/2026   | 19/06/2026      | <https://cloudjourney.awsstudygroup.com/maven-shade-plugin-guide/> |
| 6   | - Executed `mvn clean package` build commands on terminal, inspecting artifact integrity and final file size.<br>- Validated artifact decompression performance and shared standardized `pom.xml` configurations with team members. | 20/06/2026   | 20/06/2026      | Internal Team Document |

### Week 7 Achievements:
* Mastered automated build packaging workflows using Apache Maven.
* Deep technical understanding of `maven-shade-plugin` library aggregation and Uber JAR creation.
* Successfully configured Resource Transformers and signature filters, producing clean execution artifacts fully compatible with AWS Lambda JVM runtime environments.