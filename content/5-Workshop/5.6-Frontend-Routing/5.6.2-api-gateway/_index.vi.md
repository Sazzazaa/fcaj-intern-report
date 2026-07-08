---
title : "Cấu hình HTTPS với API Gateway"
date : 2026-07-06
weight : 2
chapter : false
pre : " <b> 5.6.2. </b> "
---

### Đưa backend EC2 ra ngoài bằng API Gateway

Frontend được deploy trên Amplify bằng HTTPS. Trong khi đó backend trên EC2 đang chạy HTTP port `8000`. Nếu gọi trực tiếp từ trình duyệt, rất dễ gặp lỗi **mixed content** hoặc khó quản lý domain công khai. Vì vậy ta đặt **HTTP API Gateway** phía trước backend.

#### 1. Kiểm tra request backend ở môi trường test

Trong quá trình test local, có thể dùng DevTools để kiểm tra request từ frontend tới backend EC2.

![Network request EC2](/images/5-Workshop/5.6-Frontend-Routing/z8014760739864_e165daf9d210725e62aca43dc5f544c9.jpg)

Ảnh trên cho thấy route `/projects` đang phản hồi từ backend chạy trên EC2 qua port `8000`.

#### 2. Tạo HTTP API

1. Mở **API Gateway**.
2. Tạo một **HTTP API** mới, ví dụ `project-management-api`.
3. Tạo integration kiểu **HTTP** trỏ tới:

```text
http://<ec2-public-host>:8000
```

4. Tạo route `$default` với method `ANY`.

![API Gateway integration](/images/5-Workshop/5.6-Frontend-Routing/z8015055837944_bd126c4ebb6fb08a2c95b7c33d772a56.jpg)

#### 3. Deploy stage mặc định

Tại phần **Stages**, dùng stage `$default` và bật **Automatic deployment**.

![API Gateway stage](/images/5-Workshop/5.6-Frontend-Routing/z8014993693598_79208f8b6748fc2c042d562bc54d4683.jpg)

Sau bước này, AWS sẽ cung cấp cho bạn một **Invoke URL** công khai, ví dụ:

```text
https://30o8modynj.execute-api.us-east-2.amazonaws.com
```

#### 4. Cập nhật frontend

Đặt lại biến môi trường:

```bash
NEXT_PUBLIC_API_BASE_URL=https://30o8modynj.execute-api.us-east-2.amazonaws.com
```

Rồi redeploy frontend trên Amplify. Từ thời điểm này, toàn bộ request API từ frontend sẽ đi qua API Gateway trước khi tới backend EC2.