---
title: "Proposal"
date: 2026-06-16
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# End-to-End Automated Testing Platform on a Cloud-Native Serverless Architecture on AWS

## 1. Executive Summary
The system is an End-to-End (E2E) automated testing platform for websites, eliminating the need for engineers to manually run and watch over test results every time a new deployment happens. Playwright runs inside a Docker container to simulate real user behavior in the browser, after which an AI summarization step turns raw technical logs into easy-to-understand content sent via email. The whole system runs on an event-driven serverless architecture on AWS (EventBridge, SQS, Lambda, ECS Fargate), charging only for actual test run time, with Dashboard access split across 3 roles (Admin, QA/Tester, Developer) via Amazon Cognito.

## 2. Problem Statement

**Current problem:** Manual E2E testing doesn't scale as the number of applications and test cases grows; there's no centralized system to schedule tests, track Pass/Fail trends, or auto-notify stakeholders; keeping a server running 24/7 just to wait for the next test wastes cost.

**Solution:** The system accepts requests from 2 sources (an automated schedule via EventBridge, a manual trigger via API Gateway), normalized into an SQS queue + DLQ. A Coordinator Lambda spins up a short-lived ECS Fargate task running Playwright, writes the report to S3, and shuts down. A post-processing Lambda calls an AI API to summarize the logs (with a fallback if the AI fails), and Amazon SES sends the result email.

**Benefits and ROI:** Eliminates manual work, shortens response time from hours to minutes, cost scales with actual usage, full history stored in DynamoDB for trend analysis, frees up QA time.

## 3. Solution Architecture
The system consists of a Backend Engine (scheduling, execution, report generation) and a Dashboard Console (3-role interface). Every request goes through exactly one flow: SQS → Lambda Coordinator → Fargate.

![System architecture diagram](/images/2-Proposal/architecture.png)

**AWS services used:**
* Amazon EventBridge: schedules periodic tests.
* Amazon API Gateway: accepts manual triggers, authenticated via a Lambda Authorizer.
* Amazon SQS + DLQ: buffers and normalizes requests.
* AWS Lambda (Coordinator): calls ECS RunTask to spin up Fargate.
* Amazon ECS Fargate: runs the Playwright container in a Private Subnet.
* Amazon ECR: stores the test runner's Docker image.
* Amazon S3 (2 buckets): static frontend + test reports.
* Amazon CloudWatch: logs, metrics, alerts.
* AWS Lambda (Post-processing) + OpenAI API: AI log summarization (used instead of Bedrock due to Free Tier limits).
* NAT Gateway: lets the Private-Subnet Lambda call the external AI API.
* Amazon SES: sends result emails.
* Amazon DynamoDB: stores test history and audit logs.
* Amazon CloudFront + WAF: distributes and protects the Dashboard.
* Amazon Cognito: authentication, 3-role access control.
* AWS Secrets Manager: stores the AI API key.
* Amazon VPC + VPC Endpoints: isolates Fargate, internal traffic never leaves AWS.

**Component design:** Trigger layer (EventBridge/API Gateway → SQS) → Execution layer (Coordinator Lambda → Fargate running Playwright) → Reporting layer (S3 + CloudWatch) → AI layer (post-processing Lambda + circuit-breaker fallback) → Notification layer (SES) → Access layer (Cognito at the API Gateway boundary).

## 4. Technical Implementation

**Implementation phases:** (1) Environment & Docker/Playwright container setup, (2) Event flow & Coordinator Lambda, (3) Storage & monitoring (S3, CloudWatch, DynamoDB), (4) AI summarization (Secrets Manager + circuit-breaker), (5) Dashboard & access control (CloudFront, Cognito), (6) Security hardening (least-privilege IAM, VPC Endpoints, WAF), (7) Integration testing & demo on a self-built website.

**Technical requirements:** Node.js/Playwright/Docker for the test runner; AWS SDK for the Coordinator logic; IaC (CDK/CloudFormation) recommended for environment reproducibility; scoped IAM, Secrets Manager, and VPC Endpoints for the security foundation.

## 5. Roadmap & Milestones

* **Before the project (Weeks 1-8):** Reviewed AWS fundamentals (Explore, Migrate, Optimize, Modernize, Container, Data & Analytics, AI/ML) and prepared the skills needed for the project.
* **Project phase (Weeks 9-12):**
  * **Week 9:** Finalized the project topic, assigned tasks among team members, sketched the initial architecture diagram.
  * **Week 10:** Completed the detailed description and architecture diagram; designed the DynamoDB table schemas.
  * **Week 11:** Optimized the architecture (removed SNS, replaced Bedrock with OpenAI due to Free Tier limits), finalized the tech stack, prepared for deployment.
  * **Week 12:** Deployed the infrastructure (VPC, DynamoDB, VPC Endpoints, SES), ran end-to-end testing, finalized the report.
* **After submission:** Continue refining the Dashboard and add further AI/ML features if time allows.

## 6. Budget Estimation

Detailed costs are available on the [AWS Pricing Calculator](https://calculator.aws)

*Infrastructure cost*

* AWS Fargate: 1.88 USD/month (50 tasks/day, 1 min/task, 2 GB RAM, 20 GB ephemeral storage).
* AWS Lambda: 0.00 USD/month (10,000 requests/month, 512 MB).
* Amazon SQS: 0.00 USD/month (0.0045 million standard requests/month).
* Amazon S3 – Frontend: 0.03 USD/month (1 GB storage, 50 PUT, 1,500 GET/month).
* Amazon S3 – Reports: 0.26 USD/month (3 GB storage, 37,500 PUT, 200 GET/month).
* Amazon CloudWatch: 1.85 USD/month (2.2 GB log, 1 dashboard, 3 alarms).
* Amazon DynamoDB (On-Demand): 1.88 USD/month (1 GB storage, average 5 KB items).
* Amazon VPC – PrivateLink: 0.05 USD/month (3 VPC Interface Endpoints).
* AWS Secrets Manager: 0.41 USD/month (1 secret, 1,500 API calls/month).
* Amazon Cognito: 0.26 USD/month (5 MAU).
* Amazon CloudFront: 0.11 USD/month (2,000 HTTPS requests).
* Amazon API Gateway: 0.01 USD/month (0.0075 million requests/month).
* Amazon SES: 0.45 USD/month (4,500 emails/month).

*Subtotal (excluding NAT Gateway)*: 7.19 USD/month.

* NAT Gateway (scheduled auto create/delete): 15.045 USD/month — only runs during the AI API call window, not 24/7 (running 24/7 would cost about 43 USD/month).

*Total*: 22.24 USD/month, about 266.82 USD/12 months (excluding OpenAI API cost — a third-party service billed separately based on the provider's token pricing).

{{% notice tip %}}
Note: NAT Gateway doesn't support Start/Stop like EC2. The trade-off of the scheduled approach is that NAT takes about 1-3 minutes to become ready after creation, which can cause delays if a test is triggered manually outside the scheduled window.
{{% /notice %}}

## 7. Risk Assessment

**Risk matrix:**
* Fargate task timeout: medium impact, medium likelihood.
* External AI API unavailable: low impact (fallback in place), medium likelihood.
* IAM over-permissioned during development: high impact, medium likelihood.
* DLQ backlog without alerting: medium impact, low likelihood.
* Cost overrun from NAT misconfiguration: medium impact, low likelihood.
* Latency from manual tests outside the scheduled NAT window: medium impact, medium likelihood.
* Demo website instability: medium impact, medium likelihood.

**Mitigation strategy:** CloudWatch Alarms for task duration and DLQ depth; circuit-breaker to still send the original report if AI fails; least-privilege IAM from the start; early DLQ → SNS alerting; use a self-built demo site instead of a real domain.

**Contingency plan:** Send the original report if the AI doesn't respond; auto-stop a hung Fargate task without affecting other runs; budget alerts catch abnormal cost early.

## 8. Expected Outcomes
**Technical improvements:** Manual E2E testing replaced by an automated event-driven pipeline; 3-role access consistently enforced at the API boundary.

**Long-term value:** A reusable reference architecture for other serverless projects; accumulated test history (DynamoDB) as a foundation for analyzing recurring failures; a clear usage-based cost model versus a traditional always-on server.