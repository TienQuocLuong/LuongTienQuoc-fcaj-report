---
title : "Lưu trữ & Cơ sở dữ liệu"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b> 5.3. </b> "
---

#### Tạo bảng DynamoDB lưu lịch sử test và log lỗi

Hệ thống dùng 2 bảng DynamoDB: một bảng lưu lịch sử mỗi lần chạy test, một bảng lưu lỗi hệ thống khi có message rơi vào Dead Letter Queue.

**Bước 1:** Truy cập **DynamoDB Console**.

![Truy cập DynamoDB Console](/images/5-Workshop/5.3-Data-Storage/1-access-dynamodb-console.png)

**Bước 2:** Bấm **Create table**.

![Bấm Create table](/images/5-Workshop/5.3-Data-Storage/2-create-table-button.png?featherlight=false&width=90pc)

**Bước 3:** Điền **Table name** = `playwright-test-history`.

**Bước 4:** Điền **Partition key** = `task_id`, kiểu **String**.

![Tạo bảng playwright-test-history](/images/5-Workshop/5.3-Data-Storage/3-create-test-history-table.png)

**Bước 5:** Các cài đặt khác để mặc định, bấm **Create table**.

![Create table playwright-test-history](/images/5-Workshop/5.3-Data-Storage/4-create-test-history-table.png)

**Bước 6:** Bấm **Create table** một lần nữa để tạo bảng thứ hai.

**Bước 7:** Điền **Table name** = `playwright-error-log`.

**Bước 8:** Điền **Partition key** = `error_id`, kiểu **String**.

![Tạo bảng playwright-error-log](/images/5-Workshop/5.3-Data-Storage/5-create-error-log-table.png?featherlight=false&width=90pc)

**Bước 9:** Bấm **Create table**.

![Create table playwright-error-log](/images/5-Workshop/5.3-Data-Storage/6-create-error-log-table.png?featherlight=false&width=90pc)

**Bước 10:** Chờ cả 2 bảng chuyển trạng thái sang **Active**.

![Cả hai bảng ở trạng thái Active](/images/5-Workshop/5.3-Data-Storage/7-tables-active.png?featherlight=false&width=90pc)

*(Ghi chú: Không cần tạo thêm field nào khác như `target_url`, `status`, `report_url`... — DynamoDB là NoSQL, tự nhận field khi ứng dụng ghi dữ liệu vào, không cần khai báo schema cứng trước.)*

#### Schema chi tiết

**Bảng `playwright-test-history`**

| Field | Type | Mô tả |
|---|---|---|
| task_id | String | Partition Key |
| target_url | String | URL cần test |
| test_script | String | Tên kịch bản test |
| status | String | running / success / failed |
| triggered_by | String | manual / schedule |
| started_at | String | ISO datetime |
| finished_at | String | ISO datetime |
| report_url | String | S3 Presigned URL tới báo cáo |
| ai_summary | String | Tóm tắt lỗi do AI sinh ra |

**Bảng `playwright-error-log`**

| Field | Type | Mô tả |
|---|---|---|
| error_id | String | Partition Key |
| original_message_id | String | MessageId gốc từ SQS |
| message_body | String | Nội dung message gốc |
| error_message | String | Nội dung lỗi nếu có |
| timestamp | String | ISO datetime |

#### Cấp quyền cho container Fargate ghi trực tiếp vào DynamoDB

Vì container Fargate tự ghi trạng thái `running/success/failed` trực tiếp vào bảng `playwright-test-history` (không qua Lambda), cần cấp thêm quyền cho Task Role.

**Bước 11:** Mở **IAM Console**, tìm role `playwright-ecs-task-role`.

![tìm role `playwright-ecs-task-role](/images/5-Workshop/5.3-Data-Storage/8-search-playwright-ecs-task-role.png?featherlight=false&width=90pc)

**Bước 12:** Bấm **Add permissions → Create inline policy**.

![Tạo inline policy](/images/5-Workshop/5.3-Data-Storage/9-create-inline-policy.png?featherlight=false&width=90pc)

**Bước 13:** Chọn tab **JSON**, dán nội dung sau:
```json
{
  "Version": "2012-10-17",
  "Statement": [{
    "Effect": "Allow",
    "Action": ["dynamodb:PutItem", "dynamodb:UpdateItem"],
    "Resource": "arn:aws:dynamodb:ap-southeast-1:<account-id>:table/playwright-test-history"
  }]
}
```

**Bước 14:** Thay `<account-id>` bằng Account ID thật (12 chữ số, xem ở góc trên phải Console).

**Bước 15:** Đặt tên policy, ví dụ `SecretsManagerReadWrite`, bấm **Create policy**.

![Policy đã được gắn vào role](/images/5-Workshop/5.3-Data-Storage/10-inline-policy-attached.png?featherlight=false&width=90pc)

#### Kiểm tra

- 2 bảng ở trạng thái **Active** trên Console.
- `playwright-ecs-task-role` hiển thị inline policy `SecretsManagerReadWrite` trong tab Permissions.
- Sau khi chạy thử 1 test: vào bảng `playwright-test-history` → tab **Explore table items** → thấy bản ghi có đủ `status`, `report_url`, `ai_summary`.