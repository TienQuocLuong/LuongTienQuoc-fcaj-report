---
title: "Week 12 Worklog"
date: 2026-07-03
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---

### Week 12 Objectives:
Deploy the infrastructure and assigned resources; work with the team to test the whole system.

### Tasks carried out this week:
| Day | Date | Task | Reference Material |
|---|---|---|---|
| Friday | 03/07/2026 | Worked with the team on a detailed deployment plan and configured the VPC network infrastructure (Subnet, Route Table, NAT Gateway, Security Groups) | |
| Saturday | 04/07/2026 | Worked with the team to update and finalize the deployment plan and prepare resources (source code, system configuration files) | |
| Sunday | 05/07/2026 | Directly created the two DynamoDB tables (playwright-test-history, playwright-error-log) per the designed schema; worked with the team to create two S3 buckets and two SQS queues (task queue and dead-letter queue) | |
| Monday | 06/07/2026 | Created VPC Endpoints for S3 (Gateway type) and ECR (Interface type); verified an email on SES and sent a test email to confirm; helped the team configure Lambda functions and set up the EventBridge Scheduler | |
| Tuesday | 07/07/2026 | (to be updated - testing the DynamoDB and SES parts in the end-to-end flow) | |
| Wednesday | 08/07/2026 | (to be updated - testing the whole system, fixing configuration issues, writing the self-evaluation) | |
| Thursday | 09/07/2026 | (to be updated - finalizing and submitting the internship report) | |

### Week 12 Achievements:
* Aligned with the team on the deployment plan and successfully configured the VPC network infrastructure.
* Directly created and configured the two DynamoDB tables exactly per the designed schema.
* Successfully created VPC Endpoints for S3 (Gateway) and ECR (Interface) for secure internal service communication.
* Verified and successfully tested sending email via Amazon SES.
* Worked with the team to create storage and queue resources (2 S3 buckets, 2 SQS queues including a DLQ), and supported deploying Lambda and the EventBridge Scheduler.