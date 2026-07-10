---
title : "Bảo mật & Thông báo"
date : 2024-01-01
weight : 8
chapter : false
pre : " <b> 5.8. </b> "
---

#### Tạo Secrets cho OpenAI API Key (Công Vũ)



---

#### Tạo Secrets cho Test Credentials (Công Vũ / Văn Phúc)



---

#### Verify email trên SES (Tiến Quốc)

**Bước 1:** Truy cập **SES Console** → menu bên trái chọn **Verified identities**.

**Bước 2:** Bấm **Create identity**.

**Bước 3:** Chọn loại Identity = **Email address**.

**Bước 4:** Điền địa chỉ email dùng để gửi báo cáo.

![Tạo Verified Identity trên SES](/images/5-Workshop/5.8-Security-Notification/3-create-ses-identity.png?featherlight=false&width=90pc)

**Bước 5:** Bấm **Create identity**.

**Bước 6:** Mở hộp thư email vừa điền, tìm email từ AWS chứa link xác nhận.

**Bước 7:** Bấm vào link **Verify** trong email đó.

**Bước 8:** Quay lại SES Console, refresh trang, kiểm tra trạng thái email chuyển thành **Verified**.

![Email đã Verified](/images/5-Workshop/5.8-Security-Notification/4-email-verified.png?featherlight=false&width=90pc)

---

#### Test gửi email (Tiến Quốc)

**Bước 1:** Vẫn ở trang identity đó, bấm nút **Send test email**.

**Bước 2:** Điền From address = email vừa verify.

**Bước 3:** Điền To address = 1 email đã verify khác (hoặc chính email đó nếu chỉ có 1).

**Bước 4:** Điền Subject và nội dung Body bất kỳ.

![Gửi test email từ SES](/images/5-Workshop/5.8-Security-Notification/5-send-test-email.png?featherlight=false&width=90pc)

**Bước 5:** Bấm **Send test email**.

**Bước 6:** Mở hộp thư To address, xác nhận đã nhận được email test.

---

#### Cấu hình biến môi trường cho Lambda gửi email (Tiến Quốc)

**Bước 1:** Vào **Lambda Console**, mở function `playwright-postprocessing`.

**Bước 2:** Tab **Configuration → Environment variables**, thêm biến `SES_SENDER_EMAIL` = email đã verify ở Bước 4 (phần Verify email).

**Bước 3:** Kiểm tra role `playwright-lambda-role` đã có policy `AmazonSESFullAccess` (nếu chưa, vào IAM → role đó → Add permissions → attach `AmazonSESFullAccess`).

---

#### Request Production Access (Tiến Quốc)

**Bước 1:** Vào **SES Console → Account dashboard**.

**Bước 2:** Bấm **Request production access**.

**Bước 3:** Điền form use case, submit, chờ AWS duyệt.

*(Ghi chú: SES mặc định ở chế độ Sandbox, chỉ gửi được đến email đã verify. Nên request Production Access sớm từ đầu workshop, đừng để sát ngày demo.)*

---

#### Kiểm tra

- Cả 2 secret (`openai-api-key` và `test-credentials`) hiển thị đúng trên Secrets Manager Console.
- Email hiển thị trạng thái **Verified** trên SES Console.
- Gửi test email từ Console → nhận được trong hộp thư.
- Trigger 1 test thật qua hệ thống → sau khi Lambda Post-processing chạy xong, kiểm tra hộp thư nhận được email báo cáo tự động.