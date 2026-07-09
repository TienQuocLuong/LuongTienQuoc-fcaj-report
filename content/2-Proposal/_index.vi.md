---
title: "Đề xuất dự án"
date: 2026-06-16
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# Xây Dựng Nền Tảng Kiểm Thử Tự Động End-to-End Theo Kiến Trúc Cloud-Native Serverless Trên AWS

## 1. Tóm tắt điều hành
Hệ thống là nền tảng kiểm thử tự động End-to-End (E2E) cho website, giúp loại bỏ việc kỹ sư phải tự tay chạy và canh kết quả kiểm thử mỗi khi có triển khai mới. Playwright chạy trong container Docker để giả lập hành vi người dùng thật trên trình duyệt, sau đó một bước tóm tắt bằng AI chuyển log kỹ thuật thô thành nội dung dễ hiểu gửi qua email. Toàn bộ hệ thống vận hành theo kiến trúc serverless hướng sự kiện trên AWS (EventBridge, SQS, Lambda, ECS Fargate), chỉ tính phí theo đúng thời gian chạy test thực tế, với quyền truy cập Dashboard phân theo 3 vai trò (Admin, QA/Tester, Developer) qua Amazon Cognito.

## 2. Tuyên bố vấn đề

**Vấn đề hiện tại:** Kiểm thử E2E thủ công không mở rộng được khi số ứng dụng và test case tăng lên; không có hệ thống tập trung để lên lịch, theo dõi xu hướng Pass/Fail hay tự động thông báo; duy trì server chạy 24/7 chỉ để chờ test gây lãng phí chi phí.

**Giải pháp:** Hệ thống nhận yêu cầu từ 2 nguồn (lịch tự động qua EventBridge, kích hoạt thủ công qua API Gateway), chuẩn hóa vào hàng đợi SQS + DLQ. Lambda Coordinator khởi tạo tác vụ ECS Fargate ngắn hạn chạy Playwright, ghi báo cáo vào S3 và tự tắt. Lambda hậu kỳ gọi AI API tóm tắt log (có fallback nếu AI lỗi), Amazon SES gửi email kết quả.

**Lợi ích và ROI:** Loại bỏ thao tác thủ công, rút ngắn thời gian phản hồi từ hàng giờ xuống vài phút, chi phí tính theo mức sử dụng thực tế, lưu lịch sử đầy đủ trên DynamoDB phục vụ phân tích xu hướng, giải phóng thời gian đội QA.

## 3. Kiến trúc giải pháp
Hệ thống gồm Backend Engine (lên lịch, thực thi, tạo báo cáo) và Dashboard Console (giao diện 3 vai trò). Mọi yêu cầu đều đi qua đúng 1 luồng: SQS → Lambda Coordinator → Fargate.

![Sơ đồ kiến trúc hệ thống](/images/2-Proposal/architecture.png)

**Dịch vụ AWS sử dụng:**
* Amazon EventBridge: lập lịch kiểm thử định kỳ.
* Amazon API Gateway: tiếp nhận kích hoạt thủ công, xác thực qua Lambda Authorizer.
* Amazon SQS + DLQ: đệm và chuẩn hóa yêu cầu.
* AWS Lambda (Coordinator): gọi ECS RunTask khởi tạo Fargate.
* Amazon ECS Fargate: chạy container Playwright trong Private Subnet.
* Amazon ECR: lưu Docker image test runner.
* Amazon S3 (2 bucket): frontend tĩnh + báo cáo kiểm thử.
* Amazon CloudWatch: log, metric, cảnh báo.
* AWS Lambda (Post-processing) + OpenAI API: tóm tắt log bằng AI (thay Bedrock do giới hạn Free Tier).
* NAT Gateway: cho Lambda trong Private Subnet gọi AI API bên ngoài.
* Amazon SES: gửi email kết quả.
* Amazon DynamoDB: lưu lịch sử kiểm thử, audit log.
* Amazon CloudFront + WAF: phân phối và bảo vệ Dashboard.
* Amazon Cognito: xác thực, phân quyền 3 vai trò.
* AWS Secrets Manager: lưu khóa AI API.
* Amazon VPC + VPC Endpoints: cô lập Fargate, giao tiếp nội bộ không qua Internet.

**Thiết kế thành phần:** Tầng kích hoạt (EventBridge/API Gateway → SQS) → Tầng thực thi (Lambda Coordinator → Fargate chạy Playwright) → Tầng báo cáo (S3 + CloudWatch) → Tầng AI (Lambda hậu kỳ + circuit-breaker fallback) → Tầng thông báo (SES) → Tầng truy cập (Cognito tại ranh giới API Gateway).

## 4. Triển khai kỹ thuật

**Các giai đoạn triển khai:** (1) Thiết lập môi trường & container Docker/Playwright, (2) Luồng sự kiện & Lambda Coordinator, (3) Lưu trữ & giám sát (S3, CloudWatch, DynamoDB), (4) Tóm tắt bằng AI (Secrets Manager + circuit-breaker), (5) Dashboard & phân quyền (CloudFront, Cognito), (6) Tăng cường bảo mật (IAM least-privilege, VPC Endpoints, WAF), (7) Kiểm thử tích hợp & demo trên website tự dựng.

**Yêu cầu kỹ thuật:** Node.js/Playwright/Docker cho test runner; AWS SDK cho logic Coordinator; khuyến nghị IaC (CDK/CloudFormation) để tái lập môi trường; IAM giới hạn phạm vi, Secrets Manager và VPC Endpoints cho nền tảng bảo mật.

## 5. Lộ trình & Mốc triển khai

* **Trước dự án (Tuần 1–8):** Ôn tập kiến thức nền tảng AWS (Explore, Migrate, Optimize, Modernize, Container, Data & Analytics, AI/ML) và chuẩn bị kỹ năng cần thiết cho dự án.
* **Giai đoạn dự án (Tuần 9–12):**
  * **Tuần 9:** Chốt đề tài dự án, phân công công việc cho từng thành viên, phác thảo sơ đồ kiến trúc ban đầu.
  * **Tuần 10:** Hoàn thiện bản mô tả chi tiết và sơ đồ kiến trúc; thiết kế schema hai bảng DynamoDB.
  * **Tuần 11:** Tối ưu kiến trúc (bỏ SNS, thay Bedrock bằng OpenAI do giới hạn Free Tier), chốt công nghệ sử dụng, chuẩn bị môi trường triển khai.
  * **Tuần 12:** Triển khai hạ tầng (VPC, DynamoDB, VPC Endpoint, SES), chạy kiểm thử end-to-end, hoàn thiện báo cáo.
* **Sau khi nộp báo cáo:** Tiếp tục hoàn thiện Dashboard và bổ sung thêm tính năng AI/ML nếu còn thời gian.

## 6. Ước tính ngân sách

Có thể xem chi tiết chi phí trên [AWS Pricing Calculator](https://calculator.aws)

*Chi phí hạ tầng*

* AWS Fargate: 1,88 USD/tháng (50 task/ngày, 1 phút/task, 2 GB RAM, 20 GB ephemeral storage).
* AWS Lambda: 0,00 USD/tháng (10.000 request/tháng, 512 MB).
* Amazon SQS: 0,00 USD/tháng (0,0045 triệu standard request/tháng).
* Amazon S3 – Frontend: 0,03 USD/tháng (1 GB storage, 50 PUT, 1.500 GET/tháng).
* Amazon S3 – Reports: 0,26 USD/tháng (3 GB storage, 37.500 PUT, 200 GET/tháng).
* Amazon CloudWatch: 1,85 USD/tháng (2,2 GB log, 1 dashboard, 3 alarm).
* Amazon DynamoDB (On-Demand): 1,88 USD/tháng (1 GB storage, item trung bình 5 KB).
* Amazon VPC – PrivateLink: 0,05 USD/tháng (3 VPC Interface Endpoint).
* AWS Secrets Manager: 0,41 USD/tháng (1 secret, 1.500 API call/tháng).
* Amazon Cognito: 0,26 USD/tháng (5 MAU).
* Amazon CloudFront: 0,11 USD/tháng (2.000 request HTTPS).
* Amazon API Gateway: 0,01 USD/tháng (0,0075 triệu request/tháng).
* Amazon SES: 0,45 USD/tháng (4.500 email/tháng).

*Tổng phụ (chưa gồm NAT Gateway)*: 7,19 USD/tháng.

* NAT Gateway (lên lịch tạo/xóa tự động): 15,045 USD/tháng — chỉ chạy trong khung giờ cần gọi AI API, không chạy 24/7 (nếu chạy 24/7 sẽ tốn khoảng 43 USD/tháng).

*Tổng cộng*: 22,24 USD/tháng, khoảng 266,82 USD/12 tháng (chưa gồm chi phí OpenAI API — dịch vụ bên thứ ba, tính riêng theo giá token của nhà cung cấp).

{{% notice tip %}}
Lưu ý: NAT Gateway không hỗ trợ Start/Stop như EC2. Đánh đổi của cách lên lịch tự động là NAT mất khoảng 1-3 phút để sẵn sàng sau khi tạo, có thể gây độ trễ nếu test được kích hoạt thủ công ngoài khung giờ đã lên lịch.
{{% /notice %}}

## 7. Đánh giá rủi ro

**Ma trận rủi ro:**
* Fargate task timeout: ảnh hưởng trung bình, xác suất trung bình.
* AI API bên ngoài không khả dụng: ảnh hưởng thấp (đã có fallback), xác suất trung bình.
* IAM quá nhiều quyền lúc phát triển: ảnh hưởng cao, xác suất trung bình.
* DLQ tồn đọng không cảnh báo: ảnh hưởng trung bình, xác suất thấp.
* Chi phí vượt dự kiến do cấu hình sai NAT: ảnh hưởng trung bình, xác suất thấp.
* Độ trễ khi test thủ công ngoài giờ NAT đã lên lịch: ảnh hưởng trung bình, xác suất trung bình.
* Website demo không ổn định: ảnh hưởng trung bình, xác suất trung bình.

**Chiến lược giảm thiểu:** CloudWatch Alarm cho thời lượng task và độ sâu DLQ; circuit-breaker để vẫn gửi báo cáo gốc nếu AI lỗi; least-privilege IAM từ đầu; cảnh báo DLQ → SNS sớm; dùng website demo tự dựng thay vì domain thật.

**Kế hoạch dự phòng:** Gửi báo cáo gốc nếu AI không phản hồi; tự dừng task Fargate bị treo mà không ảnh hưởng các lần chạy khác; cảnh báo ngân sách phát hiện sớm chi phí bất thường.

## 8. Kết quả kỳ vọng
**Cải tiến kỹ thuật:** Kiểm thử E2E thủ công được thay bằng pipeline tự động hướng sự kiện, phân quyền 3 vai trò nhất quán tại ranh giới API.

**Giá trị dài hạn:** Kiến trúc tham khảo tái sử dụng cho các dự án serverless khác; dữ liệu lịch sử kiểm thử (DynamoDB) làm nền tảng phân tích lỗi lặp lại; minh chứng mô hình chi phí theo mức sử dụng rõ ràng so với server chạy liên tục.