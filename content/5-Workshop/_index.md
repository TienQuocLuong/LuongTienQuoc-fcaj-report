---
title: "Workshop"
date: 2026-06-12
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Automated Playwright Testing System Using Docker on AWS (Cloud-Native Architecture)

This project builds an internal automated testing platform for the company's web applications, with the core goal of completely removing the need for a human to sit and manually run tests every time a website needs a quality check. Playwright simulates real user behavior in the browser — clicking, typing, navigating, and verifying that the site behaves as expected — after which an AI reads the logs and sends a summary by email. The whole process is packaged inside a Docker container to keep the test environment consistent, and runs on AWS following an event-driven, serverless-first architecture: the system doesn't run 24/7, only when there is work to do, avoiding wasted standing costs.

From a user's perspective, the system has two parts: the **Backend Engine** (invisible to users — receives test requests, sets up the environment, runs Playwright, collects logs, produces the report, then cleans itself up) and the **Dashboard Console** (the part people actually touch — tracks test runs, manages test scripts, configures who gets notified, and controls access).

Access is split into 3 roles: **Admin** configures the automatic test schedule and manages notification permissions; **QA/Tester** can trigger a test on demand and manage test scripts; **Developer** can only view results. AI only steps in at the very last stage, to turn the raw log into an easy-to-read summary — it never takes part in the testing itself.

### Content
1. [Overview](5.1-workshop-overview/)
2. [Prerequisite](5.2-prerequiste/)
3. [Infrastructure Setup](5.3-infrastructure-setup/)
   * 3.1 Networking (VPC)
   * 3.2 Storage & Data (S3, ECR, DynamoDB)
   * 3.3 Queue & IAM (SQS, VPC Endpoints, IAM Roles)
4. [Application Deployment](5.4-application-deployment/)
   * 4.1 Docker Image
   * 4.2 ECS Cluster & Task Definition
   * 4.3 Lambda Functions
5. [Integration & Access](5.5-integration-access/)
   * 5.1 Secrets & SES
   * 5.2 Auth & API Gateway (Cognito)
   * 5.3 Frontend (S3 + CloudFront)
   * 5.4 EventBridge Scheduling
6. [Testing & Cleanup](5.6-testing-cleanup/)
   * 6.1 End-to-End Test
   * 6.2 Cleanup