---
title: "Week 3 Worklog"
date: 2026-05-18
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Week 3 Objectives:
* Study Module 3 covering Serverless Architecture and Event-Driven Architecture (EDA) paradigms.
* Understand Function-as-a-Service (FaaS) mechanics on AWS Lambda and its pay-per-use billing model based on request counts and execution duration (Gigabyte-seconds).
* Explore common Event Sources and Triggers including S3 Events, API Gateway, DynamoDB Streams, and SQS queues.
* Master resource allocation tuning strategies for Memory (128 MB to 10,240 MB with proportional vCPU scaling) and execution Timeout settings.

### Tasks Carried Out This Week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Studied Module 3 serverless documentation, comparing total cost of ownership (TCO) and auto-scaling capabilities between EC2 instances and AWS Lambda.<br>- Researched Event-Driven Architecture concepts and event processing pipelines. | 19/05/2026   | 19/05/2026      | <https://cloudjourney.awsstudygroup.com/serverless-intro/> |
| 3   | - Created experimental Lambda functions using Management Console and AWS CLI with Java 17/21 runtime.<br>- Analyzed invocation modes: Synchronous, Asynchronous, and Polling-based Event Source Mappings. | 20/05/2026   | 20/05/2026      | <https://cloudjourney.awsstudygroup.com/lambda-invocations/> |
| 4   | - Configured Event Source Triggers with AWS Lambda (testing Amazon S3 object triggers and Amazon API Gateway HTTP requests).<br>- Analyzed raw JSON Event payloads received via function `Context` and `InputStream` objects. | 21/05/2026   | 21/05/2026      | <https://cloudjourney.awsstudygroup.com/lambda-triggers/> |
| 5   | - Benchmarked Memory configuration variations for Lambda functions (ranging from 128MB, 512MB to 2048MB).<br>- Evaluated proportional vCPU allocation scaling and its impact on computational task completion speed. | 22/05/2026   | 22/05/2026      | <https://cloudjourney.awsstudygroup.com/lambda-memory-tuning/> |
| 6   | - Configured max execution Timeouts (up to 15 minutes max limit) to safeguard functions from indefinite execution loops.<br>- Compiled performance profiling notes and reviewed findings with team members. | 23/05/2026   | 23/05/2026      | Internal Team Document |

### Week 3 Achievements:
* Comprehensive grasp of Serverless computing paradigms and Event-Driven Architecture.
* Mastery over AWS Lambda function configuration, invocation pattern mechanics, and event mapping.
* Ability to optimize Lambda execution costs and response latency through fine-tuned Memory/vCPU allocation balancing.
