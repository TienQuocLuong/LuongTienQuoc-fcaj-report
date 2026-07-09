---
title: "Worklog Tuần 2"
date: 2026-04-24
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Mục tiêu tuần:
Bắt đầu Module 02 về mạng ảo (VPC), học chậm và kỹ từng thành phần để nắm chắc nền tảng mạng.

### Công việc thực hiện trong tuần:
| Thứ | Ngày | Công việc | Nguồn tài liệu |
|---|---|---|---|
| Thứ Sáu | 24/04/2026 | Xem bài giảng Module 02 về Amazon VPC; ghi chú kiến trúc mạng tổng quan và vai trò của từng thành phần (VPC, Subnet, Gateway, Route Table) | awsstudygroup.com (Lab 3) |
| Thứ Bảy | 25/04/2026 | Thực hành Lab 3 phần tạo VPC và Subnet; vừa làm vừa tra cứu để hiểu rõ cách chia dải địa chỉ CIDR và phân biệt Public/Private Subnet | awsstudygroup.com (Lab 3) |
| Chủ Nhật | 26/04/2026 | Tiếp tục Lab 3: tạo Internet Gateway và Route Table, cấu hình định tuyến để Public Subnet ra được internet; xem thêm nội dung về VPC Security | awsstudygroup.com (Lab 3) |
| Thứ Hai | 27/04/2026 | Cấu hình Security Group cho Public và Private; do ban đầu còn nhầm giữa chiều inbound và outbound nên làm lại vài lần và kiểm tra kỹ từng rule cho đến khi hiểu rõ | awsstudygroup.com (Lab 3) |
| Thứ Ba | 28/04/2026 | Dành trọn một buổi ôn lại toàn bộ các thành phần VPC đã học, vẽ lại sơ đồ mạng ra giấy để nắm chắc cách các thành phần liên kết với nhau | |
| Thứ Tư | 29/04/2026 | Thực hành triển khai EC2 trong VPC và cấu hình EC2 Instance Connect Endpoint để truy cập instance trong Private Subnet một cách an toàn | awsstudygroup.com (Lab 3) |
| Thứ Năm | 30/04/2026 | Kiểm tra kết nối mạng giữa các EC2 trong VPC, xác minh Public/Private hoạt động đúng như thiết kế; tổng kết kiến thức Module 02 phần cơ bản | |

### Kết quả đạt được tuần 2:
* Hiểu rõ và tự cấu hình được các thành phần cốt lõi của VPC: Subnet, Internet Gateway, Route Table, Security Group.
* Phân biệt được Public Subnet và Private Subnet, nắm cách định tuyến lưu lượng ra internet.
* Triển khai thành công EC2 trong VPC và dùng Instance Connect Endpoint để truy cập instance Private an toàn.
* Khắc phục được khó khăn ban đầu về nhầm lẫn chiều inbound/outbound của Security Group.
* Xây dựng được nền tảng mạng vững để tiếp cận các lab nâng cao hơn ở tuần sau.