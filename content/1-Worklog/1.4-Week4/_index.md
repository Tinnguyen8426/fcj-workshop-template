---
title: "Week 4 Worklog"
date: 2026-05-25
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Week 4 Objectives:
* Complete Module 3 advanced labs focusing on AWS Lambda execution environments.
* Deeply study the 3 distinct phases of the Lambda Execution Environment Lifecycle: Init Phase, Invoke Phase, and Shutdown Phase.
* Analyze root causes of JVM Cold Start latency in Java environments (JVM startup, classloading overhead, heavy framework initializations, JIT compilation).
* Evaluate Cold Start mitigation techniques including Provisioned Concurrency, AWS Lambda SnapStart (CRaC - Coordinated Restore at Checkpoint), and package payload size optimization.

### Tasks Carried Out This Week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Executed Module 3 advanced hands-on labs, inspecting execution logs on Amazon CloudWatch Logs.<br>- Analyzed standardized metric lines: `Init Duration` (environment setup time), `Duration` (code execution duration), and `Billed Duration`. | 26/05/2026   | 26/05/2026      | <https://cloudjourney.awsstudygroup.com/lambda-lifecycle/> |
| 3   | - Studied details of the 3 Lambda lifecycle phases: Init Phase (Extension init, Runtime init, Function init), Invoke Phase, and Shutdown Phase.<br>- Pinpointed exact Cold Start occurrences during the Init Phase when new container execution contexts spin up. | 27/05/2026   | 27/05/2026      | <https://cloudjourney.awsstudygroup.com/lambda-lifecycle/> |
| 4   | - Benchmarked Cold Start latencies for Java-based functions on JVM runtime.<br>- Identified key overhead contributors: JVM instantiation, intensive class loading, heavy dependency instantiation, and static block execution. | 28/05/2026   | 28/05/2026      | <https://cloudjourney.awsstudygroup.com/java-coldstart-analysis/> |
| 5   | - Researched and evaluated modern Java latency mitigation strategies.<br>- Explored AWS Lambda SnapStart powered by CRaC (Coordinated Restore at Checkpoint), capturing JVM memory state snapshots post-init for rapid restoration. | 29/05/2026   | 29/05/2026      | <https://cloudjourney.awsstudygroup.com/lambda-snapstart/> |
| 6   | - Compared performance and cost trade-offs between Provisioned Concurrency (pre-warmed environments) and SnapStart.<br>- Compiled a technical strategy document for optimizing Java/Spring Boot serverless deployment. | 30/05/2026   | 30/05/2026      | Internal Team Document |

### Week 4 Achievements:
* Deep structural understanding of AWS Lambda execution environment lifecycle (Init, Invoke, Shutdown) and CloudWatch metric profiling.
* Identified exact technical factors causing JVM Cold Start delays in Java serverless applications.
* Mastered AWS Lambda SnapStart (CRaC) and Provisioned Concurrency mechanisms to pave the way for optimizing Spring Boot 3 applications.
