---
title: "Week 1 Worklog"
date: 2026-05-04
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Week 1 Objectives:
* Attend orientation sessions of the First Cloud AI Journey (FCAJ) program, review technical documentation, and setup local development environments.
* Install and configure AWS Command Line Interface (AWS CLI v2) on local machines, managing secure Named Profiles (`~/.aws/credentials` and `~/.aws/config`).
* Verify secure connection from local machines to AWS Cloud infrastructure using AWS Security Token Service (AWS STS).
* Configure automated budget monitoring rules via AWS Budgets & Billing Alarms to prevent unexpected lab costs.

### Tasks Carried Out This Week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Attended program kick-off orientation meeting, reviewed the 12-week internship roadmap and weekly reporting guidelines.<br>- Conducted theoretical research on AWS Cloud architecture and fundamental security practices. | 05/05/2026   | 05/05/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Downloaded and installed AWS CLI v2 package on local workstation.<br>- Generated Access Keys from AWS Management Console and executed `aws configure` to set default Region (`ap-southeast-1`) and JSON output format. | 06/05/2026   | 06/05/2026      | <https://cloudjourney.awsstudygroup.com/1-aws-cli-setup/> |
| 4   | - Researched named profile configuration (`--profile`) to segregate Development and Staging environments within `~/.aws/credentials`.<br>- Verified identity credentials via `aws sts get-caller-identity` to confirm proper IAM permissions. | 07/05/2026   | 07/05/2026      | <https://cloudjourney.awsstudygroup.com/1-aws-cli-setup/> |
| 5   | - Configured cost alert rules (Cost Budget Limit at $10) using AWS Budgets.<br>- Set up Email notification channels to auto-trigger alerts when actual or forecasted spending exceeds 80% threshold. | 08/05/2026   | 08/05/2026      | <https://cloudjourney.awsstudygroup.com/2-billing-alert/> |
| 6   | - Reviewed AWS Billing Dashboard and AWS Cost Explorer to confirm no idle resources were incurring unintended charges.<br>- Summarized Week 1 progress report and conducted group sync meeting. | 09/05/2026   | 09/05/2026      | Internal Team Document |

### Week 1 Achievements:
* Mastered the internship roadmap and technical requirements of the First Cloud AI Journey program.
* Established a fully configured CLI development environment using AWS CLI v2 with secure Named Profiles.
* Gained proficiency in identity verification using `aws sts get-caller-identity` prior to conducting complex cloud operations.
* Successfully implemented cost control via AWS Budgets, protecting cloud accounts from financial drift during lab experiments.
