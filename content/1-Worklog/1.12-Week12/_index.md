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
| Tuesday | 07/07/2026 | Started testing the whole website live and immediately ran into a string of serious bugs: the frontend called the API but the backend didn't return the right data because the Lambda functions had no logic to write to DynamoDB and S3; several features had no processing logic at all; the two DynamoDB tables needed for the test suite and email config didn't exist yet; and some critical environment variables were missing from the Lambda functions. Managed to handle the most urgent part that day — creating the 2 missing DynamoDB tables (test suite and email config) — and left the frontend data display and other features for the next day | |
| Wednesday | 08/07/2026 | Went back to clear the backlog from the day before: fixed test suite creation so it saves correctly to the database, and adjusted the dropdown to correctly display test suite data on the testing screen. While fixing that, discovered a fresh batch of API Gateway issues — CORS was blocking requests, some routes were missing paths, the Authorizer wasn't properly attached to the Integration, and there was no trigger connected to the backend Lambda, so the frontend couldn't fetch data. Managed to fully resolve the entire API Gateway situation that same day, and while at it also built the automated test scheduling feature, fixed the Developer account login bug, and finally got data showing up on the frontend. The test run flow itself — both manual and scheduled — still wasn't fully working end-to-end, left for the next day | |
| Thursday | 09/07/2026 | First task of the day was squashing the bug where data wasn't showing on the website; fixed it quickly, then spent the rest of the effort clearing everything left over from the previous two days. Focused entirely on the core test-run flow — both manual and scheduled — and finally got it fully working by the end of the day. Re-tested the whole system and everything ran smoothly: correct results returned, and the report email sent out exactly as designed. Spent the remainder of the day compiling and writing up everything that had been built into the internship report | |

### Week 12 Achievements:
* Aligned with the team on the deployment plan and successfully configured the VPC network infrastructure.
* Directly created and configured the two DynamoDB tables exactly per the designed schema.
* Successfully created VPC Endpoints for S3 (Gateway) and ECR (Interface) for secure internal service communication.
* Verified and successfully tested sending email via Amazon SES.
* Worked with the team to create storage and queue resources (2 S3 buckets, 2 SQS queues including a DLQ), and supported deploying Lambda and the EventBridge Scheduler.
* Found and fixed every bug that surfaced during real system testing: Lambda logic for writing to DynamoDB/S3, API Gateway configuration (CORS, routes, Authorizer, Integration, trigger), the Developer account login bug, and data not displaying on the frontend.
* Completed the core test-run flow (manual and scheduled), successfully ran a full system test — correct results returned and the report email sent.
* Finished writing the internship report covering the entire deployment process.