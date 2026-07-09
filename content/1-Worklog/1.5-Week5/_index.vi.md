---
title: "Worklog Tuần 5"
date: 2026-05-15
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Mục tiêu tuần:
Học Module 05 về bảo mật; tập trung các lab IAM và mã hóa cơ bản, bỏ các lab IAM nâng cao.

### Công việc thực hiện trong tuần:
| Thứ | Ngày | Công việc | Nguồn tài liệu |
|---|---|---|---|
| Thứ Sáu | 15/05/2026 | Xem bài giảng Module 05 về các dịch vụ bảo mật (IAM nâng cao, KMS); ghi chú các khái niệm về phân quyền và mã hóa | [youtube (playlist FCJ)](https://www.youtube.com/watch?v=tsobAlSg19g&list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i&index=150) |
| Thứ Bảy | 16/05/2026 | Thực hành Lab 48 (cấu hình IAM Role cho EC2 truy cập S3): thử cả hai cách — dùng Access/Secret Key và dùng IAM Role gắn trực tiếp vào EC2 — để so sánh mức độ an toàn | [awsstudygroup.com](https://000048.awsstudygroup.com/)  |
| Chủ Nhật | 17/05/2026 | Ôn lại kiến thức IAM và làm lại Lab 48 để nắm chắc; hiểu rõ vì sao không nên hardcode Access Key trong ứng dụng | |
| Thứ Hai | 18/05/2026 | Thực hành Lab 33 (mã hóa dữ liệu S3 với AWS KMS): tạo KMS Key, cấu hình mã hóa object trên S3 và kiểm tra quyền truy cập | [awsstudygroup.com](https://000057.awsstudygroup.com/vi/1-introduce/) |
| Thứ Ba | 19/05/2026 | Tiếp tục tìm hiểu KMS: kiểm chứng rằng người dùng không có quyền với KMS Key thì không đọc được object dù đã có quyền truy cập S3 — hiểu KMS như một lớp kiểm soát bổ sung | [awsstudygroup.com](https://000057.awsstudygroup.com/vi/1-introduce/) |
| Thứ Tư | 20/05/2026 | Thực hành Lab 08 (Amazon CloudWatch): quan sát Metrics, Logs, thiết lập Alarm và Dashboard cơ bản để giám sát tài nguyên | [awsstudygroup.com](https://000008.awsstudygroup.com/)  |
| Thứ Năm | 21/05/2026 | Xem trước bài giảng Module 06 về cơ sở dữ liệu (RDS, Aurora); quyết định bỏ các lab IAM nâng cao (Lab 22, 28, 30, 44) để dồn thời gian cho phần Database là thế mạnh | [youtube (playlist FCJ)](https://www.youtube.com/watch?v=OOD2RwWuLRw&list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i&index=217) |

### Kết quả đạt được tuần 5:
* Hiểu và thực hành được cơ chế phân quyền bằng IAM Role, nắm rõ rủi ro bảo mật của việc dùng Access Key trực tiếp.
* Hoàn thành Lab 48, biết cách gắn IAM Role vào EC2 để truy cập S3 an toàn.
* Hoàn thành Lab 33, cấu hình được mã hóa dữ liệu S3 bằng AWS KMS và quản lý quyền với KMS Key.
* Hoàn thành Lab 08, biết giám sát hệ thống cơ bản bằng CloudWatch (Metrics, Logs, Alarm, Dashboard).
* Chủ động lược bớt lab IAM nâng cao để dồn thời gian cho phần Database — nền tảng trực tiếp cho vai trò trong dự án.