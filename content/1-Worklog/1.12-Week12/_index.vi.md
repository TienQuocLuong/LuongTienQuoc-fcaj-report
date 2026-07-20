---
title: "Worklog Tuần 12"
date: 2026-07-03
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---

### Mục tiêu tuần:
Triển khai hạ tầng và các tài nguyên phụ trách; phối hợp cùng nhóm chạy thử nghiệm toàn hệ thống.

### Công việc thực hiện trong tuần:
| Thứ | Ngày | Công việc | Nguồn tài liệu |
|---|---|---|---|
| Thứ Sáu | 03/07/2026 | Cùng nhóm lập kế hoạch triển khai chi tiết và cấu hình hạ tầng mạng VPC (Subnet, Route Table, NAT Gateway, các Security Group) | |
| Thứ Bảy | 04/07/2026 | Cùng nhóm cập nhật, hoàn thiện kế hoạch triển khai và chuẩn bị tài nguyên (mã nguồn, file cấu hình hệ thống) | |
| Chủ Nhật | 05/07/2026 | Trực tiếp tạo hai bảng DynamoDB (playwright-test-history, playwright-error-log) theo schema đã thiết kế; phối hợp cùng nhóm tạo hai S3 bucket và hai SQS queue (task queue và Dead Letter Queue) | |
| Thứ Hai | 06/07/2026 | Tạo VPC Endpoint cho S3 (Gateway type) và cho ECR (Interface type); verify email trên SES và gửi thử một email để kiểm tra; hỗ trợ nhóm cấu hình các Lambda function và thiết lập EventBridge Scheduler | |
| Thứ Ba | 07/07/2026 | Bắt tay chạy thử toàn bộ website thì lộ ra hàng loạt lỗi khá nặng: phía frontend gọi API nhưng backend không trả đúng dữ liệu vì Lambda chưa được viết logic ghi vào DynamoDB và S3; nhiều tính năng còn bỏ trống hoàn toàn phần xử lý; hai bảng DynamoDB cần cho test suite và cấu hình email vẫn chưa tồn tại; một số biến môi trường quan trọng cũng chưa khai báo cho các hàm Lambda. Trong ngày xử lý được phần cấp bách nhất là tạo thêm 2 bảng DynamoDB (test suite và email config), còn phần dữ liệu hiển thị lên giao diện và các tính năng khác vẫn để lại cho ngày sau | |
| Thứ Tư | 08/07/2026 | Quay lại giải quyết tiếp đống việc còn đọng từ hôm qua: sửa xong phần tạo test suite lưu đúng vào database, chỉnh lại dropdown để hiển thị đúng dữ liệu test suite ở màn hình kiểm thử. Trong lúc sửa lại phát hiện thêm loạt lỗi mới ở API Gateway — bị CORS chặn request, một số route còn thiếu path, Authorizer với Integration gán chưa đủ, và chưa có trigger nối tới Lambda backend nên giao diện không lấy được dữ liệu. May là xử lý dứt điểm hết mảng API Gateway trong ngày, tranh thủ làm luôn tính năng đặt lịch kiểm thử tự động, sửa nốt lỗi đăng nhập của tài khoản Developer, và cuối cùng dữ liệu đã lên được giao diện. Riêng luồng chạy test — cả thủ công và tự động — vẫn chưa chạy trọn vẹn, để lại cho hôm sau | |
| Thứ Năm | 09/07/2026 | Việc đầu tiên trong ngày là dập lỗi dữ liệu không hiện lên website, xử lý nhanh xong thì dồn sức giải quyết hết những gì còn tồn từ hai ngày trước. Tập trung toàn lực vào luồng kiểm thử chính — cả chạy thủ công và chạy tự động — và cuối cùng cũng hoàn thành trong ngày. Test thử lại toàn hệ thống thì mọi thứ chạy trơn tru: trả kết quả đúng, email báo cáo cũng được gửi đi như thiết kế ban đầu. Dành phần còn lại trong ngày để tổng hợp và viết lại toàn bộ những gì đã triển khai vào báo cáo thực tập | |

### Kết quả đạt được tuần 12:
* Cùng nhóm thống nhất kế hoạch triển khai và cấu hình thành công hạ tầng mạng VPC.
* Trực tiếp tạo và cấu hình hai bảng DynamoDB đúng theo schema đã thiết kế, bổ sung thêm 2 bảng cho test suite và email config khi phát sinh nhu cầu thực tế.
* Tạo thành công VPC Endpoint cho S3 (Gateway) và ECR (Interface) để các dịch vụ giao tiếp nội bộ an toàn.
* Verify và kiểm tra thành công email gửi qua Amazon SES.
* Phối hợp cùng nhóm tạo các tài nguyên lưu trữ và hàng đợi (2 S3 bucket, 2 SQS queue gồm DLQ), hỗ trợ triển khai Lambda và EventBridge Scheduler.
* Phát hiện và khắc phục toàn bộ các lỗi phát sinh khi chạy thử hệ thống thật: logic Lambda ghi dữ liệu DynamoDB/S3, cấu hình API Gateway (CORS, route, Authorizer, Integration, trigger), lỗi đăng nhập tài khoản Developer, và dữ liệu không hiển thị trên giao diện.
* Hoàn thiện luồng kiểm thử chính (thủ công và tự động), chạy kiểm thử toàn hệ thống thành công — trả kết quả đúng và gửi được email báo cáo.
* Hoàn thành viết báo cáo thực tập tổng hợp toàn bộ quá trình triển khai.