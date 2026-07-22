---
title: "Week 12 Worklog"
date: 2026-07-20
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---

### Week 12 Objectives:
* Deploy the compiled `backend-0.0.1-SNAPSHOT.jar` artifact onto AWS Lambda via Management Console and AWS CLI.
* Configure correct Handler Entry Point syntax: `com.gearstore.config.StreamLambdaHandler::handleRequest` and attach the IAM Execution Role created in Week 2.
* Benchmark real-world performance by tuning Lambda RAM allocations (512 MB, 1024 MB, 2048 MB, 3072 MB) to find the optimal sweet spot between cost and execution latency.
* Analyze operational log metrics (Init Duration, Duration, Max Memory Used) on Amazon CloudWatch Logs, completing final project packaging acceptance.

### Tasks Carried Out This Week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Provisioned new Lambda function `gearstore-backend-service` on Java 17/21 runtime via AWS Console.<br>- Uploaded `backend-0.0.1-SNAPSHOT.jar` artifact and configured Handler string `com.gearstore.config.StreamLambdaHandler::handleRequest`. | 21/07/2026   | 21/07/2026      | <https://cloudjourney.awsstudygroup.com/lambda-deployment-jar/> |
| 3   | - Integrated Lambda with Amazon API Gateway (HTTP API), establishing `$default` catch-all routes to proxy incoming web traffic to the Lambda function.<br>- Validated API calls via Postman, confirming successful HTTP 200 OK responses. | 22/07/2026   | 22/07/2026      | <https://cloudjourney.awsstudygroup.com/apigateway-lambda-integration/> |
| 4   | - Conducted RAM allocation benchmarking across memory tiers: 512MB, 1024MB, 1536MB, 2048MB, and 3072MB.<br>- Benchmark Result: 2048MB RAM yielded optimal performance (scaling CPU capacity and slashing Cold Start Init Duration from ~4.2s down to ~1.1s). | 23/07/2026   | 23/07/2026      | <https://cloudjourney.awsstudygroup.com/lambda-memory-benchmark/> |
| 5   | - Profiled operational logs using Amazon CloudWatch Logs Insights.<br>- Analyzed `REPORT` log metrics: `Init Duration: 1120.45 ms`, `Duration: 145.20 ms`, `Billed Duration: 146 ms`, `Memory Size: 2048 MB`, `Max Memory Used: 215 MB`. Zero OutOfMemoryErrors detected. | 24/07/2026   | 24/07/2026      | <https://cloudjourney.awsstudygroup.com/cloudwatch-logs-analysis/> |
| 6   | - Enabled AWS Lambda SnapStart, driving Cold Start response times down below 400ms.<br>- Compiled the final 12-week internship report, completing full system acceptance for the GearStore serverless packaging module. | 25/07/2026   | 28/07/2026      | Final Project Documentation |

### Week 12 Achievements:
* Successfully deployed Spring Boot 3 Serverless Java Container application onto AWS Lambda integrated seamlessly with Amazon API Gateway.
* Optimized Memory allocation to 2048 MB, scaling vCPU throughput and reducing Cold Start duration by over 73%.
* Mastered CloudWatch Insights log profiling, precisely monitoring memory footprint (`Max Memory Used`).
* Successfully achieved all objectives across the 12-week First Cloud AI Journey (FCAJ) internship program.