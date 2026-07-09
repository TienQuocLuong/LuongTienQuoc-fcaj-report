---
title : "Introduction"
date : 2026-04-17
weight : 1 
chapter : false
pre : " <b> 5.1. </b> "
---

#### Introduction to AWS Cloud-Native & Serverless Automation

+ Cloud-Native architecture combined with an Event-Driven Architecture provides an optimal approach for modern automated testing systems. By leveraging AWS Serverless services, the platform provisions resources only when needed and automatically releases them after execution, reducing operational costs while improving scalability, availability, and resource efficiency.

+ The testing environment is containerized using Docker and Playwright to ensure consistent execution across all test runs. Test containers are deployed on Amazon ECS Fargate within a private subnet, where they execute End-to-End (E2E) tests, store reports in Amazon S3, collect logs in Amazon CloudWatch, and update execution data in Amazon DynamoDB. In addition, the platform integrates **Google Gemini (External AI API)** to analyze logs, summarize test results, and provide intelligent insights before delivering reports to users.

#### Workshop Overview

In this workshop, you will build and deploy an End-to-End (E2E) automated testing platform based on a Cloud-Native architecture on AWS. The solution is designed using a layered architecture to provide scalability, flexibility, security, and simplified maintenance.

+ **"Backend Engine"** receives testing requests from Amazon API Gateway or Amazon EventBridge, then forwards them to Amazon SQS for asynchronous processing. AWS Lambda acts as the coordinator, launching Docker containers running Playwright on Amazon ECS Fargate. After execution, test reports are stored in Amazon S3, execution logs are published to Amazon CloudWatch, and compute resources are automatically released using the *Pay-as-you-go* model to optimize costs.

+ **"Dashboard Console"** is hosted on Amazon S3 and distributed through Amazon CloudFront, providing a web-based interface for Administrators, QA/Testers, and Developers to manage test scenarios, monitor execution history, and review test reports. User authentication is handled by Amazon Cognito, while Amazon API Gateway and AWS Lambda process frontend requests. Test metadata and execution status are stored in Amazon DynamoDB.

+ **"AI Support & Notification"** uses AWS Lambda to preprocess execution logs before sending them to **Google Gemini (External AI API)** for analysis, result summarization, and root-cause insights. Once processing is complete, the platform automatically sends email reports through Amazon SES with a link to the generated report stored in Amazon S3. If the external AI service is temporarily unavailable, the platform still delivers the original test report to ensure uninterrupted notifications.

![overview](/images/5-Workshop/5.1-Workshop-overview/diagram1.png)