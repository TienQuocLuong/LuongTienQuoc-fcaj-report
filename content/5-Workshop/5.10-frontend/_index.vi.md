---
title : "Giao diện Frontend"
date : 2024-01-01
weight : 10
chapter : false
pre : " <b> 5.10. </b> "
---

> **Lưu ý**: Nếu không dùng CloudFront + S3 Web UI thì có thể **bỏ qua toàn bộ mục này**. Nếu frontend host ở nơi khác (Vercel, Amplify, hoặc chạy local để demo), chỉ cần đảm bảo đã cập nhật đúng Invoke URL (mục 5.9) và Cognito App Client ID/Callback URL khớp domain thực tế đang dùng.

#### Giới thiệu

Đưa giao diện Dashboard lên S3 và phân phối qua CloudFront.


---

#### Phần 1: Cập nhật cấu hình và build Frontend

**Bước 1:** Mở source code React (Dashboard, đăng nhập, lịch sử test, xem báo cáo) trong VS Code (hoặc IDE tương đương).

**Bước 2:** Mở file cấu hình (ví dụ `src/config.js`), cập nhật:
```js
// ===== CẤU HÌNH AWS =====
// Cập nhật các giá trị này sau khi deploy lên AWS

export const API_BASE_URL = 'https://8bsb7jbhu7.execute-api.ap-southeast-1.amazonaws.com'

export const COGNITO_CONFIG = {
  region: 'ap-southeast-1',
  userPoolId: 'ap-southeast-1_DXMd3Q6ee',
  clientId: '492jkd32vd241c2tuv1v160g4o',
}
```
Trong đó `API_BASE_URL` là **Invoke URL** lấy ở mục 5.9, `userPoolId` và `clientId` lấy ở Cognito Console → User pool → App integration.

**Bước 3:** Kiểm tra các endpoint API bên dưới đã tự ghép đúng từ `API_BASE_URL`:
```js
// Các endpoint API
export const API_ENDPOINTS = {
  trigger:   `${API_BASE_URL}/trigger`,
  history:   `${API_BASE_URL}/history`,
  schedules: `${API_BASE_URL}/schedules`,
  reports:   `${API_BASE_URL}/reports`,
}
```

![Cấu hình config.js đã cập nhật Invoke URL và Cognito](/images/5-Workshop/5.10-Frontend/1-config-js-updated.png?featherlight=false&width=90pc)

**Bước 4:** Mở Terminal trong VS Code (hoặc terminal riêng), `cd` vào thư mục project Frontend, chạy lệnh:
```bash
npm run build
```

**Bước 5:** Chờ đến khi thấy dòng `✓ built in ...ms`, xác nhận thư mục `dist` được tạo ra với các file (`index.html`, `assets/index-xxxx.css`, `assets/index-xxxx.js`...), sẵn sàng upload lên S3.

![Build thành công, tạo thư mục dist](/images/5-Workshop/5.10-frontend/2-npm-build-success.png?featherlight=false&width=90pc)

---

#### Phần 2: Upload lên S3

**Bước 1:** Vào **S3 Console** → mở bucket `playwright-webui-xxx`.

**Bước 2:** Bấm nút **Upload**.

**Bước 3:** Bấm **Add files** để thêm `favicon.svg`, `icons.svg`, `index.html`; bấm **Add folder** để thêm folder `assets/` (chứa file `.css` và `.js` đã build). Xác nhận khung **Files and folders** hiển thị đủ **5 total** file (`index-xxxx.css`, `index-xxxx.js`, `favicon.svg`, `icons.svg`, `index.html`).

![Danh sách file sẵn sàng upload lên S3](/images/5-Workshop/5.10-Frontend/3-s3-upload-file-list.png?featherlight=false&width=90pc)

**Bước 4:** Kéo xuống cuối trang, bấm **Upload**, chờ tới khi hiện thông báo **"Upload succeeded"**.

---

#### Phần 3: Cấu hình Block Public Access

**Bước 1:** Vào bucket `playwright-webui-xxx` → tab **Permissions**.

**Bước 2:** Kéo xuống mục **Block public access (bucket settings)**, bấm **Edit**.

**Bước 3:** Giữ nguyên **tất cả 4 mục đều tick** (Block all public access = ON) — vì sẽ chỉ cho CloudFront truy cập qua Origin Access Control, không truy cập trực tiếp bucket.

**Bước 4:** Bấm **Save changes**, gõ `confirm` vào ô xác nhận, bấm **Confirm**.

---

#### Phần 4: Tạo CloudFront Distribution

**Bước 1:** Tại thanh tìm kiếm AWS Console, gõ `CloudFront`, chọn **CloudFront**.

**Bước 2:** Bấm nút cam **Create distribution**.

**Bước 3:** Origin domain: bấm vào ô, chọn bucket `playwright-webui-xxx.s3.ap-southeast-1.amazonaws.com` từ danh sách gợi ý.

**Bước 4:** Origin access: chọn **Origin access control settings (recommended)** → bấm **Create control setting** → giữ mặc định Signing behavior = **Sign requests (recommended)** → **Create**.

**Bước 5:** Kéo xuống mục **Default root object**, điền `index.html`.

**Bước 6:** Các mục còn lại (Price class, WAF...) giữ mặc định, có thể đặt Name tùy ý (ví dụ `playwright-cloudfront-123`). Bấm **Create distribution**.

**Bước 7:** Xác nhận thông báo **"Successfully created new distribution"** — ghi lại **Distribution domain name** (ví dụ `d2qnbza21ik9r.cloudfront.net`), lúc này **Last modified** sẽ hiển thị trạng thái **Deploying**.

![Distribution vừa tạo, trạng thái Deploying](/images/5-Workshop/5.10-Frontend/4-distribution-created.png?featherlight=false&width=90pc)

**Bước 8:** Sau khi tạo xong, CloudFront hiện banner màu vàng: **"The S3 bucket policy needs to be updated"** → bấm **Copy policy**.

**Bước 9:** Mở tab mới, vào lại **S3 bucket** `playwright-webui-xxx` → tab **Permissions** → kéo xuống **Bucket policy** → bấm **Edit** → paste policy vừa copy vào → **Save changes**.

**Bước 10:** Quay lại **Cognito Console** → User pool `playwright-user-pool` → **App integration** → App client `playwright-app` → **Edit** → cập nhật **Callback URL(s)** thành CloudFront Domain Name (thay cho `http://localhost:3000` tạm thời ở mục 5.9) → **Save changes**.

---

#### Phần 5: Lấy Domain Name và kiểm tra

**Bước 1:** Quay lại **CloudFront Console** → chọn Distribution vừa tạo.

**Bước 2:** Chờ cột **Status** chuyển từ **Deploying** sang **Enabled** (thường mất 3-5 phút).

**Bước 3:** Copy **Domain Name** hiển thị trên Console, dạng `dxxxxxxxxxxxxx.cloudfront.net`.

**Bước 4:** Mở Domain Name trên trình duyệt (tab ẩn danh để tránh cache), xác nhận Dashboard hiển thị đúng giao diện đăng nhập.

**Bước 5:** Thử truy cập trực tiếp URL S3 dạng `https://playwright-webui-xxx.s3.ap-southeast-1.amazonaws.com/index.html` — phải bị chặn, trả lỗi **403 Forbidden**.

---

#### Kiểm tra

- Mở Domain Name của CloudFront trên trình duyệt, Dashboard hiển thị đúng.
- Truy cập trực tiếp URL S3 bị chặn (403), phải qua CloudFront mới xem được.
- Đăng nhập thử bằng 1 trong 3 tài khoản test (Admin/QA/Developer) đã tạo ở mục 5.9, xác nhận đăng nhập thành công và gọi được API (không lỗi CORS/401).

**Ghi chú:** CloudFront cache nội dung — nếu sửa Frontend build lại và upload mới mà không thấy thay đổi, vào CloudFront Console → chọn Distribution → tab **Invalidations** → **Create invalidation** → Object paths điền `/*` → **Create invalidation**.