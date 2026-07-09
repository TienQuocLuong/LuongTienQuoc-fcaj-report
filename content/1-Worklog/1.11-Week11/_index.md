---
title: "Week 11 Worklog"
date: 2026-06-26
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Week 11 Objectives:
Finalize the architecture diagram optimized for cost and security; assign tasks and prepare the deployment environment.

### Tasks carried out this week:
| Day | Date | Task | Reference Material |
|---|---|---|---|
| Friday | 26/06/2026 | Team meeting to optimize the architecture diagram: decided to drop SNS since it wasn't needed for the current flow, replaced AWS Bedrock with an alternative solution due to Free Tier account limitations, and discussed the VPC network flow configuration | |
| Saturday | 27/06/2026 | Reviewed the two DynamoDB table designs to align with the new data flow after the architecture was optimized; adjusted a few fields accordingly | |
| Sunday | 28/06/2026 | Researched in detail how to set up VPC Endpoints so Lambda and Fargate could communicate internally with DynamoDB, S3, and ECR without going through the internet, improving security and reducing cost | |
| Monday | 29/06/2026 | Prepared the email used to send reports and researched the Amazon SES verification process; noted that SES defaults to Sandbox mode, so it can only send to verified emails | |
| Tuesday | 30/06/2026 | Made the final architecture adjustments with the team: placed the Lambda processing function in a Private Subnet, routed through a NAT Gateway to call the external AI API; finalized the architecture diagram | |
| Wednesday | 01/07/2026 | Received specific task assignments; agreed with the team on the tech stack (Frontend: Next.js, Backend: Python Boto3); reconfirmed my part of the work: DynamoDB, VPC Endpoint, and SES | |
| Thursday | 02/07/2026 | Prepared a Boto3 script in advance to create the two DynamoDB tables and reviewed the necessary configuration for the VPC Endpoints ahead of deployment day | |

### Week 11 Achievements:
* Worked with the team to finalize an optimized and secure system architecture: placed ECS Fargate in a Private Subnet using VPC Endpoints to communicate internally with S3, DynamoDB, and ECR; placed the processing Lambda in a Private Subnet routed through a NAT Gateway to call the AI API.
* Finished adjusting the two DynamoDB table designs to match the new data flow.
* Gained a solid grasp of VPC Endpoint configuration and the SES email verification process.
* Was assigned clear tasks and aligned with the team on the technology stack.
* Prepared the Boto3 script and necessary configuration in advance, ready for the deployment phase.