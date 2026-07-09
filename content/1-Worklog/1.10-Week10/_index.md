---
title: "Week 10 Worklog"
date: 2026-06-19
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

### Week 10 Objectives:
Finalize the detailed description and architecture diagram; focus on designing the data layer (DynamoDB) and researching VPC Endpoints.

### Tasks carried out this week:
| Day | Date | Task | Reference Material |
|---|---|---|---|
| Friday | 19/06/2026 | Reviewed the modules and practiced sketching a few candidate architecture diagrams for the system | |
| Saturday | 20/06/2026 | Worked with the team to draft the detailed topic description; contributed the design for two DynamoDB tables used to store test history and error logs | |
| Sunday | 21/06/2026 | Designed the detailed schema for the playwright-test-history table (partition key: task_id) and the playwright-error-log table (partition key: error_id), clearly defining the fields and data types | |
| Monday | 22/06/2026 | Worked with the team on the architecture diagram, identifying where DynamoDB fits in the system and the read/write data flows from Lambda | |
| Tuesday | 23/06/2026 | Reviewed the data connection flows, identified and adjusted parts that weren't quite right; added services related to my assigned part | |
| Wednesday | 24/06/2026 | Presented the architecture diagram to the mentor with the team for review; noted the points needing adjustment and discussed how to address them | |
| Thursday | 25/06/2026 | Thoroughly researched VPC Endpoints: distinguished the Gateway Endpoint (for S3, DynamoDB) from the Interface Endpoint (for ECR), preparing for my part of the deployment | |

### Week 10 Achievements:
* Worked with the team to finalize the detailed description and architecture diagram of the system (including CloudFront, S3, Cognito, API Gateway, SQS, ECS Fargate, ECR, DynamoDB, Lambda, CloudWatch, Secrets Manager, VPC, SES).
* Completed the detailed schema design for the two DynamoDB tables that are part of my assigned work.
* Participated in reviewing and adjusting the data flows in the architecture.
* Thoroughly researched and distinguished the two types of VPC Endpoint (Gateway and Interface), ready for the deployment phase.