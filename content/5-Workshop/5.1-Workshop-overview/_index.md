---
title: "Overview"
date: 2026-06-16
weight: 1
chapter: false
pre: " <b> 5.1. </b> "
---

### Introduction

#### Introduction to AWS Cloud-Native & Serverless Automation
* Event-Driven Architecture is the optimal model for modern automated testing systems. By using Serverless services on AWS, the system only provisions resources when a request comes in and automatically releases them once the task is done, optimizing cost, improving scalability, and ensuring availability.
* The test environment is containerized with Docker and Playwright to ensure consistency across runs. Containers are deployed on Amazon ECS Fargate inside a Private Subnet to perform End-to-End testing, storing reports on Amazon S3, writing logs to Amazon CloudWatch, and updating status in Amazon DynamoDB. The system also integrates Google Gemini (external AI API) to help analyze logs, summarize test results, and suggest fixes before sending the report to users.

### Workshop Overview
In this workshop, you will build and deploy an End-to-End (E2E) automated testing platform on a Cloud-Native architecture on AWS. The system is designed with multiple layers to ensure scalability, flexibility, and easy maintenance.

* **Backend Engine** accepts test requests from Amazon API Gateway or Amazon EventBridge, then forwards them to Amazon SQS for asynchronous processing. AWS Lambda acts as the coordinator, triggering Docker containers running Playwright on Amazon ECS Fargate. Once complete, the report is stored on Amazon S3, logs are recorded in Amazon CloudWatch, and resources are automatically released following a pay-as-you-go model to optimize operating cost.
* **Dashboard Console** is deployed on Amazon S3 combined with Amazon CloudFront, providing a management interface that lets Admin, QA/Tester, and Developer roles manage test scripts, track execution history, and view test reports. Users are authenticated via Amazon Cognito, while Amazon API Gateway and AWS Lambda handle requests from the frontend. All test data and status are stored in Amazon DynamoDB.
* **AI Support & Notification** uses AWS Lambda to process and clean log data before sending it to Google Gemini (external AI API) to analyze, summarize results, and help identify the root cause of failures. Once done, the system automatically sends a report email via Amazon SES with a link to download the report from Amazon S3, while still guaranteeing the report is sent even if the AI service is temporarily unavailable.
* ![System architecture diagram](/images/5-Workshop/5.1-Workshop-overview/diagram.jpeg)