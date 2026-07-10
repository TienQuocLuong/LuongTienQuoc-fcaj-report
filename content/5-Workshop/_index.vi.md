---
title: "Workshop"
date: 2026-06-12
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Hệ Thống Tự Động Kiểm Thử Playwright Bằng Docker Trên AWS (Cloud-Native Architecture)

Dự án xây dựng một nền tảng kiểm thử tự động nội bộ cho các ứng dụng web của doanh nghiệp, với mục tiêu cốt lõi là loại bỏ hoàn toàn việc con người phải ngồi canh và tự tay chạy kiểm thử mỗi khi cần kiểm tra chất lượng một website. Hệ thống dùng Playwright để giả lập hành vi người dùng thật trên trình duyệt — click, nhập liệu, điều hướng trang, kiểm tra kết quả hiển thị — sau đó AI sẽ đọc log và tóm tắt gửi về email. Toàn bộ quá trình được đóng gói trong Docker container để đảm bảo môi trường chạy test luôn nhất quán, và vận hành trên AWS theo kiến trúc Cloud-Native hướng sự kiện, không máy chủ thường trực — hệ thống không chạy liên tục 24/7 mà chỉ hoạt động khi có việc, tránh phí duy trì lãng phí.

Nhìn từ góc độ người dùng, hệ thống chia làm hai phần: **Backend Engine** (không ai nhìn thấy trực tiếp — nhận lệnh kiểm thử, dựng môi trường, chạy Playwright, ghi log, xuất báo cáo, rồi tự dọn dẹp) và **Dashboard Console** (giao diện con người thực sự chạm vào — theo dõi tình trạng test, quản lý kịch bản, cấu hình người nhận thông báo, phân quyền truy cập).

Hệ thống chia theo 3 vai trò: **Admin** cấu hình lịch tự động và quản lý quyền hạn thông báo; **QA/Tester** có thể tự bấm nút kiểm tra ngay khi cần và quản lý kịch bản test; **Developer** chỉ xem kết quả. AI chỉ tham gia ở bước cuối cùng để tóm tắt log thành văn bản dễ hiểu, không tham gia vào việc kiểm tra web.

### Nội dung
1. [Tổng quan](5.1-workshop-overview/)
2. [Chuẩn bị](5.2-prerequiste/)
3. [Thiết lập hạ tầng](5.3-infrastructure-setup/)
   * 3.1 Networking (VPC)
   * 3.2 Lưu trữ & Dữ liệu (S3, ECR, DynamoDB)
   * 3.3 Hàng đợi & IAM (SQS, VPC Endpoints, IAM Roles)
4. [Triển khai ứng dụng](5.4-application-deployment/)
   * 4.1 Docker Image
   * 4.2 ECS Cluster & Task Definition
   * 4.3 Các Lambda Function
5. [Tích hợp & Phân quyền](5.5-integration-access/)
   * 5.1 Secrets & SES
   * 5.2 Xác thực & API Gateway (Cognito)
   * 5.3 Frontend (S3 + CloudFront)
   * 5.4 Lên lịch tự động với EventBridge
6. [Kiểm thử & Dọn dẹp](5.6-testing-cleanup/)
   * 6.1 Kiểm thử toàn luồng (End-to-End)
   * 6.2 Dọn dẹp tài nguyên