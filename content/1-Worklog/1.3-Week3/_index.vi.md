---
title: "Worklog Tuần 3"
date: 2026-05-01
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Mục tiêu tuần:
Học các lab nâng cao của Module 02 (DNS Resolution, VPC Peering). Do phần mạng khá khó nên chỉ tập trung một vài lab cốt lõi và làm thật kỹ.

### Công việc thực hiện trong tuần:
| Thứ | Ngày | Công việc | Nguồn tài liệu |
|---|---|---|---|
| Thứ Sáu | 01/05/2026 | Xem hướng dẫn Lab 10 (DNS Resolution) và Lab 19 (VPC Peering); ghi chú các bước và điều kiện chuẩn bị trước khi thực hành | https://www.youtube.com/watch?v=HACor1gL3ww&list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i&index=50  https://www.youtube.com/watch?v=sllYqAECBoM&list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i&index=56|
| Thứ Bảy | 02/05/2026 | Xem lại kỹ hai lab, tìm hiểu trước về Route53 Resolver, Inbound Endpoint và Private Hosted Zone để không bị bỡ ngỡ khi làm | |
| Chủ Nhật | 03/05/2026 | Bắt đầu thực hành Lab 10; template CloudFormation mẫu triển khai bị lỗi nên phải nghiên cứu cách tạo Inbound Endpoint thủ công thay vì dùng script sẵn | https://www.youtube.com/watch?v=EQ-5P6U7Ph4&list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i&index=47 |
| Thứ Hai | 04/05/2026 | Tiếp tục Lab 10: cấu hình Private Hosted Zone và liên kết với VPC để hoàn thành phần phân giải DNS nội bộ | https://www.youtube.com/watch?v=HACor1gL3ww&list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i&index=50 |
| Thứ Ba | 05/05/2026 | Hoàn thành Lab 10; đọc thêm tài liệu để hiểu rõ toàn bộ luồng phân giải tên miền nội bộ trong VPC hoạt động như thế nào |  |
| Thứ Tư | 06/05/2026 | Thực hành Lab 19 (VPC Peering): gặp lỗi hai EC2 ở hai VPC không ping được nhau, dùng công cụ traceroute để lần theo và phát hiện lỗi ở Route Table, sau đó sửa lại và kết nối thành công | https://www.youtube.com/watch?v=sllYqAECBoM&list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i&index=56 |
| Thứ Năm | 07/05/2026 | Ôn lại toàn bộ phần mạng đã học; cân nhắc tiến độ và quyết định tạm gác Lab 20 (Transit Gateway) để dành thời gian cho các module sau | |

### Kết quả đạt được tuần 3:
* Hoàn thành Lab 10 (DNS Resolution) và Lab 19 (VPC Peering).
* Tự xử lý được sự cố khi template CloudFormation lỗi bằng cách cấu hình thủ công Inbound Endpoint và Private Hosted Zone.
* Hiểu được cơ chế phân giải DNS nội bộ trong VPC.
* Biết cách dùng traceroute để chẩn đoán và khắc phục lỗi định tuyến trong VPC Peering.
* Rèn được kỹ năng tự tra cứu, xử lý lỗi khi gặp tình huống không theo đúng hướng dẫn mẫu.