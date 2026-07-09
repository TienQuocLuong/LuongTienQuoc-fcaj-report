---
title : "Giới thiệu"
date : 2024-01-01 
weight : 1
chapter : false
pre : " <b> 5.1. </b> "
---

#### Giới thiệu về AWS Cloud-Native & Serverless Automation

+ Kiến trúc Cloud-Native kết hợp với mô hình hướng sự kiện (Event-Driven Architecture) giúp xây dựng hệ thống kiểm thử tự động có khả năng mở rộng, tính sẵn sàng cao và tối ưu chi phí nhờ sử dụng các dịch vụ Serverless trên AWS.
+ Hệ thống sử dụng Docker và Playwright để thực thi kiểm thử trên Amazon ECS Fargate, lưu trữ báo cáo trên Amazon S3, ghi log vào Amazon CloudWatch và tích hợp Amazon Bedrock để hỗ trợ phân tích, tóm tắt kết quả kiểm thử.

#### Tổng quan về workshop

Trong workshop này, bạn sẽ xây dựng và triển khai một hệ thống kiểm thử tự động End-to-End (E2E) trên nền tảng AWS.

+ **"Backend Engine"** tiếp nhận yêu cầu kiểm thử từ Amazon API Gateway hoặc Amazon EventBridge, điều phối quá trình thực thi bằng AWS Lambda, chạy các bài kiểm thử trên Amazon ECS Fargate và lưu kết quả trên Amazon S3 cùng Amazon CloudWatch.

+ **"Dashboard Console"** cung cấp giao diện quản trị giúp quản lý kịch bản kiểm thử, theo dõi lịch sử thực thi và phân quyền người dùng thông qua Amazon S3 và Amazon CloudFront.

+ **"AI Support & Notification"** sử dụng AWS Lambda kết hợp Amazon Bedrock để phân tích kết quả kiểm thử, sau đó gửi báo cáo tự động qua Amazon SES/SNS, đồng thời vẫn đảm bảo quá trình thông báo không bị gián đoạn khi dịch vụ AI gặp sự cố.

![overview](/images/5-Workshop/5.1-Workshop-overview/diagram.jpeg)
