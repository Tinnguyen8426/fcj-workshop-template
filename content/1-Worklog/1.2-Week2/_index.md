---
title: "Week 2 Worklog"
date: 2026-05-11
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Week 2 Objectives:
* Complete Module 1 & Module 2 focusing on server virtualization and advanced cloud authorization models.
* Deeply analyze JSON syntax and structural blocks of IAM Policy (`Effect`, `Action`, `Resource`, `Condition`, and Explicit Deny rules).
* Master Amazon Resource Name (ARN) formatting standards across AWS services.
* Provision and apply IAM Execution Roles for Serverless compute services adhering strictly to the Principle of Least Privilege.

### Tasks Carried Out This Week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Studied Modules 1 & 2 covering virtual machine architecture (EC2) and identity/resource-based access control models.<br>- Analyzed structural JSON policy blocks: Statement, Effect (Allow/Explicit Deny), Action, and Resource ARN. | 12/05/2026   | 12/05/2026      | <https://cloudjourney.awsstudygroup.com/iam-basics/> |
| 3   | - Practiced evaluating sample IAM policies, verifying how Explicit Deny overrides all Allow statements within the IAM evaluation engine.<br>- Wrote custom JSON policies enforcing IP-range conditions (`aws:SourceIp`). | 13/05/2026   | 13/05/2026      | <https://cloudjourney.awsstudygroup.com/iam-policies/> |
| 4   | - Investigated IAM Role architecture and temporary credential delegation via AWS Security Token Service (STS AssumeRole).<br>- Differentiated identity lifecycles between long-term IAM Users and service-bound IAM Roles. | 14/05/2026   | 14/05/2026      | <https://cloudjourney.awsstudygroup.com/iam-roles/> |
| 5   | - Configured an IAM Execution Role dedicated to AWS Lambda serverless execution environments.<br>- Set up Trust Policies allowing `lambda.amazonaws.com` service principal to assume the role and attached CloudWatch logging permissions. | 15/05/2026   | 15/05/2026      | <https://cloudjourney.awsstudygroup.com/iam-execution-role/> |
| 6   | - Audited IAM Role configurations using AWS CLI tools (`aws iam get-role` and `aws iam list-attached-role-policies`).<br>- Documented IAM research findings and shared insights with team members. | 16/05/2026   | 16/05/2026      | Internal Team Document |

### Week 2 Achievements:
* Gained comprehensive understanding of IAM evaluation logic, Explicit Deny precedence, and JSON policy construction.
* Mastered Amazon Resource Name (`arn:aws:service:region:account-id:resource-id`) formatting rules.
* Proficiently configured IAM Execution Roles for serverless compute workloads, enforcing Least Privilege access controls.
