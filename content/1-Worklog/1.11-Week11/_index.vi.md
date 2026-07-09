---
title: "Worklog Tuần 11"
date: 2026-06-26
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Mục tiêu tuần:
Hoàn thiện sơ đồ kiến trúc tối ưu về chi phí và bảo mật; phân công công việc và chuẩn bị môi trường triển khai.

### Công việc thực hiện trong tuần:
| Thứ | Ngày | Công việc | Nguồn tài liệu |
|---|---|---|---|
| Thứ Sáu | 26/06/2026 | Họp nhóm tối ưu sơ đồ kiến trúc: quyết định bỏ dịch vụ SNS do không cần thiết cho luồng hiện tại, thay AWS Bedrock bằng giải pháp khác vì tài khoản Free Tier bị giới hạn, và thảo luận phương án cấu hình luồng mạng VPC | |
| Thứ Bảy | 27/06/2026 | Rà soát lại thiết kế hai bảng DynamoDB cho khớp với luồng dữ liệu mới sau khi kiến trúc được tối ưu; điều chỉnh vài trường cho phù hợp | |
| Chủ Nhật | 28/06/2026 | Tìm hiểu chi tiết cách đặt VPC Endpoint để Lambda và Fargate giao tiếp nội bộ với DynamoDB, S3 và ECR mà không cần đi qua internet, giúp tăng bảo mật và giảm chi phí | |
| Thứ Hai | 29/06/2026 | Chuẩn bị email dùng để gửi báo cáo và tìm hiểu quy trình verify trên Amazon SES; lưu ý SES mặc định ở chế độ Sandbox nên chỉ gửi được tới các email đã verify | |
| Thứ Ba | 30/06/2026 | Cùng nhóm chỉnh sửa kiến trúc lần cuối: xác định Lambda Processing nằm trong Private Subnet, định tuyến qua NAT Gateway để gọi API AI bên ngoài; hoàn tất sơ đồ kiến trúc cuối cùng | |
| Thứ Tư | 01/07/2026 | Nhận phân công công việc cụ thể; cùng nhóm thống nhất công nghệ sử dụng (Frontend: Next.js, Backend: Python Boto3); xác nhận lại phần việc của mình gồm DynamoDB, VPC Endpoint và SES | |
| Thứ Năm | 02/07/2026 | Chuẩn bị trước script Boto3 để tạo hai bảng DynamoDB và rà soát các cấu hình cần thiết cho VPC Endpoint trước ngày triển khai | |

### Kết quả đạt được tuần 11:
* Cùng nhóm hoàn thiện kiến trúc hệ thống tối ưu và an toàn: đặt ECS Fargate trong Private Subnet dùng VPC Endpoint để giao tiếp nội bộ với S3, DynamoDB, ECR; đặt Lambda xử lý trong Private Subnet định tuyến qua NAT Gateway để gọi API AI.
* Hoàn tất điều chỉnh thiết kế hai bảng DynamoDB cho khớp luồng dữ liệu mới.
* Nắm chắc cách cấu hình VPC Endpoint và quy trình verify email SES.
* Được phân công rõ phần việc và thống nhất stack công nghệ của nhóm.
* Chuẩn bị sẵn script Boto3 và cấu hình cần thiết, sẵn sàng cho giai đoạn triển khai.