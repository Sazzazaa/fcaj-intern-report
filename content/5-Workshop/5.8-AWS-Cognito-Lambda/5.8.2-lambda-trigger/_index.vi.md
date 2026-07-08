---
title : "Viết AWS Lambda Trigger"
date : 2026-07-07
weight : 2
chapter : false
pre : " <b> 5.8.2. </b> "
---

### Đồng bộ người dùng Cognito về cơ sở dữ liệu ứng dụng

Trong dự án này, bảng `User` của backend có trường `cognitoId` là khóa định danh duy nhất. Vì vậy sau khi một tài khoản được xác thực thành công trên Cognito, ta nên tự động tạo bản ghi tương ứng trong PostgreSQL.

#### 1. Vì sao cần Lambda Trigger

Backend hiện có route:

```text
POST /users
```

và controller `postUser` nhận các trường chính:

* `username`
* `cognitoId`
* `profilePictureUrl`
* `teamId`

Lambda Trigger giúp tự động gọi logic này ngay khi user xác nhận tài khoản, thay vì phải tạo tay.

#### 2. Chọn đúng loại trigger

Trong Cognito User Pool, gắn Lambda vào trigger:

* **Post Confirmation**

Đây là thời điểm phù hợp nhất vì người dùng đã hoàn tất email verification và Cognito đã cấp `sub`.

#### 3. Luồng xử lý gợi ý

Lambda có thể lấy dữ liệu từ event của Cognito:

* `event.userName`
* `event.request.userAttributes.sub`
* `event.request.userAttributes.email`

Sau đó:

1. tạo payload user mới,
2. gọi backend API `/users` hoặc logic ghi DB tương đương,
3. trả lại `event`.

#### 4. Lưu ý khi triển khai thật

* Nếu API Gateway đã gắn authorizer, hãy chừa một route phù hợp cho Lambda hoặc cấu hình cách xác thực riêng cho service-to-service call.
* Nên ghi log CloudWatch để dễ debug khi việc tạo user ở DB thất bại.
* Nên thêm kiểm tra trùng `cognitoId` để tránh tạo lặp dữ liệu.